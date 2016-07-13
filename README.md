# **Tri**angle**Fin**der
A small piece of JAVA code that determines type of triangles and provides guidelines to divide and conquer complex real world problems.

# **TriFin**
 **Tri**angle**Fin**der (**TriFin**) is a small JAVA application that detects three types of triangles i.e.  Equilateral, isosceles and scalene.  The major purpose of this application is to explain: 

*	How to formulate and solve a real world problem in modern programming language.
*	How to overcome a complex problem by dividing it into smaller and easier to solve tasks. 
*	To provide some coding guidelines to write programmer –friendly code, i.e.  Comprehensible, extensible and reusable code.
*	To explain some features of OOP paradigm using JAVA.
*	How to write unit tests, integration tests and use build automation tool such as Maven. 

## Installation
The application requires [JRE]( http://www.oracle.com/technetwork/java/javase/downloads/jre8-downloads-2133155.html) to be run and [Java SE Development Kit]( http://www.oracle.com/technetwork/java/javase/downloads/index.html) along with any editor for code editing such as [Eclipse] (http://www.eclipse.org/downloads/packages/eclipse-ide-java-developers/keplersr1), [NetBeans]( https://netbeans.org/features/java/) or [IntelliJ IDEA]( https://www.jetbrains.com/idea/). You can also edit the code in the default editor of your operating system.  To build the application you need to have [Apache Maven]( https://maven.apache.org/download.cgi) (required) for any further testing [Junit]( http://junit.org/junit4/), [Mockito]( http://mockito.org/) or [TestNG](http://testng.org/doc/index.html) can be used. 

## Application Core
The core application logic is based on following classes; each class solves an important piece of the puzzle, i.e. original problem.

*	**TriangleMeasurementValidator:** Examines the validity/legitimacy of the arguments provided to determine the triangle.
* **TriangleTypeDetectionController:** Makes use of triangleTypeDetectionService implementation to determine the type of triangle and TriangleDto class used as a [Data Transfer Object](https://en.wikipedia.org/wiki/Data_transfer_object) to cut the Inter Process communication/transmission cost. 
*	**TriangleTypeDetectionServiceImpl:** Implements riangleTypeDetectionService and returns the triangle type.
*	**Driver:**	Main application class that contains main() and wires all components of the application together.

##Tests: 
Unit tests are performed on all major classes i.e. TriangleTypeDetectionController, TriangleMeasurementValidator and TriangleTypeDetectionServiceImpl. 

## Usage
To run the application, you need to clone the repository, unzip it, and then keeping the repository as a root type and run:  *mvn clean install exec:java*

You need to specify triangle side measurements using command line arguments. 
Example:   *mvn clean install exec:java -Dside1.length=20.0 -Dside2.length=20.0 -Dside3.length=30.0*


## Credits 
To [James Gosling]( https://www.linkedin.com/in/jamesgosling) and fellows for developing [world’s most popular programming language](http://www.tiobe.com/tiobe_index). 




