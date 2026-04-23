# Loose Equality vs Strict Equality

## Loose Equality

Compares two values for equality after performing type conversion if necessary. This can lead to unexpected results (implicit Type Coercion), especially when comparing values of different types.

```js
"5" == 5      // true (string "5" is converted to number 5)
0 == false    // true (false is converted to 0)
null == undefined // true
[] == ''  //true
[] == ![]  //true
```

> Type coercion follows some ECMA Script rules for == operator. Opeartors are coerced based on operator precedence. (Paranthesis >> !,unary >> ** >> *,/,% >> +,- >> Equality >> && >> assignment).

If Any Operand is:

| Operand Type -> Converted to |   Conversion Rule    |
|---------------------   |----------------------------|
| Boolean -> Number      |                            |
| Object -> Primitive    | using valueOf() toString() | 
| String -> Number       |                            |

If both sides are Primitives of same data type, comparison is done & coercion stops.

## Strict Equality

Compares both value and type, without performing any type conversion. Returns true only if both operands are of the same type and have the same value. Safer & more predictable.

```js
"5" === 5     // false (different types: string vs number)
0 === false   // false (different types: number vs boolean)
5 === 5       // true (same type and value)
```