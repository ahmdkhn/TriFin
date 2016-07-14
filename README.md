# **Tri**angle**Fin**der
A small piece of JAVA code that determines type of triangles and provides guidelines to divide and conquer complex real world problems.

# **TriFin**
 **Tri**angle**Fin**der (**TriFin**) is a small JAVA application that detects three types of triangles i.e.  Equilateral, isosceles and scalene.  The major purpose of this application is to explain: 

*	How to formulate and solve a real world problem in modern programming language.
*	How to overcome a complex problem by dividing it into smaller and easier to solve tasks. 
*	To provide some coding guidelines to write programmer–friendly code following themodern design pattaerns, i.e.  Comprehensible, extensible and reusable code.
*	To explain some features of OOP paradigm using JAVA.
*	How to write unit tests, integration tests and use build automation tool such as Maven. 

The core design decisions and logic behind the entire application is as follows:

## Design Decision-1## 
**Use of MVC**: I chose MVC to be the base design framework. This is ideally suited for web applications but the benefits still hold in this case, for example "Separation of concern" and loosely coupled code.


##Implementation Details##
**Use of TriangleDto as Model**: In this example, I do not see need for separate model or Data Transfer Object classes . However, in real world implementations I always recommend creating separate objects for all 3 entities to be used in data layer, domain object to be used in business layer and DTO to be used for transfering information in or out of application.

##TriangleTypeDetectionController as Controller##
Business Service interface is TriangleTypeDetectionService. Code can work with any implementation of TriangleTypeDetectionService. View in this application is "main" method in main.Driver class.

##Design Decision-2##
**Use of Dependecy Injection**: Secondly, I decided to choose depedency injection pattern, so all the depedencies must be provided externally and dependency creation code must lie outside of the controller. This makes code easy to maintain and reusable. For example, pluging in a new implementation of Business service in controller class can be done easily even without looking into Controller class (Although I have a bad habit of always looking 
inside, which theoritically doesnot make sense). 

##Implemenation Details##:
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
Integration tests for Controllers are carreid out. Unit tests are performed on all major classes i.e. TriangleTypeDetectionController, TriangleMeasurementValidator and TriangleTypeDetectionServiceImpl. 

##Implemenation Details##
TriangleTypeDetectionControllerTest class covers all integration tests for our controller.

##Design Decision-6## 
Business Service must thoroughly be tested against business requirements.

##Implementation Details##
With cyclomatic complexity of 3, all paths in TriangleTypeDetectionServiceImpl are tested in TriangleTypeDetectionControllerTest class.

## Design Decision-7##
Controller must not be polluted by Validation Logic.

##Implementation Details##
TriangleMeasurementValidator class contains the validation code and validation is done outside contoller in main.Driver class. Generally I use external framweorks for validation.

##Some Lazinesses##
I created the object of immutable DTO inside controller. Generally it is good to create a factory in such cases or use of an external mapper library, however, in the context of this small task application, I considered it an overkill.

## Usage##
To run the application, you need to clone the repository, unzip it, and then keeping the repository as a root type and run:  *mvn clean install exec:java*

You need to specify triangle side measurements using command line arguments. 
Example:   *mvn clean install exec:java -Dside1.length=20.0 -Dside2.length=20.0 -Dside3.length=30.0*


## Credits 
To [James Gosling]( https://www.linkedin.com/in/jamesgosling) and fellows for developing [world’s most popular programming language](http://www.tiobe.com/tiobe_index). 




