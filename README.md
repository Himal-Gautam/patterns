# High level Code documentation

## * com.upgrad.patterns -> DiseaseApplication.java

Contains the main class that starts the application

## * com.upgrad.patterns.Authentication -> AuthenticationProvider.java

Contains an abstract class AuthenticationProvider and an abstract method Authenticate

## * com.upgrad.patterns.Authentication -> Authenticator.java

Contains a class named Authenticator
Contains a method named GetAuthProcessor. The purpose of this method is to chain the authentication processors. First, the JWT processor is tried, and if it cannot be used, basic authentication (username and password) is tried.
Contains a method named GetAuthProvider

## * com.upgrad.patterns.Authentication -> BasicAuthProvider.java

An implementation of the AuthenticationProvider class; implements the Authenticate method
Contains the implementation of basic authentication; authenticates the username and password provided

## * com.upgrad.patterns.Authentication -> JwtAuthProvider.java

An implementation of the AuthenticationProvider class; implements the Authenticate method.
Contains implementation of the Jwt authentication; authenticates the jwt token

## * com.upgrad.patterns.config -> RestServiceGenerator.java

Contains the implementation for the singleton pattern
RestTemplate object is instantiated only once and used throughout the application; GetInstance method contains the implementation for the same

## * com.upgrad.patterns.Constants -> sourceType.java

Contains an enum named SourceType with 2 enumerators namely DiseaseSh and JohnHopkins

## * com.upgrad.patterns.Controllers ->DiseaseController.java

Contains the controller class DiseaseController
GetDiseaseShCount method returns the disease count using Disease.io as the source
GetJohnHopkinsCount method returns the disease count using John Hopkins as the source
GetInfectedRatio method returns the infected ratio

## * com.upgrad.patterns.Entity -> DiseaseShResponse.java

Contains the class named DiseaseShResponse
JSON property names are mapped to the java field’s name

## * com.upgrad.patterns.Entity -> JohnHopkinResponse.java

Contains the class named JohnHopkinResponse
JSON property names are mapped to the java field’s name

## * com.upgrad.patterns.Entity -> stat.java

Contains the class named Stat
JSON property names are mapped to the java field’s name

## * com.upgrad.patterns.filters -> AuthFilter.java

<visit again>

## * com.upgrad.patterns.interfaces -> IndianDiseaseStat.java

Contains the IndianDiseaseStat interface that contains the declaration of a method named GetActiveCount

## * com.upgrad.patterns.Middleware -> AuthenticationProcessor.java

Contains the abstract class named AuthenticationProcessor along with an abstract method named isAuthorised

## * com.upgrad.patterns.Middleware -> BasicProcessor.java

Contains the implementation of the abstract method named isAuthorised; if username and password are provided, use them to authenticate, else use the next processor.

## * com.upgrad.patterns.Middleware -> JwtAuthProcessor.java

Contains the implementation of the abstract method named isAuthorised; if JWT tokens are provided, use them to authenticate, else use the next processor.

## * com.upgrad.patterns.Service -> DiseaseCountFacade.java

Contains the DiseaseCountFacade class that has implementations of two methods, namely getJohnHopkinsCount and getDieseaseShCount
Contains the implementation for the facade pattern. The getJohnHopkinsCount and the getDieseaseShCount functions of the DiseaseCountFacade class encapsulate the complexities of fetching from each source. These can be called from the controller without the controller worrying about any additional details.

## * com.upgrad.patterns.Service -> IndianDiseaseStatFactory.java

Contains the IndianDiseaseFactory class that contains the implementation for GetInstance method
Contains the implementation for the factory pattern. The GetInstance method allows to fetch the strategy to obtain active case count from the source type mentioned in the request parameter. You can use the functionality in runtime based on the strategy mentioned by the user.

## * com.upgrad.patterns.Strategies -> DiseaseShStrategy.java & JohnHopkinsStrategy.java

You create separate classes for each source and implement the IndianDiseaseNumbers interface. In the GetActiveCount(), write the implementations that uniquely describe how to fetch data from each source. Hence, you wrap around different sources to fetch the required data from different sources.