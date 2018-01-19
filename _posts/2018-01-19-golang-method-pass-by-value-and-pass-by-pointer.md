---
layout: post
title: pass by value vs pass by pointer
---

Golang method pass by value vs pass by pointer
===================

Pass by value vs Pass by pointer
-------------
Golang defines a method to any type by add an extra parameter (call ***receiver***) between keyword ***func*** and the function name.

There are two types of receivers in Go: ***value receivers*** and ***pointer receivers***.

For ***value receiver***, Go always make a copy of the passing value. Actions inside the method only manipulate on the copy. It therefore won't make value change to the original one.

For ***pointer receiver***, Go make a copy of the pointer, which points to the same address in memory shared between pointers. So, it changes passing value.

Let's have a simple example to show how this works:

```
type name struct {
	firstname string
	lastname  string
}

func (n name) passvalue(first string) {
	n.firstname = first
}

func (n *name) passpointer(first string) {
	n.firstname = first
}

func main() {

	n := name{"donald", "ryan"}
	fmt.Println(n)

	n.passvalue("bill")
	fmt.Println(n)

	n.passpointer("bill")
	fmt.Println(n)
}
```


Running this piece of code, we should see some message like: 
```
{donald ryan}
{donald ryan}
{bill ryan}
```

There are two different methods value receiver and pointer receiver.  When we pass a name value type to method passvalue, it made a copy the n. Even thought it assign a new string value to firstname, it does not affect to n after method is returned. Next, when we pass a name pointer type to passpointer, the change it made to firstname inside the method takes affection outside the method. 

Predetermined choice
-------------
**Cases that we have to pass value:**

 - If we need to change the value, we have to pass the value into the method.
 - If we pass a slice or a map, we should pass by value as it won't make a whole copy of the data in memory.

**Cases that we have to pass pointer :**

 - if we need to pass a big struct or a big array, we should pass by
   pointer to avoid copying the whole data in memory.
