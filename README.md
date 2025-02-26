🔹 Angular Basics
1️⃣ What is Angular?
Angular is a TypeScript-based, open-source front-end framework developed by Google for building single-page applications (SPAs). It provides a structured and scalable way to create dynamic web applications.
Why Use Angular?
 ✅ A complete framework for front-end development.
 ✅ Supports two-way data binding for automatic UI updates.
 ✅ Uses TypeScript, offering better code maintainability.
 ✅ Built-in features like routing, forms, and dependency injection.

2️⃣ Features of Angular
✔ Component-Based Architecture – Applications are built using reusable and independent components.
 ✔ Two-Way Data Binding – Syncs data between the model and view automatically.
 ✔ Dependency Injection (DI) – Manages dependencies efficiently.
 ✔ Directives – Extends HTML functionality using built-in and custom directives.
 ✔ Routing – Enables navigation between different views using the Angular Router.
 ✔ Forms Handling – Supports Template-Driven and Reactive Forms.
 ✔ RxJS & Observables – Handles asynchronous operations efficiently.
 ✔ Ahead-of-Time (AOT) Compilation – Improves performance by compiling HTML and TypeScript before the browser loads the app.
 ✔ Lazy Loading – Loads only required modules for better performance.

3️⃣ Angular vs. Other Frameworks (React & Vue)
✔ Angular 🅰️ (Google)
Angular is a full-fledged framework with built-in tools (routing, HTTP client, DI). Ideal for enterprise-level applications.
Uses TypeScript for better maintainability.
Supports two-way data binding and RxJS for state management.
Best for large-scale enterprise applications.
✔ React ⚛ (Meta)
React is a library for UI development. It needs external tools for state management and routing. Best for highly interactive UIs.
Uses JSX and Virtual DOM for high performance.
One-way data binding needs Redux or Context API for state management.
Best for highly interactive and dynamic UIs.
✔ Vue 🔥 (Independent)
Vue is a lightweight, progressive framework that is simple and easy to integrate. Great for small to medium applications.
Uses template-based syntax and Virtual DOM.
Supports two-way binding and state management with Vuex or Pinia.
Best for small-to-medium, fast applications.
When to Choose Angular?
✔ If you need a complete framework with built-in tools.
 ✔ If you’re building large-scale enterprise applications.
 ✔ If you prefer TypeScript for better maintainability.

4️⃣ Setting Up an Angular Project (Angular CLI)
🔹 Installing Angular CLI
Angular CLI (Command Line Interface) helps efficiently create and manage Angular projects.
🔹 Install Angular CLI globally using npm:
npm install -g @angular/cli
🔹 Verify installation:
ng version
🔹 Creating a New Angular Project
ng new my-angular-app
🔹 Navigate to the project folder:
cd my-angular-app
🔹 Serve the application locally:
ng serve
🔹 Open http://localhost:4200/ in your browser to see the default Angular page.
🔹 Angular Project Structure
📂 src/ → Contains the main application files.
 📂 app/ → Houses components, services, and modules.
 📄 index.html → Main entry point of the app.
 📄 main.ts → Bootstraps the Angular application.
 📄 app.module.ts → Declares modules and components.
 📄 app.component.ts → Root component of the application.

🔹 Angular Bootstrap Process (How an Angular App Starts)
Angular follows a structured bootstrapping process to start an application. This process involves various files working together to render the app.

1️⃣ Server Loads index.html
The server serves the index.html file to the browser.
It contains the root selector (<app-root></app-root>), which Angular replaces with the AppComponent.
Example:
 <body>
  <app-root></app-root>
</body>


2️⃣ main.ts – Entry Point of the Application
This is the first file executed when the app loads.
It bootstraps the Angular application by loading AppModule.
Code inside main.ts:
 import { platformBrowserDynamic } from '@angular/platform-browser-dynamic';
import { AppModule } from './app/app.module';

platformBrowserDynamic().bootstrapModule(AppModule)
  .catch(err => console.error(err));
platformBrowserDynamic().bootstrapModule(AppModule) starts the app by passing AppModule.

3️⃣ app.module.ts – Declares Components & Modules
Angular loads AppModule to register components, modules, and services.
The bootstrap array defines the first component that Angular should load.
Example:
```javascript
 import { NgModule } from '@angular/core';
import { BrowserModule } from '@angular/platform-browser';
import { AppComponent } from './app.component';

@NgModule({
  declarations: [AppComponent],  // Declares components
  imports: [BrowserModule],      // Imports necessary modules
  providers: [],                 // Services go here
  bootstrap: [AppComponent]       // AppComponent is the first component to load
})
export class AppModule {}
```

This tells Angular which components to recognize and which one to load first.



4️⃣ app.component.ts – Root Component
The @Component decorator defines a selector, template, and styles for a component.
The selector (app-root) matches <app-root> in index.html.
Example:
 import { Component } from '@angular/core';

@Component({
  selector: 'app-root', // Matches <app-root> in index.html
  templateUrl: './app.component.html',
  styleUrls: ['./app.component.css']
})
export class AppComponent {
  title = 'My Angular App';
}
templateUrl refers to app.component.html, which holds the actual content.

5️⃣ How Angular Bundles the App
Running ng serve does the following: ✅ Compiles TypeScript into JavaScript
 ✅ Bundles required JavaScript files
 ✅ Injects them into index.html
 ✅ Serves the app in the browser

6️⃣ Final Flow Summary
1️⃣ index.html loads → Finds <app-root>
 2️⃣ main.ts executes → Bootstraps AppModule
 3️⃣ app.module.ts registers AppComponent
 4️⃣ Angular replaces <app-root> with app.component.html content
 5️⃣ The app is now running 🚀




🔹 Angular Components & Modules (Well-Structured Notes)
This guide covers components and modules in Angular with clear definitions and examples. 🚀

1️⃣ What is a Component in Angular?
A component is the building block of an Angular application. It controls a section of the UI (User Interface) and consists of:
 ✔ A TypeScript class (for logic)
 ✔ An HTML template (for UI)
 ✔ CSS styles (for design)
🔹 Example of a Component
// my-component.component.ts
import { Component } from '@angular/core';

@Component({
  selector: 'app-my-component',  // Custom HTML tag
  templateUrl: './my-component.component.html',  // External HTML file
  styleUrls: ['./my-component.component.css']  // External CSS file
})
export class MyComponent {
  message: string = "Hello, Angular!";  // Class property
}
<!-- my-component.component.html -->
<h1>{{ message }}</h1>  <!-- Display the class property -->
/* my-component.component.css */
h1 { color: blue; }

💡 Usage in another template:
<app-my-component></app-my-component>

This will render:
<h1>Hello, Angular!</h1>


2️⃣ How to Create a Component in Angular?
📌 Manually: Create the .ts, .html, and .css files and register in app.module.ts.
 📌 Using Angular CLI:
ng generate component my-component

This command automatically creates:
app/
 ├── my-component/
 │   ├── my-component.component.ts
 │   ├── my-component.component.html
 │   ├── my-component.component.css
 │   ├── my-component.component.spec.ts


3️⃣ Decorators in Angular Components
Angular uses decorators to add metadata to classes. The @Component decorator is used to define a component.

Property

Description

Example
selector
Defines how to use the component in HTML
<app-my-component>
templateUrl
Links to an external HTML file
'./my-component.component.html'
styles
Defines inline styles
styles: ['h1 { color: red; }']
styleUrls
Links to external stylesheets
styleUrls: ['./my-component.component.css']


4️⃣ What is a Module in Angular?
A module in Angular is a container for components, directives, pipes, and services. The main module in every Angular app is AppModule.
🔹 Example of a Module
// app.module.ts (Main Module)
import { NgModule } from '@angular/core';
import { BrowserModule } from '@angular/platform-browser';
import { AppComponent } from './app.component';
import { MyComponent } from './my-component/my-component.component';

@NgModule({
  declarations: [   // Declaring components
    AppComponent,
    MyComponent
  ],
  imports: [ BrowserModule ], // Importing other modules
  bootstrap: [AppComponent]   // Starting component (root)
})
export class AppModule { }

💡 Key Points about Modules: 
✔ The @NgModule decorator bundles components together.
 ✔ The declarations array registers components inside the module.
 ✔ The imports array imports external modules.
 ✔ The bootstrap array specifies the root component (usually AppComponent).

5️⃣ How Components & Modules Work Together?
1️⃣ main.ts starts the application by bootstrapping AppModule.
 2️⃣ app.module.ts defines the structure and registers all components.
 3️⃣ app.component.ts is the root component, which loads the entire app.
 4️⃣ Other components (my-component) are nested inside app.component.html.

6️⃣ How to Nest Components?
📌 A component can be placed inside another component by using its selector.
🔹 Example:
<!-- app.component.html -->
<h1>Welcome to My App</h1>
<app-my-component></app-my-component>  <!-- Nested component -->
✔ app.component.html is the root template
 ✔ app-my-component is the custom tag for MyComponen



🔹 Data Binding in Angular
Data Binding in Angular is the communication between the TypeScript component and the HTML template to output data or respond to user events.
1️⃣ Types of Data Binding in Angular
Angular provides four types of data binding:
Type
Syntax
Description
String Interpolation
{{ data }}
Outputs dynamic content in templates.
Property Binding
[property]="data"
Binds a TypeScript property to an HTML element property.
Event Binding
(event)="expression"
Listens to user actions (e.g., clicks, keypress).
Two-Way Binding
[(ngModel)]="data"
Updates both UI and TypeScript variables simultaneously.


2️⃣ String Interpolation ({{ }})
✔ Used to display data dynamically inside the template.
 ✔ Whatever is inside {{ }} must return a string.
 ✔ Cannot be used for complex logic like loops or conditions.
🔹 Example
export class AppComponent {
  appTitle = 'Angular Data Binding!';
}
<h1>{{ appTitle }}</h1>  <!-- Displays 'Angular Data Binding!' -->
✔ Works like:
<h1>Angular Data Binding!</h1>
💡 Best for: Outputting text, numbers, or method return values.
3️⃣ Property Binding ([property]="data")
✔ Binds a TypeScript property to an HTML element’s property.
 ✔ Use when changing properties dynamically (e.g., disabled, src, value).
🔹 Example
export class AppComponent {
  isButtonDisabled = true;
}
<button [disabled]="isButtonDisabled">Click Me</button> <!-- Button is disabled -->

💡 Best for: Dynamically updating element properties.

4️⃣ Property Binding vs. String Interpolation
✔ Both can bind data, but they are used in different cases.
Use Case
String Interpolation ({{ }})
Property Binding ([ ])
For inserting text
✅ Yes
❌ No
For changing element properties dynamically
❌ No
✅ Yes
Example
<p>{{ title }}</p>
<input [value]="title">

✔ ❌ Don’t mix both! ❌ ✔
 🚫 Wrong: <p [innerText]="{{ title }}"></p> (Mixing [] with {{ }} is invalid)





🔹 Different Ways of Property Binding in Angular
Property binding in Angular allows us to bind a property in the TypeScript component to an HTML element's property dynamically.


1️⃣ Basic Property Binding ([property]="value")
✔ Used to set an HTML element’s property dynamically.
 ✔ Uses square brackets [ ].
🔹 Example: Binding disabled Property
export class AppComponent {
  isButtonDisabled = true;
}

<button [disabled]="isButtonDisabled">Click Me</button> <!-- Button is disabled -->

✔ If isButtonDisabled is true, the button remains disabled.

2️⃣ Binding Component Property to Input Field
✔ You can bind a TypeScript variable to an input field’s value.
🔹 Example
export class AppComponent {
  username = 'John Doe';
}
<input [value]="username"> <!-- Displays 'John Doe' in input field -->
✔ If username changes, the input field updates automatically.
3️⃣ Binding an Attribute Using attr. Prefix
✔ Some HTML attributes (like colspan, aria-label) are not standard DOM properties.
 ✔ Use attr. prefix for these attributes.
🔹 Example: Binding colspan Attribute
export class AppComponent {
  columnSpan = 2;
}

<td [attr.colspan]="columnSpan">Table Data</td> <!-- Spans 2 columns -->

✔ Best for: colspan, aria-label, role, data-* attributes, etc.

4️⃣ Class Binding ([class.className]="expression")
✔ Dynamically adds or removes CSS classes.
🔹 Example: Applying a Class Conditionally
export class AppComponent {
  isActive = true;
}

<p [class.active]="isActive">This text is styled.</p>

✔ If isActive is true, the active class is applied to the <p> tag.

5️⃣ Style Binding ([style.property]="value")
✔ Dynamically changes the inline styles of an element.
🔹 Example: Setting Font Color Dynamically
export class AppComponent {
  textColor = 'red';
}

<p [style.color]="textColor">Styled Text</p> <!-- Text appears in red -->

✔ The text color changes dynamically based on the textColor value.

6️⃣ Binding to Custom Component Properties
✔ You can bind data from a parent component to a child component's input property using @Input().
🔹 Example: Passing Data to a Child Component
Parent Component (app.component.ts)
export class AppComponent {
  message = 'Hello from Parent!';
}

Parent Component Template (app.component.html)
<app-child [childMessage]="message"></app-child>

Child Component (child.component.ts)
import { Component, Input } from '@angular/core';

@Component({
  selector: 'app-child',
  template: `<p>{{ childMessage }}</p>`
})
export class ChildComponent {
  @Input() childMessage!: string;
}

✔ The parent component passes message to the child using [childMessage].

7️⃣ Binding with Expressions
✔ You can bind expressions instead of direct property names.
🔹 Example: Using Expressions
<button [disabled]="5 > 2">Click Me</button> <!-- Button is always disabled -->

✔ Since 5 > 2 is always true, the button remains disabled.

5️⃣ Event Binding ((event)="expression")
✔ Executes a method in the component when an event occurs (e.g., click, keyup).
 ✔ Uses parentheses ( ) instead of brackets [ ].
🔹 Example
export class AppComponent {
  onButtonClick() {
    console.log('Button clicked!');
  }
}

<button (click)="onButtonClick()">Click Me</button>

✔ Event Binding captures user interactions (e.g., mouse clicks, key presses, form submissions).
 ✔ Avoid writing logic inside the template; use methods in TypeScript instead.
💡 Best for: Handling button clicks, form submissions, or key events.

6️⃣ Using $event in Event Binding
✔ $event contains data about the event, like mouse click position or input value.
🔹 Example: Capturing Input Value
export class AppComponent {
  onKeyPress(event: Event) {
    console.log((<HTMLInputElement>event.target).value); // Typecasting
  }
}

<input (input)="onKeyPress($event)" placeholder="Type something">

💡 Best for: Accessing user input dynamically.

7️⃣ Two-Way Data Binding ([(ngModel)]="data")
✔ Combines Property Binding + Event Binding.
 ✔ Updates both the UI and TypeScript property when the user types.
🔹 Example
export class AppComponent {
  username = 'John Doe';
}

<input [(ngModel)]="username">  <!-- Two-way binding -->
<p>Your name: {{ username }}</p>  <!-- Displays updated value -->

✔ When the user types in the input, the username is updated automatically.
💡 Best for: Forms, user input fields.

8️⃣ Enabling ngModel for Two-Way Binding
✔ ngModel belongs to FormsModule, so we must import it before using it.
🔹 Steps to Enable ngModel
1️⃣ Import FormsModule in app.module.ts:
import { FormsModule } from '@angular/forms';
@NgModule({
  imports: [ FormsModule ]
})

2️⃣ Now, [(ngModel)] can be used in your components.

9️⃣ Summary: Key Takeaways
✔ String Interpolation ({{ }}) – Outputs text in the template.
 ✔ Property Binding ([property]) – Dynamically updates element properties.
 ✔ Event Binding ((event)) – Reacts to user actions like clicks.
 ✔ Two-Way Binding ([(ngModel)]) – Syncs the UI and TypeScript data.
 ✔ Use $event to access user input values.
 ✔ Import FormsModule to use ngModel.


🔹 Directives in Angular
Directives are instructions that tell Angular how to modify the DOM (Document Object Model).
Directives in Angular are instructions that extend HTML's functionality, allowing developers to manipulate the DOM

🔹 Types of Directives
1️⃣ Structural Directives → Modify the structure of the DOM (add/remove elements).
 2️⃣ Attribute Directives → Modify the appearance or behavior of an element.
 3️⃣ Custom Directives → User-defined directives that add custom behavior.

1️⃣ Structural Directives (*ngIf, *ngFor, *ngSwitch)
✔ Used to change the DOM structure (e.g., adding or removing elements).
✔ Structural directives are responsible for manipulating the DOM  layout by adding, removing, or manipulating elements based on conditions. They are denoted by an asterisk (*) preceding the directive name and are commonly used to alter the structure of the DOM based on conditions


📌 *ngIf → Conditionally Show/Hide Elements
✔ Removes/creates elements in the DOM based on a boolean condition.
 ✔ If the condition is false, the element is removed from the DOM, not just hidden.
Example: Using *ngIf
export class AppComponent {
  isLoggedIn = true;
}
<p *ngIf="isLoggedIn">Welcome, User!</p>  <!-- Will show only if isLoggedIn is true -->

📌 *ngIf with else
✔ You can define an else block using <ng-template>.
<p *ngIf="isLoggedIn; else loggedOutTemplate">Welcome, User!</p>
<ng-template #loggedOutTemplate>
  <p>Please log in!</p>
</ng-template>

✔ If isLoggedIn = false, it will show "Please log in!".

📌 *ngFor → Loops Over an Array
✔ Loops through an array and creates elements dynamically.
Example: Using *ngFor

export class AppComponent {
  users = ['Alice', 'Bob', 'Charlie'];
}

<ul>
  <li *ngFor="let user of users">{{ user }}</li>
</ul>

✔ This generates:
<ul>
  <li>Alice</li>
  <li>Bob</li>
  <li>Charlie</li>
</ul>

📌 *ngFor with Index
✔ You can access the index of the current loop.
<ul>
  <li *ngFor="let user of users; let i = index">{{ i + 1 }}. {{ user }}</li>
</ul>

✔ Output:
<ul>
  <li>1. Alice</li>
  <li>2. Bob</li>
  <li>3. Charlie</li>
</ul>


📌 *ngSwitch → Multiple Conditional Rendering
✔ Similar to a switch-case statement in JavaScript.
 ✔ Used when you need multiple conditions.
Example: Using *ngSwitch
export class AppComponent {
  role = 'admin';
}

<div [ngSwitch]="role">
  <p *ngSwitchCase="'admin'">Admin Panel</p>
  <p *ngSwitchCase="'user'">User Dashboard</p>
  <p *ngSwitchDefault>Guest Page</p>
</div>

✔ If role = 'admin', "Admin Panel" will be displayed.

2️⃣ Attribute Directives (ngStyle, ngClass)
✔ Modify the appearance or behavior of an element.
 ✔ Do not change the DOM structure.

📌 ngStyle → Apply Styles Dynamically
✔ Allows you to apply styles dynamically.
Example: Using ngStyle
export class AppComponent {
  textColor = 'blue';
}

<p [ngStyle]="{ color: textColor }">This text is blue.</p>

✔ You can also use a method instead of a variable:
<p [ngStyle]="{ color: getColor() }">Dynamic Color</p>

getColor() {
  return Math.random() > 0.5 ? 'green' : 'red';
}

✔ Text color will randomly change between red and green.

📌 ngClass → Apply CSS Classes Dynamically
✔ Adds/removes CSS classes based on conditions.
Example: Using ngClass
export class AppComponent {
  isActive = true;
}

<p [ngClass]="{ 'active': isActive, 'inactive': !isActive }">This text has a class.</p>

✔ If isActive = true, the "active" class is applied.
 ✔ If isActive = false, the "inactive" class is applied.

3️⃣ Custom Directives (Creating Your Own Directive)
✔ You can create your own directive to apply custom behavior.
📌 Example: Creating a Custom Directive (appTurnGreen)
✔ This directive changes the background color of an element to green.
1️⃣ Create a New Directive
Run the command:
ng generate directive turnGreen
✔ This creates: turn-green.directive.ts.
2️⃣ Implement Custom Logic
Modify the generated directive file:
import { Directive, ElementRef, Renderer2, OnInit } from '@angular/core';

@Directive({
  selector: '[appTurnGreen]'
})
export class TurnGreenDirective implements OnInit {
  constructor(private el: ElementRef, private renderer: Renderer2) {}

  ngOnInit() {
    this.renderer.setStyle(this.el.nativeElement, 'background-color', 'green');
  }
}

✔ This modifies the element’s background to green when applied.
3️⃣ Use the Custom Directive in HTML
<p appTurnGreen>This text has a green background!</p>

✔ Any <p> element with appTurnGreen will get a green background.

3️⃣ Component Directives
Components are directives with templates. They are the building blocks of Angular applications, encapsulating both the UI (User Interface) and the behavior of a part of the application. Components are used to create reusable and modular UI elements. They are declared using the @Component decorator and typically have a corresponding HTML template.

Syntax: In the component below, we have used the @Component here to define a component.

import { Component } from '@angular/core';

@Component({
    selector: 'app-root',
    templateUrl: './app.component.html',
})
export class AppComponent {}


