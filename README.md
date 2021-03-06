# Hikers_Bridges
A tool to solve the night crossing hikers of multiple bridges.
Each hiker has speed measured in feet/minute. Each bridge has length in feet. 
There is one torsh and each bridge can only take two hikers at a time.
The idea is to use YAML files to describe the problem and do code performance measurement.


We used yaml-cpp lib: https://github.com/jbeder/yaml-cpp/ to create a YAML file parser to describe the problem (there are examples YAML files).
The tool get the minimum cross time per bridge and total cross time for all bridges.

Note: 
	Please install yaml-cpp library to be able to compile this tool.

We have two ways to evaluate the solutions:
    1- Use priority queue to keep track of the fastest hiker.
    2- Just use STL std::max_element() to get the fastest hiker.

We used a generic Timer (included in the src) to measure the performance.
For the same file, we see that method #2 is better in terms of time (63 msec compared to 288 msec for the priority queue).

Example to parse file:
	./v1 myFirst.yaml

We also created a tool to generate these YAML files.

Here how to use it:

 - To generate a YAML file with these properties (using random numbers)
	./v1 -b <n# bridges> -k <max n# hikers> -l <max bridge len> -s <max hikers speed> -f <file name> -r <rand seed>,
 
Example to generate file:
	./v1 -b 5 -k 4 -l 500 -s 26 -f myFirst.yaml -r 12345


To get help: 
	./v1 or ./v1 -help or ./v1 -h --> to generate this help message

Notes: 
	 - At the end of each run we print how much time used to run the program.
	 - We do not support negative or zero bridge lengths nor negative or zero hikers speeds.
	 - We support both Linux (tested) and Windows devlopment (testeing ongoing).