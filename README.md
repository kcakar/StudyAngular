# Angular  

## Terms  
* **Angular Module**    
  Angular uses modules to organize an application. It is not the same as ES modules.  
  
* **ES Modules**  
  ES modules are used to organize code.  
  
* **Typescript**  
  Angular is mostly used with typescript. Its a strongly typed language with OOP features.  
    
  Variables:  
  `name:string = 'kerem'`  
    
  Functions:  
  `functionName(): void { }`
  
* **Decorator**  
  Decorators add additional functionality to classes. In angular it is the MetaData. Angular has built in decorators. Syntax:  
   ```
   @DecoratorName({  
    DecoratorProp:DecoratorValue  
   })  
   export class ClassName{}
   ```  
   
* **Component**  
  Angular consists of components. Every component is a **class** with the **Component** decorator. Components can be rendered as **directives** or as a **routing target**. Syntax:  
   ```
   @Component({  
      selector: "custom-html-element",  
      templateUrl: "./my.component.html"  
   })  
   export class MyComponent{
    constructor(public variable:string){}
   }
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
    - <-**Interopelation**: Uses double curly bracelets to bind the data to the template. It is a **one way** binding, from the class, to the template. Interopelation always converts to string.
      ```
        <h1>{{pageTitle}}</h1>
        <h2>{{"Title:" + getTitle()}}</h2>
        <h3 innerText={{pageTitle}}></h3>
      ```
    - <-**Property Binding**: This is also one way binding, from the class to the template. It is a **one way** binding. It doesnt convert the result to a string, so it is good for binding nonstring variables to directives.
    [BindingTarget]:'BindingSource'  
    
        ```
        <img [src]='product.imageUrl'
             [title]='product.productName'
             [style.width.px]='imageWidth'
             [style.height.px]='imageWidth'
             [style.margin.px]='imageMargin'>
        ```
    - ->**Event binding**: This is used to bind events to functions in the class. It is a **one way** binding.
    (targetEvent)='functionName()'
        ```
          <button class="btn btn-primary" (click)='toggleImage()'></button>
        ```
    - <->**Two-way Binding**: To use two way bindign, you need to use ngModel directive.    
    [ ] are to indicate property binding, from the class property to the template.  
    ( ) to indicate event binding, to send a notification when the data changes in tempalate , to the class.  
    [()] BANANA IN A BOX!  
    
        ```
          <input [(ngModel)]=''
        ```
* **Pipes**  
  Pipes transform bound properties before display. Angular has built in pipes for date, number, decimal, uppercase, lowercase percent, currency, json, slice etc. You can also have custom pipes. Pipes are part of @angular/core.
  ```
    {{component.variableName | pipe1:'param1':'param2':'param3' | pipe2 | pipe3 }}
  ```
  - **Custom pipes**: To implement a custom pipe, you should decorate the class with @Pipe keyword and then implement PipeTransform interface. Also you need to add the pipe to the declarations part of the module. **DO NOT USE IT FOR FILTERING**
    ```
    @Pipe({
       name:'convertToSpaces'
    })
    export class ChangeCharacterPipe implements PipeTransform{
      transform(value: string, character:string):string {
        return value.replace(character,"");
      }
    }
    ```
  
* **Interface**
  Interfaces specify a related set of properties and methods. Classes implement interfaces to support them. You can use interfaces as   data types. Create class only if there's some functionality to use.
  ```
    export interface IProduct{
      productId: number;
      calcualateDiscount(percent:number):number; 
    }
  ```
* **Dependency Injection**  
  A coding pattern in which a class receives the instances of objects it needs(dependencies) from an external source rather than  creating them itself.  

* **Observables** (RXJS) 
  - Observables help managing asynchronous data. They threat events as a collection.  
  - You can subscribe to receive notifications about these events to act on them.
  ```
    x.subscribe();
    x.subscribe(Observer);
    //long version
    let sub =  productService.getProducts().subscribe({
      next: products => this.products=products,
      error: err => this.errorMessage = err,
      completeFn
    });
    //short version
     let sub =  productService.getProducts().subscribe({
      next(products) {this.products=products},
      error (err) => {this.errorMessage = err},
      completeFn
    });
    
  ```
  - **Observable Operators:** These are methods on observables that compose new observables. They can transform the observable by processing each value as they are emitted. Ex: map,filter,take,merge  
  - You can use the below website to play around with observables:  
     https://rxmarbles.com/
  - **Composing Operators:** Also referred as pipable operators because they use the pipe method. This is a way of combining multiple observable operators.
  - **Promises vs Observables**: 
      - Promise retursn a single future value while observable emits multiple values over time. 
      - Promise is lazy but Observable is not lazy. 
      - Promise is not cancellable but observable is.
   

## Convention  
* Modules are named with PascalCasing. Add Module at the end of the name: **NameModule**
* Components are named with PascalCasing. Add Component at the end of the name: **NameComponent**
* Properties are named with camelCasing: **propertyName**. 
* Functions are named with camelCasing: **functionName**
* Each component has their own folder. Their files are named as below:    
  * app.component.css  
  * app.component.html  
  * app.component.ts  
* Variables that refer to an observable end with a dollar sign: **source$**

# Packages
 * Anglular CLI  
 * Angular  
 * Typescript  

# Angular built-in modules:
  * **BrowserModule**: Has structural stuff like \*ngFor, \*ngIf, \*ngSwitch etc. Also has some pipes.
  * **FormsModule**: Has form stuff. Has @ngModal directive used for two-way binding.
 
# Angular's Built-in Directives  
  The asteriks in front of a directive means its a structural directive. These direcives are part of the BrowserModule.
  * \*ngIf: Removes or adds element depending on the condition.  
    ```
      <table class="table" *ngIf="products && products.length"></table>
    ```
  * \*ngFor: Foreach!
    ```
    <tr *ngFor="let product of products">
      <td></td>
      <td>{{product.productName}}</td>
      <td>{{product.productCode}}</td>
      <td>{{product.releaseDate}}</td>
      <td>{{product.starRating}}</td>
    </tr>
    ```
  
   * for of vs for in:
     for of iterates over iterable objects such as array.
     for in iterates over properties of an object.
  * \*ngSwitchCase:

## Getters and Setters  
    ```
    get filter():string{
      return this._filter;
    }
    set filter(value:string){
      this._filter=value;
      this.filterProducts();
    }
    ```
    
    
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

## Passing data from parent component to child component  
   To achieve this, you need to use **@Input** decorator.  
   **Child component**:  
   ```
   import {Input,Component, OnChanges} from "@angular/core";

   @Component({
     selector :'pm-star',
     templateUrl : './star.component.html',
     styleUrls:['./star.component.css']
   })
   export class StarComponent implements OnChanges{
     @Input() rating:number;
     starWidth:number;

     ngOnChanges(): void {
       this.starWidth = this.rating * 75 / 5;
     }
   }
   ```  
   **Parent component**:  
   ```
   <pm-star [rating]='product.starRating'></pm-star>
   ```
## Raising an event on Parent component when a data changes on child component
   To achieve this, you need to use **@Output** decorator.
   **Only variables with the type EventEmitter should be marked with the @Output decorator.**
   **Child component**:  
   ```
   import {Input, Output, Component, OnChanges} from "@angular/core";

   @Component({
     selector :'pm-star',
     templateUrl : './star.component.html',
     styleUrls:['./star.component.css']
   })
   export class StarComponent implements OnChanges{
     @Input() rating:number;
     starWidth:number;
     @Output() notify: EventEmitter<string> = new EventEmitter<string>();
     
     onClick(){
      this.notify.emit('clicked!');
     }
   }
   ```  
   **Component html**:
   ```
   <div (click)='onClick()'></div>
   ```
   **Parent component**:
   ```
   @Component({
      selector: "pm-products",
      templateUrl: "./products.component.html",
      styleUrls:["./products.component.css"]
    })
    export class ProductsComponent implements OnChanges {
      onNotify(message:string):void{} 
    }
   ```
   **Parent html**
   ```
    <pm-star (notify)='onNotify($event)'></pm-star>
   ```
## Services
   Angular is using an injector to provide services to the app. This injector creates a singleton instance of the service and lets you use its data and functions. 
   - Create service class
   - Define the metadata with a decorator: **@Injectable()**
   - Register the service to Angular
   - Inject the service on the constructor of the desired componenet  
     
   You can register a server to the Root Injector or to a Component. If you inject it to the root, its available to everywhere. If you inject it to a component, its available to that component and its children. If you inject it to a component, a new instance of service is created for each component. If not theres only one instance of the service is created for the app.  
   
   **Registering service syntax:**
   ```
   @Injectable({
      providedIn: 'root'
   })
   export class ProductService{ }
   ```  
   **Usage of service in a component:**  
   ```  
   //LONG VERSION
   export class ProductsComponent{
     private _productService;
     constructor(productService:ProductService){
        this._productService = productService;
     }
   }
   //SHORTHAND
    export class ProductsComponent{
     constructor(private productService:ProductService){
     }
   }
   ```  
   **NOTE: DO NOT DO STUFF WITH SIDE EFFECTS OR STUFF THAT TAKES TIME IN CONSTRUCTOR**
   
## HTTP Service 
   **Usage**:
   1) Import the service module to the desired module
   ```
   @NgModule({
    imports: [
        HttpClientModule
      ],
      declarations: [
        AppComponent
      ],
      bootstrap: [AppComponent]
   })
   export class AppModule { }
   ```
   2) Inject the service in the component's constructor
   3) Use the service
   ```  
   export class ProductService{
      private productUrl = 'www.service.com/api/products';
      
      constructor(private http: HttpClient){}
      
      getProducts(): Observable<IProduct[]>{
        this.http.get<IProduct[]>(this.productUrl);
      }
   }
   ```  


