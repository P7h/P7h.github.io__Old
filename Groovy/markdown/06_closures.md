## Closures
* Not to be confused with [Clojure](http://clojure.org), another JVM based dynamic programming language. 
* Closure is a free-standing, named block of code.
* It is a behavior that doesn’t have a surrounding class.
* Helps in greater flexibility.
* Metaprogramming to enhance existing libraries.
* As of this writing, Java does not have this feature.
* Java 8 is scheduled to come with this most wanted feature coined as [Lambdas](http://docs.oracle.com/javase/tutorial/java/javaOO/lambdaexpressions.html) in March, 2014.

---V

* Closures without any parameters

```groovy
def x = 5, y = 6;
def printNum {
    println x + " " + y
}
printNum()
```
<br>

* Closures with parameters

```groovy
def printSum = { a, b -> 
	print a + b
}
printSum 5, 7
```

---V

* **Traditional mainstream languages**

Data can be stored in variables, passed around, combined in structured ways to form more complex data; code stays put where it is defined.

* **Languages supporting closures**

Data _and code_ can be stored in variables, passed around, combined in structured ways to form more complex algorithms and data.

```groovy
doubleNum = { 
    num -> num * 2
}
assert doubleNum(3) == 6

def processThenPrint = { num, closure ->
    num = closure(num);
}
assert processThenPrint(3, doubleNum) == 6
assert processThenPrint(10) { it / 2 } == 5
```

---V

### Implicit variables

* A Closure that takes a single argument may omit the parameter definition of the Closure.

```groovy
def printStr = { 
	print it
}
printStr "Print but with a custom method"
```
<br>

```groovy
String.methods.each {
    println it
}
```

* _More about Closures in List and Map Comprehensions later._

---V

### [Currying](http://en.wikipedia.org/wiki/Currying)

* Transform function with particular number of parameters and returns a function with some of the parameter values fixed, creating a new function.
* Curry as many parameters as required.
* The first curry call fills in the leftmost parameter.
* Each subsequent call fills in the next parameter to the right.

```groovy
/* Tax calculation example */

def calculateTax = { taxRate, amount ->
	amount + (taxRate * amount)
}

def tax = calculateTax.curry(0.1)

(10..15).each {
	println "Total cost: ${tax(it)}"
}
```

---V

### Loop variants

```groovy
def result = ''
def compute = { 
    if (!it) {
        result = '0'
    } else {
        result += it
    }
}

5.times compute
assert '01234' == result

0.upto 7, compute
assert '01234567' == result

0.step 10, 2, compute
assert '02468' == result
```