# javaspecialists Newsletter Notes

## 002 Anonymous Inner Classes

Initialize a collection in one line of code with anonymous inner class. Example ArrayList:

```
List<String> myList = new ArrayList<String>(3) {{ add("abc"); add("def"); add("ghi"); }};
```

The verbose way:
```
Collection temp_names = new Vector(3);
temp_names.add("abc");
temp_names.add("def");
temp_names.add("ghi");
universityRegistration.addNames(temp_names);
```

Shorter way:
```
universityRegistration.addNames(new Vector(3)
  {{ add("abc"); add("def"); add("ghi"); }});
```

How it works:

Uses a class that extends Vector with an intializer block instead of initialization in the constructor:

```
public class MyVector extends Vector {
  { // initializer block
    add("abc"); add("def"); add("ghi");
  }
  public MyVector() {
    super(3); // to initialise it with a size of 3
  }
}
```
Transform it into an anonymous inner class:
```
Vector myVector =
  new Vector(3) { // defining anonymous inner class
  {
    add("abc"); add("def"); add("ghi");
  }
};
```



### 004 Logging Part 2
How to find out within a method where the method was invoked from?
-> Throw exception, print stacktrace and parse it
