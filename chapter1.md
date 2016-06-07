---
title       : Basic testwhat functions
description : Some questions about basic functions in the testwhat package.

--- type:MultipleChoiceExercise lang:r xp:50 skills:1 key:562bf06a1d
## test_mc

Suppose you're writing a Multiple Choice Exercise (like the exercise you're taking right now), where there are three options. The second option is the correct one. Which `test_mc()` call do you need?

*** =instructions
- `test_mc(c(1 = 'bad', 2 = 'good', 3 = 'bad'))
- `test_mc(correct = 1, feedback_msgs = c('bad', 'bad', 'good'))`
- `test_mc(correct = 2, feedback_msgs = c('bad', 'good', 'bad'))`
- `test_mc(correct = 2, feedback_msgs = c('bad', 'bad', 'good'))

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

