# Robotics-Software-Standards

## General Rules:
 * Avoid unecessary use of Globals 
 * Add some sort of data logging system for debug and implement a flush cycle 
 * Use proper convetions for creating source files, clean root 
 * No hard coded file paths, assume different PC's will have different file structs (use Argeparse if possible)
 * 

## C++ Rules:
* Makefiles

* Use Clang formatter 

## Python Rules: 
* Include shebang to allow script to be run like a standale executable. 
```
# For Python 3 use:
#!/usr/bin/env python3

# For Python 2 use:
#!/usr/bin/env python2

# For compatibility with Python 2 & 3 use:
#!/usr/bin/env python
```

* Follow [Pep-8 Format](https://pep8.org/) or use an [Auto-PEP](https://marketplace.visualstudio.com/items?itemName=himanoa.Python-autopep8) Formatter in your IDE. 

* Use DocStrings for Class specifications. 
```
 """
    RotationCalculator holds helper methods and computation functions for performing
    point data manipulation. Most functions operate on unit blocks of size 256
    Methods
    ----------
    get_spatial_reordering()
        Returns an array with indices from 0-255 of beam & beamlet indices oriented in freespace.
    get_local_angles()
        Returns a matrix of baseline spatial offsets for theta and phi for each set of 256 points
    """
```

* Use DocStrings for Function specifications. 
```
def sum (a, b):
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

        c = float (a + b)
        return c
```

* All main Python scripts should use a dunder to prevent accidental script [invocation](https://stackoverflow.com/questions/419163/what-does-if-name-main-do). 
```
def main():
    print("Hello World!")

if __name__ == '__main__':
    main()
```

* Use Profilehooks and or Time module for Profiling function calls to optimize code.
```
# To use Profilehooks import the module and run it on a 
# function by using the decorator @profile

from profilehooks import profile

@profile
def my_function(args, etc):
    pass
``` 
```
# To prifile a function call or any other block of code import
# the time module and wrap the code within two time calls 
# then proceed to print the results

import time

start = time.time()
# The function call you want to profile
end = time.time()
print("Execution Time:", end - start)
```