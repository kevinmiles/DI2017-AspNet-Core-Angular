### Angular CLI Styles and Scripts

```json
"styles": [
"../node_modules/bootstrap/dist/css/bootstrap.css",
"../node_modules/bootstrap/dist/css/bootstrap-theme.css",
"../node_modules/font-awesome/css/font-awesome.css",
"../node_modules/toastr/build/toastr.css"
],
"scripts": [
    "../node_modules/jquery/dist/jquery.js",
    "../node_modules/toastr/toastr.js",
    "../node_modules/bootstrap/dist/js/bootstrap.js",
],
```

### Modules to add

* FormsModule
* HttpClientModule


### Todo Routes

```ts
const routes: Routes = [
    { path: '', redirectTo: 'todo', pathMatch: 'full'},
    { path: 'hello', component: HelloComponent, pathMatch: 'full'},
    { path: 'todo', component: TodoComponent, pathMatch: 'full'},
];
```

### Todo CSS

```css
form input:not(.ng-pristine).ng-invalid,
select:not(.ng-pristine).ng-invalid, textarea:not(.ng-pristine).ng-invalid
{
    background: lightpink;
    border-left: 5px solid red;
}
form input:not([type=submit]):not([type=checkbox]):not([type=radio]):not([type=file]):not(.ng-pristine).ng-valid,
select:not(.ng-pristine).ng-invalid, textarea:not(.ng-pristine):not(.ng-untouched).ng-valid
{
    background: #adfbdc;
    border-left: 5px solid green;
}

.todo-item {
    padding: 5px;
    border-bottom: 1px solid silver;
    transition: opacity 900ms ease-out;
}
.todo-header {
    font-weight: bold;
    font-size: 1.2em;
    color: #457196;
}
.todo-content {
    padding-left: 30px;
}
.todo-content .fa-check {
    color: green !important;
    font-weight: bold;
    font-size: 1.2em;
}
.completed {
    text-decoration: line-through;
    font-style: italic;
    opacity: 0.4;

}
```

### Todo Class

```ts
export class TodoItem {
    id = "";
	title = "";
	description = "";
	entered = new Date();
	completed = false;
}
```

```ts
todos: TodoItem[] = [
    {
        id: "",
        title: "Dev Intersection presentation",
        description: "Try to show up on time this time",
        entered: new Date(),
        completed: false
    },
    {
        id: "",
        title: "Do Angular presentation",
        description: "Should go good, let's hope I don't crash n' burn...",
        entered: new Date(),
        completed: false
    },
    {
        id: "",
        title: "Fret and worry until Presentation",
        description: "It's never done... 'just one more tweak'.",
        entered: new Date(),
        completed: false
    },
    {
        id: "",
        title: "Arrive at conference",
        description: "Arrive in Vegas and catch a cab to hotel",
        entered: new Date(),
        completed: true
    }
];
activeTodo: TodoItem = new TodoItem();
```

### Todo List Template Rendering

```html
<div *ngFor="let todo of todos"
     class="todo-item"
     [ngClass]="{completed: todo.completed}">

    <div class="pull-left" (click)="toggleCompleted(todo)">
        <i class="fa "
           [ngClass]="{'fa-bookmark-o': !todo.completed,'fa-check': todo.completed }"
           style="cursor: pointer">
        </i>
        <!--<input type="checkbox"-->
        <!--title="check to complete todo"-->
        <!--[(ngModel)]="todo.completed" />-->
    </div>

    <div class="pull-right">
        <i class="fa fa-remove"
           (click)="removeTodo(todo)"
           style="color: darkred; cursor: pointer"></i>
    </div>

    <div class="todo-content">
        <div class="todo-header">
            {{ todo.title}}
        </div>
        <div>
            {{todo.description}}
        </div>
    </div>
</div>
```

### Todo Entry Form

```html
<div class="well">
    <form name="form1" id="form1" #form1="ngForm">
        <div class="form-group">
            <div class="input-group">
                    <span class="input-group-addon">
                        <i class="fa fa-bookmark"></i>
                    </span>
                <input type="text" class="form-control"
                       id="name" name="name"
                       [(ngModel)]="activeTodo.title"
                       placeholder="Enter the title for this ToDo"
                       required />
            </div>
        </div>

        <div class="form-group">
            <!--<label class="control-label" for="form-group-input">Description:</label>-->
            <textarea class="form-control"
                      id="description" name="description"
                      style="height: 100px"
                      [(ngModel)]="activeTodo.description"
                      minlength="10"
                      placeholder="Enter the description for this placeholder"
                      required></textarea>
        </div>

        <button class="btn btn-primary" type="button"
                (click)="addTodo(activeTodo,form1)"
                [disabled]="form1.invalid">
            <i class="fa fa-plus"></i> Add Todo
        </button>
        <button class="btn btn-primary" type="button"
                (click)="loadTodos()">
            <i class="fa fa-download"></i>
            Load ToDos</button>
    </form>
</div>
```

### Add Observables Extra Methods

```ts
import {Observable} from "rxjs/Observable";
import 'rxjs/add/operator/map';
import 'rxjs/add/operator/catch';
```
### Declare Var Syntax

```ts
declare var $:any;
declare var toastr:any;
declare var window:any;
```