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

How can you robustly test whether a student correctly typed a comment:

```
# This is my comment
```

*** =instructions

- `test_student_typed("# This is my comment")`
- `test_student_typed(c("# This is my comment", "# this is my comment"))`
- `test_student_typed("^#\\s*[T|t]his is my comment")`
- `test_student_typed("^#\\s*[T|t]his is my comment", fixed = FALSE)`

*** =hint
No hints, I'm sorry!

*** =sct
```{r}
msg1 <- "There are many ways in which people type this comment, so you'll need a regex."
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
- `i  live in Boston`
- `  i  live in Boston`

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
msg2 <- "YTou have to have at least one space between words, so you need a `+`."
msg3 <- "You need at least one letter in the place where you live, so `.*?` is not appropriate"
msg4 <- "Great. As you see, writing good regular expressions is vital. To learn more about this, check out the [documentation on regexes in R](https://stat.ethz.ch/R-manual/R-devel/library/base/html/regex.html)."
test_mc(2) # if 2 is the correct option.
```


--- type:MultipleChoiceExercise lang:r xp:50 skills:1 key:7df833a013
## test_object (1)

`test_object()` allows you to robustly compare the objects a student created with the objects that are created if you run the solution code.


*** =instructions
- option 1
- option 2
- option 3

*** =hint
No hints, I'm sorry!

*** =pre_exercise_code
```{r}
# pec
```

*** =sct
```{r}
test_mc(2) # if 2 is the correct option.
```


--- type:MultipleChoiceExercise lang:r xp:50 skills:1 key:28575361b9
## test_object(2)

Assignment comes here. Use Markdown for text formatting.

*** =instructions
- option 1
- option 2
- option 3

*** =hint
No hints, I'm sorry!

*** =pre_exercise_code
```{r}
# pec
```

*** =sct
```{r}
test_mc(2) # if 2 is the correct option.
```


--- type:MultipleChoiceExercise lang:r xp:50 skills:1 key:c61881f8ee
## test_function (1)

Assignment comes here. Use Markdown for text formatting.

*** =instructions
- option 1
- option 2
- option 3

*** =hint
No hints, I'm sorry!

*** =pre_exercise_code
```{r}
# pec
```

*** =sct
```{r}
test_mc(2) # if 2 is the correct option.
```

--- type:MultipleChoiceExercise lang:r xp:50 skills:1 key:1f8qwc6188
## test_function (2)

Assignment comes here. Use Markdown for text formatting.

*** =instructions
- option 1
- option 2
- option 3

*** =hint
No hints, I'm sorry!

*** =pre_exercise_code
```{r}
# pec
```

*** =sct
```{r}
test_mc(2) # if 2 is the correct option.
```


--- type:MultipleChoiceExercise lang:r xp:50 skills:1 key:c954b2cec9
## test_error

Assignment comes here. Use Markdown for text formatting.

*** =instructions
- option 1
- option 2
- option 3

*** =hint
No hints, I'm sorry!

*** =pre_exercise_code
```{r}
# pec
```

*** =sct
```{r}
test_mc(2) # if 2 is the correct option.
```


