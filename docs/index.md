[toc]

# Picture Environment - LaTeX on Brainly

\- By Purva, [@QGP](https://brainly.in/app/profile/48021), Brainly India



Environments in LaTeX are a way to group certain type of commands together. You may have used the `array` and `tabular` environments while making tables. Here, we look at the `picture` environment, which is helpful in creating diagrams.



## Pre-Requisites

It will helpful if you understand **Coordinate Geometry** and have a basic understanding of how **Vectors** work. 

Working with the Picture Environment becomes immensely easier if you look at it from a perspective of coordinate geometry.



In case you haven't studied it yet, you can look at these videos about [Coordinate Plane by Khan Academy](https://www.khanacademy.org/math/basic-geo/basic-geo-coord-plane). Watch the videos until Quiz 1. 

## The Starting Blocks

In the Picture Environment, we can imagine a canvas area, where we draw our stuff. We need to define the width and height of this canvas area. And then we start putting the things we want on our canvas.



### Defining Unit Length

The first step is defining what 1 unit length means in our system. *1 unit* is an abstract idea of length. On the contrary, 1 cm, 1 mm, 1 inch, etc are all physical and concrete ideas of length which are well-defined.



We can define 1 unit length to be anything. Examples:

- 1 unit = 1 cm
- 1 unit = 23 mm
- 1 unit = 2 in (inches)



For simplicity, we will define **1 unit = 1 cm**. We declare it as:

```latex
\setlength{\unitlength}{1cm}
```



### Setting the Drawing Canvas Dimensions

The basic syntax of declaring the dimensions is:

**`\begin{picture}(width, height)`**



Similar to the begin command, there is also an _end_ command to mark the end of the picture environment code. It is simply

**`\end{picture}`**



So, for example, we can display a $\sf 6 \times 8$ cm block as:



```latex
\setlength{\unitlength}{1cm}
\begin{picture}(6, 8)

code

\end{picture}
```



We could set a different unit length and declare a different canvas area size as required. It will become clearer what numbers to use once you become a bit familiar with the Picture Environment.



This all is just the structure to define the start and end of the picture environment code. Now, we learn how to draw stuff.



### The `\put` command



Think of our canvas as a coordinate plane, as if on a graph sheet. **The lower-left corner is the Origin (0,0).** The `\put` command _"puts"_ an _object_ at the given coordinates. 

The syntax of the put command is:

`\put(x, y){object}`

where (x, y) refers to the coordinates where we want to place the object. What kind of object? It can be lines, arrows, circles, and more, as shown in the next section: Drawing.

We can also put some text simply at some coordinates. Consider placing the text _Brainly_ at (2, 3).

```latex
\setlength{\unitlength}{1cm}
\begin{picture}(6, 8)

\put(2, 3){\sf Brainly}

\end{picture}
```



Now, we learn to actually draw stuff.



