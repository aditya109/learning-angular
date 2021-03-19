# Angular 

## Introduction to Angular Concepts

> Angular is a platform and framework for building single-page client applications using HTML and TS. 
>
> Angular is written in TS.

### Architecture of Angular Application

- The basic building blocks are Angular components that are organized into *NgModules*.

- *NgModules* collect related code into functional sets; an Angular app is defined by a set of *NgModules*.
- An app always has atleast a *root module* that enable bootstrapping, and typically has many more *features module*.
  - Components define *views*, which are sets of screen elements that Angular can choose among and modify according to one's program logic and data.
  - Components use *services*, which provides a specific functionality not directly related to views. Service providers can be *injected* into components as *dependencies*.

- Modules, components and services are classes that use *decorators*. These decorators mark their type and provide metdata that tells Angualr how to use them.
  - The metadata for a component class associates it with a *template* that defines a view. A template combines ordinary HTML with Angular *directives* and *binding markup* that allow Angular to modify the HTML before rendering it for display.
  - The metadata for a service class providers the information Angular needs to make it available to components that *dependency injection (Di).*

- An app's components typically define many views, arrranged hierarchically. Angular provides the Router service to help you define navigation paths among views.

### Modules

- Angular *NgModules* differ from and complement JS (ES2015) modules. 

> An *NgModule* declares a compilation context for a set of components that is dedicated to an application domain, a workflow, or a closely related set of capabilities. An NgModule can associate its components with related code, such as services, to form functional units.

- Every Angular app has a *root module*, conventionally name `AppModule`, which provides the bootstrap mechanism that launches the application. An app typically contains many functional modules.

- Like JS modules, <u>*NgModules* can import functionality from other *NgModules*</u> and allow their own functionality to be exported and used by other *NgModules*.
- This techniques also take advantage of *lazy-loading*--that is, loading modules on demand, to minimize the amount of code that needs to be loaded at startup.

### Components

- Every Angular application has at least one component, the root component that connects a component hierarchy with the page DOM. 
- Each components defines a class that contains application data and logic, and is associated with an HTML *template* defines a view to be displayed in a target environment.
- The `@Component()` decorator identifies the class immediately below it as a component, and provides the template and related component-specific metadata.

#### Templates, directives and data binding

- A template combines HTML with Angular markup that can modify HTML elements before they are displayed.

- Template *directives* provides program logic, and *binding markup* connects one's application data and the DOM. 

  They are two types of data binding:

  -  *Event binding* lets one's app respond to user input in the target environment by updating one's application data.
  - *Property binding* lets you interpolate value that are computed from one's application data into the HTML.

- Before a view is displayed, Angular evaluated the directives and resolves the binding syntax in the template to modify the HTML elements and the DOM, according to one's program data and logic.

- Angular supports *two-way data binding*, meaning that changes in the DOM, such as user choices, are also reflected in one's program data.

- The templates can use *pipes* to improve the user experience by transforming values for display. Angular provides predefined pipes for common transformations, and one can also define our own pipes.

### Services and dependency injection

- For data and logic that isn't associated with a specific view, and that one wants to share across components, one has to create a *service* class. 
- A *Service* class definition is immediately preceded by the `@Injectable()` decorator. 
- The decorator provider the metadata that allows other providers to be **injected** as dependencies into the class.

> *Dependency injection (Di)* lets you keep one's component classes lean and efficient. 
> They don't fetch data from the server, validate user input, or log directly to the console; they delegate such task to services.

#### Routing

- The Angular `Router` NgModule provided a service that lets you define a navigation path among the different application states and view hierarchies in the app.

> It is modeled on the familiar browser navigation conventions:
>
> - Enter a URL in the address bar and the browser navigates to a corresponding page.
> - Client links on the page and the browser navigates to a new page.
> - Click the browser's back and forward buttons and the browser navigates backward and forward through the history of pages one's has seen.

- The router maps URL-like paths to views instead of pages. When a user performs an action, such as clicking a link, that would load a new page in the browser, the router intercepts the browser's behavior, and shows or hides view hierarchies.
- If the router determines that the current application state requires particular functionality, and the module that defines it hasn't been loaded, the router can *lazy-load* the module on demand.
- The router interprets a link URL according to app's view navigation rules and data state.
  To define navigation rules, you associate *navigation paths* with one's components. 

```
												👆👉👉👉👉Template<>👉👉👉👇<==================== Directive[Metadata] 
							(Property Binding)  👆					        👇 (Event Binding)
Service [Injector]=============================>👆👈Component[Metadata]👈👈👇
```

