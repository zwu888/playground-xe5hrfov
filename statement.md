# 
```C++ runnable
#include <iostream>

class Singleton
{
private:

    Singleton();
    ~Singleton();  

public:

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
}


int main()
{
    MyFunction();
    return 0;
}
