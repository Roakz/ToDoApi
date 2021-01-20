# ToDoApi
A Simple Todo API with ASP.net core

This is the example application that Microsoft docs guide us through to help understand the ASP.net core frameworks API scaffolding and how the controllers and models work within the framework.

This was created from Visual Studio 2019 which provides endless support and a substantial amount of scaffolding for ease and speed of development. I also find the IIS express web server integration on windows machines really handy.

<h3>Controllers<h3>

The controllers in the this framework are essentialy specify what routes you want to use. This is declared with what they call attributes.

```c#
[HttpGet]
```

The preceding code gives a small example of what a GET attribute looks like. These attributes precede the controller methods which define the endpoints, perform the appropriate CRUD action and return the appropriate response. The whole controller can literally be scaffolded with a couple of button clicks and you have a full page of CRUD functionality.

There is also an [ApiController] attribute at the top of the controller. This attribute is specific to developing API's and provides a whole heap of features:

- Attribute routing requirement
- Automatic HTTP 400 responses
- Binding source parameter inference
- Multipart/form-data request inference
- Problem details for error status codes


[More on this here](https://docs.microsoft.com/en-us/aspnet/core/web-api/?view=aspnetcore-5.0#attribute-routing-requirement).

Controllers are included by default in the ConfigureServices method in the startup class. This is where we must declare our services to ASP.net core.

Services seem to be an encouraged concept in ASP.net core in general. They are way of creating reusable independent parts of code that can be registered with a service provider and have their dependancies handled where needed with dependancy injection. But essentially They shouldn't need to rely on anything else. They are self contained and simply provide a service that can be accessed from anywhere. 

<h3> Models </h3>

The models in ASP.net are fairly straight forward. They are a class which defines a bunch of properties that become the shape of your entity. They are kept by convention in models folder and are included in the Application.Models namespace.

In This application I stored the ToDoContext in the models folder. Im not sure on the convention but I feel like this could also go in a services folder. We used an in memory SQL DB in this application to keep it simple. One the appropriate Nuget packages are installed its simply a matter of Creating a context class. This class is then given to AddDbContext in the startup.cs which creates a DB context service and ensures that it is handled by the dependancy injection container.

<h3> DTO </h3>

DTO meaning Data Transfer Object is used in this small API application to demonstrate the implementation. This is handy to know when creating an API that may be exposed to clients...which I guess would make sense as it is an API! It enables us to offer a contract to the client. A garunteed data object for them to recieve. This enables us to implement backwards compatability in our models and controllers without potentially breaking our clients applications. It can also aid with efficiency by only containing exactly what it needs to and preventing us from exposing our inner entities to our clients.
