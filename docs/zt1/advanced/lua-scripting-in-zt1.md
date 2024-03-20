
!!! warning "Difficulty: Advanced"

# Lua Scripting in ZT1: A Brief Primer

[Lua](https://en.wikipedia.org/wiki/Lua_(programming_language)) is a lightweight, high-level, programming language designed to be embedded in other applications and is usually a popular choice for game scripting because it's easy to learn and use. In fact, Zoo Tycoon 2, which came out only a few years after Zoo Tycoon 1, uses Lua for its scripting, but Zoo Tycoon 1 did not come with Lua support. [EMU API](/docs/zt1/reference/emu/index.md) is a tool that gives us scripting capabilities for Zoo Tycoon 1, which means we can make the game do things that it wasn't originally designed to do. This guide will serve as a brief primer for Lua and how to use it in Zoo Tycoon 1.

## What is Scripting?

[Scripting](https://en.wikipedia.org/wiki/Scripting_language) is a way to give the game new behaviors without having to touch the game's internal machinations. As far as modding goes, the only thing that Blue Fang (the game's original developer) gave us was the ability to read and edit the configuration files, and that's it. Although editing configuration files is powerful, it's not enough to make the game do everything we want it to do. This is where scripting comes in because we can puppeteer the game's behavior to our liking.

## Programming Languages

There are many [programing languages](https://en.wikipedia.org/wiki/Programming_language) out there. They are languages in the sense that we as programmmers use them to communicate with the computer. However, it's not a conversation like we can have with each other. Instead, we have to be very specific and precise with our instructions. Following a recipe is a good analogy for programming because like in cooking, if you miss a step, the computer will not understand what you want it to do and the end result isn't so tasty. I mean, functional. Unless we're talking artificial intelligence, but that's a whole other can of worms we won't get into.

In fact, Zoo Tycoon 1 and EMU API were written in a popular programmming called C++. C++ is a powerful language, but it can also be very complex and difficult to learn. Lua on the other hand is much simpler and easier to learn, and it's also very fast. It's great for modding enthusiasts because though it's still programming, a lot has been abstracted away behind the scenes to make it easier to work with.

Here is an example of a simple C++ program that prints "Hello, World!" to the console:

```cpp
#include <iostream>

int main() {
    std::cout << "Hello, World!" << std::endl;
    return 0;
}
```

And here is the same program written in Lua:

```lua
print("Hello, World!")
```

As you can see, the Lua program is much simpler and easier to understand, so it makes it a great choice for scripting in games. 

I sort of touched on this just now, but what EMU API does is it does something called abstraction. This means it takes the complex C++ code and packages it up in a way that users can interact with it using Lua. This is a very powerful concept and it's what makes Lua scripting in Zoo Tycoon 1 possible.

When we use Lua scripts in Zoo Tycoon 1, we are essentially calling the complicated C++ code that has been hidden away from us. This is why we need EMU API to use Lua in Zoo Tycoon 1. It's the bridge that connects the two languages, and in turn, it's the bridge that connects us to the game.

## Programming in Lua

This guide will only serve as a brief primer for Lua. If you want to deep dive into the language, I highly recommend checking out the [official documentation](https://www.lua.org/manual/5.4/). It's a great resource and it's free to use. There are also a ton of youtube tutorials since it's a popular language for game scripting.

### Variables

Variables in programming languages mean essentially the same thing as they do in math. They're a container that stores a value, and can be used again when the name of the variable is called. Here is an example of a variable in Lua:

```lua
local number = 2
```

In the example above, we've created a variable called `number` and assigned it the value of `2`. When we want to use the value of `2` again, we can simply call the variable `number`.

### Operators

Operators are symbols that we can use to perform operations on variables. At the end of the day, programming is just a bunch of math. Here are some examples of operators in Lua:

```lua
local number = 2 + 3 -- addition
local number = 2 - 3 -- subtraction
local number = 2 * 3 -- multiplication
local number = 2 / 3 -- division
local number = 2 % 3 -- modulus
```

### Types

Lua is a dynamically typed language, which means that we don't have to declare the type of a variable when we create it. In other languages like C++ that are statically typed, we have to declare the type of a variable when we create it. If this seems confusing, don't worry about. All you need to know is that Lua will figure out the type of a variable for us. Here are some examples of types in Lua:

```lua
local number = 2 -- number
local string = "Hello, World!" -- string
local boolean = true -- boolean
```
### Functions

Functions are blocks of code that we can define and give a name to. We can then call this name to run the block of code. I made a recipe analogy earlier, and this is a good time to bring it back. Functions are like recipes. We can write a recipe for a cake, and then we can call the recipe to make a cake. Here is an example of a function in Lua:

```lua
function sayHello()
    print("Hello, World!")
end

function callFunction()
    sayHello()
end
```

In the example above, we've defined a function called `sayHello` that prints "Hello, World!" to the console. We've then defined another function called `callFunction` that calls the `sayHello` function. When we call the `callFunction` function, it will print "Hello, World!" to the console.

### Control Structures

Control structures are logic chains that we can use to control the program. They are essentially points in our code where the computer reaches a condition, and then makes a decision based on that condition. Here are some examples of control structures in Lua:

```lua
local number = 2 + 3
local number2 = 5
local number3 = 6

if number == number2 then
    print("Number is equal to Number2")
elseif number == number3 then
    print("Number is equal to Number3")
else
    print("Number is not equal to Number2 or Number3")
end
```

In the example above, we've used an `if` statement to check if `number` is equal to `number2`. If it is, it will print "Number is equal to Number2". If it's not, it will check if `number` is equal to `number3`. If it is, it will print "Number is equal to Number3". If it's not, it will print "Number is not equal to Number2 or Number3".


#### Conditional Operators

Conditionals are a type of operator that we can use to make decisions in our code. They are essentially a way to check if something is true or false. Here are some examples of conditionals in Lua:

```lua
local number = 2
local number2 = 2

print(number == number2) -- compares if number is equal to number2
print(number ~= number2) -- compares if number is not equal to number2
print(number > number2) -- compares if number is greater than number2
print(number < number2) -- compares if number is less than number2
print(number >= number2) -- compares if number is greater than or equal to number2
print(number <= number2) -- compares if number is less than or equal to number2
```

### Tables

Tables are a way to store multiple values in a single variable. They are similar to arrays in other programming languages. Here are some examples of tables in Lua:

```lua
local table = {1, 2, 3, 4, 5}
local table2 = {"Hello", "World"}
local table3 = {name = "Goosifer", gender = "male"}
```

In the example above, we've created three tables. The first table contains numbers, the second table contains strings, and the third table contains key-value pairs.

To access these values, we can use the following syntax:

```lua
print(table[1]) -- 1
print(table2[1]) -- Hello
print(table3.name) -- Goosifer
print(table3.gender) -- male
```

### Loops

Loops are a way to run the same block of code over and over again. This is useful when we want to iterate over a table, or when we want to run a block of code a certain number of times. Here are some examples of loops in Lua:

Example 1:
```lua
for i = 1, 5 do
    print(i) -- 1, 2, 3, 4, 5
end
```

Example 2:
```lua
local table = {1, 2, 3, 4, 5}
for i = 1, #table do
    print(table[i]) -- 1, 2, 3, 4, 5
end
```

Example 3:
```lua
local table = {name = "Goosifer", gender = "male"}
for key, value in pairs(table) do
    print(key, value) -- name, Goosifer
end
```

### Bringing it All Together

Here is an example of a simple Lua script that uses all of the concepts we've covered so far:

```lua
local number = 2
local hello = "Hello, World!"

function sayHello()
    if number == 2 then
        print(hello) -- Hello, World!
    else 
        for i = 1, 5 do
            print(i) -- 1, 2, 3, 4, 5
        end
    end
end

sayHello() -- executes the sayHello function
```

In the example above, we've created a variable called `number` and assigned it the value of `2`. We've also created a variable called `hello` and assigned it the value of `"Hello, World!"`. We've then defined a function called `sayHello` that checks if `number` is equal to `2`. If it is, it will print `hello`. If it's not, it will print the numbers `1` through `5`. It's a useless program, but it's a good example to show the power of using a programming language to control the game. As you get better, you can create more complex scripts that do more interesting things.


### Conclusion

There is more to Lua as a programming language, but this guide should give you a good starting point to get started with Zoo Tycoon 1 scripting. As mentioned before, I highly recommend checking out the [official documentation](https://www.lua.org/manual/5.4/) for more information.

## Scripting in Zoo Tycoon 1

Now that we have a basic understanding of Lua, we can start scripting in Zoo Tycoon 1. The game on its own doesn't support Lua scripting, so we will need to use EMU API to do this. EMU API is a tool that gives us scripting capabilities for Zoo Tycoon 1. You can download the latest version on its [GitHub page](https://github.com/openztcc/EMU). Instructions to install and use EMU API can be found on the GitHub page.

Note that Lua scripts for EMU API carry the `.emu` file extension, so if you're using Visual Studio Code, you might want to set up syntax highlighting for this file type so that your editor color-codes your scripts and you can tell what are comments, strings, numbers, functions, etc. You can check out the [Using Visual Studio Code](../tool-guides/visual-studio-code.md) guide for more information.


The next few guides in this series will cover a few different examples of how we can leverage our new scripting knowledge to create new kinds of mods for the game.