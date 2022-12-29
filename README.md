# Create react app without using npx-create-react-app :1st_place_medal: :golf:   
## how react actually work  
how does  react actually  work ?
we all know we can ceate react components using JSX and then render on the web using react dom or in mobile app using react native,
we also have access to incredile features like the state or the componenents lifecycle and finally it is extremely fast and flexible 
but what is actually heppening behind the scenes ?
So to know exactly how react work we will focus on reconciliation and rendering , the virtual DOM , the react diffing algorithm .
### First 
we have to understand the difference between react components , elements and component instances  
1. React component : 
react component look like this :    
`const App = () =>{`    
`   return (`    
`       <div>App component</div>`    
`   );`  
`};`  

React component return some react elements using JSX , the javascript XML , but for react , the return value is an object that looks like this    
`{`  
    `"$$tupeof": Sympbol(react.element),`  
    `key: null,`  
    `props: {children: "App component"},`  
    `ref: null,`  
    `type: "div",`  
`}`  
So if you want to check for yourSelf , you can just log it in the console . whan we call the component , we get the real return value .
So what exacltly is happening ??, so
the JSX gets converted to many ReactElement function calls ,then each of them returns the appropraite object .
The fact that JSX gets converted to the Reaxt.createElement funtions is the reason why we always have to import react whan using JSX .  
     
!["image"](/Capture.PNG)  
Well the react component is a function or a class that outputs an element tree   
if it is the function the output  is the return value of function , and if it is a class  
the output is the return value of the method  
2. Component react 👍
When react element describe a comonent , react keeps track of it and create a component instance ;each instace has state and lifestyle and those instaces are in fact very familiar to us .
In functional components , we can access the state and the lifestyle using Hooks , and in te class components , we make use of predefined methoss and the "this" keyword, which refers to the individual componet instance ; the same way react calls our components , it also manages our instances bu mounting and unmounting them .
3. Reconciliation :+1:  
we know that all react element does is create a tree of elements this process is very fast , because react elemenys are just plain javascript object , and we can basically create thousands ofobjects in an instant ;this is happening when we call the render() method  
react generate this tree of elements by starting at the very top and recurdively moving to the very bottom , if it ecounters a component , it calls it and keeps descending down to the returned react element  
react keep this tree of elements in memory , it is called the virtual DOM  the next thing to do is to sync the virtual DOM with the real DOM
On the initial render , react has to insert the full tree into the DOM .
Making those kinds of adjustments to the DOM is very expensive , but on the initial render , there is not way around it .  
But if the tree of elements changes ??  
React once again very quickly generates a new tree of elements and won have two trees  .the old ine and the new one

