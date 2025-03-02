
2024-08-16 23:19

Tags: #Cpp_Intro

# Good Practises to Code in C++

### General Important Points

- **Write in a clear and consistent coding style.** You can see some examples of my code in the samples from Assignment 1 and the sample from the Diagnostic test. This is not the exact style you need to follow, but pick a style and stick with it; all of your submitted code should be formatted the same way.
- **Code should be self-documenting.** Variables should be sensibly named, function names descriptive of their purpose. Reserve comments for places where clarification is valuable; if you have a long piece of code and it is hard to tell what it does, consider splitting it up into several functions whose names will describe what is going on.
- **Keep your headers clean**. Put the absolute minimum required in your headers for your interface to be used. Anything that can go in a source (.cpp) file should. Don’t #include any system headers in your .h files that are not absolutely required in that specific file.
- **Don’t expose your classes’ private parts**. Keep as much of your classes private as possible. All data members should be private; mark them as such by using a leading underscore: int someVariable; You can then write the getter/setter functions for this variable as int someVariable() const; and int& someVariable( int value );. Avoid friend functions.
- **Use const wherever possible.** All member functions that do not modify their object should be const. If your function takes a reference to an object and does not modify that object, you should be passing a const reference.
- **Write portable code.** Don’t use any very compiler-specific features or depend on long or unsigned types being a particular size. Prefer to use size_t for array indexing, especially when dealing with the STL.
- **Don’t leak memory.** Every heap allocation using new should have a corresponding delete.

### Classes in C++

Follow the rule of three. If your class needs a non-trivial destructor, you should also either implement or disable the copy constructor and copy assignment operators. (Furthermore, if you want your data to have the ability to be moved cheaply, also define the move constructor and move assignment.)
Don’t use global data. Instead, encapsulate it in a class and design your interfaces effectively.
Use the constructor initializer list.

Other

Prefer using nullptr to NULL.
Prefer using auto as long as it helps clarity. For example, auto dirPtr = Directory::create( "home" ); is probably better than declaring the type of dirPtr. Refer to Herb Sutter’s post on using auto.
Prefer uniform initialization syntax. You should be constructing objects with curly braces whenever possible, like so: auto someObj = SomeObject{};.
Associate asterisks and ampersands with the variable name, not data type. Declare your pointers like 
```c++
int *a, *b; 
```
and references like
```c++
int &foo = other;
```
Do take advantage of the standard library. Generally don’t try to rewrite data structures and algorithms that have already been implemented well in the standard library unless you have a good reason.


# References
---


	