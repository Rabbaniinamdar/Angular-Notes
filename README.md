# Angular Basics

## 1. What is Angular?
Angular is a TypeScript-based, open-source front-end framework developed by Google for building single-page applications (SPAs). It provides a structured and scalable way to create dynamic web applications.

### Why Use Angular?
- ✅ A complete framework for front-end development.
- ✅ Supports two-way data binding for automatic UI updates.
- ✅ Uses TypeScript, offering better code maintainability.
- ✅ Built-in features like routing, forms, and dependency injection.

## 2. Features of Angular
- **Component-Based Architecture** – Applications are built using reusable and independent components.
- **Two-Way Data Binding** – Syncs data between the model and view automatically.
- **Dependency Injection (DI)** – Manages dependencies efficiently.
- **Directives** – Extends HTML functionality using built-in and custom directives.
- **Routing** – Enables navigation between different views using the Angular Router.
- **Forms Handling** – Supports Template-Driven and Reactive Forms.
- **RxJS & Observables** – Handles asynchronous operations efficiently.
- **Ahead-of-Time (AOT) Compilation** – Improves performance by compiling HTML and TypeScript before the browser loads the app.
- **Lazy Loading** – Loads only required modules for better performance.

## 3. Angular vs. Other Frameworks (React & Vue)

### **Angular (Google)** 🅰️
- Full-fledged framework with built-in tools (routing, HTTP client, DI).
- Uses TypeScript for better maintainability.
- Supports two-way data binding and RxJS for state management.
- Best for **large-scale enterprise applications**.

### **React (Meta)** ⚛
- UI development library requiring external tools for state management and routing.
- Uses JSX and Virtual DOM for high performance.
- One-way data binding, requiring Redux or Context API for state management.
- Best for **highly interactive and dynamic UIs**.

### **Vue (Independent)** 🔥
- Lightweight, easy-to-integrate framework for small to medium applications.
- Uses template-based syntax and Virtual DOM.
- Supports two-way binding and state management with Vuex or Pinia.
- Best for **small-to-medium, fast applications**.

### **When to Choose Angular?**
✔ If you need a complete framework with built-in tools.<br>
✔ If you’re building **large-scale enterprise applications**.<br>
✔ If you prefer **TypeScript** for better maintainability.<br>

## 4. Setting Up an Angular Project (Angular CLI)

### Installing Angular CLI
Angular CLI (Command Line Interface) helps efficiently create and manage Angular projects.

#### Install Angular CLI globally using npm:
```bash
npm install -g @angular/cli
```

#### Verify installation:
```bash
ng version
```

### Creating a New Angular Project
```bash
ng new my-angular-app
```

### Navigate to the project folder:
```bash
cd my-angular-app
```

### Serve the application locally:
```bash
ng serve
```

### Open in Browser:
Visit `http://localhost:4200/` to see the default Angular page.

## 5. Angular Project Structure
- 📂 **src/** → Contains the main application files.
- 📂 **app/** → Houses components, services, and modules.
- 📄 **index.html** → Main entry point of the app.
- 📄 **main.ts** → Bootstraps the Angular application.
- 📄 **app.module.ts** → Declares modules and components.
- 📄 **app.component.ts** → Root component of the application.

## 6. Angular Bootstrap Process (How an Angular App Starts)
Angular follows a structured bootstrapping process to start an application. This process involves various files working together to render the app.

### 1️⃣ Server Loads `index.html`
- The server serves the `index.html` file to the browser.
- It contains the root selector (`<app-root></app-root>`), which Angular replaces with the `AppComponent`.

#### Example:
```html
<body>
  <app-root></app-root>
</body>
```

### 2️⃣ `main.ts` – Entry Point of the Application
- This is the first file executed when the app loads.
- It bootstraps the Angular application by loading `AppModule`.

#### Code inside `main.ts`:
```typescript
import { platformBrowserDynamic } from '@angular/platform-browser-dynamic';
import { AppModule } from './app/app.module';

platformBrowserDynamic().bootstrapModule(AppModule)
  .catch(err => console.error(err));
```

### 3️⃣ `app.module.ts` – Declares Components & Modules
- Angular loads `AppModule` to register components, modules, and services.
- The `bootstrap` array defines the first component that Angular should load.

#### Example:
```typescript
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

### 4️⃣ `app.component.ts` – Root Component
- The `@Component` decorator defines a selector, template, and styles for a component.
- The selector (`app-root`) matches `<app-root>` in `index.html`.

#### Example:
```typescript
import { Component } from '@angular/core';

@Component({
  selector: 'app-root', // Matches <app-root> in index.html
  templateUrl: './app.component.html',
  styleUrls: ['./app.component.css']
})
export class AppComponent {
  title = 'My Angular App';
}
```

`templateUrl` refers to `app.component.html`, which holds the actual content.


## 5. How Angular Bundles the App

When you run `ng serve`, Angular performs the following steps:

- ✅ Compiles TypeScript into JavaScript.
- ✅ Bundles required JavaScript files.
- ✅ Injects them into `index.html`.
- ✅ Serves the app in the browser.

## 6. Final Flow Summary
- 1️⃣ `index.html` loads → Finds `<app-root>`
- 2️⃣ `main.ts` executes → Bootstraps `AppModule`
- 3️⃣ `app.module.ts` registers `AppComponent`
- 4️⃣ Angular replaces `<app-root>` with `app.component.html` content
- 5️⃣ The app is now running 🚀

---

# Angular Components & Modules

This guide explains components and modules in Angular with definitions and examples. 🚀

## 1. What is a Component in Angular?

A component is the building block of an Angular application. It controls a section of the UI and consists of:

- ✔ A TypeScript class (for logic)
- ✔ An HTML template (for UI)
- ✔ CSS styles (for design)

### Example of a Component

#### my-component.component.ts
```typescript
import { Component } from '@angular/core';

@Component({
  selector: 'app-my-component',  // Custom HTML tag
  templateUrl: './my-component.component.html',  // External HTML file
  styleUrls: ['./my-component.component.css']  // External CSS file
})
export class MyComponent {
  message: string = "Hello, Angular!";  // Class property
}
```

#### my-component.component.html
```html
<h1>{{ message }}</h1>  <!-- Display the class property -->
```

#### my-component.component.css
```css
h1 { color: blue; }
```

💡 **Usage in another template:**
```html
<app-my-component></app-my-component>
```

This will render:
```
Hello, Angular!
```

## 2. How to Create a Component in Angular?

📌 **Manually:** Create the `.ts`, `.html`, and `.css` files and register them in `app.module.ts`.
📌 **Using Angular CLI:**
```bash
ng generate component my-component
```

This command automatically creates:
```
app/
 ├── my-component/
 │   ├── my-component.component.ts
 │   ├── my-component.component.html
 │   ├── my-component.component.css
 │   ├── my-component.component.spec.ts
```

## 3. Decorators in Angular Components

Angular uses decorators to add metadata to classes. The `@Component` decorator is used to define a component.

### **Component Metadata in Angular**  

#### **1️⃣ selector**  
- Defines how to use the component in an HTML file.  
- Example:  
  ```html
  <app-my-component></app-my-component>
  ```

#### **2️⃣ templateUrl**  
- Links to an **external HTML file** that contains the component’s template.  
- Example:  
  ```typescript
  templateUrl: './my-component.component.html'
  ```

#### **3️⃣ styles**  
- Defines **inline styles** for the component.  
- Example:  
  ```typescript
  styles: ['h1 { color: red; }']
  ```

#### **4️⃣ styleUrls**  
- Links to **external stylesheets** for the component.  
- Example:  
  ```typescript
  styleUrls: ['./my-component.component.css']
  ```


4️⃣ # Angular Components & Modules


## 4. What is a Module in Angular?
A **module** in Angular is a container for **components, directives, pipes, and services**. The main module in every Angular app is `AppModule`.

### Example of a Module
```typescript
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
```

### 💡 Key Points about Modules:
✔ The `@NgModule` decorator bundles components together.<br>
✔ The `declarations` array registers components inside the module.<br>
✔ The `imports` array imports external modules.<br>
✔ The `bootstrap` array specifies the root component (usually `AppComponent`).<br>

---

## 5. How Components & Modules Work Together?
1️⃣ `main.ts` starts the application by bootstrapping `AppModule`.<br>
2️⃣ `app.module.ts` defines the structure and registers all components.<br>
3️⃣ `app.component.ts` is the root component, which loads the entire app.<br>
4️⃣ Other components (`my-component`) are nested inside `app.component.html`.<br>

---

## 6. How to Nest Components?
📌 A component can be placed inside another component by using its selector.

### Example:
```html
<!-- app.component.html -->
<h1>Welcome to My App</h1>
<app-my-component></app-my-component>  <!-- Nested component -->
```
✔ `app.component.html` is the root template.<br>
✔ `<app-my-component>` is the custom tag for `MyComponent`.<br>



# **🔹 Data Binding in Angular**  
Data binding in Angular enables communication between the **TypeScript component** and the **HTML template** to output data or respond to user interactions.

---

## **1️⃣ Types of Data Binding in Angular**  
Angular provides four main types of data binding:  

| **Type**               | **Syntax**              | **Description** |
|------------------------|------------------------|----------------|
| **String Interpolation** | `{{ data }}` | Displays dynamic content in the template. |
| **Property Binding**    | `[property]="data"`    | Binds a TypeScript property to an HTML element. |
| **Event Binding**       | `(event)="expression"` | Listens to user actions (e.g., clicks, keypresses). |
| **Two-Way Binding**     | `[(ngModel)]="data"`   | Updates both the UI and TypeScript variable simultaneously. |

---

## **2️⃣ String Interpolation (`{{ }}`)**  
✔ Used to display dynamic content inside the template.  
✔ The expression inside `{{ }}` must return a string.  
✔ Cannot contain complex logic like loops or conditions.  

🔹 **Example**  
```typescript
export class AppComponent {
  appTitle = 'Angular Data Binding!';
}
```
```html
<h1>{{ appTitle }}</h1>  <!-- Displays 'Angular Data Binding!' -->
```
✔ This works like:  
```html
<h1>Angular Data Binding!</h1>
```

💡 **Best for:** Outputting text, numbers, or method return values.

---

## **3️⃣ Property Binding (`[property]="data"`)**  
✔ Binds a **TypeScript property** to an **HTML element property** dynamically.  
✔ Useful for updating properties like `disabled`, `src`, `value`, etc.  

🔹 **Example**  
```typescript
export class AppComponent {
  isButtonDisabled = true;
}
```
```html
<button [disabled]="isButtonDisabled">Click Me</button> <!-- Button is disabled -->
```
💡 **Best for:** Dynamically updating element properties.

---

## **4️⃣ Property Binding vs. String Interpolation**  

| **Use Case** | **String Interpolation (`{{ }}`)** | **Property Binding (`[ ]`)** |
|-------------|---------------------------------|------------------------------|
| **For inserting text** | ✅ Yes | ❌ No |
| **For changing element properties dynamically** | ❌ No | ✅ Yes |

🔹 **Example**  
```html
<p>{{ title }}</p>  <!-- Correct usage for inserting text -->
<input [value]="title">  <!-- Correct usage for binding value -->
```

🚫 **Don't mix both!** 🚫  
❌ **Wrong:** `<p [innerText]="{{ title }}"></p>` (Mixing `[]` with `{{ }}` is invalid)  

---

## **5️⃣ Different Ways of Property Binding in Angular**  
### **1️⃣ Basic Property Binding (`[property]="value"`)**  
✔ Used to set an HTML element’s property dynamically.  
✔ Uses square brackets `[ ]`.  

🔹 **Example: Binding `disabled` Property**  
```typescript
export class AppComponent {
  isButtonDisabled = true;
}
```
```html
<button [disabled]="isButtonDisabled">Click Me</button> <!-- Button is disabled -->
```
✔ If `isButtonDisabled` is `true`, the button remains disabled.

---

### **2️⃣ Binding Component Property to Input Field**  
✔ You can bind a TypeScript variable to an input field’s value.  

🔹 **Example**  
```typescript
export class AppComponent {
  username = 'John Doe';
}
```
```html
<input [value]="username"> <!-- Displays 'John Doe' in input field -->
```
✔ If `username` changes, the input field updates automatically.

---

### **3️⃣ Binding an Attribute Using `attr.` Prefix**  
✔ Some HTML attributes (like `colspan`, `aria-label`) are **not standard DOM properties**.  
✔ Use `attr.` prefix for these attributes.  

🔹 **Example: Binding `colspan` Attribute**  
```typescript
export class AppComponent {
  columnSpan = 2;
}
```
```html
<td [attr.colspan]="columnSpan">Table Data</td> <!-- Spans 2 columns -->
```
💡 **Best for:** `colspan`, `aria-label`, `role`, `data-*` attributes.

---

### **4️⃣ Class Binding (`[class.className]="expression"`)**  
✔ Dynamically adds or removes CSS classes.  

🔹 **Example: Applying a Class Conditionally**  
```typescript
export class AppComponent {
  isActive = true;
}
```
```html
<p [class.active]="isActive">This text is styled.</p>
```
✔ If `isActive` is `true`, the `active` class is applied to the `<p>` tag.

---

### **5️⃣ Style Binding (`[style.property]="value"`)**  
✔ Dynamically changes the **inline styles** of an element.  

🔹 **Example: Setting Font Color Dynamically**  
```typescript
export class AppComponent {
  textColor = 'red';
}
```
```html
<p [style.color]="textColor">Styled Text</p> <!-- Text appears in red -->
```
✔ The text color changes dynamically based on `textColor`.

---

### **6️⃣ Binding to Custom Component Properties**  
✔ Bind data from a **parent component** to a **child component** using `@Input()`.  

🔹 **Example: Passing Data to a Child Component**  

#### **Parent Component (app.component.ts)**  
```typescript
export class AppComponent {
  message = 'Hello from Parent!';
}
```
#### **Parent Template (app.component.html)**  
```html
<app-child [childMessage]="message"></app-child>
```
#### **Child Component (child.component.ts)**  
```typescript
import { Component, Input } from '@angular/core';

@Component({
  selector: 'app-child',
  template: `<p>{{ childMessage }}</p>`
})
export class ChildComponent {
  @Input() childMessage!: string;
}
```
✔ The parent passes `message` to the child using `[childMessage]`.

---

### **7️⃣ Binding with Expressions**  
✔ You can bind **expressions** instead of direct property names.  

🔹 **Example: Using Expressions**  
```html
<button [disabled]="5 > 2">Click Me</button> <!-- Button is always disabled -->
```
✔ Since `5 > 2` is always `true`, the button remains disabled.

---

## **6️⃣ Event Binding (`(event)="expression"`)**  
✔ Executes a method in the component when an **event occurs** (e.g., `click`, `keyup`).  
✔ Uses parentheses `( )` instead of brackets `[ ]`.  

🔹 **Example**  
```typescript
export class AppComponent {
  onButtonClick() {
    console.log('Button clicked!');
  }
}
```
```html
<button (click)="onButtonClick()">Click Me</button>
```
✔ Best for: Handling button clicks, form submissions, or key events.

---

### **7️⃣ Using `$event` in Event Binding**  
✔ `$event` contains event data like **mouse click position** or **input value**.  

🔹 **Example: Capturing Input Value**  
```typescript
export class AppComponent {
  onKeyPress(event: Event) {
    console.log((<HTMLInputElement>event.target).value);
  }
}
```
```html
<input (input)="onKeyPress($event)" placeholder="Type something">
```

---

## **8️⃣ Two-Way Data Binding (`[(ngModel)]="data"`)**  
- ✔ Combines **Property Binding + Event Binding**.  
- ✔ Updates both the UI and TypeScript property when the user types.  

🔹 **Example**  
```typescript
export class AppComponent {
  username = 'John Doe';
}
```
```html
<input [(ngModel)]="username">  
<p>Your name: {{ username }}</p>  
```

✔ To use `ngModel`, **import `FormsModule`** in `app.module.ts`:
```typescript
import { FormsModule } from '@angular/forms';

@NgModule({
  imports: [ FormsModule ]
})
```

---

## **9️⃣ Summary: Key Takeaways**  
- ✔ Use **String Interpolation (`{{ }}`)** for inserting text.  
- ✔ Use **Property Binding (`[property]`)** for updating element properties.  
- ✔ Use **Event Binding (`(event)`)** for user interactions.  
- ✔ Use **Two-Way Binding (`[(ngModel)]`)** for input synchronization.
    
### 🔹 Directives in Angular
Directives are instructions that tell Angular how to modify the DOM (Document Object Model). They extend HTML's functionality, allowing developers to manipulate the DOM.

### 🔹 Types of Directives
- 1️⃣ **Structural Directives** → Modify the structure of the DOM (add/remove elements).
- 2️⃣ **Attribute Directives** → Modify the appearance or behavior of an element.
- 3️⃣ **Custom Directives** → User-defined directives that add custom behavior.

---
### 1️⃣ Structural Directives (*ngIf, *ngFor, *ngSwitch)
- ✔ Used to change the DOM structure (e.g., adding or removing elements).
- ✔ Structural directives are responsible for manipulating the DOM layout by adding, removing, or altering elements based on conditions.
- ✔ They are denoted by an asterisk (*) preceding the directive name.

#### 📌 *ngIf → Conditionally Show/Hide Elements
- ✔ Removes/creates elements in the DOM based on a boolean condition.
- ✔ If the condition is false, the element is removed from the DOM, not just hidden.

**Example:**
```typescript
export class AppComponent {
  isLoggedIn = true;
}
```
```html
<p *ngIf="isLoggedIn">Welcome, User!</p>  <!-- Will show only if isLoggedIn is true -->
```

#### 📌 *ngIf with else
✔ You can define an else block using `<ng-template>`.
```html
<p *ngIf="isLoggedIn; else loggedOutTemplate">Welcome, User!</p>
<ng-template #loggedOutTemplate>
  <p>Please log in!</p>
</ng-template>
```
✔ If `isLoggedIn = false`, it will show "Please log in!".

#### 📌 *ngFor → Loops Over an Array
✔ Loops through an array and creates elements dynamically.

**Example:**
```typescript
export class AppComponent {
  users = ['Alice', 'Bob', 'Charlie'];
}
```
```html
<ul>
  <li *ngFor="let user of users">{{ user }}</li>
</ul>
```
✔ Output:
```html
<ul>
  <li>Alice</li>
  <li>Bob</li>
  <li>Charlie</li>
</ul>
```

#### 📌 *ngFor with Index
```html
<ul>
  <li *ngFor="let user of users; let i = index">{{ i + 1 }}. {{ user }}</li>
</ul>
```
✔ Output:
```html
<ul>
  <li>1. Alice</li>
  <li>2. Bob</li>
  <li>3. Charlie</li>
</ul>
```

#### 📌 *ngSwitch → Multiple Conditional Rendering
✔ Similar to a `switch-case` statement in JavaScript.
✔ Used when you need multiple conditions.

**Example:**
```typescript
export class AppComponent {
  role = 'admin';
}
```
```html
<div [ngSwitch]="role">
  <p *ngSwitchCase="'admin'">Admin Panel</p>
  <p *ngSwitchCase="'user'">User Dashboard</p>
  <p *ngSwitchDefault>Guest Page</p>
</div>
```
✔ If `role = 'admin'`, "Admin Panel" will be displayed.

---
### 2️⃣ Attribute Directives (ngStyle, ngClass)
✔ Modify the appearance or behavior of an element.
✔ Do not change the DOM structure.

#### 📌 ngStyle → Apply Styles Dynamically
✔ Allows you to apply styles dynamically.

**Example:**
```typescript
export class AppComponent {
  textColor = 'blue';
}
```
```html
<p [ngStyle]="{ color: textColor }">This text is blue.</p>
```
✔ You can also use a method instead of a variable:
```html
<p [ngStyle]="{ color: getColor() }">Dynamic Color</p>
```
```typescript
getColor() {
  return Math.random() > 0.5 ? 'green' : 'red';
}
```
✔ Text color will randomly change between red and green.

#### 📌 ngClass → Apply CSS Classes Dynamically
✔ Adds/removes CSS classes based on conditions.

**Example:**
```typescript
export class AppComponent {
  isActive = true;
}
```
```html
<p [ngClass]="{ 'active': isActive, 'inactive': !isActive }">This text has a class.</p>
```
✔ If `isActive = true`, the "active" class is applied.
✔ If `isActive = false`, the "inactive" class is applied.

---
### 3️⃣ Custom Directives (Creating Your Own Directive)
✔ You can create your own directive to apply custom behavior.

#### 📌 Example: Creating a Custom Directive (appTurnGreen)
✔ This directive changes the background color of an element to green.

1️⃣ **Create a New Directive**
Run the command:
```bash
ng generate directive turnGreen
```
✔ This creates: `turn-green.directive.ts`.

2️⃣ **Implement Custom Logic**
Modify the generated directive file:
```typescript
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
```
✔ This modifies the element’s background to green when applied.

3️⃣ **Use the Custom Directive in HTML**
```html
<p appTurnGreen>This text has a green background!</p>
```
✔ Any `<p>` element with `appTurnGreen` will get a green background.

---
### 4️⃣ Component Directives
- ✔ Components are directives with templates.
- ✔ They are the building blocks of Angular applications, encapsulating both the UI and the behavior of a part of the application.
- ✔ Declared using the `@Component` decorator and typically have a corresponding HTML template.

#### 📌 Syntax:
```typescript
import { Component } from '@angular/core';

@Component({
    selector: 'app-root',
    templateUrl: './app.component.html',
})
export class AppComponent {}
```
---
🎯 **Summary:**
- ✔ Structural directives (`*ngIf`, `*ngFor`, `*ngSwitch`) modify the DOM structure.
- ✔ Attribute directives (`ngStyle`, `ngClass`) modify appearance or behavior.
- ✔ Custom directives allow you to create your own behaviors.
- ✔ Component directives are the foundation of Angular applications.

### **🔹 Understanding @Input, @Output, and @ViewChild in Angular**  

Angular provides powerful decorators like `@Input()`, `@Output()`, and `@ViewChild()` to facilitate **communication between components** and access DOM elements.

---

## **✅ @Input() Decorator**  
### **📌 Definition:**  
- `@Input()` is used to pass data **from a parent component to a child component**.  
- It allows the parent component to bind a value to a property in the child component.

### **📌 Example: Passing Data from Parent to Child**  

#### **1️⃣ Child Component (server.component.ts)**
```typescript
import { Component, Input } from '@angular/core';

@Component({
  selector: 'app-server',
  template: `<p>Server Name: {{ serverName }}</p>`,
})
export class ServerComponent {
  @Input() serverName: string = '';  // Accepts value from parent
}
```

#### **2️⃣ Parent Component (app.component.html)**
```html
<app-server [serverName]="'Main Server'"></app-server>
```

✔️ **Output in Browser:**  
```
Server Name: Main Server
```

✔️ **Custom Property Name with Alias:**  
```typescript
@Input('srvElement') serverName: string = '';  // Renaming property
```
```html
<app-server [srvElement]="'Main Server'"></app-server>
```

---

## **✅ @Output() Decorator**  
### **📌 Definition:**  
- `@Output()` is used to emit an **event from a child component to a parent component**.  
- It allows the child component to send data back to the parent component using `EventEmitter`.

### **📌 Example: Sending Data from Child to Parent**  

#### **1️⃣ Child Component (server.component.ts)**
```typescript
import { Component, EventEmitter, Output } from '@angular/core';

@Component({
  selector: 'app-server',
  template: `<button (click)="onAddServer()">Add Server</button>`,
})
export class ServerComponent {
  @Output() serverCreated = new EventEmitter<string>();  // Define custom event

  onAddServer() {
    this.serverCreated.emit('New Server Created');  // Emit event with data
  }
}
```

#### **2️⃣ Parent Component (app.component.html)**
```html
<app-server (serverCreated)="onServerAdded($event)"></app-server>
```

#### **3️⃣ Parent Component (app.component.ts)**
```typescript
onServerAdded(serverName: string) {
  console.log('Received from Child:', serverName);
}
```

✔️ **Console Output when button is clicked:**  
```
Received from Child: New Server Created
```

✔️ **Emitting an Object Instead of a String:**  
```typescript
@Output() serverCreated = new EventEmitter<{ name: string; status: string }>();

onAddServer() {
  this.serverCreated.emit({ name: 'Server 1', status: 'Active' });
}
```
```typescript
onServerAdded(eventData: { name: string; status: string }) {
  console.log('Server Name:', eventData.name, 'Status:', eventData.status);
}
```

---

## **✅ @ViewChild() Decorator**  
### **📌 Definition:**  
- `@ViewChild()` is used to access a **local reference of an HTML element or a child component** inside a TypeScript file.  
- It helps interact with DOM elements **or child component methods/properties** directly.

### **📌 Example 1: Accessing an HTML Element**  

#### **1️⃣ Template File (server.component.html)**
```html
<input #serverNameInput type="text">
<button (click)="onAddServer()">Add Server</button>
```

#### **2️⃣ Component File (server.component.ts)**
```typescript
import { Component, ViewChild, ElementRef } from '@angular/core';

@Component({
  selector: 'app-server',
  templateUrl: './server.component.html',
})
export class ServerComponent {
  @ViewChild('serverNameInput') nameInputRef!: ElementRef;  // Access local reference

  onAddServer() {
    console.log(this.nameInputRef.nativeElement.value);  // Get input value
  }
}
```

✔️ **When user enters "Hello" in input and clicks the button, the console prints:**  
```
Hello
```

---

### **📌 Example 2: Accessing a Child Component**  
You can also use `@ViewChild()` to access a child component inside a parent.

#### **1️⃣ Child Component (server.component.ts)**
```typescript
import { Component } from '@angular/core';

@Component({
  selector: 'app-server',
  template: `<p>Server Status: {{ getStatus() }}</p>`,
})
export class ServerComponent {
  getStatus() {
    return 'Online';
  }
}
```

#### **2️⃣ Parent Component (app.component.ts)**
```typescript
import { Component, ViewChild } from '@angular/core';
import { ServerComponent } from './server/server.component';

@Component({
  selector: 'app-root',
  template: `<app-server></app-server>
             <button (click)="checkServerStatus()">Check Status</button>`,
})
export class AppComponent {
  @ViewChild(ServerComponent) serverComponent!: ServerComponent;

  checkServerStatus() {
    console.log('Server Status:', this.serverComponent.getStatus());
  }
}
```

✔️ **When button is clicked, console prints:**  
```
Server Status: Online
```

---

## **🔹 Summary Table**
| **Decorator**  | **Purpose**  | **Direction** | **Used In**  |
|---------------|-------------|--------------|--------------|
| `@Input()`   | Pass data **from parent to child** | Parent → Child | Child Component |
| `@Output()`  | Send event/data **from child to parent** | Child → Parent | Child Component |
| `@ViewChild()` | Access an element or child component in TS | **Access template DOM or child component** | Parent Component |

---

## **🔹 Key Differences**
| **Feature**       | **@Input()**        | **@Output()**       | **@ViewChild()**      |
|------------------|-------------------|-------------------|-------------------|
| **Purpose**      | Pass data from parent to child | Send event from child to parent | Access template element or child component |
| **Binding Type** | Property binding (`[]`) | Event binding (`()`) | Direct reference |
| **Direction**    | **Parent → Child** | **Child → Parent** | **Access DOM/Child Component** |
| **Used In**      | Child Component | Child Component | Parent Component |

---

### **🚀 Conclusion**
- **Use `@Input()`** when **parent** needs to pass data **to child**.  
- **Use `@Output()`** when **child** needs to send data **to parent**.  
- **Use `@ViewChild()`** to access **local references** (HTML elements or child components) in **TypeScript**.  

