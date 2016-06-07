---
title       : Basic testwhat functions
description : Some questions about basic functions in the testwhat package.

--- type:MultipleChoiceExercise lang:r xp:50 skills:1 key:562bf06a1d
## First question

This is the first exercise

*** =instructions
- Option A
- Option B
- Option C
- Option D

*** =hint
No hints, I'm sorry!

*** =sct
```{r}
msg_bad <- "That is not correct!"
msg_success <- "Exactly!"
test_mc(correct = 2, feedback_msgs = c(msg_bad, msg_success, msg_bad, msg_bad))
```

