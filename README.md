_Course Project of CS474: Object-Oriented Languages and Environments_
======================================================================

_Instructor_

[Dr. Mark Grechanik](https://www.cs.uic.edu/k-teacher/mark-grechanik-phd/)

_Team Members_

    •	 Gautam: gautam5@uic.edu
    •	 Sachin Mathew: smathe37@uic.edu
    •	 Pratyush Bagaria: pbagar2@uic.edu
    •	 Pavan Bharadwaj Holenarasipura: pholen2@uic.edu


_**1. Overview**_

Aim of this project was to build compile time error free code for java language. Production rules for which is specified in a configuration file along with certain constraints. Using these production rules and constraints for each cases we build a random java program. We have considered all basic production rules in java along with advanced rules of interfaces, inheritance and recurssion. 


_**2. Implementation Description**_

All the production rules and constraints are defined in the configuration file named 'config'. The application reads this configuration file and adds the incoming data into the memory. 'FileRead' Package reads configuration file line by line and all the data is stored into the memory using the package named 'Data'. Then using 'Generator' package we create the tree whose leaves when traversed left to right will give final output. 'FileWriter' Package finally creates and writes the code in the proper file with correct file name (i.e. name of the file will be same as the name of the public class generated randomly during application execution) and appropriate file extension. Details on these packages below-

•	 'FileRead' package - It reads all the production rules one by one until it reaches the end of the file. After reading the first production rule, it is first splitted in two parts LHS and RHS based on the separator ":=". We use Hash Map and Vector to store these rules. LHS forms the key value in the hash map. RHS part of the production rule is again splitted on the basis of separator "|" and each value is stored in a vector. Its upper and lower bound is noted and is made as the value of key in the hash map. For the following example producction rule, "production:=expression1|expression2|expression3" we will have <Key, value> = <production, 0-2> where 0-2 represent range of values or lower and upper bound of the vector where the RHS part is stored. Data structure of 'Vector' is chosen to store the RHS part because vector grows dynamically and the number of rules associated with any non terminal expression is unknown or varies. 

•	 'Data' Package - All the data needed for code generation and processed from the configuration file is stored using static variables. 

•	 'Generator' Package - Interfaces and Methods are created based on the contraints which is done using 'InterfaceGenerator' and 'Method_Generator'. 'RandomGenerator' helps in creating a random number which is supposed to be used further. It is instantiated in 'InterfaceGenerator', 'Method_Generator' and 'MainGenerator'. 'MainGenerator' creates the main method of the required java program.


_**3. About the Random Java Program generated**_

    •	 Final random java program generated will have exactly one public class.
    •	 Contains Generic class and interfaces with default methods.
    •	 Application may or may not choose to inherit classes.
    •	 Random number of classes will be present which ranges from min and max classes constraint in the config file.
    •	 Either of these or all can be found in the final program generated using this application; Field declarations, Conditional statements, Loop statements etc.
    •	 Minimum 1 method will be there for each class while maximum number of methods depends on the max value in the 'config' file. The max value is randomly computed with upper limit in the config file.
    
_**4. Execution Steps**_

A. using gradle build

	1. Traverse to the directory, where the Project is present.
	2. From the Command prompt run ./gradlew build.
	3. Run ./gradlew run.
	4. Run ./gradlew Test

B. using sbt build

	1. From Command Prompt
			a. Navigate to the directory where the project is located
			b. Open the Command prompt Run - sbt compile
			c. Run - sbt run

	2. From Sbt Shell
			a. compile
			b. run

_**5. Foot Notes**_

The random java program which is syntactically correct but semantically meaningless as desired can be located in the directory '/out/' after successful execution. JUnit tests are also included.