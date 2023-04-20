# ToDoListTesting | Bug Reports API (ShortVer)
## <span style="color: orange">1.3 The possibility of creating task with long title (256 characters) - Medium Priority </span>

**Description** 

When we try to create the task with too long title we get 500 Error.

*(Send POST request)*
Postman -> Body -> raw -> JSON

**Steps to reproduce**

>1. To create pre-request (JS) to install variable {{randomString}} with limit of symbols equal 256 symbols.To avoid of writing title by hand evry time.
Look Postman collection.

>2. To complete a Body of request:
```json
{
    "title": "{{randomString}}", //  variable
    "completed": false
}
```

>3. To  send request using method POST   
https://sky-todo-list.herokuapp.com

>4. To check status code
>>Expected Result: 400 Bad request  
>> <span style="color:red">Result: 500 </span>

>5. To check a body response structure  
>> Expected Result:   
Error! 
```json
{ 
     "status": 400, "message": "Invalid input data"
} 
```
>> <span style="color:red">Result:</span>  
```json   
{
    "status": 500,
    "message": "An unexpected error ocurred, please try again"
}  
```


## <span style="color: orange">1.5 The possibility of creating task with empty title - High Priority </span>

**Description** 

When we try to create the task with empty title the task is succesfully created.(201 Status)  

*(Send POST request)*  
Postman -> Body -> raw -> JSON

**Steps to reproduce**

>1. To complete body to send parameters:  
```json  
{
 "title": ""
 "completed": false
}
```
>2. To  send request using method POST   
https://sky-todo-list.herokuapp.com

>3. To check status code
>>Expected Result: 400 Bad request  
>> <span style="color: red">Result: 201 Created</span> 

>4. To check a body response structure
>> Expected Result:   
Error! 
```json  
{
    "status": 400,
    "message": "Title is obligatory to fill"
}
```
>> <span style="color: red">Result: </span> 
```json
{
    "id": 69750,    // TaskId - variable
    "title": null,
    "completed": false,
    "order": null,
    "url": "/69750"  // TaskId - variable
}
```

## <span style="color: orange">2.10 The possibility of changing task title to long title. - Medium Priority </span> 

**Description** 

There is a necessary pre-condition: To create a task with valid title;
The next step is attemption to change title to long title. (Getting 500 Error)

*(Send PATCH request)*   
Postman -> Body -> raw -> JSON

**Steps to reproduce**

>1. To create pre-request (JS) to install variable {{randomString}} with limit of symbols equal 256 symbols.To avoid of writing title by hand evry time. Install variable {{TaskID}}not to input by hand.
Look Postman collection:

>2. Complete a Body of request: 

```json
{
    "title": "{{randomString}}" // variable
}
```

>3. To  send request using method PATCH   
 https://sky-todo-list.herokuapp.com/{{TaskID}}

>4. To check status code
>> Expected Result: 400 Bad request  
>><span style="color:red">Result: 500 </span> 

>5. To check a body response structure
>> Expected Result:      
Error! Required structure of JSON body response:    

```json
{
        "status": 400,
        "message": "Invalid input data"
}
```
>><span style="color:red">Result: 500 </span>   
 
```json
{
    "status": 500,
    "message": "An unexpected error ocurred, please try again"
} 
```


## <span style="color: orange">2.11 The possibility of changing task title to null title. - Medium priority </span> 
 

**Description** 

There is a necessary pre-condition: To create a task with valid title;
The next step is attemption to change title to null title. (Getting 201 Status)

*(Send PATCH request)*  
Postman -> Body -> raw -> JSON

**Steps to reproduce**

>1. To create pre-request (JS) to install variable {{randomString}} with limit of symbols equal 256 symbols and  to install variable {{TaskID}}. To avoid of writing title by hand evry time.
Look Postman collection:

>2. To complete a Body of request: 
```json
{
  "title": null
}
``` 

>3. To  send request using method PATCH  
 https://sky-todo-list.herokuapp.com/{{TaskID}}

>4. To check status code
>>Expected Result: 400 Bad request   

>><span style="color:red">Result: 500 </span>  

>5. To check a body response structure:  
>> Expected Result:   
Error!    
```json
{
    "status": 400,
    "message": "Invalid input data"
}
```
>> <span style="color:red">Result:</span>  
```json
{
    "id": 69752,    //  {{TaskID}}
    "title": null,
    "completed": false,
    "order": null,
    "url": "/69752"   // {{TaskID}}
}
```

## <span style="color: orange">2.12 The possibility of changing task title to empty title - High Priority </span>

**Description** 

There is a necessary pre-condition: To create a task with valid title;
The next step is attemption to change title to emptyl title. (Getting 201 Status)

*(Send PATCH request)*   
Postman -> Body -> raw -> JSON

**Steps to reproduce**

>1. To create pre-request (JS) to install variable {{baseurl}} and  to install variable {{TaskID}}. To avoid of rewriting taskid into the path by hand evry time.
Look Postman collection:

>2. Complete a Body of request:   
```json
{
 "title": ""
}
```

>3. To  send request using method PATCH  
https://todo-app-sky.herokuapp.com/{{TaskID}}

>4. To check status code
>>Expected Result: 400 Bad request   
>><span style="color:red">Result: 201 Created</span> 

>5. To check a body response structure
>> Expected Result:   
Error!  
```json
{
    "status": 400,
    "message": "Title is obligatory to fill"
}
```
>> <span style="color:red">Result:</span>  
```json
{
    
    "id": 69753,    //  {{TaskID}}
    "title": null,
    "completed": false,
    "order": null,
    "url": "/69753"   //  {{TaskID}}
} 
```

## <span style="color: orange">3.17 The possibility of deleting non-existent task. - Low priority </span>


**Description** 

There is a necessary pre-condition: To create a task with valid title and delete this task.
The next step is attemption to delete previously deleted task. (Getting 204 Status)

*(Send DELETE request)*  
Postman -> Body -> raw -> JSON

**Steps to reproduce**

>1. To create pre-request (JS) to install variable {{baseurl}} and  to install variable {{TaskID}}. To avoid of rewriting taskid into the path by hand evry time.
Look Postman collection:

>2. To  send request using method DELETE  
 https://sky-todo-list.herokuapp.com/{{TaskID}}

>3. To check status code
>>Expected Result: 404 Not found   
>><span style="color:red">Result:204 No content </span>

>4. To check a body response structure  
>> Expected Result:   
```json
{
    "status": 404,
    "message": "Todo with identifier '{{TaskID}}'' does not exist."
}
```
>><span style="color:red">Result:204. has no body.</span>
