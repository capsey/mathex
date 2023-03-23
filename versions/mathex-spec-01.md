# Mathex Specification v0.1

## Table of Contents

- [Introduction](#introduction)
- [Definitions and Terminology](#definitions-and-terminology)
  - [Expression](#expression)
  - [Identifier](#identifier)
  - [Operator](#operator)
  - [Operand](#operand)
  - [Variable](#variable)
  - [Number](#number)
- [Feature Set](#feature-set)
- [Expression Syntax](#expression-syntax)
- [Error Handling](#error-handling)

## Introduction

Mathex is a specification for evaluating mathematical expressions from user input strings. The goal of Mathex is to provide a consistent, easy-to-use, and safe way to evaluate mathematical expressions regardless of programming language.

## Definitions and Terminology

### Expression

Expression is a combination of numbers, variables, and operations that can be evaluated to produce a numerical result.

### Identifier

Identifier is a word or collocation containing only latin letters, digits or underscores, but doesn't start with a digit. They are used as names for user-defined variables and functions.

### Operator

Operator is a symbol or function used to perform a mathematical operation on one or more operands.

- Binary operator is a symbol that takes two operands on both sides and produces one numerical value.
- Unary operator is a symbol that takes one operand from either side and produces one numerical value.
- Function is an identifier followed by a parenthesized list of arguments separated with comma and produces one numerical value.

### Operand

Operand is a number, variable, or parenthesized expression that is operated on by an operator.

### Variable

Variable is an identifier that has constant predefined value. Value of a variable should not be reevaluated each time it is used; for this purpose a zero argument function should be used for explicitness.

### Number

Number is a number literal that consists of four parts:

    45242.21435E+23
    ^____ Integer part
         ^ Period
          ^____ Fractional part
               ^___ Exponent part

The number should always contain either an integer part, a fractional part, or both. If either integer part or fractional part is absent, it is considered to be 0. Period is optional, unless fractional part is not absent.

Exponent part is always optional and is used to represent values in scientific notation. Sign of the exponent is optional and can be `+` or `-`.

## Feature Set

Library implementing this specification must include these features:

- Basic arithmetic operations, including addition, subtraction, multiplication, and division.
- Support for parentheses to specify order of operations.
- Support for variables, which can be defined a value by the user of the library and be used in expressions.
- Support for functions, which can be defined by the user of the library using validator and operator functions and be used in expressions.

## Expression Syntax

The syntax for mathematical expressions in Mathex follows standard mathematical notation. The syntax rules are as follows:

1. Binary operators must always by surrounded with operands.
2. Unary operators must always have an operand on appropriate side.
3. Operands should never stay side by side without a non unary operator or comma between them.
4. Arguments inside function parentheses should be valid expressions.
5. Comma is only allowed inside of function parentheses.
6. Non-ASCII characters are not allowed.

## Error Handling

In case of an error during evaluation it is not recommended to throw an exception or language equivalent, since invalid input is not an exceptional case. Instead, library should return an error code or appropriate alternative.

Here are all kinds of errors that can occur during evaluation:

- Invalid syntax.
- Undefined identifier.
- Incorrect number of arguments for a function call.
- Invalid argument(s) for a function call.
- Division by zero.
- Value is overflowing representation range.
