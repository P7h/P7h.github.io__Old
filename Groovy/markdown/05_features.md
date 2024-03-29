## Groovy Features

* Automatic imports
* Import aliasing
* Optional semicolons & parens
* Optional return statements
* Optional datatype declaration
* Operator overloading
* Safe dereferencing
* Autoboxing
* Groovy Truth
* Embedded Quotes & Heredocs
* GStrings
* POJO vs. POGO

---V

* Automatic imports

```groovy
import java.lang.*
import java.util.*
import java.net.*
import java.io.*
import java.math.BigInteger
import java.math.BigDecimal

import groovy.lang.*
import groovy.util.*
```

* Import aliasing

```groovy
import java.text.SimpleDateFormat as SDF
SDF sdf = new SDF("MM/dd/yyyy")
println sdf.format(new Date())
```

---V

* Optional semicolons and parentheses
* Optional return statements

```groovy
firstName = "James"
lastName = "Strachan"

String getFullName() {
  "${firstName} ${lastName}"
}
println getFullName()
```

---V

* Optional datatype declaration
* Operator overloading

```groovy
def date = new Date()
date.next()
(1..3).each { 
	println date++
}
```

---V

* Safe dereferencing

Groovy

```groovy
def str = "A String"
println str.size()

str = null
str.size() // Caught: java.lang.NullPointerException: Cannot invoke method size() 
           // on null object at ConsoleScript3.run(ConsoleScript3:5)
println str?.size()
```

---V
* Safe dereferencing

Java

```java
if (order != null) {
    if (order.getCustomer() != null) {
        if (order.getCustomer().getAddress() != null) {
            System.out.println(order.getCustomer().getAddress());
        }
    }
}
```
<br>
Groovy

```groovy
println order?.customer?.address
```

---V

* Autoboxing

```groovy
def someNumber = 2
println someNumber.class

//Assign the same variable a different value / datatype.
someNumber = 2.0d
println someNumber.class
```

---V

* Groovy Truth

```groovy
//true
if(1) // any non-zero value is true
if(-1)
if(!null) // any non-null value is true
if( "John" ) // any non-empty string is true
Map family = [dad: "John" , mom: "Jane" ]
if(family) // true since the map is populated
String[] sa = new String[1]
if(sa) // true since the array length is greater than 0
StringBuilder sb = new StringBuilder()
sb.append( "Hi" )
if(sb) // true since the StringBuilder is populated

//false
if(0) // zero is false
if(null) // null is false
if( "" ) // empty strings are false
Map family = [:]
if(family) // false since the map is empty
String[] sa = new String[0]
if(sa) // false since the array is zero length
StringBuilder sb = new StringBuilder()
if(sb) // false since the StringBuilder is empty
```

---V

* Embedded Quotes

```groovy
def s1 = 'You either die a "hero" or you live long enough to see yourself become the "villain".'
def s2 = "You either die a 'hero' or you live long enough to see yourself become the 'villain'."
def s3 = "You either die a \"hero\" or you live long enough to see yourself become the \"villain\"."
```

* Heredocs

```groovy
String groovyHereDocs1 = """Harvey said "You either die a hero or 
you live long enough to see yourself become the villain.""""
def groovyHereDocs2 = '''You either die a hero or 
you live long enough to see yourself become the villain.'''
println groovyHereDocs2.class
```
* GStrings

```groovy
def firstName = "James"
def lastName = "Strachan"
println "Ahoy ${firstName} ${lastName}, today is ${new Date()}"
```

---V

* POJO

```java
public class Person {

	private String firstName;
	private String lastName;

	public String getFirstName() {
		return firstName;
	}

	public void setFirstName(String firstName) {
		this.firstName = firstName;
	}

	public String getLastName() {
		return lastName;
	}

	public void setLastName(String lastName) {
		this.lastName = lastName;
	}

	public String toString() {
		return firstName + " " + lastName;
	}
}
Person person = new Person();
person.setFirstName("James");
person.setLastName("Strachan");
  
System.out.println("Name: " + person);
```

---V

* POGO

```groovy
class Person {
    String firstName
    String lastName
    String toString() {
        firstName + " " + lastName
    }
}
//One way of instantiating an object in Groovy.
def person01 = new Person()
person01.firstName = "James"
person01.lastName = "Strachan"
println "Name: " + person01
```

```groovy
//Another way of instantiating an object in Groovy.
person01.with {
    firstName = "Guillaume"
    lastName = "Laforge"
}
println "Name again: " + person01
```

```groovy
//Yet another way of instantiating an object in Groovy.
def person02 = new Person(lastName: "Rocher", firstName: "Graeme")
println "Name yet again: " + person02
```

---V

* Groovy coding guidelines

[Groovy style and language feature guidelines for Java developers](http://groovy.codehaus.org/Groovy+style+and+language+feature+guidelines+for+Java+developers)