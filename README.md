## Connecting spring rest api and angular

Angular project creation

in cmd inside angular project folder 

```tsx
>ng new angularConnection --no-standalone --routing --ssr=false;
```

first we need to create a model class in frontend

model class is used to create objects

create a model folder inside src or app compenent

inside folder create a ts file 

properties should be same as backend

copy properties from model class of spring project  model class —backend

creation of objects inside model folder

```tsx
export class student{

    studentId:number|null;
    sName:string;
    sMarks:number;

    constructor()
    {
        this.studentId=null;
        this.sName=""; 
        this.sMarks=0;
    }
}

```

output

```tsx
ng serve 
```

next we need to create a component

control 

main .ts —→ index.html—>appcomponent.html

to make control to welcome component 

create a folder under src called components 

run the below command

```tsx
ng g c components/welcome --no-standalone
```

components/ stands for folder name 

we need to create html page so we create component 

and it take lot of time to load  if we create html page

angular helps create components to make a project faster and dynamic loading

 

now to change control from index.html which is default to welcome component 

first we go to  app.html 

```tsx
<router-outlet></router-outlet>//control will go to app routing
```

then in app router html

```tsx
const routes: Routes = [{path:"",component:WelcomeComponent}];
```

app routing

```tsx
  FormsModule,
    ReactiveFormsModule
```

we create a form of student details

create studentregister component 

in studentregister html

```html
<p>studentregister works!</p>
<form #studentRegisterForm="ngForm"  (ngSubmit)="registerStudent()" >    <!--name to form and making it angular form --> 

  StudentName:<input type="text" name="StudentName" [(ngModel)]="student.sName" required> <!--name to input and making it angular form --> <br> <!--required is used to make the field mandatory -->
  StudentID:<input type="text" name="StudentID" [(ngModel)]="student.studentId" required> <br> <!--name to input and making it angular form -->
  StudentMarks:<input type="text" name="StudentMarks" [(ngModel)]="student.sMarks" required>

  <input type="submit" value="StudentRegister"> <!--submit button to submit the form -->
  <input type="reset" value="Reset"> <!--reset button to reset the form -->
</form>
```

in student register component  we write  fuctionality in ts  

```tsx
export class StudentregisterComponent  {

  student=new student();

  registerStudent()
  {
    console.log(this.student);
  }
}

```

to connect to spring restapi we create a model folder and in model folder we create ts file called student

```tsx
export class student{

    studentId:number|null;
    sName:string;
    sMarks:number;

    constructor()
    {
        this.studentId=null;
        this.sName=""; 
        this.sMarks=0;
    }
}

```

to attach the different component(different page onclick ) in router we mention

```tsx
const routes: Routes = [{path:"",component:WelcomeComponent},{path:'registerstudenturl',component:StudentregisterComponent}];
```

to import angular form modules 

```tsx
  imports: [
    BrowserModule,
    AppRoutingModule,
    FormsModule,
    ReactiveFormsModule
  ],
```

connect component to service 

subscribe  means use the object from spring
