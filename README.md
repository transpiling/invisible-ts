Invisible Type System
---------------------

This is (concept of)
> **Invisible static type checker for JavaScript**

It is the child of TypeScript, but more simple and compatible with standards and Babel transpiler. Implementation mechanism is similar with [asm.js][].

### Use case

It can be utilised if you just want try to use static types, if you have no intent to rewrite all your code on TypeScript (or FlowType) yet.

## Features

#### ✔ Invisible Type checking    
Type-checking without type declarations! ([Type Inference][]).    
As a bonus, your code will get many of type safety with your standard javascript transpiler or interpreter, even if you doesn't use Invisible TS checker.
  
#### ✔ Easy to learn    
No need for big documentation. Invisible TS is not a programming language, it designed just to bring type safety to javascript.
  
#### ✔ Intuitive, not new syntax    
Even if developer doesn't know anything about [type systems][], hi can assume how client code will work, because Invisible TS using standard js:    
Type declarations hidden in default values, described by javascript operators (void, ||, &&, undefined, null, Number, Boolean, String, Object).
  
#### ✔ Variable Type Safety and Inline TypeScript
(not implemented yet)    
You can start using typescript functionality in babel-based project with low cost.

## Syntax

```js
     
     'use strict type'
     
     // Variables //
     
     let n = Number()
     let i = 0 // the same as Number()
     let s = "string"
     let b = Boolean() // initial value - false, can't be undefined or null
     let b3 = void Boolean // initial value - undefined
     let any = undefined
     let anyOf = Number || String || Boolean || Object || null || undefined

     let uninitiated = void HTMLElement
     let theSame  = HTMLElement && undefined
     let nullable = HTMLElement && null
     
     // Functions //
     
     // define function, that return boolean and require one argument:
     void Boolean
     function invert( value = Boolean() || TypeError() ){
         return ! value
     }
     
     // Objects & Classes //
     
     let o = Object()
     let obj = {requiredProperty: HTMLCollection && null, 
                optionalProperty: undefined && "string"}
    
```

## Rules

* If variable can change type, it should be declared before.
* [?] Default values should be declared for all variables and arguments.

### Custom types and type casting

How to cast types in javascript? There is one standard solution - you can call constructor as function, without operator new:

    let b = Boolean("false")
    console.log(b, typeof b) // true "boolean"

So, to describe how to convert one type to another, you can check ´this´ in constructor.


## Why not TypeScript?

1. Typescript has many parts - it is programming language, type-checker and transpiler all-in-one. Invisible TS is only type-checker (it doesn't extend the language, like typescript with interfaces and polymorphism).
2. It introduce special syntax, and it doesn't look good with ES6 defaults and destructuring.

## Why not Flowtype?

1. Flowtype utilize special syntax to declare types (just like typescript), so typed code can't be simply copy-pasted into untyped javascript.
2. It [doesn't fully][] support [Type Inference][inference-ts], mechanism used to hide type declarations.
3. It hard to extend: It wasn't wrote on javascript.

## Download/Install

This is just concept :)     
Please star this repo and I will create type-checker with ESLint or/and Babel plugin.

[Type Inference]: https://en.wikipedia.org/wiki/Type_inference
[inference-ts]: https://www.typescriptlang.org/docs/handbook/type-inference.html
[doesn't fully]: https://github.com/facebook/flow/issues/5693
[type systems]: https://en.wikipedia.org/wiki/Type_system
[asm.js]: https://en.wikipedia.org/wiki/Asm.js
