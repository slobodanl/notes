_Written by: Reza Shams Amiri_
# main

## Streams

- **Example 1:**
``` java
List<String> list = people.stream().map(Person::getName).collect(Collectors.toList());
```
``` java
val list = people.map { it.name }
// toList() not needed
```
- **Example 2:**

``` java
String joined = things.stream()
                       .map(Object::toString)
                       .collect(Collectors.joining(", "));
int total = employees.stream()
                      .collect(Collectors.summingInt(Employee::getSalary)));
Map<Department, List<Employee>> byDept
     = employees.stream()
                .collect(Collectors.groupingBy(Employee::getDepartment));
```

``` java
val joined = things.joinToString(", ")
val total = employees.sumBy { it.salary }
val byDept = employees.groupBy { it.department }
```

- **Example 3:**
``` java
    public static List<MyAxisCompanySize> fromNames(List<String> names) {
        return names.stream().map(MyAxisCompanySize::fromName).collect(Collectors.toList());
    }
```

``` java
fun fromNames(names: List<String>): List<MyAxisCompanySize> {
    return names.map { Companion.fromName(it) };
}
```

* * *
Creation date: _2019-04-05_
