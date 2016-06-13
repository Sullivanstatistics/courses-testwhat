---
title       : Logic-inducing testwhat functions
description : Some questions about logic-inducing functions in the testwhat package.


--- type:MultipleChoiceExercise lang:r xp:50 skills:1 key:2cec9c954b
## test_correct (1)

Suppose you want the student to code up the following answer (where `vec` is predefined in the sample code):

```
vec <- c(1:50, NA, 51:100)

# Call mean on vec, store in res
res <- mean(vec, na.rm = TRUE)
```

Which SCT functions do you need to robustly test if `res` was correctly created? You want the feedback in case of an incorrect submission to be as specific as possible.

*** =instructions
- `test_object("res")`
- `test_output_contains("res")`
- `test_correct(test_object("res"), test_function("mean", args = c("x", "na.rm")))`
- `test_correct(test_object("res"), test_function("mean", args = c("vec", "na.rm")))`
- `test_correct(test_object("res"), test_function("mean"))`



*** =hint
No hints, I'm sorry!

*** =sct
```{r}
msg1 <- "You'll want to use `test_correct()` to give more specific feedback about the function call."
msg2 <- "`test_output_contains()` makes no sense here."
msg3 <_ "Well done! You could even specify the `*_msg` arguments in both `test_object()` and `test_function()` to go more specific."
msg4 <- "The arguments inside `test_function()` are not correctly specified."
msg5 <- "Close, but not specific enough: you know which arguments the student should specify!"
test_mc(3, feedback_msgs = c(msg1, msg2, msg3, msg4, msg5))
```

--- type:MultipleChoiceExercise lang:r xp:50 skills:1 key:54b2cec9c9
## test_correct (2)

You can also use `test_correct()` with entire sub-SCTs that are composed of several SCT calls. In this case, you simply have to use `{ }` to group these calls.

Suppose you want the student to code the same variable `res` as before, but this time you also want to see it printed out. A possible solution to the exercise is the following:

```
vec <- c(1:50, NA, 51:100)

# Call mean on vec, store in res
res <- mean(vec, na.rm = TRUE)

# Print out res
res
```

Which SCT call do you opt for?

Option A

```
test_correct({
  test_object('res')
  test_output_contains('res')
}, {
  test_function('mean', args = c("x", "na.rm"))
})
```

Option B

```
test_correct({
  test_output_contains('res')
}, {
  test_object('res')
  test_function('mean', args = c("x", "na.rm"))
})
```

Option C

```
test_correct({
  test_object('res')
}, {
  test_function('mean', args = c("x", "na.rm"))
  test_output_contains('res')
})
```


*** =instructions
- Option A
- Option B
- Option C

*** =hint
No hints, I'm sorry!

*** =sct
```{r}
msg1 <- "Correct. You have to test that both `res` is correct and `res` is correctly printed out."
msg2 <- "In this case, the SCT can pass if the student simply did `res <- 1` and then printed out `res`. `test_output_contains()` executes `res` acting as the student, with his or her environment."
msg3 <- "It's not enough to simply test whether `res` is correct. This SCT will also pass if the student creates `res` correctly but doesn't print it out."
test_mc(1, feedback_msgs = c(msg1, msg2, msg3))
```

--- type:MultipleChoiceExercise lang:r xp:50 skills:1 key:2c053bec9c
## test_or

`test_or()` is much less often used than `test_correct()`. Basically, it allows you to specify several sub-SCTs, one of which should pass.

Have a look at the following SCT that uses `test_student_typed()`:

```
test_student_typed(c("a", "b", "c"))
```

Which `test_or()` function call containing `test_student_typed()` calls is equivalent to the above call?

*** =instructions
- `test_student_typed(test_or("a", "b", "c"))`
- `test_or(test_student_typed("a"), test_student_typed("b"), test_student_typed("c"))`
- `test_or(test_student_typed('a")); test_or(test_student_typed("b")); test_or(test_student_typed("c"))`
- `test_student_typed_or("a", "b", "c")

*** =hint
No hints, I'm sorry!

*** =sct
```{r}
msg1 <- "Incorrect; `test_or()` should be the 'top-level' function here."
msg2 <- "Correct!"
msg3 <- "This SCT makes no sense: `test_or()` should combine different `test_student_typed()` tests."
msg4 <- "`test_student_typed_or()` is not a function in the `testwhat` package."
test_mc(2, feedback_msgs = c(msg1, msg2, msg3, msg4))
```

