# Turtle Races: Redux

In this workbook you will create a turtle racing game with Python.

We'll build from the of showing a turtle into creating a small game where turtles race each other.

**Time:** 60 minutes

**Experience:** Beginner

**Skills:** Basic python programming

[//]: # (TODO: Images)

## Draw a Turtle

You can draw a turtle in python with a built in package called `turtle`.

```python
import turtle

my_turtle = turtle.Turtle()
my_turtle.shape("turtle")

turtle.exitonclick()
```

**Wow!** That was easy!

### What have we done

We imported a package called `turtle`, created a new turtle named `my_turtle` and set the shape as a turtle.

Finally, we tell the program to exit if you click on the screen.

### Exercises

* What happens if you remove the line setting the shape?
* Try changing the shape - you can use 'arrow', 'blank', 'circle', 'classic', 'square', 'triangle', 'turtle'

## Move the Turtle

We can add a little code to move the turtle across the screen.

```python
import turtle

my_turtle = turtle.Turtle()
my_turtle.shape("turtle")
my_turtle.penup()
my_turtle.setx(-350)

while my_turtle.xcor() < 350:
    my_turtle.forward(10)

turtle.write("Finished!")

turtle.exitonclick()
```

**Zoom!**

### What have we done

We added a new line after setting the shape that lifts the pen from the canvas (this stops lines being drawn). We then
move the turtle to the left of the screen.

Now we create a loop using `while`, this loops until the turtle has moved across the screen. Ever loop it moves the
turtle forward 10 steps.

Finally, we write "Finished!" when the turtle has moved far enough.

#### Details

The numbers use to move the turtle are called "pixels" (or px), your computer screen contains lots of pixels. When you
run a turtle application the size of the window is 960px wide and 810px high.

### Exercises
* Try changing the speed of the turtle - what happens if you change the number `10` to `2`, or `20`?
* Change the numbers when moving the turtle to the start `setx()` or the finish line `350`, what happens?

## More Turtles



