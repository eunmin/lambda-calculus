# Lambda Calculus

## Expressions

```
λ x . x
```

```javascript
function(x) {
  return x;
}
```

```
y x
```

```javascript
y(x);
```

```
y x z
```

```javascript
y(x(z));
```

```
λ x . (λ y . y x)
```

```javascript
function(x) {
  return function(y) {
           return y(x);
         };
}
```

```
λ x y . y x
```

```javascript
function(x, y) {
  return y(x);
}
```

```
(λ x . x) y
```

```javascript
(function(x) {
   return x;
})(y);
```

```
(λ x . x) (λ x . x)
```

```javascript
(function(x) {
  return x;
})(function(x) {
  return x;
});
```

## α-conversion

```
λ x . x == λ y . y
```

```
λ x . x != λ x . y
```

```
(λ x . x) (λ x . x) == (λ x . x) (λ y . y)
```

## β-reduction

```
(λ x. x) y
y
```

```
(λ x . x) (λ y . y)
λ y . y
```

```
(λ x y . x y) (λ x . x) (λ x . x)
(λ x . x) (λ x . x)
λ x . x
```

```
(λ x y . x y) (λ x . x) (λ x . x)
(λ x . x) (λ x . x)
λ x . x
```

## Church Numeral

```
λ s z . z           0
λ s z . s z         1
λ s z . s (s z)     2
λ s z . s (s (s z)) 3
```

## +

```
λ x y. (λ s z . (x s (y s z)))
```

```
1 + 2

(λ x y. (λ s z . (x s (y s z))))(λ s2 z2 . s2 z2)(λ s3 z3 . s3 (s3 z3))
λ s z . (λ s2 z2 . s2 z2) s ((λ s3 z3 . s3 (s3 z3)) s z))
λ s z . s ((λ s3 z3 . s3 (s3 z3)) s z))
λ s z . s (s (s z))
```

## Boolean

```
λ t f . t           true
λ t f . f           false
```

## Condition

```
λ b t f . b t f
```

```
if true
  1
else
  2

(λ b t f . b t f)(λ t f . t)(λ s z . s z)(λ s z . s (s z))
(λ t f . t)(λ s z . s z)(λ s z . s (s z))
λ s z . s z
```

## Loop

```
λ y . (λ x . y (x x)) (λ x . y (x x))
```

```
Y f

(λ y . (λ x . y (x x)) (λ x . y (x x)))f
(λ y . (λ x2 . y (x2 x2)) (λ x3 . y (x3 x3)))f
(λ x2 . f (x2 x2)) (λ x3 . f (x3 x3))
f (λ x3 . f (x3 x3)) (λ x3 . f (x3 x3))
f Y f
```
