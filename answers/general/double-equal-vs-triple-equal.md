# What is difference between '==' and '===' ?

The biggest difference between '==' and '===' is [type coercion](what-is-type-coercion.md). When you use '===' the statement checks stricly and does not coerce into a different type any part of the statement. Consider the follow.

```javascript
1 === true // returns false as 1 is not stricly equal to true
```

However if you use '==' Javascript will attempt to type coerce. Observe below.

```javascript
1 == true // returns true as 1 is coerced into true
```

Using == is typically bad form since when you are comparing for equality you typically want strict equality.