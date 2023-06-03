# MotionLayout: Android Animation Made Easy

As kids we have all used Microsoft's Power Point to make beautiful slides with animations, where we used to define a object such as an Image or a Text and then draw paths to control the movements across the slide.

Now, MotionLayout brings the same power of easy animation to Android. 

**MotionLayout** is built upon **ConstraintLayout** and is compatible till **API Level 14(Ice Cream Sandwich)**. It brings in all the features of **ConstraintLayout** with the added functionalities of animation.

## Understanding how **MotionLayout** Works:

To understand how **MotionLayout** works we first need to understand how **ConstraintLayout** works. 

So in easy terms, in **ConstraintLayout** we first add some views, constrain them to other views/helpers or the parent, and boom we have got a layout design.

The same logic goes with **MotionLayout**, the only difference is we need to define 2 or more set of constraints, which tells Constraint layout how and where to place all the elements before and after animation, just like a slide show.

## Now the next question arise, Why should we use **MotionLayout**?

Yes, its true that android has multiple ways to animate views, but all of them have their drawbacks:

|Animation| Cons |
|-|-|
|Animated Vector Drawable|<span style="color: red;">Only for icons and images</span>|
|Property Animation framework |<span style="color: red;">Only for icons and images</span> |
|LayoutTransition animations|<span style="color: red;">Only for icons and images</span> |
|Layout transitions with TransitionManager|<span style="color: red;">Only for icons and images</span>|
|CoordinatorLayout|<span style="color: red;">Only for icons and images</span>|

#### Then there comes the **ConstraintLayout** our saviour.

## Lets Jump into some code:

To implement MotionLayout we need to add the below dependency in our app level gradle file :

```
dependencies {
    implementation 'androidx.constraintlayout:constraintlayout:<version>'
}
```

Replace `<version>` with the latest version from <a href="https://mvnrepository.com/artifact/androidx.constraintlayout/constraintlayout">here</a>. *(It is always recommended to use the stable version.)*

After this has been added create a layout file with the root element as `ConstraintLayout` and then in the layout editor change Right Click on the ConstraintLayout and Click on **Convert to MotionLayout**


