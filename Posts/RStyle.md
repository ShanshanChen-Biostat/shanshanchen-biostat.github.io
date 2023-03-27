---
layout:default
---

This post documents my preferences of R coding style. Whatever coding style you use, make sure it's consistent and human understandable. You can also use automatic R format package "formatR" developed by [Yihui Xie](https://yihui.org/formatr/#substitute-with)

### Naming conventions of variables

>“There are only two hard things in Computer Science: cache invalidation and naming things.” 
> — Phil Karlton

According [Hadley Wickham](http://adv-r.had.co.nz/Style.html), 

>Variable and function names should be lowercase. Use an underscore (_) to separate words within a name. 
>Generally, variable names should be nouns and function names should be verbs. Strive for names that are concise and meaningful (this is not easy!)

Example:
```
# Good
day_one
day_1

# Bad
first_day_of_the_month
DayOne
dayone
djm1
```
Naming conventions vary per programming languages and [programmers](https://github.com/ktaranov/naming-convention/blob/master/R%20style%20guide%20and%20name%20convention.md), 
However, in the context of R, I agree with Wickham's convention. 


### Naming conventions of files 




### Assignment 
[Wickham](http://adv-r.had.co.nz/Style.html) mentioned 
> Use <-, not =, for assignment.
This rule is out of date, the only advantage of using "<-" is that you can direct it the other way, as in "->" so you can assign the value from the left (evaluation) to the right (object). As assignment convention in most programming languages goes from the right to the left, assigning from left to right is not any considerate and sane coder would do.   

So use "=" if you enjoy its simplicity and convention-following nature. Not to mention it's much easier to reach on the keyboard. 



