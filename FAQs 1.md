Here is a compilation of common TypeScript interview questions and their answers: 
# Basic Concepts: 

## What is TypeScript? 

TypeScript is a statically typed superset of JavaScript that compiles to plain JavaScript. It adds optional static typing, classes, interfaces, and other features to enhance code quality and maintainability. [1]  

## Why use TypeScript over JavaScript? 

TypeScript offers enhanced type safety, better tooling support (autocompletion, error checking in IDEs), improved code maintainability, and facilitates collaboration in larger projects. 

## Explain Type Inference in TypeScript. 

Type inference is TypeScript's ability to automatically deduce the type of a variable or expression when a type annotation is not explicitly provided. 

## What are the basic types in TypeScript? 

## Primitive types include number, string, boolean, null, undefined, symbol, and bigint. Other types include any, unknown, void, never, object, arrays, tuples, and enums. 

## What is the any type and when should it be used? 

The any type allows a variable to hold values of any type, effectively opting out of type checking. It should be used sparingly and only when the type is truly unknown or when working with dynamic data where type checking is not feasible. [2]  

## What is the unknown type and how does it differ from any? 

unknown is a safer alternative to any. While it can hold any value, you must perform type narrowing (e.g., using typeof or instanceof) before performing operations on an unknown typed variable. 

## Explain Interfaces in TypeScript. 

Interfaces define the shape of an object, specifying the properties and methods an object must have. They are used for type checking and do not generate any JavaScript code at runtime. 

## Explain Enums in TypeScript. 

Enums (enumerations) allow defining a set of named constants. They can be numeric, string-based, or heterogeneous. 

## What is the tsconfig.json file? 

This file configures the TypeScript compiler, specifying options like target JavaScript version, module system, strictness flags (e.g., noImplicitAny), and file inclusion/exclusion. 

# Intermediate Concepts: 

## Explain Modules in TypeScript. 

Modules are a way to organize and encapsulate code, promoting reusability and preventing global namespace pollution. They can be internal (namespaces) or external (using import/export). 

## What are Decorators? 

Decorators are special kinds of declarations that can be attached to classes, methods, accessors, properties, or parameters. They provide a way to add metadata or modify the behavior of these declarations. 

## Explain Mixins in TypeScript. 

Mixins are a pattern for composing classes by combining simpler partial classes. They allow for code reuse and building complex classes from reusable components. 

## What are Conditional Types? 

Conditional types allow you to define a type based on a condition, using the extends keyword in a type expression. 

## What is the never type and when is it used? 

The never type represents values that will never occur. It is typically used for functions that throw an error or enter an infinite loop, or for exhaustive type checking in conditional types. 

# Advanced Concepts: 

## How do you manage complex types across multiple files in large-scale TypeScript projects? 

Utilize TypeScript's module system (e.g., export and import statements), organize types into dedicated files, and potentially use barrel files (e.g., index.ts) for cleaner exports. 

## How do you ensure type safety when working with external services or REST APIs? 

Define interfaces or types that represent the expected structure of API responses, and use these types to validate the data received from external services. 

Discuss the differences between extends and implements in TypeScript. 

extends is used for class inheritance, where a subclass inherits properties and methods from a parent class. implements is used by a class to declare that it adheres to the contract defined by an interface. [3]  

AI responses may include mistakes.

[1] https://coderpad.io/interview-questions/typescript-interview-questions/[2] https://www.naukri.com/code360/library/typescript-interview-questions[3] https://dev.to/m_midas/30-frontend-interview-questions-typescript-12c2
