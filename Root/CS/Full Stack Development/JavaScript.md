- It is an **Interpreted Language**: That is it will not compile the whole thing first then give you an exe to execute, once you run it then it will convert the code line by line to binary and execute.
	- *Can run partially if the error comes later.* One of perks.
	- Another example of an **Interpreted Language** is Python.
- To run any `.js` file you can type `node <file_name>.js`
- It can also be used for Backend Development using `Node.js`.
- **Loosely Typed**: So, allows you to change data type of variable after declaration. Not very good to have in a large codebase. This is why **Typescript** came to light.
- **Single Threaded Language**: Considered to be bad for **scalable systems**.
	- It runs line by line as we saw earlier, and only one line is running at a time.
- **Variables**:
	-  `let` = We can change values.
	-  `var` = Not there in any good program.
	-  `const` = Constant, so only define it once and if we change its value it will throw an error.
***
# Callbacks
```
function mult(a, b, func) {
	let number = a*b;
	func(a*b);
}

fucntion print(res) {
	console.log("Soluiton: " + res);
}

function print2(res) {
	console.log("Do it yourself");
}

mult(1, 2, print);
mult(1, 2, print2);
```
***
# setTimeout

```
fuction hello() {
	console.log("hello");
}
setTimeout(hello(), 1*0000);
```
After given number of seconds it calls the given function. This is another example of [[#Callbacks]].
***

