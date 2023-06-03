# MotionLayout: Android Animation Made Easy

As kids we have all used Microsoft's Power Point to make beautiful slides with animations, where we used to define a object such as an Image or a Text and then draw paths to control the movements across the slide.

Now, MotionLayout brings the same power of easy animation to Android. 

`MotionLayout` is built upon `ConstraintLayout` and is compatible till **API Level 14(Ice Cream Sandwich)**. It brings in all the features of `ConstraintLayout` with the added functionalities of animation.

## Understanding how **MotionLayout** Works:

To understand how `MotionLayout` works we first need to understand how `ConstraintLayout` works. 

So in easy terms, in `ConstraintLayout` we first add some views, constrain them to other views/helpers or the parent, and boom we have got a layout design.

The same logic goes with `MotionLayout`, the only difference is we need to define 2 or more set of constraints, which tells Constraint layout how and where to place all the elements before and after animation, just like a slide show.