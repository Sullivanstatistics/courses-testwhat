---
title       : Basic testwhat functions
description : Some questions about basic functions in the testwhat package.

--- type:MultipleChoiceExercise lang:r xp:100 skills:1 key:8cd4c6ae94
## Getting started

In this course, you can test your understanding of the `testwhat` package. `testwhat` contains a bunch of functions to create so-called Submission Correctness Tests, or SCTs.

To learn more about course creation for DataCamp, make sure to visit the [DataCamp Teach Documentation](www.datacamp.com/teach/documentation).

To easily use `testwhat`, you'll want to install it on your own system and load the package in your R session. That way, you can easily access the documentation of all functions.

You can install `testwhat`, you use:

```
library(devtools)
install_github('datacamp/testwhat')
```

Which command do you need to load the `testwhat` package after installation?

*** =instructions
- `import(testwhat)`
- `library(testwhat)`
- `rqre(testwhat)`
- `lib(testwhat)`

*** =hint
No hints, I'm sorry!

*** =sct
```{python}
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
```{python}
msg1 <- "Incorrect. You have to specify the `correct` and `feedback_msgs` arguments inside `test_mc()`."
msg2 <- "The second option is correct, so you need `correct = 2`."
msg3 <- "Well done!"
msg4 <- "The second option is correct, but the order of the messages you pass in the `feedback_msgs` is not correct!"
test_mc(correct = 3, feedback_msgs = c(msg1, msg2, msg3, msg4))
```


--- type:MultipleChoiceExercise lang:r xp:50 skills:1 key:0beefc3850
## test_student_typed

More exercises coming soon!

*** =instructions
- a
- b
- c
- d

*** =hint
No hints, I'm sorry!

*** =sct
```{python}
test_mc(correct = 1)
```

