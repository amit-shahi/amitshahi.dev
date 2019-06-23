---
templateKey: blog-post
title: Big 'O' Notation
date: 2019-06-23T07:32:00.000Z
description: >+
  Big O notation is used in Computer Science to describe the performance or
  complexity of an algorithm. Big O specifically describes the worst-case
  scenario and can be used to describe the execution time required or the space
  used (e.g. in memory or on disk) by an algorithm.

featuredpost: false
featuredimage: /img/bigonotation.png
tags:
  - Big 'O' Notation
  - Big 'O'
  - Space Complexity
  - Time Complexity
  - Worst-Case Scenario
---
![Big O Complexity Chart](/img/bigocomplexitychart.jpeg "Big O Complexity Chart")

## O(1) - Constant Running Time

O(1) describes an algorithm that will always execute in the same time (or space) regardless of the size of the input data set.

```
bool IsFirstElementNull(List<string> elements)
{
    return elements[0] == null;
}
```

## O(N) - Linear Running Time

O(N) describes an algorithm whose performance will grow linearly and in direct proportion to the size of the input data set. The example below also demonstrates how Big O favours the worst-case performance scenario; a matching string could be found during any iteration of the for loop and the function would return early, but Big O notation will always assume the upper limit where the algorithm will perform the maximum number of iterations.

```
bool ContainsValue(List<string> elements, string value)
{
    foreach (var element in elements)
    {
        if (element == value) return true;
    }

    return false;
}
```

## O(N2) - Quadratic Running Time

O(N2) represents an algorithm whose performance is directly proportional to the square of the size of the input data set. This is common with algorithms that involve nested iterations over the data set. Deeper nested iterations will result in O(N3), O(N4) etc.

```
bool ContainsDuplicates(List<string> elements)
{
    for (var outer = 0; outer < elements.Count; outer++)
    {
        for (var inner = 0; inner < elements.Count; inner++)
        {
            // Don't compare with self
            if (outer == inner) continue;

            if (elements[outer] == elements[inner]) return true;
        }
    }

    return false;
}
```

## O(2^N) - Exponential Running Time

O(2^N) denotes an algorithm whose growth doubles with each addition to the input data set. The growth curve of an O(2^N) function is exponential - starting off very shallow, then rising meteorically. An example of an O(2N) function is the recursive calculation of Fibonacci numbers:

```
int Fibonacci(int number)
{
    if (number <= 1) return number;

    return Fibonacci(number - 2) + Fibonacci(number - 1);
}
```

## O(log N) - Logarithmic Running Time
