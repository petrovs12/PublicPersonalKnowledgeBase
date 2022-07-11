---
id: y9x375ibokpltgpqhrdzt3c
title: Software Design exercises
desc: ''
updated: 1657567889471
created: 1657559251436
---


From [here](https://etutorials.org/Programming/Software+engineering+and+computer+games/Part+I+Software+Engineering+and+Computer+Games/Chapter+5.+Software+design+patterns/Exercises/)



# Exercise 5.1: Strategy Pattern and sales chart display

Suppose that you have a cSalesData object with a drawGraph() method. Draw a UML including a few lines of code to show how you could use a Strategy Pattern to select at runtime between drawing a bar graph or a pie graph of the data.


type A<C> = 
    object a: C
    function b: C->1
end

A<C>(a::C,b::C->1) = new A(a,b)
A<C>(a::C) = new A(a,x->{})

execute(a::A) =a.b(a.a)


cSalesData = A(salesData)
cSalesData.b = {...

drawBar
..
} 



Exercise 5.2:
Template Method patterna dn opening diverse file types

Template methd pattern and opening 


