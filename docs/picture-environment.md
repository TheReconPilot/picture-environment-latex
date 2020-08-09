# Picture Environment - LaTeX on Brainly

\- By Purva, [@QGP](https://brainly.in/app/profile/48021), Brainly India



Environments in LaTeX are a way to group certain type of commands together. You may have used the `array` and `tabular` environments while making tables. Here, we look at the `picture` environment, which is helpful in creating diagrams.



## Pre-Requisites

It will helpful if you understand **Coordinate Geometry** and have a basic understanding of how **Vectors** work. 

Working with the Picture Environment becomes immensely easier if you look at it from a perspective of coordinate geometry.



In case you haven't studied it yet, you can look at these videos about [Coordinate Plane by Khan Academy](https://www.khanacademy.org/math/basic-geo/basic-geo-coord-plane). Watch the videos until Quiz 1. 



---

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



---



## Basic Drawing

There are various kinds of objects that we can draw. Let's look at them. 

**All of these objects go under the \put command.**



### Line Segments

The syntax of a line segment is:

```latex
\put(x, y){\line{x1, y1){length}}
```

Here:

- `(x, y)` are the co-ordinates from where the line-segment will start from (as the put command starts to place the object from there)
- `(x1, y1)` is the direction vector, pointing towards the direction where the line is to be drawn
- `length` is the length of the line-segment



#### The Direction Vector

Imagine an arrow starting from (0, 0) and pointing to (x1, y1). The direction of this arrow is the direction along which the line segment will be drawn. 

So, for example:

- `\line(1, 0){2}` draws a line segment of length 2 units, towards (1, 0). If you imagine, (1, 0) lies on the X-axis. So, this line is drawn towards the horizontal-right of the starting point. 
  - Now, imagine the direction vector to be (x1, y1) = (2, 0). This is also towards the right side, and hence logically the same as (1, 0).
- `\line(1, 1){3}` draws a line segment of length 3 units, towards (1, 1). This points diagonally towards the top-right. Just like a vector pointing towards (1, 1). 
  - Just as in the first example, direction vectors (2, 2), (3, 3) and all are logically equivalent to (1, 1).
- `\line(-1, 0){2.4}` draws a line segment of length 2.4 units towards (-1, 0), which is horizontally to the left. 
- `\line(3, -2){1.5}` draws a line segment of length 1.5 units towards (3, -2). This is somewhere diagonally towards the bottom-right. Not a perfect diagonal bottom-right, but a slightly different direction.



#### Restrictions on the Direction Vector

The syntax of the line segment is 

```latex
\put(x, y){\line{x1, y1){length}}
```



The direction vector `(x1, y1)` has a couple of important restrictions on the values of `x1` and `y1`.

- **`x1` and `y1` can only take integer values from -6 to 6.** We can only assign values from -6, -5, -4, -3, -2, -1, 0, 1, 2, 3, 4, 5, 6. We cannot put fractional values, else the line segment won't work.
  - So, (3, 5) is a valid direction vector. However, (3, -7) is not.
  - (1.5, 3.4) is not a valid direction vector, as the values of x1 and y1 are not integers.

- **`x1` and `y1` must be relatively prime.** This means that the HCF (Highest Common Factor) or the GCD (Greatest Common Divisor) of x1 and y1 should be 1. That is to say that there should be no common factors.
  - 2 and 3 are relatively prime. However, 4 and 6 are not relatively prime, as they can be divided by a common factor of 2. Hence, (2, 3) is a valid direction vector. Putting in (4, 6) should be fine too, however, it can have unexpected behaviour. So, avoid it.
  - (1, 1) is a valid direction vector. However, (2, 2), (3, 3), (4, 4) and similar others are not valid. They can be reduced to (1, 1). 
    - If you happen to use (2, 2) or (2, -2) or (-2, 2) or (-2, -2), you will see a stream of arrow-heads instead of a line-segment. Similar unexpected behaviour with variants of (3, 3), (4, 4) and more. 
