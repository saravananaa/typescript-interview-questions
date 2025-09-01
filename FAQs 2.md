# TypeScript Interview Questions

URL: https://nabendu82.medium.com/typescript-interview-questions-80d4bb1e9733

Nowadays most modern ReactJS and NodeJS apps are created using TypeScript. Angular was already having it in-built. So, you go for a Reactt, Node or Angular interview, TypeScript questions ill be asked.

## Question 1 — What is TypeScript?

TypeScript is a superset of JavaScript in which you add types to JavaScript. JavaScript is a loosely typed language which leads to lot of types error in production code. With TypeScript developers can catch those error, even before running the code.

## Question 2 — What is explicit and implicit type assignment?

Explicit means writing out the type. Like below -

let firstName: string = "Nabendu";
Implicit means TypeScript will guess the type, based on the value. Like below type will be considered a number

let age = 41;
## Question 3 — Difference between any, unknown and never in TypeScript?

The type of any is used to assign any type of a variable. It will not give error even if you reassign another type. Like below -

let x: any = 10;
x = 'hello'; // No TypeScript error
console.log(x.toUpperCase()); // No TypeScript error
The type unknown is better than type any, because it requires us checking the type before performing operations on value. Like below -

let y: unknown = 10;
// Type assertion needed before using y as number
if (typeof y === 'number') {
    console.log(y.toFixed(2));
}
The type never represents value that never occurs. It is typically used for return statements of function that doesn’t returns properly. Like below -

function throwError(message: string): never {
    throw new Error(message);
}
## Question 4 — How do you give the type of Arrays?

For typing array, we need to give the type as below. In this below example the array can contain type of string only.

const names: string[] = ["Nabendu", "Shikha", "Hriday"];
names.push("Dylan"); // no error
We can also use a readonly keyword, which prevents the array been changed.

const names: readonly string[] = ["Nabendu", "Shikha", "Hriday"];
names.push("Jack"); // Error: Property 'push' does not exist on type 'readonly string[]'.
## Question 5 — What is Type Inference in array?

If we don’t give any type to an array, it will infer the type. Like below -

const numbers = [1, 2, 3]; // inferred to type number[]
numbers.push(4); // no error
## Question 6 — What are tuples?

It is a type array with pre-defined length and types. It is very useful in giving types of mixed array with different types, like below.

let ourTuple: [number, boolean, string];

// initialize correctly
ourTuple = [5, false, 'Coding Hero was here'];
## Question 7 — What are readonly tuples?

If we don’t make a tuple readonly, we can add more items to the one defined and TypeScript will not throw any error, like below.

let ourTuple: [number, boolean, string];

// initialize correctly
ourTuple = [5, false, 'Coding Hero was here'];
//No safety in indexes from 3
ourTuple.push('This is wrong');
Now, to fix it we use the keyword readonly before the type.

let ourTuple: readonly [number, boolean, string];
// initialize correctly
ourTuple = [5, false, 'Coding Hero was here'];
// throws error as it is readonly
ourTuple.push('Coding Hero took a day off');
## Question 8 — How to give the types for Objects?

We can give the type of object by creating another object like structure and specifying the keys and the type of the keys in the object.

const car: { brand: string, model: string, year: number } = {
  brand: "Tata",
  model: "Tiago",
  year: 2016
};
## Question 9 — How to have optional properties in Objects?

To give an optional property or key, we need to add the ? after thet key, like below.

const car: { brand: string, model: string, year?: number } = {
  brand: "Tata",
  model: "Punch"
};
## Question 10 — Explain enum in TypeScript?

An enum is a type of variables which are constants. You have to use the values within it only. The values are numeric by default and starts with 0 and increments by 1.

enum allDirections { North, East, South, West }

let currentDirection = allDirections.North;
console.log(currentDirection);
// logs 0
## Question 11 — What is String enum?

If you want the enum to contain strings instead of the default number, you need to specify the same.

enum allDirections {
  North = "North",
  East = "East",
  South = "South",
  West = "West"
};

let currentDirection = allDirections.North;
console.log(currentDirection);
// logs "North"
## Question 12 — What are Type Aliases?

They allow to define type with a custom name and can be used for all primitive types like string and number and also complex type like objects and arrays. Like below -

type Year = number
type Type = string
type Model = string
type Car = {
  year: Year,
  type: Type,
  model: Model
}

const carYear: Year = 2005
const carType: Type = "Tata"
const carModel: Model = "Tiago"
const car: Car = {
  year: Year,
  type: Type,
  model: Model
};
## Question 13 — What are interfaces?

Interfaces are like type but can be used only for objects. Like below -

interface Square {
   length: number
}

const square: Square {
  length: 20
}
## Question 14 — How to extend interfaces?

Interfaces can be extended with the extend keyword. Like below -

interface Square {
   length: number
}

interface ColorSquare extends Square {
    color: string
}

const square: ColorSquare {
  length: 20,
  color: blue
}
## Question 15 — What are Union types?

Union types are used when the property can be more then one value, like string or number. For this reason, they are also called OR and are used by using | symbol. Like below -

function printSucessCode(code: string | number) {
  console.log(`My success code is ${code}.`)
}
printSucessCode(200);
printSucessCode('200');
## Question 16 — How to give the return type in function?

We can give the return types of functions with : symbol after function name. Like below -

function getSum(): number {
    return 24;
}

function printMessage(): void {
    console.log("Good Morning");
}
## Question 17 — How to give type of parameters in function?

We can give the type of parameters by mentioning them after each parameter with : symbol.

function sum(a: number, b: number) {
  return a + b;
}
## Question 18 — How to give optional, default and rest parameters in function?

With default parameter, we can mark a parameter as optional. Like this, where c is optional and denoted by ?.

function substract(a: number, b: number, c?: number) {
  return a - b -(c || 0);
}
The default values(an ES6 feature), goes after the type/ Like below -

function multiply(a: number, b: number=10) {
  return a * b;
}
The rest parameters(an ES6 feature), are given the type of array, because they convert passed items in array. Like below -

function add(a: number, b: number, ...rest: number[]) {
  return a + b + rest.reduce((acc, curr) => acc+ curr, 0);
}
## Question 19 — What is casting in TypeScript?

Get Nabendu Biswas’s stories in your inbox
Join Medium for free to get updates from this writer.

Enter your email
Subscribe
Casting is the process of overriding a type of a variable. Like in the below example, the type is unknown but is made string while using with the as keyword.

let y: unknown = 'Welcome';
console.log((y as string).length);
We can also use <> in place of as. Both means the same.

let y: unknown = 'Welcome';
console.log((<string>y).length);
## Question 20 — How to give type of a variable in Class?

In this simple example, we have given the type of name as string in a class.

class Developer {
  name: string;
}

const dev = new Developer();
dev.name = "Nabendu";
## Question 21 — What is public, private and protected in TypeScript classes?

Below is the meaning of all -

public — Default if not mentioned and allows the class member to be accessed from anywhere.
private- The class member can be accessed from only within the class.
protected — The class member can be accessed by itself or an inherited class.
Example of public -

class Developer {
  public name: string;
}

const dev = new Developer();
dev.name = "Nabendu";
Example of private. Note that we generally have a get function to access the private member.

class Developer {
  private name: string;

  public constructor(name: string) {
    this.name = name;
  }

  public getName(): string {
    return this.name;
  }
}

const dev = new Developer("Nabendu");
console.log(person.getName());
We can also write the shorthand version of above, by directly adding the private variable in the constructor.

class Developer {
  public constructor(private name: string) {}

  public getName(): string {
    return this.name;
  }
}

const dev = new Developer("Nabendu");
console.log(person.getName());
For protected we need to inherit from a base class, which we do with the extends keyword. Also, we can get data from an interface to a class, using the implements keyword.

interface Shape {
  getArea: () => number;
}
      
class Rectangle implements Shape {
  public constructor(protected width: number, protected height: number) {}

  public getArea(): number {
    return this.width * this.height;
  }
}
      
class Square extends Rectangle {
  public constructor(width: number) {
    super(width, width);
  }
}

const mySq = new Square(20);
console.log(mySq.getArea()); //Logs 400
## Question 22 — What is the readonly keyword in reference to classes in TypeScript?

The readonly keyword prevent a class member from being changed. We generally use readonly with private or protected members.

In the below example, name cannot be changed after the initial definition.

class Developer {
  private readonly name: string;

  public constructor(name: string) {
    this.name = name;
  }

  public getName(): string {
    return this.name;
  }
}

const dev = new Developer("Nabendu");
console.log(person.getName());
## Question 23 — How to implement overriding in classes of TypeScript?

Overriding is an important OOPs concept, where the inherited class overrides a function(mostly) in it’s parent class. We implement the same by using override keyword in the function.

interface Shape {
  getArea: () => number;
}

class Rectangle implements Shape {
  public constructor(protected readonly width: number, protected readonly height: number) {}

  public getArea(): number {
    return this.width * this.height;
  }

  public toString(): string {
    return `Rectangle width is ${this.width} and height is ${this.height}`;
  }
}

class Square extends Rectangle {
  public constructor(width: number) {
    super(width, width);
  }

  public override toString(): string {
    return `Square width is ${this.width}`;
  }
}

const square = new Square(20);
console.log(square.toString()); // Logs - Square width is 20
## Question 24 — What are Abstract classes?

When we declare a base class with abstract keyword, we cannot create objects for the same. In this method, we generally use the methods of the abstract class in a child class.

Also, if we add abstract keyword in front of a function inside base class, we need to create it in the child class. But this is not required for a non-abstract function.

abstract class Polygon {
  public abstract getArea(): number;

  public toString(): string {
    return `Polygon area is ${this.getArea()}`;
  }
}

class Rectangle extends Polygon {
  public constructor(protected width: number, protected height: number) {
    super();
  }

  public getArea(): number {
    return this.width * this.height;
  }
}

const rect = new Rectangle(10,20);
console.log(rect.getArea()); // Logs - 200
console.log(rect.toString());// Logs - Polygon area is 200
## Question 25 — What are Singleton classes.

The Singleton classes are special types of classes, to ensure that we only have one instance of a class.

To make this class, we make the constructor private, preventing the use of new to create objects. Next, we use static method to create a single instance of the class. The example is below -

class Coder {
  private static instance: Coder;

  private constructor() {}

  static getInstance() {
    if (this.instance) {
      return this.instance;
    }
    this.instance = new Coder();
    return this.instance;
  }
}

const c1 = Coder.getInstance();
const c2 = Coder.getInstance();

console.log(c1 === c2); //Logs - true
## Question 26 — What are Generics in TypeScript. Give examples in functions, classes and type aliases.

Generics allows to create type variables which can be used to create classes, functions and type aliases. Here, we don’t have to define the types that they use.

Function example -

function createArray<S, T>(v1: S, v2: T): [S, T] {
  return [v1, v2];
}

console.log(createArray<string, number>('JS', 42)); //Logs - ['JS', 42]
Class example -

class GenericClass<T> {
  private _value: T | undefined;

  constructor(private name: string) {}

  public setValue(value: T) {
    this._value = value;
  }

  public getValue(): T | undefined {
    return this._value;
  }

  public toString(): string {
    return `${this.name}: ${this._value}`;
  }
}
      
const value = new GenericClass<number>('theNum');2
value.setValue(10);
console.log(value.toString()); // theNum: 10
Type aliases example -

type Numberic<T> = { value: T };
const ageValue: Numberic<number> = { value: 40 };
## Question 27 — What is Partial, utility type.

Partial changes all the properties to be optional in an object. In the below example, the interface have width and height. But, we have given only width because ew have made rectPart as Partial.

interface Rectangle {
  width: number;
  height: number;
}
            
let rectPart: Partial<Rectangle> = {}; 
rectPart.width = 100;

console.log(rectPart); // Logs - { width: 100 }
## Question 28 — What is Required, utility type.

Required changes all the properties to be required in an object. In the belo example, the milage is made optional in the interface. But when we had made it Required while creating the object, we are forced to give the milage.

interface Car {
  make: string;
  model: string;
  mileage?: number;
}
            
let myCar: Required<Car> = {
  make: 'Tata',
  model: 'Tiago',
  mileage: 20 // `Required` forces mileage to be defined
};

console.log(myCar); // Logs - { make: 'Tata', model: 'Tiago', mileage: 20 }
## Question 29 — What is Record, utility type.

Record is a shortcut to define an object, with specified key type and value type.

const nameAgeObj: Record<string, number> = {
  'Nabendu': 42,
  'Shikha': 41
};

console.log(nameAgeObj);// Logs - { Nabendu: 42, Shikha: 41 }
## Question 30 — What is Omit, utility type.

Omit removes keys from any object type. Like in the below example, omit have removed age and location from the type, which cannot be defined.

interface Coder {
  name: string;
  age: number;
  location?: string;
}
    
const nabs: Omit<Coder, 'age' | 'location'> = {
  name: 'Nabendu'
};

console.log(nabs); // Logs - { name: 'Nabendu' }
## Question 31— What is Pick, utility type.

Pick removes all the keys from any object, excep the specified keys. Like in the below example, pick have removed age and location from the type, which cannot be defined.

interface Coder {
  name: string;
  age: number;
  location?: string;
}
    
const nabs: Pick<Coder, 'name'> = {
  name: 'Nabendu'
};

console.log(nabs); // Logs - { name: 'Nabendu' }
## Question 32 — What is Exclude, utility type.

Exclude is used to removes types from a union. Like in the below example boolean cannot be used, because it is excluded.

type Marks = string | number | boolean;

const value: Exclude<Marks, boolean> = '56';

console.log(typeof value); // Logs - string
## Question 33 — What is Readonly, utility type.

Readonly is used to create a type which cannot be modified once assigned a value. Like in the below example once we had assigned a value to the person object, it cannot be changed.

interface Person {
    name: string;
    age: number;
}

const person: Readonly<Person> = {
    name: "Nabendu",
    age: 42,
};

person.name = 'Parag'; // Logs error
## Question 34 — What is Nullish Coalescence.

Nullish Coalescence is used in expressions which have a fallback feature while dealing with null or undefined. It is used with the ?? operator.

Like in the below example mileage can be number, null or undefined. Here, we are using ?? to make it NA when the value is null or undefined.

function showMileage(mileage: number | null | undefined) {
  console.log(`Mileage: ${mileage ?? 'NA'}`);
}
            
showMileage(null); // Logs 'Mileage: NA'
showMileage(0); // Logs 'Mileage: 0'
showMileage(undefined); // Logs 'Mileage: NA'
