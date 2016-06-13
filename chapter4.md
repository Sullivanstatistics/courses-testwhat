---
title       : testwhat case studies
description : Some case studies to see how different testwhat functions can work together

--- type:MultipleChoiceExercise lang:r xp:50 skills:1 key:cb2ce954c9
## Case 1

Sometimes it is not totally clear which SCT function to use. Say, for example, that you want the student to print out a summary of `mtcars`:

```
summary(mtcars)
```

In your SCT, you can use:

```
test_output_contains("summary(mtcars)")
```

Or you can use 

```
test_function("summary", args = "object")
```

There are reasons for using either of the above SCTs. Can you select the option that explains the pros and cons about them?

`test_output_contains()`, but you can also use `test_function()


*** =instructions
- `test_output_contains()` can cause backend errors if you execute `summary(mtcars)`. `test_function()` doesn't have this problem.
- `test_output_contains()` actually checks if output was generated, but you'll have to specify your own custom feedback message. `test_function()` is robust and can generate meaningful feedback, but doesn't check if the appropriate output was generated.
- `test_function()` cannot check the contents of the parameters you pass it, but it generates meaningful feedback.

*** =hint
No hints, I'm sorry!

*** =sct
```{r}
msg1 <- "It's true that `test_output_contains` can cause backend errors, but this is only when `mtcars` is no longer defined; as this is an object that is defined in the `datasets` package and is loaded by default, this is not going to be a problem."
msg2 <- "Correct! You'll probably want to go with `test_output_contains()` where you manually specify an `incorrect_msg` argument."
msg3 <- "This is not true: `test_function()` cal also check the contents of the paramters you pass it."
test_mc(2, feedback_msgs = c(msg1, msg2, msg3))
```