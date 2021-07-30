# Robotics-Software-Standards
### Guidelines for writing code and commiting to an active repository. 
## General Rules:
 * Use consistent ***indentation*** amongst all src files.

 * Avoid unecessary use of ***Globals***.

 * Use ***verbs*** for function names and ***nouns*** for classes and attributes.
 ```
class Product {

    private $price;
    public function increasePrice($dollarsToAddToPrice){
        $this->price += $dollarsToAddToPrice;
    }
}
 ```
 
 * Add some sort of ***data logging system*** for debug and implement a flush cycle. 

 * Use proper convetions for creating ***file structure*** and keep a clean root. 

 * No hard coded ***file paths***, assume different PC's will have different file structs (use argument parsers if possible). 
 
 * Keep fuction sizing small.


## ROS:
* Define an iterface that includes publishers and subcribers with a block diagrams for all embedded classes.

* ROS Documentation built into Scripts



## Version Control:
* Always start a fresh repository with a ***README*** document, which should be updated as the repository grows.

* Avoid making changes directly to the ***Main Branch*** of a repository. 

* Always create a new ***Development Branch*** with an appropirate name to test out your code. 

* Commit your changes often and use descriptive ***Commit Messages*** for future reference. 

* Before merging branches a ***Code Review*** should be initiated in the form of a ***pull request***, after the review has concluded and changes have been made; proceed to ***squash & merge***. 

## C++ Rules:
* Do not directly compile src files, instead use a ***makefile*** to invoke compilition.

* Use ***Clang*** formatter on all source files.
```
# In a terminal navigate to the source directory 
cd /Dir/src/main.cpp

# Run the clang formatter on the target source file  
clang-format -i main.cpp
```

* Use multiline comments for ***Class*** specifications. 
```
/**
* GPS holds helper methods and computation functions for GPS based localization.
* Methods:
* ---------- 
* get_current_location()
*    Returns two floating point values representing current Latitude and Longitude of the robot.
*
* get_corrected_position()
*    Returns corrected robot poisiton based on a fusion of other calibrated sensors (i.e encoder, magnetometer) in the form of Latitude and Longitude.
*/
class MyClass{
} 
```

* Use multiline comments for ***Method*** specifications.
```
/**
 * Sum numbers in a vector.
 *
 * @param values Container whose values are summed.
 * @return sum of `values`, or 0.0 if `values` is empty.
 */
double sum(std::vector<double> & const values) { 
}
```


## Python Rules: 
* Include ***Shebang*** to allow script to be run like a standale executable. 
```
# For Python 3 use:
#!/usr/bin/env python3

# For Python 2 use:
#!/usr/bin/env python2

# For compatibility with Python 2 & 3 use:
#!/usr/bin/env python
```

* Follow [Pep-8 Format](https://pep8.org/) or use an [Auto-PEP](https://marketplace.visualstudio.com/items?itemName=himanoa.Python-autopep8) formatter in your ***IDE***. 

* Use DocStrings for ***Class*** specifications. 
```
"""
GPS holds helper methods and computation functions for GPS based localization.
Methods:
----------
get_current_location()
    Returns two floating point values representing current Latitude and Longitude of the robot.
get_corrected_position()
    Returns corrected robot poisiton based on a fusion of other calibrated sensors (i.e encoder, magnetometer) in the form of Latitude and Longitude.
"""
class GPS:
```

* Use DocStrings for ***Method*** specifications. 
```
"""
Definition
----------
Function to return the floating point sum of two integers.

Parameters
----------
a : First number to sum (int)  
b : Second number to sum (int)  

Returns
----------
c : Sum of int a & int b casted as a floating point number (float) 
"""
def sum (a, b):
    c = float (a + b)
    return c
```

* All main Python scripts should use a ***dunder*** to prevent accidental script [invocation](https://stackoverflow.com/questions/419163/what-does-if-name-main-do). 
```
# Example Main.py script

def main():
    print("Hello World!")

if __name__ == '__main__':
    main()
```

* Use ***Profilehooks*** and or ***Time*** module for Profiling function calls to optimize code.
```
# To use Profilehooks import the module and run it on a 
# function by using the decorator @profile

from profilehooks import profile

@profile
def my_function(args, etc):
    pass
``` 
```
# To profile a function call or any other block of code import
# the time module and wrap the code within two time calls 
# then proceed to print the results

import time

start = time.time()
# The function call you want to profile
end = time.time()
print("Execution Time:", end - start)
```