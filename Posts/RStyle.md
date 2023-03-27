---
layout: default
---

This post documents my preferences of R coding style. Whatever coding style you use, make sure it's consistent and human understandable. You can also use automatic R format package "formatR" developed by [Yihui Xie](https://yihui.org/formatr/#substitute-with).

### Naming conventions of variables

>“There are only two hard things in Computer Science: cache invalidation and naming things.” 
> — Phil Karlton

According [Hadley Wickham](http://adv-r.had.co.nz/Style.html), 

>Variable and function names should be lowercase. Use an underscore (_) to separate words within a name. 
>Generally, variable names should be nouns and function names should be verbs. Strive for names that are concise and meaningful (this is not easy!)

That's Wickham's preference. Personally, I also distinguish variables and function names by capitalizing Variable_names and lowercase "function_names"

Example:
```
# Good
Day_one
DayOne
Day_1

# Bad
first_day_of_the_month
djm1
```
Naming conventions vary per programming languages and [programmers](https://github.com/ktaranov/naming-convention/blob/master/R%20style%20guide%20and%20name%20convention.md), 
However, in the context of R, I agree with Wickham's convention. 


### Naming conventions of functions 
Generally, variable names should be nouns and function names should be verbs. I prefer beginning function name with lowercase, and begin the word following the action verb with capital letters, e.g. "cleanData()" or "clean_data()" 



### Top-level Assignment 
[Wickham](http://adv-r.had.co.nz/Style.html) mentioned 
> Use <-, not =, for assignment.

This rule is out of date, the only advantage of using "<-" is that you can direct it the other way, as in "->" so you can assign the value from the left (expression) to the right (variable). As assignment convention in most programming languages goes from the right to the left, assigning from left to right is not any considerate and sane coder would do. 

So use "=" if you enjoy its simplicity and convention-following nature. Not to mention it's much easier to reach on the keyboard. 



