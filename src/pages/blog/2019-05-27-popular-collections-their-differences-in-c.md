---
templateKey: blog-post
title: 'Popular Collections & their differences in C#'
date: 2019-05-26T09:10:46.871Z
description: >-
  We all have worked with different types of collections in C# or other
  programming languages, right? But have we ever thought, why there are so many
  of them? what's the purpose of having different types of collections when they
  are doing the same things. Well, there is more to it than just what we know.
  In this post, I will walk you through popular collections and the reason why
  and when we should use them.
featuredpost: true
featuredimage: /img/collections-in-c-sharp.png
tags:
  - Collections
  - Generics
  - List
  - Hashtable
  - Hashset
  - Dictionary
  - ''
---
![Collections in C#](/img/collections-in-c-sharp.png "Collections in C#")

## List < T >

* It represents a **strongly typed list** of objects that can be accessed by **index**.
* It provides methods to do a **search** 
* it provide out-of-box **sorting** 
* It let us **manipulate** **a list** by doing Add, Remove, and Insert functions
* As it's a **generic class**, it let us create strongly typed collection of value types and reference types.

- - -

**Space & Time Complexity:**

> **Space Complexity**

**Best-Case:**

Lookup -    Insertion -   Deletion - 

**Average-Case:**

Lookup -    Insertion -   Deletion - 

**Worst-Case:**

Lookup -    Insertion -   Deletion - 

> **Time Complexity**

**Worst-Case:**

****

**Advantage:** 

1. The **List**<> takes less time to add strings when compared to **HashSet**<>. The reason behind this is List.Add() simply adds an item to the list whereas HashSet.Add() will skip new item if it (is)equal to one of the existing items. This takes time to execute HashSet.Add() method as compare to List.Add() method.

**Disadvantage:**

1. **List**<> provides slower lookup for the element compare to **HashSet**<>.
2. Removal operation of **List**<> is slower than the **HashSet**<>. The Remove operation also works similar to the Contains operation.

Example:

Add an item to the list

```
List<string> _list = new List<string();
_list.Add("A");
_list.Add("B");
_list.Add(null); // Note: Can't do binary search on null values
_list.Add("1");
_list.Add("2");
```

Remove an item from the list

```
_list.Remove("B");
_list.RemoveAt(1); // Note: 1 is an index of B.
```

Iterate through List collection

```
foreach(var item in _list) {
  Console.WriteLine($"item => "+ item);
}
```

Do a binary search in an ordered list collection, when the searched item is found in the list it returns it's index value otherwise it returns -1. 

```
_list.BinarySearch("1");
```

## HashSet < T >

* We use HashSet<T> when we want to store a list of values, where a value 
* can be **null**
* and can be **non-unique**
* It's a generic class

- - -

**Space & Time Complexity:**

> **Space Complexity**

**Best-Case:**

Lookup -    Insertion -   Deletion - 

**Average-Case:**

Lookup -    Insertion -   Deletion - 

**Worst-Case:**

Lookup -    Insertion -   Deletion - 

> **Time Complexity**

**Worst-Case:**

****

**Advantage:** 

1. **HashSet**<> provides faster lookup for the element than the **List**<>.
2. This is because of no duplicate data in the **HashSet**<>. The **HashSet** maintains the Hash for each item in it and arranges these in separate buckets containing hash for each character of item stored in HashSet.
   When the lookup occurs, the **HashSet** hashes it and jumps it to the matching bucket for each character starting from the first character and extracts the element from **HashSet**.
3. Removal operation of HashSet<> is faster than the List<>. The Remove operation also works similar to the Contains operation.

**Disadvantage:**

1. The **HashSet**<> takes more time to add strings when compared to **List**<>. The reason behind this is List.Add() simply adds an item to the list whereas HashSet.Add() will skip new item if it (is)equal to one of the existing items. This takes time to execute HashSet.Add() method as compare to List.Add() method.

Example:

Add an item to the HashSet

```
HashSet<string> _hashSet = new HashSet<string();
_hashSet.Add("Wordpress");
_hashSet.Add("CMS");
_hashSet.Add(null);
_hashSet.Add("CMS"); // Adding duplicate value
```

Remove an item from the HashSet

```
_hashSet.Remove("Wordpress");
_hashSet.RemoveWhere(c=>c.Contains("CMS");
```

Iterate through HashSet collection

```
foreach(var item in _hashSet) {
  Console.WriteLine($"item => "+ item);
}
```

There are no binary search available for HashSet, instead we can use .Contains() to lookup an item in a HashSet. 

```
_hashSet.Contains("Wordpress");
```

**NOTE:**

There is a performance benefit of using HashSet<T> over List<T>

## Dictionary < TKey, TValue >

* It's a **generic class** which **stores Key-Value pairs** 
* **cannot have null keys**
* **can have duplicate**  and **null values**
* keys **must be unique** otherwise it will throw an exception at runtime. This can be avoided by using TryGetValue() method.

- - -

**Space & Time Complexity:**

> **Space Complexity**

**Best-Case:**

Lookup -    Insertion -   Deletion - 

**Average-Case:**

Lookup -    Insertion -   Deletion - 

**Worst-Case:**

Lookup -    Insertion -   Deletion - 

> **Time Complexity**

**Worst-Case:**

****

**Advantage:** 

**Disadvantage:**

- - -

Example:

Add an item to the Dictionary

```
Dictionary<int, string> _dictionary = new Dictionary<int, string();
_dictionary.Add(1, "Wordpress");
_dictionary.Add(2, "CMS");
_dictionary.Add(3, null); // can have null values
//_dictionary.Add(3, "Three"); // can't have duplicate key
_dictionary.Add(4, "CMS"); // can have duplicate value
```

Remove an item from the Dictionary

```
_dictionary.Remove(1); // Pass in the key
_dictionary.Remove<TKey, TValue>(string key, out string value);
```

Iterate through Dictionary collection

```
foreach(KeyValuePair<int, string> item in _dictionary) {
  Console.WriteLine($"{item.Key} : => {item.Value ?? "null"}");
}
```

There are no binary search available for Dictionary, instead we can use .Contains() to lookup an item in a Dictionary. 

```
_dictionary.Contains("Wordpress");
```

## Hashtable

* It's a non-generic class which **stores Key-Value pairs** 
* where **Key cannot be duplicated**
* **It doesn't allow null keys**
* As it is synchronized, it comes with it's cost. **Only one thread can access it in one time**.
* It **prints the values in a reverse order** (like LIFO)

- - -

**Space & Time Complexity:**

> **Space Complexity**

**Best-Case:**

Lookup -    Insertion -   Deletion - 

**Average-Case:**

Lookup -    Insertion -   Deletion - 

**Worst-Case:**

Lookup -    Insertion -   Deletion - 

> **Time Complexity**

**Worst-Case:**

****

**Advantage:** 

**Disadvantage:**

- - -

Example:

Add an item to the Hashtable

```
Hashtable  _hashTable = new Hashtable();
_hashTable.Add(1, "One");
_hashTable.Add(2, "CMS");
_hashTable.Add(3, null); // can add null values
_hashTable.Add("B", "An Alphabet"); // can add key as any type
_hashTable.Add(4, "Duplicate Key"); // Can't add duplicate key "4"
_hashTable.Add(null, "Adding null"); // Can't add "null" as a key
```

Remove an item from the HashSet

```
_hashTable.Remove(object key); // object can be of any type - like below
_hashTable.Remove(1);  
_hashTable.Remove("B"); 
```

Iterate through Hashtable collection

```
foreach(DictionaryEntry item in _hashTable.Values) {
  Console.WriteLine($"{item.Key} : => {item.Value ?? "null"}");
}
```

There are no binary search available for HashSet, instead we can use .Contains() to lookup an item in a HashSet. 

```
_hashSet.Contains("Wordpress");
```
