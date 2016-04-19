# Evolution of a Lambda (Intermediate)

```Java
List<T> someList = ...

collect.sort(someList, (T e1, T e2){ return e1.field().compareTo(e2.field());})
```
* Better, more concise. However still room for improvement

```Java
List<T> someList = ...
collect.sort(someList,(T e1, T e2) -> e1.field().compareTo(e2.field()))
```

