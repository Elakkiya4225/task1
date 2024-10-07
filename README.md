# task1
Name: Elakkiya.K
Domain: Web Development
Codetech IT Id:CT6WDS1808

#html
"<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <link rel="stylesheet" href="style.css">
    <title>ToDo List</title>
</head>
<body>
    <div id="wrapper">
        <h2>Todo List</h2>
        <input type="text" id="input">
        <button id="add">Add</button>
        <div id="todoList">

        </div>
    </div>
    <script src="app.js"></script>
</body>
</html>"


#style.css
html,
body{
   margin: 0;
   font-family: 'Poppins', sans-serif;
   background-color:#f5e8ba;
}

#wrapper h2{
    display:flex;
    justify-content: center;
    
}

h2{
    color:#ffeba7;
    letter-spacing: 1px;
}
input{
    border-radius: 5px;
    border: 2px solid black ;
    margin-top:30px;
    height:2.5em;
    width:250px;
    padding-left:10px;
}

input:active{
    border:none;
}
#wrapper{
    height:500px;
    width:400px;
    margin:200px auto;
    background-color:#1f2029;
    border-radius:10px;
    padding:30px;
}

button{
    margin-top:20px;
    background-color:#ffeba7;
    border-radius: 4px;
    height: 44px;
    font-weight: 600;
    padding: 0 30px;
    letter-spacing: 1px;
    border: none;
    color: #102770;
}

button:hover{
    cursor:pointer;
}
#todoList{
    color:white;
    font-size:28px;  
    margin-top:10px; 
}

#todoList p{
  margin:10px 0px;
}

#todoList p:hover{
  cursor: pointer;
}


#java script
let button = document.getElementById('add')
let todoList = document.getElementById('todoList')
let input = document.getElementById('input');
//local storage,cookies
let todos = [];
window.onload = ()=>{
    todos = JSON.parse(localStorage.getItem('todos')) || []
    todos.forEach(todo=>addtodo(todo))
}

button.addEventListener('click',()=>{
    todos.push(input.value)
    localStorage.setItem('todos',JSON.stringify(todos))
    addtodo(input.value)
    input.value=''
})

function addtodo(todo){
    let para = document.createElement('p');
    para.innerText = todo;
    todoList.appendChild(para)
    
    para.addEventListener('click',()=>{
        para.style.textDecoration = 'line-through'
        remove(todo)
    })
    para.addEventListener('dblclick',()=>{
        todoList.removeChild(para)
        remove(todo)
    })
}

function remove(todo){
    let index = todos.indexOf(todo)
    if (index > -1) {
        todos.splice(index, 1);
      }
    localStorage.setItem('todos',JSON.stringify(todos))
}+++++++++++++++++++++++++++++++++++++++++++++++++++++
