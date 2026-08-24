# INTRODUCTION

**TypeScript** is a strongly typed programming language built on top of JavaScript. It adds **static typing** and other features to JavaScript, which helps developers catch errors during development instead of finding them at runtime.

TypeScript code is eventually converted into **JavaScript**, so it can run anywhere JavaScript runs.

### Benefits of TypeScript

* **Static Type Checking** — Detects many errors during development.
* **Better Code Completion** — Provides better autocomplete and suggestions in code editors.
* **Easy Refactoring** — Makes it safer and easier to modify large codebases.
* **Better Readability** — Types make the purpose and expected structure of code clearer.
* **Better Maintainability** — Helps keep large applications easier to understand and maintain.
* **JavaScript Compatible** — Existing JavaScript code can be used with TypeScript.

### Behind The Scenes

When **TypeScript** code is compiled, it goes through several stages before JavaScript is generated.

* **Lexer** — Reads the source code and breaks it into small meaningful units called **tokens**.

* **Parser** — Takes these tokens and builds an **Abstract Syntax Tree (AST)** that represents the structure of the code.

* **Binder** — Takes the AST and connects declarations with their corresponding symbols. It creates information such as the **symbol table**, **parent relationships**, and **control-flow information**.

* **Checker** — Performs **type checking** and semantic analysis. It checks whether the code follows TypeScript's type rules and reports type-related errors.

* **Emitter** — Generates the output files. For example, it converts TypeScript code into **JavaScript** and can also generate files such as **declaration files (`.d.ts`)** and **source maps**, depending on the compiler configuration.

### Simple Flow

```text
TypeScript Code
      ↓
    Lexer
      ↓
    Parser
      ↓
     AST
      ↓
    Binder
      ↓
    Checker
      ↓
    Emitter
      ↓
JavaScript / Other Output Files
```