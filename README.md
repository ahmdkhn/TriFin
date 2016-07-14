# **Tri**angle**Fin**der
A small piece of JAVA code that determines type of triangles and provides guidelines to divide and conquer complex real world problems.

# **TriFin**
 **Tri**angle**Fin**der (**TriFin**) is a small JAVA application that detects three types of triangles i.e.  Equilateral, isosceles and scalene.  The major purpose of this application is to explain: 

*	How to formulate and solve a real world problem in modern programming language.
*	How to overcome a complex problem by dividing it into smaller and easier to solve tasks. 
*	To provide some coding guidelines to write programmer–friendly code following the modern design patterns, i.e. Comprehensible, extensible and reusable code.
*	To explain some features of OOP paradigm using JAVA.
*	How to write unit tests, integration tests and use build automation tool such as Maven. 

The core design decisions and logic behind the entire application is as follows:

## Design Decision-1
**Use of MVC**: MVC is chosen as the base design framework. Generally, MVC is more suitable for large scale web applications to enforce "Separation of concerns", as loosely coupled code is more manageble and and extensible.


##Implementation Details
**Use of TriangleDto as Model**: In this example, there is no need to separate Model or Data Transfer Object classes . However, in real world implementations it is a recommended prcatice to separate objects for all the entities to be used in data layer, domain object to be used in business layer and DTO to be used for transfering information in or out of application. In this example TriangleTypeDetectionController is used as a Controller and TriangleTypeDetectionService is used as Business Service interface. Code can work with any implementation of TriangleTypeDetectionService. View in this application is "main" method in main.Driver class.

##Design Decision-2
**Use of Dependecy Injection**: Secondly, I decided to choose depedency injection pattern, so all the depedencies must be provided externally and dependency creation code must lie outside of the controller. This makes code easy to maintain and reusable. For example, pluging in a new implementation of Business service in controller class can be done easily even without looking into Controller class (Although I have a bad habit of always looking inside, which theoritically does not make sense). 

##Implemenation Details:
main.Driver class initializes and provides all the dependencies on need basis. 

## Design Decision-3##
**Use Interfaces**: Always tie the code with Business Service Interface instead of implementation. This is for high usability plus some advance frameworks can be used to generate proxy implementations on the fly for easy testing and mocking. 

##Implemenation Details##
Interface is TriangleTypeDetectionService and implementation is TriangleTypeDetectionServiceImpl. Code is not coupled to the implementation but to the the interface.

##Design Decision-4##
**Triangle Domain Object must be Immutable**: Triangle Domain Object should be extensible and immutable. Usually, In real world, often the requirment is immutable classes should not be inhertied. However, in this case I intentionally left it extensible, (it can be inherrited and child implementation may choose to compromise immuatable behavior). This is because if it is going to be used for some user drawing application then triangle object being immutable will be a short coming.

##Implementation Details:##
TriangleDto does not implement any setters to mimic immutable behavior. However, it is not final and thus extensible. Although I am not a big fan of inheritting DTOs.

##Design Decision-5##
Integration tests for Controllers are carreid out. 

##Implemenation Details##
TriangleTypeDetectionControllerTest class covers all the integration tests required for the controller.  

##Design Decision-6
Business Service must thoroughly be tested against business requirements.

##Implementation Details##
With cyclomatic complexity of 3, all paths in TriangleTypeDetectionServiceImpl are tested in TriangleTypeDetectionControllerTest class.

## Design Decision-7##
Controller must not be polluted by Validation Logic.

##Implementation Details##
TriangleMeasurementValidator class contains the validation code and validation is done outside contoller in main.Driver class. Generally it is recommended to use external framweorks for validation.

##Some Lazinesses##
I created the object of immutable DTO inside controller. Generally it is good to create a factory in such cases or use of an external mapper library, however, in the context of this small task application, I considered it an overkill.

## Usage##
To run the application, you need to clone the repository, unzip it, and then keeping the repository as a root type and run:  *mvn clean install exec:java*

You need to specify triangle side measurements using command line arguments. 
Example:   *mvn clean install exec:java -Dside1.length=20.0 -Dside2.length=20.0 -Dside3.length=30.0*


## Credits 
To [James Gosling]( https://www.linkedin.com/in/jamesgosling) and fellows for developing [world’s most popular programming language](http://www.tiobe.com/tiobe_index). 




