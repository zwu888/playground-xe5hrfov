# 
```C++ runnable
#include <iostream>

class Singleton
{
private:

    Singleton();
    ~Singleton();  

public:
    Singleton(const Singleton&) = delete;
    Singleton(Singleton&&) = delete;
    Singleton& operator=(const Singleton&) = delete;
    Singleton& operator=(Singleton&&) = delete;

    static Singleton& instance()
    {
        static Singleton INSTANCE;
        return INSTANCE;
    }

    void Test();
};

void Singleton::Test()
{
    std::cout << "Test() called" << std::endl;
}

Singleton::Singleton()
{
    std::cout << "CONSTRUCTOR CALLED" << std::endl;
}

Singleton::~Singleton()
{
    std::cout << "DESTRUCTOR CALLED" << std::endl;
}

void MyFunction()
{
    // use the singleton class
    Singleton * MySingleton = &Singleton::instance(); 
    
    MySingleton->Test();
    std::cout << MySingleton << std::endl;
    MySingleton = nullptr;
}


struct Test 
{
    Test():ins(&Singleton::instance()) 
    {
        std::cout << "Test ctor" << std::endl;
    }
    ~Test() 
    { 
        std::cout << "Test dtor" << std::endl;
        //ins = nullptr;
    }
    Singleton* ins;
};

int main()
{
    Test tt;
    //MyFunction();
    
    return 0;
}
