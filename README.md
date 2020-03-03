# Angular  

## Terms  
* **Angular Module**    
  Angular uses modules to organize an application. It is not the same as ES modules.  
  
* **ES Modules**  
  ES modules are used to organize code.  
  

   
* **Typescript**  
  Angular is mostly used with typescript. Its a strongly typed language with OOP features.  
  
* **Decorator**  
  Decorators add additional functionality to classes. In angular it is the MetaData. Angular has built in decorators. Syntax:  
   ```
   @DecoratorName({  
    DecoratorProp:DecoratorValue  
   })  
   export class ClassName{}
   ```  
   
* **Component**  
  Angular consists of components. Every component is a **class** with the **Component** decorator. Syntax:  
   ```
   @Component({  
      selector: "custom-html-element",  
      templateUrl: "./my.component.html"  
   })  
   export class MyComponent{}
   ```
   **Note**: A component can belong to only one module! You can import a module if you want to use a component in that module.
   
* **Directive**
  Directive is the html element that refers to a component.
     ```
   <div>
      <ang-my-app></ang-my-app>
   </div>
   ```
* **Template**
  The HTML of the component.
  
* **Template Expression**
  {{code}} -> These are template expressions. Their context is always the component.
  
* **Binding**
  The data communication between the class and the template. Binding syntax is located at the template.
  Types of bindings:  
    - **Interopelation**: Uses double curly bracelets to bind the data to the template. It is a **one way** binding, from the class, to the template.
    ```
      <h1>{{pageTitle}}</h1>
      <h2>{{"Title:" + getTitle()}}</h2>
      <h3 innerText={{pageTitle}}></h3>
    ```

   
## Convention  
* Modules are named with PascalCasing. Add Module at the end of the name: **NameModule**
* Components are named with PascalCasing. Add Component at the end of the name: **NameComponent**
* Properties are named with camelCasing: **propertyName**. 
* Functions are named with camelCasing: **functionName**
* Each component has their own folder. Their files are named as below:    
  * app.component.css  
  * app.component.html  
  * app.component.ts  

# Packages
 * Anglular CLI  
 * Angular  
 * Typescript  

## What you need
 * Create index file. Create a custom element for the root component.
 * Create root **AppComponent**. Decorate it with Component tag. Add selector and template.
 * Create root **AppModule**. Decorate it with NgModule tag. Add declarations, imports and boostrap. Bootstrap is the root component. Declarations are the list of components that the module uses. Imports are helper stuff.
 * On Main.ts, use your AppModule to bootstrap your application.
 ```
 import { enableProdMode } from '@angular/core';
 import { platformBrowserDynamic } from '@angular/platform-browser-dynamic';

 import { AppModule } from './app/app.module';
 import { environment } from './environments/environment';

 if (environment.production) {
   enableProdMode();
 }

 platformBrowserDynamic()
   .bootstrapModule(AppModule)
   .catch(err => console.error(err));

 ```
# Functions  

    

