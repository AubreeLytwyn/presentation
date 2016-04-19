# Talk

* Place your talk here
* Remember, no more than 20 slides
* And exactly 15 seconds per slide
* That gives you exactly 5 minutes for your talk!

# Second slide

```python
def blah():
	"""The blah function demonstrates doc strings"""
	return 42
```	

* The content of the second slide is here
* Here you would talk about the above code
* Hopefully you have a far more interesting example :)

# Third slide

* This is the third slide
* There are 17 more slides after this one
* Good luck with your presentation!


# Thirteenth slide

* Naive long form variation

```Java
List<T> someList = ...

class compareElements implements comparator<T> {
    @override
    Public bool compare(T elem1, T elem2) {
        return elem1.getField().compareTo(elem2.getField())
    }
}

Collections.sort(someList, new compareElements())
```
# Fourteenth slide

```Java
List<T> someList = ...

Collections.sort(someList, (T elem1, T elem2){ return elem1.getField().compareTo(elem2.getField());})
```
* Better, more concise. However still room for improvement

```Java
List<T> someList = ...

Collections.sort(someList, (T elem1, T elem2) -> elem1.getField().compareTo(elem2.getField()))
```
* We can do better still...

# Fifteenth slide

* Final lambda
* Types can be inferred from interface

```Java
List<T> someList = ...

Collections.sort(someList, (elem1, elem2) -> getField().compareTo(elem2.getField()))
```
