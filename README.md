# R-Seventh-Assignment

> data("Indometh")
> list(Indometh)
[[1]]
   Subject time conc
1        1 0.25 1.50
2        1 0.50 0.94
3        1 0.75 0.78
4        1 1.00 0.48
5        1 1.25 0.37
6        1 2.00 0.19
7        1 3.00 0.12
8        1 4.00 0.11
9        1 5.00 0.08
10       1 6.00 0.07
11       1 8.00 0.05
12       2 0.25 2.03
13       2 0.50 1.63
14       2 0.75 0.71
15       2 1.00 0.70
16       2 1.25 0.64
17       2 2.00 0.36
18       2 3.00 0.32
19       2 4.00 0.20
20       2 5.00 0.25
21       2 6.00 0.12
22       2 8.00 0.08
23       3 0.25 2.72
24       3 0.50 1.49
25       3 0.75 1.16
26       3 1.00 0.80
27       3 1.25 0.80
28       3 2.00 0.39
29       3 3.00 0.22
30       3 4.00 0.12
31       3 5.00 0.11
32       3 6.00 0.08
33       3 8.00 0.08
34       4 0.25 1.85
35       4 0.50 1.39
36       4 0.75 1.02
37       4 1.00 0.89
38       4 1.25 0.59
39       4 2.00 0.40
40       4 3.00 0.16
41       4 4.00 0.11
42       4 5.00 0.10
43       4 6.00 0.07
44       4 8.00 0.07
45       5 0.25 2.05
46       5 0.50 1.04
47       5 0.75 0.81
48       5 1.00 0.39
49       5 1.25 0.30
50       5 2.00 0.23
51       5 3.00 0.13
52       5 4.00 0.11
53       5 5.00 0.08
54       5 6.00 0.10
55       5 8.00 0.06
56       6 0.25 2.31
57       6 0.50 1.44
58       6 0.75 1.03
59       6 1.00 0.84
60       6 1.25 0.64
61       6 2.00 0.42
62       6 3.00 0.24
63       6 4.00 0.17
64       6 5.00 0.13
65       6 6.00 0.10
66       6 8.00 0.09

> head(Indometh)
  Subject time conc
1       1 0.25 1.50
2       1 0.50 0.94
3       1 0.75 0.78
4       1 1.00 0.48
5       1 1.25 0.37
6       1 2.00 0.19
> 
> summary(Indometh)
 Subject      time            conc       
 1:11    Min.   :0.250   Min.   :0.0500  
 4:11    1st Qu.:0.750   1st Qu.:0.1100  
 2:11    Median :2.000   Median :0.3400  
 5:11    Mean   :2.886   Mean   :0.5918  
 6:11    3rd Qu.:5.000   3rd Qu.:0.8325  
 3:11    Max.   :8.000   Max.   :2.7200  
 
> plot(Indometh)


> mys3class <- list(
+   subject = "1",
+   time = "0.25",
+   concentration = "1.50"
+ )
> class(mys3class) <- "Indometh"

> mode(mys3class)
[1] "list"

> class(mys3class)
[1] "Indometh"

> attributes(mys3class)
$names
[1] "subject"       "time"          "concentration"

$class
[1] "Indometh"


> setClass("Indometh",
+   representation(
+    subject = "numeric",
+    time = "numeric",
+    concentration = "numeric"
+ ))
> mys3class <- new(
+   "Indometh",
+      subject = 1,
+      time = 0.25,
+      concentration = 1.50
+ )
> mys3class
An object of class "Indometh"
Slot "subject":
[1] 1

Slot "time":
[1] 0.25

Slot "concentration":
[1] 1.5

> mode(mys3class)
[1] "S4"

> mode(slot(mys3class, "time"))
[1] "numeric"

> mys3class@concentration
[1] 1.5

> isS4(mys3class)
[1] TRUE


Example of S3 using Function UseMethod()

> student <- list(name = "Dhwani", age = 22, major = "Bioinformatics and Computational Biology")
> class(student) <- "student"
> get_info <- function(x) {
+     UseMethod("get_info")
+ }
> get_info.student <- function(x) {
+     cat("Name: ", x$name, "\n")
+     cat("Age: ", x$age, "\n")
+     cat("Major: ", x$major, "\n")
+ }

> my_student <- student
> get_info(my_student)

Name:  Dhwani 
Age:  22 
Major:  Bioinformatics and Computational Biology


Example of S4 using Function setGeneric()

> setClass("Person", 
+          slots = c(name = "character", age = "numeric", major = "character"))
> setGeneric("summary")
[1] "summary"

> setMethod("summary", "Person", function(object) {
+     cat("Name: ", object@name, "\n")
+     cat("Age: ", object@age, "\n")
+     cat("Major: ", object@major, "\n")
+ })
> 
> person1 <- new("Person", name = "Dhwani", age = 22, major = "Bioinformatics and Computational Biology")
> summary(person1)

Name:  Dhwani 
Age:  22 
Major:  Bioinformatics and Computational Biology
