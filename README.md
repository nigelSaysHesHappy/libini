# libini
Read and write Windows style INI files

# Usage

```cpp
#include <string>
#include <iostream>
#include "libini.h"

int main()
{
    INIObject config ("settings.conf");
    
    std::cout<<config("user","name")<<": \n";
    std::cout<<"Info: "<<config("user","info")<<'\n';
    
    std::cout<<"Input favorite pizza for "<<config("user","name")<<": ";
    
    std::string favPizza;
    std::cin>>favPizza;
    
    config("user","pizza") = favPizza;
    
    std::cout<<std::endl;
    
    std::cout<<"Save current config? "<<std::endl;
    
    char answer;
    std::cin>>answer;
    
    if (answer == 'y')
    {
        config.write("settings.conf");
        std::cout<<"Saved to \"settings.conf\" . . ."<<std::endl;
    }
    
    return 0;
}
```

You can also use the `skipItem` and `skipTopic` arguments when a file will have multiple items/topics of the same name.

