---
title       : Basic testwhat functions
description : Some questions about basic functions in the testwhat package.

--- type:MultipleChoiceExercise lang:r xp:100 skills:1 key:8cd4c6ae94
## Getting started

In this course, you can test your understanding of the `testwhat` package. `testwhat` contains a bunch of functions to create so-called Submission Correctness Tests, or SCTs.

To learn more about course creation for DataCamp, make sure to visit the [DataCamp Teach Documentation](www.datacamp.com/teach/documentation).

To easily use `testwhat`, you'll want to install it on your own system and load the package in your R session. That way, you can easily access the documentation of all functions.

To install `testwhat`, follow the instructions in the [GitHub README](https://github.com/datacamp/testwhat) on GitHub. 

Once installed, which command do you need to load the `testwhat` package after installation?

*** =instructions
- `import(testwhat)`
- `library(testwhat)`
- `rqre(testwhat)`
- `lib(testwhat)`

*** =hint
No hints, I'm sorry!

*** =sct
```{r}
msg1 <- "Incorrect."
msg2 <- "Correct!"
msg3 <- msg1
msg4 <- msg1
test_mc(correct = 2, feedback_msgs = c(msg1, msg2, msg3, msg4))
```

--- type:MultipleChoiceExercise lang:r xp:50 skills:1 key:562bf06a1d
## test_mc

Suppose you're writing a Multiple Choice Exercise (like the exercise you're taking right now), where there are three options. The second option is the correct one. Which `test_mc()` call do you need?

*** =instructions
- `test_mc(c(1 = 'bad', 2 = 'good', 3 = 'bad'))`
- `test_mc(correct = 1, feedback_msgs = c('bad', 'bad', 'good'))`
- `test_mc(correct = 2, feedback_msgs = c('bad', 'good', 'bad'))`
- `test_mc(correct = 2, feedback_msgs = c('bad', 'bad', 'good'))`

*** =hint
No hints, I'm sorry!

*** =sct
```{r}
msg1 <- "Incorrect. You have to specify the `correct` and `feedback_msgs` arguments inside `test_mc()`."
msg2 <- "The second option is correct, so you need `correct = 2`."
msg3 <- "Well done!"
msg4 <- "The second option is correct, but the order of the messages you pass in the `feedback_msgs` is not correct!"
test_mc(correct = 3, feedback_msgs = c(msg1, msg2, msg3, msg4))
```

--- type:MultipleChoiceExercise lang:r xp:50 skills:1 key:169eaba475
## test_student_typed

`test_student_typed()` is a very basic `testwhat` function to test whether a student typed something.

Suppose you want to test whether a student typed a comment, like this:

```
# This is my comment
```

Which function call should you include in your SCT to do this robustly?

*** =instructions
- `test_student_typed("# This is my comment")`
- `test_student_typed(c("# This is my comment", "# this is my comment"))`
- `test_student_typed("^#\\s*[T|t]his is my comment")`
- `test_student_typed("^#\\s*[T|t]his is my comment", fixed = FALSE)`

*** =hint
No hints, I'm sorry!

*** =sct
```{r}
msg1 <- "There are many ways in which people type this comment, so you'll need a regular expression."
msg2 <- msg1
msg3 <- "The regex makes sense, but you have to make sure to set the `fixed` argument appropriately if you use a regex."
msg4 <- "Correct!"
test_mc(4, feedback_msgs = c(msg1, msg2, msg3, msg4))
```


--- type:MultipleChoiceExercise lang:r xp:50 skills:1 key:d84512adbe
## test_output_contains

`test_output_contains()` runs the R expression that you pass it, and compares the output it generates to the output that the student generated with his or her submission. It is a very good way to check if the student produced the correct output.

Suppose the student has to print out the second column of the `pressure` dataset, that's available by default in R. Which `test_output_contains()` call do you need?

In the options below, `msg` is equal to `"Have you printed out the second columns of `pressure`?".

*** =instructions
- `test_output_contains("pressure[,2]", incorrect_msg = msg)`
- `test_output_contains("pressure", incorrect_msg = msg)`
- `test_output_contains("pressure[2,]", incorrect_msg = msg)`
- `test_output_contains("print(pressure[2,])", incorrect_msg = msg)`

*** =hint
No hints, I'm sorry!

*** =sct
```{r}
msg1 <- "Correct!"
msg2 <- "You don't want to check if the student printed out the entire data frame."
msg3 <- "You don't want to check if the student printed out the second row."
msg4 <- msg3
test_mc(1, feedback_msgs = c(msg1, msg2, msg3, msg4))
```

--- type:MultipleChoiceExercise lang:r xp:50 skills:1 key:f3aa69c612
## test_output_regex

Compared to `test_output_contains()`, `test_output_regex()` does not execute any additional code. Instead, it simply searches for patterns in the output that the student generated with his or her submission. 

Suppose that you want the student to print out where he lives, in the following format:

```
I live in ...
```

You want to do this as robustly as possible. All of the following submissions should be accepted:

- `I live in Leuven, Belgium`
- `I live in a small house`
- `i live in San Diego`

Which call would be most appropriate? We left out the part that specified `incorrect_msg`, although it's advised to specify this custom message for `test_output_regex()`.

*** =instructions
- `test_output_regex("[I|i] live in \\w+$")`
- `test_output_regex("[I|i]\\s*live\\s*in\\s*.*?$")`
- `test_output_regex("[I|i]\\s+live\\s+in\\s+.*?$")`
- `test_output_regex("[I|i]\\s+live\\s+in\\s+.+?$")`

*** =hint
No hints, I'm sorry!

*** =sct
```{r}
msg1 <- "It should be possible to have multiple spaces, and also non-alphanumerical characters."
msg2 <- "You have to have at least one space between words, so you need a `+`."
msg3 <- "You need at least one letter in the place where you live, so `.*?` is not appropriate"
msg4 <- "Great. As you see, writing good regular expressions is vital. To learn more about this, check out the [documentation on regexes in R](https://stat.ethz.ch/R-manual/R-devel/library/base/html/regex.html)."
test_mc(4, feedback_msgs = c(msg1, msg2, msg3, msg4))
```


--- type:MultipleChoiceExercise lang:r xp:50 skills:1 key:7df833a013
## test_object (1)

`test_object()` allows you to robustly compare the objects a student created with the objects that are created if you run the solution code.

Suppose that the student has to create the object `x`, equal to the sum of 2 and 4. How do you use `test_object()` to test this?

*** =instructions
- `test_object(x, 2 + 4)`
- `test_object("x", "2 + 4")`
- `test_object(x)`
- `test_object("x")`

*** =hint
No hints, I'm sorry!

*** =sct
```{r}
msg1 <- "You have to place `x` in quotes, and there's no need to specify the value that `x` should have; this is inferred from the solution code."
msg2 <- "There's no need to specify that value that `x` should have; this is inferred from the solution code"
msg3 <- "You have to place `x` in quotes!"
msg4 <- "Correct. Pretty easy, right?"
test_mc(4, feedback_msgs = c(msg1, msg2, msg3, msg4))
```


--- type:MultipleChoiceExercise lang:r xp:50 skills:1 key:28575361b9
## test_object(2)

`test_object()` can use different 'equality conditions', such as "equal" and "equivalent". The latter checks the contents of an object, but does not check whether its attributes (such as the names of the elements) correspond to the object in the solution. `eq_condition = "equivalent"` is the default setting used by `test_object()`.

Suppose you want the student to create the following vector `y`:

```
y <- c(a = 1, b = 2, c = 3)
```

You want to check if this vector is correctly created, both the values as well as the names. Which `test_object()` call is your pick?

*** =instructions
- `test_object(y, names = TRUE)`
- `test_object("y", names = TRUE)`
- `test_object(y, eq_condition = "equal")`
- `test_object("y", eq_condition = "equal")`
- `test_object(y)`
- `test_object("y")`

*** =hint
No hints, I'm sorry!

*** =sct
```{r}
msg1 <- "You have to place quotes around the object name."
msg2 <- "`names` is not an argument of `test_object`"
msg3 <- msg1
msg4 <- "Correcto perfecto!"
msg5 <- msg1
msg6 <- "Simply using `test_object(\"y\")` will not check the names you give to the vector elements."
test_mc(4, feedback_msgs = c(msg1, msg2, msg3, msg4, msg5, msg6))
```


--- type:MultipleChoiceExercise lang:r xp:50 skills:1 key:c61881f8ee
## test_function (1)

With `test_function()`, you can test whether the student called a function, optionally with the correct arguments.

Suppose you've written an exercise that asks the student to use the `mean()` function as follows:

```
vec <- c(1:50, NA, 51:100)
mean(vec, na.rm = TRUE)
```

Which `test_function()` call should you use in your SCT to test a submission?

*** =instructions
- `test_function(mean)`
- `test_function("mean")`
- `test_function("mean", args = c("x", "na.rm"))
- `test_function(mean, args = c(x, na.rm))`
- `test_function("mean", args = c("vec", "TRUE"))`
- `test_function(mean, args = c(vec, TRUE))`

*** =hint
No hints, I'm sorry!

*** =sct
```{r}
msg1 <- "Make sure to wrap `mean` in quotes inside `test_function()`."
msg2 <- "You also have to specify the arguments that you want to check through the `args` argument of `test_function()`."
msg3 <- "Correct!"
msg4 <- "Make sure to wrap `mean` and the arguments in quotes inside `test_function()`."
msg5 <- "You did not correctly specify the arguments. You have to specify the argument names as they appear in the documentation of `mean()`, so `\"x\"` and `\"na.rm\"`."
msg6 <- "You have to use quotes around `mean`; you haven't specified the arguments correctly."
test_mc(3, feedback_msgs = c(msg1, msg2, msg3, msg4, msg5, msg6))
```

--- type:MultipleChoiceExercise lang:r xp:50 skills:1 key:1f8qwc6188
## test_function (2)

There's many more arguments to specify in `test_function()`. Among them are `allow_extra`, `eval` and `eq_condition`, and of course all `_msg` arguments to override the automatically generated feedback messages.

Suppose you've written an exercise that again asks the student to use the `mean()` function, but this time on a random vector, so you don't want to check the actual contents of the vector. Also, you want to make sure that `trim` was not defined (so you don't want to allow extra arguments).

Which call below should you add to your SCT?

*** =instructions
- `test_function("mean", args = c("x", "na.rm"), allow_extra = FALSE)`
- `test_function("mean", args = c("x", "na.rm"), eval = FALSE)`
- `test_function("mean", args = c("x", "na.rm"), eval = c(FALSE, TRUE))`
- `test_function("mean", args = c("x", "na.rm"), allow_extra = FALSE, eval = c(FALSE, TRUE))`
- `test_function("mean", args = c("x", "na.rm"), allow_extra = FALSE, eq_condition = "equal")`

*** =hint
No hints, I'm sorry!

*** =sct
```{r}
msg1 <- "Incorrect; you also have to specify `eval`"
msg2 <- "Incorrect; `eval` is not correctly specified and you also have to specify `allow_extra`."
msg3 <- "Incorrect; you also have to specify `allow_extra`."
msg4 <- "Correct! Notice how `eval` tells for each argument whether or not it should be evaluated."
msg5 <- "Incorrect: you should specify `eval` instead of `eq_condition`."
test_mc(4, feedback_msgs = c(msg1, msg2, msg3, msg4, msg5))
```

--- type:MultipleChoiceExercise lang:r xp:50 skills:1 key:c954b2cec9
## test_error

`test_error()` simply checks if the code that the student submitted leads to a runtime error.

It's a good idea to place `test_error()` in all your SCTs, but where?

*** =instructions
- At the end: that way, the student can get specific feedback about the submission before getting confronted with a potentially unmeaningful error message.
- In the beginning: you want to point the student to an error as quickly as possible.

*** =hint
No hints, I'm sorry!

*** =sct
```{r}
msg1 <- "Correct! Although there's something to say for this approach, it's better to use SCT feedback instead of R-generated error messages to guide the student."
msg2 <- "Although there's something to say for this approach, it's better to use SCT feedback instead of R-generated error messages to guide the student."
test_mc(1, feedback_msgs = c(msg1, msg2))
```


