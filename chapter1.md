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

--- type:MultipleChoiceExercise lang:r xp:50 skills:1 key:0beefc3850
## Placeholder

More exercises coming soon!

*** =instructions
- a
- b
- c
- d

*** =hint
No hints, I'm sorry!

*** =sct
```{r}
test_mc(correct = 1)
```


--- type:MultipleChoiceExercise lang:r xp:50 skills:1 key:169eaba475
## test_student_typed

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


--- type:MultipleChoiceExercise lang:r xp:50 skills:1 key:d84512adbe
## test_output_contains

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


--- type:MultipleChoiceExercise lang:r xp:50 skills:1 key:f3aa69c612
## test_output_regex

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


<<<<<<< HEAD
--- type:MultipleChoiceExercise lang:r xp:50 skills:1 key:0d7b0ebd0b
=======
--- type:MultipleChoiceExercise lang:r xp:50 skills:1 key:ae6a452afd
## test_output_regex

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


--- type:MultipleChoiceExercise lang:r xp:50 skills:1 key:e81f043acf
>>>>>>> 4bf22ba074863526317b70960d24abb3e0097072
## test_object (1)

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


