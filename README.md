# Springbootcurd-mongodb-angular8
Spring boot back end and front end application is developed

Spring Boot + Angular + MongoDB CRUD Example Tutorial
posted by Nagarjuna Guntupalle on Feb 04, 2020

In this tutorial, we will be building step by step an Angular CRUD Web Application using Spring Boot + Angular + MongoDB from scratch. 

In my previous tutorial on Spring Boot MongoDB CRUD Example, we did not have any UI or front-end, so we had to test out an application using REST client but here we will use Angular on front-end side so that we can easily make this application as a full-stack and deliver to the end-users for performing real-time activities.

Angular is a platform and framework for building client applications in HTML and TypeScript. Angular is written in TypeScript. It implements core and optional functionality as a set of TypeScript libraries that you import into your apps.

Prerequisites
Spring Boot MongoDB CRUD Example
Tools and technologies used
Server-side technologies
Spring Boot - 2.0.5.RELEASE
JDK - 1.8 or later
Spring Framework - 5.0.8 RELEASE
Hibernate - 5.2.17.Final
Spring Data JPA - 2+
Front end technologies
Angular 8.0.0
Bootstrap 4
npm- 6.9.0
JQuery
Note that we are using the latest release of Spring Boot 2 and Angular 8 as of now.
Features Implementation
Create an Employee
Update an Employee
List of Employees
Delete Employee
View Employee
You will develop your first FULL STACK Application with Angular 8 and Spring Boot.
What we will build?
Below are the screenshots that show UI of our Employee Management System App that we are going to develop in this tutorial.
Employee List Page


Add Employee Page


Update Employee Page


View Employee Details Page


Delete Employee


Enable CORS on Server
To enable CORS on the server, add a @CrossOrigin annotation to the EmployeeController:
@CrossOrigin(origins = "http://localhost:4200")
@RestController
@RequestMapping("/api/v1")
public class EmployeeController {
 // ....
}
Angular 8 CRUD App Development
Let's develop a step by step CRUD (Create, Read, Update, Delete) Web Application using Angular 8 which consumes CRUD rest APIs, which we created in at Spring Boot MongoDB CRUD Example Tutorial article.
I assume that you have installed Node.js. Now, we need to check the Node.js and NPM versions. Open the terminal or Node command line then type these commands.
C:\Angular>node -v
v10.15.3

C:\Angular>npm -v
6.9.0
Install the latest version of Angular CLI
To install or update Angular 8 CLI, type this command in the Terminal or Node Command-Line.
npm install -g @angular/cli
Now, let's check the latest version of Angular CLI:
C:\angular>ng --version

     _                      _                 ____ _     ___
    / \   _ __   __ _ _   _| | __ _ _ __     / ___| |   |_ _|
   / △ \ | '_ \ / _` | | | | |/ _` | '__|   | |   | |    | |
  / ___ \| | | | (_| | |_| | | (_| | |      | |___| |___ | |
 /_/   \_\_| |_|\__, |\__,_|_|\__,_|_|       \____|_____|___|
                |___/


Angular CLI: 8.0.1
Node: 10.15.3
OS: win32 x64
Angular:
...

Package                      Version
------------------------------------------------------
@angular-devkit/architect    0.800.1
@angular-devkit/core         8.0.1
@angular-devkit/schematics   8.0.1
@schematics/angular          8.0.1
@schematics/update           0.800.1
rxjs                         6.4.0
Create Angular 8 Client Application using Angular CLI
The Angular CLI is a command-line interface tool that you use to initialize, develop, scaffold, and maintain Angular applications.
If you are new to Angular CLI then check out official documentation at https://cli.angular.io.
Let's use the below command to generate an Angular 8 Client application. We name this project as "angular8-springboot-client".
ng new angular8-springboot-client
Identify Components, Services, and Modules
Let's list out what are components, services, and modules we are going to create in this application. We will use Angular CLI to generate components, services because Angular CLI follows best practices and saves much of time.
Components
create-employee
employee-list
employee-details
update-employee
Services
employee.service.ts - Service for Http Client methods
Modules
FormsModule
HttpClientModule
AppRoutingModule
Employee Class (Typescript class)
employee.ts: class Employee (id, firstName, lastName, emailId)
In this next step, we will generate these components, classes, and services using Angular CLI.
Create Service & Components using Angular CLI
Let's auto-generate the service and components using Angular CLI. Change your project directory to angular8-springboot-client\src\app and run the following commands:
- ng g s employee
– ng g c create-employee
– ng g c employee-details
– ng g c employee-list
Here is complete command and output for your reference:
C:\Angular\angular8-springboot-crud-tutorial\angular8-springboot-client>cd src/app

C:\Angular\angular8-springboot-crud-tutorial\angular8-springboot-client\src\app>ng g s employee
CREATE src/app/employee.service.spec.ts (343 bytes)
CREATE src/app/employee.service.ts (137 bytes)

C:\Angular\angular8-springboot-crud-tutorial\angular8-springboot-client\src\app>ng g c create-employee
CREATE src/app/create-employee/create-employee.component.html (34 bytes)
CREATE src/app/create-employee/create-employee.component.spec.ts (685 bytes)
CREATE src/app/create-employee/create-employee.component.ts (304 bytes)
CREATE src/app/create-employee/create-employee.component.css (0 bytes)
UPDATE src/app/app.module.ts (509 bytes)

C:\Angular\angular8-springboot-crud-tutorial\angular8-springboot-client\src\app>ng g c employee-list
CREATE src/app/employee-list/employee-list.component.html (32 bytes)
CREATE src/app/employee-list/employee-list.component.spec.ts (671 bytes)
CREATE src/app/employee-list/employee-list.component.ts (296 bytes)
CREATE src/app/employee-list/employee-list.component.css (0 bytes)
UPDATE src/app/app.module.ts (617 bytes)

C:\Angular\angular8-springboot-crud-tutorial\angular8-springboot-client\src\app>ng g c employee-list
ERROR! src/app/employee-list/employee-list.component.html already exists.
ERROR! src/app/employee-list/employee-list.component.spec.ts already exists.
ERROR! src/app/employee-list/employee-list.component.ts already exists.
ERROR! src/app/employee-list/employee-list.component.css already exists.
The Schematic workflow failed. See above.

C:\Angular\angular8-springboot-crud-tutorial\angular8-springboot-client\src\app>ng g c employee-details
CREATE src/app/employee-details/employee-details.component.html (35 bytes)
CREATE src/app/employee-details/employee-details.component.spec.ts (692 bytes)
CREATE src/app/employee-details/employee-details.component.ts (308 bytes)
CREATE src/app/employee-details/employee-details.component.css (0 bytes)
UPDATE src/app/app.module.ts (737 bytes)
Integrate JQuery and Bootstrap with Angular
Use NPM to download Bootstrap & JQuery. Bootstrap and jQuery will be installed into the node_modulesfolder.
npm install bootstrap jquery --save
Configure installed Bootstrap & JQuery in an angular.json file:
...
 
"styles": [
  "src/styles.css",
  "node_modules/bootstrap/dist/css/bootstrap.min.css"
],
"scripts": [
  "node_modules/jquery/dist/jquery.min.js",
  "node_modules/bootstrap/dist/js/bootstrap.min.js"
]
 
...
If bootstrap won't work then try to import bootstrap CSS in style.css like:
/* You can add global styles to this file, and also import other style files */

@import '~bootstrap/dist/css/bootstrap.min.css';

.footer {
    position: absolute;
    bottom: 0;
    width:100%;
    height: 70px;
    background-color: blue;
    text-align: center;
    color: white;
}
Let's discuss each of the above generate components and service files and we will customize it as per our requirement.
Create an Employee Model (TypeScript)
Path - src/app/employee.ts
Before defining the EmployeeListComponent, let’s define an Employee class for working with employees. create a new file employee.ts inside src/app folder and add the following code to it -
export class Employee {
    id: number;
    firstName: string;
    lastName: string;
    emailId: string;
    active: boolean;
}
Creating Employee List Template and Component
Employee List Component
Path - src/app/employee-list/employee-list.component.ts
Let's create EmployeeListComponent component which will be used to display a list of employees, create a new employee, and delete an employee.
Update/remove the content of employee-list.component.ts inside src/app directory and add the following code to it -
import { EmployeeDetailsComponent } from '../employee-details/employee-details.component';
import { Observable } from "rxjs";
import { EmployeeService } from "../employee.service";
import { Employee } from "../employee";
import { Component, OnInit } from "@angular/core";
import { Router } from '@angular/router';

@Component({
  selector: "app-employee-list",
  templateUrl: "./employee-list.component.html",
  styleUrls: ["./employee-list.component.css"]
})
export class EmployeeListComponent implements OnInit {
  employees: Observable<Employee[]>;

  constructor(private employeeService: EmployeeService,
    private router: Router) {}

  ngOnInit() {
    this.reloadData();
  }

  reloadData() {
    this.employees = this.employeeService.getEmployeesList();
  }

  deleteEmployee(id: number) {
    this.employeeService.deleteEmployee(id)
      .subscribe(
        data => {
          console.log(data);
          this.reloadData();
        },
        error => console.log(error));
  }

  employeeDetails(id: number){
    this.router.navigate(['details', id]);
  }
}
Employee List Template
Path - src/app/employee-list/employee-list.component.html 
Add employee-list.component.html file with the following code to it -
<div class="panel panel-primary">
  <div class="panel-heading">
    <h2>Employee List</h2>
  </div>
  <div class="panel-body">
    <table class="table table-striped">
      <thead>
        <tr>
          <th>Firstname</th>
          <th>Lastname</th>
          <th>Email</th>
          <th>Actions</th>
        </tr>
      </thead>
      <tbody>
        <tr *ngFor="let employee of employees | async">
          <td>{{employee.firstName}}</td>
          <td>{{employee.lastName}}</td>
          <td>{{employee.emailId}}</td>
          <td><button (click)="deleteEmployee(employee.id)" class="btn btn-danger">Delete</button>
              <button (click)="employeeDetails(employee.id)" class="btn btn-info" style="margin-left: 10px">Details</button>
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</div>
Create Add Employee Template and Component
Create Employee Component
Path - src/app/create-employee/create-employee.component.ts
CreateEmployeeComponent is used to create and handle a new employee form data. Add the following code to it -
import { EmployeeService } from '../employee.service';
import { Employee } from '../employee';
import { Component, OnInit } from '@angular/core';
import { Router } from '@angular/router';

@Component({
  selector: 'app-create-employee',
  templateUrl: './create-employee.component.html',
  styleUrls: ['./create-employee.component.css']
})
export class CreateEmployeeComponent implements OnInit {

  employee: Employee = new Employee();
  submitted = false;

  constructor(private employeeService: EmployeeService,
    private router: Router) { }

  ngOnInit() {
  }

  newEmployee(): void {
    this.submitted = false;
    this.employee = new Employee();
  }

  save() {
    this.employeeService.createEmployee(this.employee)
      .subscribe(data => console.log(data), error => console.log(error));
    this.employee = new Employee();
    this.gotoList();
  }

  onSubmit() {
    this.submitted = true;
    this.save();    
  }

  gotoList() {
    this.router.navigate(['/employees']);
  }
}
Create Employee Template
Path - src/app/create-employee/create-employee.component.html
The create-employee.component.html shows the add employee HTML form. Add the following code to it -
<h3>Create Employee</h3>
<div [hidden]="submitted" style="width: 400px;">
  <form (ngSubmit)="onSubmit()">
    <div class="form-group">
      <label for="name">First Name</label>
      <input type="text" class="form-control" id="firstName" required [(ngModel)]="employee.firstName" name="firstName">
    </div>

    <div class="form-group">
      <label for="name">Last Name</label>
      <input type="text" class="form-control" id="lastName" required [(ngModel)]="employee.lastName" name="lastName">
    </div>

    <div class="form-group">
      <label for="name">First Name</label>
      <input type="text" class="form-control" id="emailId" required [(ngModel)]="employee.emailId" name="emailId">
    </div>

    <button type="submit" class="btn btn-success">Submit</button>
  </form>
</div>

<div [hidden]="!submitted">
  <h4>You submitted successfully!</h4>
  <!-- <button class="btn btn-success" (click)="newEmployee()">Add</button> -->
</div>
Update Employee Template and Component
Let's create update employee component with following Angular CLI command:
> ng g c update-employee
Update Employee Component
Path - src/app/update-employee/update-employee.component.ts
UpdateEmployeeComponent is used to update an existing employee. In this UpdateEmployeeComponent, we first get the employee object using REST API and populate in HTML form via data binding. Users can edit the employee form data and submit the form. Let's add the following code to UpdateEmployeeComponent -
import { Component, OnInit } from '@angular/core';
import { Employee } from '../employee';
import { ActivatedRoute, Router } from '@angular/router';
import { EmployeeService } from '../employee.service';

@Component({
  selector: 'app-update-employee',
  templateUrl: './update-employee.component.html',
  styleUrls: ['./update-employee.component.css']
})
export class UpdateEmployeeComponent implements OnInit {

  id: number;
  employee: Employee;

  constructor(private route: ActivatedRoute,private router: Router,
    private employeeService: EmployeeService) { }

  ngOnInit() {
    this.employee = new Employee();

    this.id = this.route.snapshot.params['id'];
    
    this.employeeService.getEmployee(this.id)
      .subscribe(data => {
        console.log(data)
        this.employee = data;
      }, error => console.log(error));
  }

  updateEmployee() {
    this.employeeService.updateEmployee(this.id, this.employee)
      .subscribe(data => console.log(data), error => console.log(error));
    this.employee = new Employee();
    this.gotoList();
  }

  onSubmit() {
    this.updateEmployee();    
  }

  gotoList() {
    this.router.navigate(['/employees']);
  }
}
Update Employee Template
Path - src/app/update-employee/update-employee.component.html 
The update-employee.component.html shows the update employee HTML form. 
Add the following code to this file -
<h3>Update Employee</h3>
<div [hidden]="submitted" style="width: 400px;">
  <form (ngSubmit)="onSubmit()">
    <div class="form-group">
      <label for="name">First Name</label>
      <input type="text" class="form-control" id="firstName" required [(ngModel)]="employee.firstName" name="firstName">
    </div>

    <div class="form-group">
      <label for="name">Last Name</label>
      <input type="text" class="form-control" id="lastName" required [(ngModel)]="employee.lastName" name="lastName">
    </div>

    <div class="form-group">
      <label for="name">First Name</label>
      <input type="text" class="form-control" id="emailId" required [(ngModel)]="employee.emailId" name="emailId">
    </div>

    <button type="submit" class="btn btn-success">Submit</button>
  </form>
</div>
Create View Employee Details Template and Component
Here we create view employee details functionality. Let's create an HTML template and component of Employee details functionality.
Employee Details Component
Path - src/app/employee-details/employee-details.component.ts
The EmployeeDetailsComponent component used to display a particular employee detail. Add the following code to it -
import { Employee } from '../employee';
import { Component, OnInit, Input } from '@angular/core';
import { EmployeeService } from '../employee.service';
import { EmployeeListComponent } from '../employee-list/employee-list.component';
import { Router, ActivatedRoute } from '@angular/router';

@Component({
  selector: 'app-employee-details',
  templateUrl: './employee-details.component.html',
  styleUrls: ['./employee-details.component.css']
})
export class EmployeeDetailsComponent implements OnInit {

  id: number;
  employee: Employee;

  constructor(private route: ActivatedRoute,private router: Router,
    private employeeService: EmployeeService) { }

  ngOnInit() {
    this.employee = new Employee();

    this.id = this.route.snapshot.params['id'];
    
    this.employeeService.getEmployee(this.id)
      .subscribe(data => {
        console.log(data)
        this.employee = data;
      }, error => console.log(error));
  }

  list(){
    this.router.navigate(['employees']);
  }
}
Employee Details Component Template
Path - src/app/employee-details/employee-details.component.html
The employee-details.component.html display a particular employee detail. Add the following code to it -
<h2>Employee Details</h2> 

<hr/>
<div *ngIf="employee">
  <div>
    <label><b>First Name: </b></label> {{employee.firstName}}
  </div>
  <div>
    <label><b>Last Name: </b></label> {{employee.lastName}}
  </div>
  <div>
    <label><b>Email Id: </b></label> {{employee.emailId}}
  </div>  
</div>

<br>
<br>
<button (click)="list()" class="btn btn-primary">Back to Employee List</button><br>
Employee Service
Path - src/app/employee.service.ts
The EmployeeService will be used to get the data from backend by calling spring boot APIs. Update the employee.service.ts file inside src/app directory with the following code to it -
import { Injectable } from '@angular/core';
import { HttpClient } from '@angular/common/http';
import { Observable } from 'rxjs';

@Injectable({
  providedIn: 'root'
})
export class EmployeeService {

  private baseUrl = 'http://localhost:8080/api/v1/employees';

  constructor(private http: HttpClient) { }

  getEmployee(id: number): Observable<any> {
    return this.http.get(`${this.baseUrl}/${id}`);
  }

  createEmployee(employee: Object): Observable<Object> {
    return this.http.post(`${this.baseUrl}`, employee);
  }

  updateEmployee(id: number, value: any): Observable<Object> {
    return this.http.put(`${this.baseUrl}/${id}`, value);
  }

  deleteEmployee(id: number): Observable<any> {
    return this.http.delete(`${this.baseUrl}/${id}`, { responseType: 'text' });
  }

  getEmployeesList(): Observable<any> {
    return this.http.get(`${this.baseUrl}`);
  }
}
Note that update employee functionality is not implemented so you can take as exercise and try to implement yourself (Tip 1: Add an update button to the employee list page and based on employee id you can implement update functionality. Note that Rest API is already created for update employee functionality. Tip 2: Refer to employee details functionality to get employee id from one component to another component (Update Employee Component) ).
npm package.json - Configure Dependencies
Path: /package.json 
The package.json file contains project configuration information including package dependencies which get installed when you run npm install.
Note that angular version 8.0.0 in the dependencies section in the below file.
{
  "name": "angular8-springboot-client",
  "version": "0.0.0",
  "scripts": {
    "ng": "ng",
    "start": "ng serve",
    "build": "ng build",
    "test": "ng test",
    "lint": "ng lint",
    "e2e": "ng e2e"
  },
  "private": true,
  "dependencies": {
    "@angular/animations": "~8.0.0",
    "@angular/common": "~8.0.0",
    "@angular/compiler": "~8.0.0",
    "@angular/core": "~8.0.0",
    "@angular/forms": "~8.0.0",
    "@angular/platform-browser": "~8.0.0",
    "@angular/platform-browser-dynamic": "~8.0.0",
    "@angular/router": "~8.0.0",
    "bootstrap": "^4.3.1",
    "jquery": "^3.4.1",
    "rxjs": "~6.4.0",
    "tslib": "^1.9.0",
    "zone.js": "^0.9.1"
  },
  "devDependencies": {
    "@angular-devkit/build-angular": "~0.800.0",
    "@angular/cli": "~8.0.1",
    "@angular/compiler-cli": "~8.0.0",
    "@angular/language-service": "~8.0.0",
    "@types/node": "~8.9.4",
    "@types/jasmine": "~3.3.8",
    "@types/jasminewd2": "~2.0.3",
    "codelyzer": "^5.0.0",
    "jasmine-core": "~3.4.0",
    "jasmine-spec-reporter": "~4.2.1",
    "karma": "~4.1.0",
    "karma-chrome-launcher": "~2.2.0",
    "karma-coverage-istanbul-reporter": "~2.0.1",
    "karma-jasmine": "~2.0.1",
    "karma-jasmine-html-reporter": "^1.4.0",
    "protractor": "~5.4.0",
    "ts-node": "~7.0.0",
    "tslint": "~5.15.0",
    "typescript": "~3.4.3"
  }
}
App Routing Module
Path: /src/app/app.routing.module.ts
Routing for the Angular app is configured as an array of Routes, each component is mapped to a path so the Angular Router knows which component to display based on the URL in the browser address bar.
import { EmployeeDetailsComponent } from './employee-details/employee-details.component';
import { CreateEmployeeComponent } from './create-employee/create-employee.component';
import { NgModule } from '@angular/core';
import { Routes, RouterModule } from '@angular/router';
import { EmployeeListComponent } from './employee-list/employee-list.component';
import { UpdateEmployeeComponent } from './update-employee/update-employee.component';

const routes: Routes = [
  { path: '', redirectTo: 'employee', pathMatch: 'full' },
  { path: 'employees', component: EmployeeListComponent },
  { path: 'add', component: CreateEmployeeComponent },
  { path: 'update/:id', component: UpdateEmployeeComponent },
  { path: 'details/:id', component: EmployeeDetailsComponent },
];

@NgModule({
  imports: [RouterModule.forRoot(routes)],
  exports: [RouterModule]
})
export class AppRoutingModule { }
App Component
Path: /src/app/app.component.ts
The app component is the root component of the application, it defines the root tag of the app as with the selector property of the @Component decorator.
import { Component } from '@angular/core';

@Component({
  selector: 'app-root',
  templateUrl: './app.component.html',
  styleUrls: ['./app.component.css']
})
export class AppComponent {
  title = 'Spring Boot + Angular + MongoDB CRUD Example Tutorial';
}
App Component Template
Path: /src/app/app.component.html
Defines the HTML template associated with the root AppComponent.
<nav class="navbar navbar-expand-sm bg-primary navbar-dark">
  <!-- Links -->
  <ul class="navbar-nav">
    <li class="nav-item">
        <a routerLink="employees" class="nav-link" routerLinkActive="active">Employee List</a>
    </li>
    <li class="nav-item">
        <a routerLink="add" class="nav-link" routerLinkActive="active">Add Employee</a>
    </li>
  </ul>
</nav>
<div class="container">
  <br>
  <h2 style="text-align: center;">{{title}}</h2>
  <hr>  
  <div class="card">
    <div class="card-body">
  <router-outlet></router-outlet>
    </div>
  </div>
</div>

<footer class="footer">
  <div class="container">
      <span>All Rights Reserved 2019 @JavaGuides</span>
  </div>
</footer>
App Module
Path: /src/app/app.module.ts
Defines the root module, named AppModule, that tells Angular how to assemble the application. Initially declares only the AppComponent. As you add more components to the app, they must be declared here.
import { BrowserModule } from '@angular/platform-browser';
import { NgModule } from '@angular/core';
import { FormsModule } from '@angular/forms';
import { AppRoutingModule } from './app-routing.module';
import { AppComponent } from './app.component';
import { CreateEmployeeComponent } from './create-employee/create-employee.component';
import { EmployeeDetailsComponent } from './employee-details/employee-details.component';
import { EmployeeListComponent } from './employee-list/employee-list.component';
import { HttpClientModule } from '@angular/common/http';
import { UpdateEmployeeComponent } from './update-employee/update-employee.component';
@NgModule({
  declarations: [
    AppComponent,
    CreateEmployeeComponent,
    EmployeeDetailsComponent,
    EmployeeListComponent,
    UpdateEmployeeComponent
  ],
  imports: [
    BrowserModule,
    AppRoutingModule,
    FormsModule,
    HttpClientModule
  ],
  providers: [],
  bootstrap: [AppComponent]
})
export class AppModule { }
Main Index Html File
Path: /src/index.html
The main index.html file is the initial page loaded by the browser that kicks everything off. Webpack bundles all of the javascript files together and injects them into the body of the index.html page so the scripts get loaded and executed by the browser.
<!doctype html>
<html lang="en">
<head>
  <meta charset="utf-8">
  <title>Angular8SpringbootClient</title>
  <base href="/">

  <meta name="viewport" content="width=device-width, initial-scale=1">
  <link rel="icon" type="image/x-icon" href="favicon.ico">
</head>
<body>
  <app-root></app-root>
</body>
</html>
Main (Bootstrap) File
Path: /src/main.ts
The main file is the entry point used by angular to launch and bootstrap the application.
import { enableProdMode } from '@angular/core';
import { platformBrowserDynamic } from '@angular/platform-browser-dynamic';

import { AppModule } from './app/app.module';
import { environment } from './environments/environment';

if (environment.production) {
  enableProdMode();
}

platformBrowserDynamic().bootstrapModule(AppModule)
  .catch(err => console.error(err));
Polyfills
Path: /src/polyfills.ts
Some features used by Angular 8 are not yet supported natively by all major browsers, polyfills are used to add support for features where necessary so your Angular 8 application works across all major browsers.
import 'core-js/features/reflect';
import 'zone.js/dist/zone';
TypeScript tsconfig.json
Path: /tsconfig.json
The tsconfig.json file configures how the TypeScript compiler will convert TypeScript into JavaScript that is understood by the browser. More information is available on the TypeScript docs.
{
  "compileOnSave": false,
  "compilerOptions": {
    "baseUrl": "./",
    "outDir": "./dist/out-tsc",
    "sourceMap": true,
    "declaration": false,
    "module": "esnext",
    "moduleResolution": "node",
    "emitDecoratorMetadata": true,
    "experimentalDecorators": true,
    "importHelpers": true,
    "target": "es2015",
    "typeRoots": [
      "node_modules/@types"
    ],
    "lib": [
      "es2018",
      "dom"
    ]
  }
}
This completes the Angular 8 web application configuration and app-related components.
Running Angular 8 App
Let's run the above developed Angular App with a command:
ng serve
By default, the Angular app runs on 4200 port but you can change default port with the following command:
ng serve --port 4201
Demo
Hit http://localhost:4200 link in a browser will host this Angular 8 CRUD app.

Below are the screenshots shows UI of our Employee Management System App:
Employee List Page


Add Employee Page


Update Employee Page


View Employee Details Page


Delete Employee


This completed the complete development of Angular 8 CRUD application with spring boot as a back end.
Download Source Code
The source code of this tutorial available on my GitHub repository at https://github.com/RameshMF/springboot-angular-mongodb-crud-tutorial
