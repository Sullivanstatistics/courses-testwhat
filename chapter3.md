---
title       : Advanced testwhat functions
description : Some questions about advanced functions in the testwhat package.

--- type:MultipleChoiceExercise lang:r xp:50 skills:1 key:1c2b6es822
## test_data_frame

You can think of `test_data_frame()` as a `test_object()` specific for R data frames, a very common data structure when using R for data science.

Suppose you prepare a data frame `df`, and you want your student to add a column to the data frame as follows:

```
df$timespan <- df$end - df$start
```

Which `test_data_frame()` call do you need to test whether the student did this correctly?


*** =instructions
- `test_data_frame(df$timespan)`
- `test_data_frame("df$timespan")`
- `test_data_frame(df, columns = timespan)`
- `test_data_frame("df", columns = "timespan")`
- `test_data_frame("df", columns = c("start", "end"))`

*** =hint
No hints, I'm sorry!

*** =sct
```{r}
msg1 <- "You should split the name of the dataframe and the column you want to check over different arguments of `test_data_frame()`."
msg2 <- msg1
msg3 <- "You need quotes around the parameters in the function call."
msg4 <- "That's it!"
msg5 <- "There's no point in checking the `start` and `end` columns; you want to test the `timespan` column!"
test_mc(4, feedback_msgs = c(msg1, msg2, msg3, msg4, msg5))
```


--- type:MultipleChoiceExercise lang:r xp:50 skills:1 key:1c2b6es823
## test_if_else

Suppose you've written an exercise with the following solution:

```
if (x < 0) {
	print("x is negative")
} else {
	print("x is positive")
}
```

with a corresponding SCT:

```
test_if_else(if_cond_test = test_student_typed(c("x < 0", "0 > x"), not_typed_msg = "wrong condition!"),
             if_expr_test = test_function("print", "x"),
             else_expr_test = test_function("print", "x"))
```

Suppose now that the student submitted the following code:

```
if (x < 0) {
	print("x is negative")
} else {
	print("x is purrrrsitive")
}
```

Which 'sub-SCT' of the `test_if_else()` call would notice the mistake and generate a meaningful feedback message?

*** =instructions
- `if_cond_test`
- `if_expr_test`
- `else_expr_test`

*** =hint
No hints, I'm sorry!

*** =sct
```{r}
msg1 <- "The if condition is fine..."
msg2 <- "The if expression is fine..."
msg3 <- "Correct!"
test_mc(3, feedback_msgs = c(msg1, msg2, msg3))
```


--- type:MultipleChoiceExercise lang:r xp:50 skills:1 key:1c2b6es824
## test_for_loop

Suppose you've written an exercise with the following solution:

```
for (i in 1:10) {
	print(i)
}
```

with a corresponding SCT:

```
test_correct(
  test_output_contains("invisible(lapply(1:10, print))"),
  test_for_loop(cond_test = test_student_typed("in 1:10"),
                expr_test = test_function("print", "x", eval = FALSE)))
```

Suppose now that the student submitted the following code:

```
for (x in 2:11) {
	print(x - 1)	
}
```

What happens?

*** =instructions
- `test_output_contains()` fails and generates an appropriate feedback message.
- The output of the code is the same as the solution, so `test_output_contains()` passes and the `test_correct()` function is exited.
- The `cond_test` of `test_for_loop()` notices a mistake and generates feedback.
- As the for loop is not identical to the one in the solution, the for loop is not found by `test_for_loop()`, which generates a message about this.

*** =hint
No hints, I'm sorry!

*** =sct
```{r}
msg1 <- "`test_output_contains()` will not fail! The output of the expression is also in the output the student generated with his or her submission."
msg2 <- "Correcto perfecto!"
msg3 <- "`test_for_loop()` is never reached as `test_output_contains()` passes and `test_correct()` is abandoned after that."
msg4 <- "`test_for_loop()` is never reached as `test_output_contains()` passes and `test_correct()` is abandoned after that. Even then, the for loop would've been found."
test_mc(2, feedback_msgs = c(msg1, msg2, msg3, msg4))
```

--- type:MultipleChoiceExercise lang:r xp:50 skills:1 key:1c2b6es826
## test_function_definition

Suppose you've written an exercise with the following solution:

```
# Define my_fun
my_fun <- function(a, b) {
	abs(a) + abs(b)
}
```

with corresponding SCT:

```
test_function_definition("my_fun",
                         function_test = {
                           test_expression_result("my_fun(1,2)")
                           test_expression_result("my_fun(-1,2)")
                           test_expression_result("my_fun(1,-2)")
                           test_expression_result("my_fun(-1,-2)")
                         },
                         body_test = {
                           	test_function("abs", index = 1)
                            test_function("abs", index = 2)
                         })
```

Suppose now that the student submits the following code:

```
my_fun <- function(a, b) {
	abs(a) + abs(b) + 1
}
```

What happens?

*** =instructions
- The first test in `function_test` fails, leading to `body_test` being executed. These tests pass, so `function_test` is executed again, this time generating feedback.
- The first test in `function_test` fails, leading to `body_test` being executed. The first test in this sub-SCT fails, generating feedback.
- The first test in `function_test` fails, generating feedback.
- The SCT passes.

*** =hint
No hints, I'm sorry!

*** =sct
```{r}
msg1 <- "Correct! Behind the scenes, `test_function_definition()` works kind of like `test_correct()`."
msg2 <- "Incorrect. All tests in `body_test` pass."
msg3 <- "Almost correct, but also `body_test` is executed before `function_test` is executed 'loudly'."
msg4 <- "This SCT does not pass..."
test_mc(1, feedback_msgs = c(msg1, msg2, msg3, msg4))
```