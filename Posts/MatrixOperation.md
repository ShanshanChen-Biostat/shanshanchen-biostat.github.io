### Use sweep function to conduct row-wise or column-wise matrix operation
```
sweep(Matrix, MARGIN = 1, STATS= 100, FUN ="/") ## devide row-wise elements by 100
# MARGIN = 1 operates by row; MARGIN = 2 operates by column
# STATS: Specifies usually the value that should be used for the operation (e.g. the value that should be added or subtracted).
# FUN: The operation that should be carried out 
```

```
tappy()
```
