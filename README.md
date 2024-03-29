# R-cheat-sheet

## General
* [import and tidy data](https://github.com/jananiravi/cheatsheets/blob/master/r/tidyverse-data-import-cheatsheet.pdfhttps://github.com/jananiravi/cheatsheets/blob/master/r/tidyverse-data-import-cheatsheet.pdf)
* [correlations](https://www.guru99.com/r-pearson-spearman-correlation.html)
* [operators](https://www.tutorialspoint.com/r/r_operators.htm)

<details><summary>Useful functions</summary>
<p>

* random
```ruby
min, max, range, summary
colSums, rowMeans etc.
is.numeric(), is.logical(), is.character(), typeof(), mode()
strsplit()
rnorm(), runif(), rbinom() #random distributions
prod() #multiply
seq(from, to, by) #create a  regularsequence
sample(x, size) #sample from a vector
rep(vector, each = 2) #repeat each element from a vector a certain number of times
setwd("C:/Users/me/Documents/PIPS") #set working directory
write.csv(InsectSprays, "InsectSprays.csv", row.names = FALSE) #save a file
```
* importing data
```ruby
fread() #library(data.table)
read.csv2() #reads a file in a table format and creates df
```
* check the structure of an object
```ruby
str()
```
* convert a logical vector to a single vector: are they all TRUE, or is any of those TRUE, respectively
```ruby
all(), any() 
```
* remove all duplicates in a vector, returning only the unique elements of a vector
```ruby
unique() 
```
* compute means of each column/row of a matrix or dataframe
```ruby
colMeans(), rowMeans() 
```
* paste() and strsplit()
```ruby
#combine string vectors
a <- paste("studentID", 1:10, sep = "_")

#use in a loop
print(paste("Dice roll no. :", counter))
print(paste("Wallet :", wallet ))

#elementwise glueing
vector1 <- c("Ana", "Tango", "Tum")
vector2 <- c("Banana", "Mango", "Yum")
combined <- paste(vector1, vector2)
[1] "Ana Banana", "Mango Tango", "Tum Yum"

#glueing into a single string
comb <- paste(vector1, collapse = "-")
[1] "Ana-Tango-Tum"

#splitting
strsplit(a, split="_")
```
* rep(x, 3) - repeat x three times
```ruby
#populate a vector fast
empty_vector <- rep(0,1000000)
for(i in 1:1000000) {empty_vector[i] <- i}

#repeat a dataframe, but use data.frame() bcs it will otherwise return a list
doubled_data <- data.frame(rep(data, 3))
```
* replace
```ruby
data_obs[data_obs < 0] = NA
data_obs <- replace(data_obs, data_obs < 0, NA)
```
* find and replace
```ruby
grep(pattern = "student", data) #find
grepl() #same but logical
gsub("find_me", "replace_with", data) #find and replace
```
* look at parts of data
```ruby
slice(gapminder, 3:nrow(gapminder)) # Look at the 3rd row to the last row
slice(gapminder, 3:n()) # Special n() command to index last element
#if you assign it to something it's like subset()
```
* choose only even numbers
```ruby
(i %% 2) == 0
```
* give error or warning
```
add <- function(x, na.rm = TRUE) {
  if(!is.numeric(x)) {
    stop("only numeric values allowed") #gives an Error message
  }
  if(sum(is.na(x)) > 0) {
    warning("NA values detected") #gives a Warning message
  }
```
* operators
    * relational: ==, !=, < > <= >=!
    * logical: &, |, !
    * && looks at only first element of the vector
```
 
```

</p>
</details>      

<details><summary>WEEK 1</summary>
<p>
      
## *Week 1*
### Vectors
* indexing
```ruby
x[4] # take 4th element
x[4:6] # take 4th through 6th elements
x[c(3, 5)] # take 3rd and 5th elements
x[-2] # take all elements except the 2nd element
x[x > 0] # take elements of x greater than 0
```
* logical vectors
```ruby
#let's say you have a vector with ages
#you can just put a logical argument and it will assign T / F values
ages_logic <- (ages < 44)
```
### Matrices
* creating and binding
```ruby
a <- matrix(ncol = 3, nrow = 3, 1:9) # a matrix filled with the numbers 1 through 9
b <- matrix(ncol = 6, nrow = 3, rnorm(18)) # a matrix filled with 18 normally distributed numbers
cbind(a, b) #c stands for column
cbind(b, a) # change the order of binding
rbind(m, c(1,2,3)) #r stands for row

#if you don't want it to be filled by columns
m <- matrix(1:6, 6, 4, byrow = TRUE)

#create a super random matrix
set.seed(1234)
NRows <- sample(2:200,1) #Find a random number of rows
NCols <- sample(2:200,1) #Find a random number of columns
MyArray <- matrix(data=seq(1,NRows*NCols), nrow = NRows, ncol=NCols) #Make a matrix (array)
dim(MyArray)
```
* indexing
```ruby
a[, 2] # take 2nd column
a[2, ] # take 2nd row
a[2,2] # take element at 2nd row, 2nd column
a[,-2] # remove the 2nd column
a[ c(TRUE,FALSE), ] #select all even rows 
```

### Arrays
```ruby
array(1:12, dim=c(1,2,3))

#can be filled with a loop, notice the indexing
#imagine a line, a plane, a cube
exponential_array <- array(dim = c(5, 5, 100))
for (i in 1:100) {
  exp_draws <- rexp(25, rate = i)
  exponential_array[, , i] = matrix(exp_draws, nrow = 5, ncol = 5)}
```

### Lists
```ruby
#to index a list use [[ or $
v1 <-c(5,10,2,13)
l1 <-list(v1=v1, m1=n)
l1$v1

#make a list of matrices
myList <- rep(list(matrix(sample(1:10, replace=TRUE), 6, 5)), 5)
#make every matrix unique
for(i in 1:5) {myList[[i]] <- (matrix(sample(1:10, replace=TRUE), 6, 5))}
      
#change a single element in a matrix in a list
l1$m1[2,2]<-0

#lists are a popular way of returning data
t.test(1:9)
result <- t.test(1:9)
result$p.value
```

### Data frames
* turn into a data frame
```ruby
df <- data.frame()
```
* create a data frame
```ruby
data.frame(
    FirstVariable = rep(c(),5),
    SecondVariable = c()
    ThirdVariable = variable3
    )
```

</p>
</details>

<details><summary>WEEK 2</summary>
<p>

## *Week 2*
### Conditional statements
* if statements
    * make sure you include all possibilities!
    * take care of the ORDER of the statements
```ruby
#first assign variables
shot <- "missed"
jumped <- "right"
our_goals <- 1
their_goals <- 1

#create a condition: logical statement
if ((shot != jumped) & (shot != "missed")) {
  our_goals <- our_goals + 1
} else if (shot == "missed") {
  print("Coach OUTRAGED")
} else {
  our_goals <- our_goals + 0
  print("Sad sport fans.")
}
print(our_goals)
```
* it will only use the first element: add *all*
```ruby
small_numbers <- seq(0, 1, by=.001)
they_are_small <- FALSE
if (all(small_numbers > 1.1)) {
  they_are_small <- TRUE
}
```
* ifelse statements
```ruby
ifelse(conditon, if true, if false)
#condition must be a logical vector of length >=1
x <- 1:7
ifelse(x %% 2 == 0, 'even', 'odd')
```

### Explicit loops
* general: next: loop continues but skips current iteration; break: loop stops
* while loops
```ruby
#play the dice game until we broke
wallet <- 10
while(wallet > 0)
{dice <- sample(1:6, 3, replace=TRUE)
  if(length(unique(dice)) == 3)
  {wallet <- wallet + 1
  } else {
    wallet <- wallet - 3
  }
}

#create conditions for when to stop rolling the dice
#notice that all() and sort() are used
while(!all(dice == c(6,6,6)) & !all(sort(dice) == c(1,2,3))) {
  dice <- sample(1:6, 3, replace = TRUE)
  print(dice)
}
  
#can also use break statement:
ctr <- 1
While(ctr <= 7) {
   if(ctr %% 5 == 0) {    # while loop will be abandoned 
         break
     }
      print(paste("ctr is set to", ctr))
      ctr <- ctr + 1                                    
} 
```
* for loops
```ruby
for (counter in 1:n) {body}

#if you want to replace all values in v with 0
for(i in 1:length(v))
{if(v[i] %% 2 == 0)
  {v[i] <- 0
  }
}

#use it to fill a matrix
my_matrix <- matrix(nrow = 3, ncol = 3)
for(row in 1:3)
{for(column in 1:3)
  {my_matrix[row,column] <- row * column
  }
}

#or use it to compute
my_vector <- 1:4
my_sum = 0
for(i in 1:length(my_vector)){
  my_sum <- my_sum + my_vector[i]
}
my_sum
  
#use to create a statement, nested loop
for(i in 1:nrow(data)){
  for(j in 1:ncol(data)){
    print(paste("On row", i, "and column", j, "we have", data[i,j]))
  }
 }
```

### Implicit loops
* apply
```ruby
apply(X,       # Array, matrix or data frame
      MARGIN,  # 1: columns (line), 2: rows (plane), c(1, 2): rows and columns, 3: cube
      FUN, ...)# Function to be applied
```
* lapply: applies a function to a list or a vector, returning a list of the same length as the input
* sapply: applies a function to a list or a vector, returning a vector or matrix if it can, or an array
```ruby
sapply(X,   # Vector, list or expression object
       FUN, # Function to be applied
       ..., # Additional arguments to be passed to FUN
       simplify = TRUE,  # If FALSE returns a list. If "array" returns an array if possible 
       USE.NAMES = TRUE) # If TRUE and if X is a character vector, uses the names of X

sapply(1:3, function(i) {matrix(i, ncol = 3, nrow = 3)}, simplify = "array")
within_range <- function(mph, low, high){
  if(mpg>= low & mpg <= high){
    return(TRUE)
  }else {return(FALSE)}
}
index <- sapply(X=data$mpg, FUN=within_range, low = 15, high = 20)
#here we have the first arguement defined by the data we defined and we additionaly defined the other two arguements

#if you use it on a dataframe it will apply the function to each column
sapply(df, FUN = sum)
```
* mapply: can be used to apply multiple vectors at the same time
```ruby
function(arg1, arg2){if arg1 is this, do that etc.}
```
### Advanced flow control
  * switch: tests an expression against elements of a list
  ```
  yoo no comprendo
  ```
  * 
</p>
</details>

<details><summary>WEEK 4</summary>
<p>

## *Week 4*

### tidyverse
* the pipe: read it left to right
```ruby
#read it left to right
my_norm_data %>% abs() %>% mean(na.rm=TRUE) 

#base r pipe:
my_norm_data |> abs() |> mean(na.rm=TRUE)
```
* filter data
* mutate a variable (into a new variable)
* sort data
      * *and don't forget to use the pipe again after every line*
      * *also if you want to have the changes saved do* gapminder_new <-
```ruby
gapminder %>%
    filter(year == 2007) %>%
    mutate(lifeExpMonths = 12 * lifeExp) %>%
    arrange(desc(lifeExpMonths))
```
* summarize(): generate stats for columns in a dataset
```ruby
data %>% summarize(mean_c1 = mean(c1),
                   median_c2 = medial(c2))
data %>% summarize_all(list(mean = mean), na.rm = TRUE)
#will generate column names on its own

#cool functions to apply to each column
summarize(count = n(column)) # how many elements
                  n_distinct(column) # how many unique elements
```
* grouping
```ruby
data %>% group_by(Class) %>%
         mutate(overachievers = Grade - mean(Grade)) #will calculate mean within Class
```
* make long data
```ruby
gapminder_long <- gapminder %>%
  pivot_longer(
    lifeExp:gdpPercap, #take those three columns
    names_to = "measure", #put the names of the columns to measure variable
    values_to = "value" #put the values to value function
  )
#have the participantID column in the data but not use it in the function!
```
* make wide data
```ruby
#starting with elongated data
gapminder_tidy <- gapminder_long %>%
  pivot_wider(names_from=measure, values_from=value)

#starting with original data
 gapminder_wide <- gapminder %>%
  pivot_wider(
    names_from = year,
    values_from = c(lifeExp, pop, gdpPercap)
  )
``` 
### Cleaning and ordering data
* observe data and missing values
```ruby
summary(TPT_scores[,45:50])
dim(TPT_scores)
colSums(is.na(TPT_scores))
```
* create a new variable
```ruby
df$newvariable <- df$extra + df$group
```
* rename a variable
```ruby
colnames(df)[3] <- "New name"
```
* remove several variables
```ruby
new_df <- select(df, !(2:44))
data1 <- data1 %>% slice(3:n())
slice(data1, -(1:2)) #select which rows to drop
```
* combine data
```ruby
#when you want to join data based on a key variable
combined_df <- join(df1, df2, by = "Participant", type = "full")
type = "inner" drop all records that didn't exist in BOTH tables
type = "left" keep all records of the FIRST table, even if missing in the second
type = "full" don't drop any records

#if you have the same info with different column names in two tables
combined_df <- join(df1, df2, by="Participant", "gender" = "sex", type = "full")

#find out which records have / not have a match in the second df
df1 %>% semi_join(df2, by = "Participant")
df1 %>% anti_join(df2, by = "Participant")

#when data overlaps
combined_df <- bind_rows(list(df1, df2))
combined_df <- list(df1, df2) %>% bind_rows()
```
* choose a subset of a data frame
```ruby
subset(df, group == 1)
df[df$group == 1]
```
</p>
</details>
      
<details><summary>how to</summary>
<p>
____________________________________________________________________________________________________________________________________________

## How to use this format:

* writing a list
* is like this

## This is the second title

1. haha
2. hehe
3. hihi

```
{
  "firstName": "John",
  "lastName": "Smith",
  "age": 25
}
```

| Syntax | Description |
| ----------- | ----------- |
| Header | Title |
| Paragraph | Text |

[title](https://www.example.com)
  
- [x] Write the press release
- [ ] Update the website
- [ ] Contact the media

~~The world is flat.~~

**bold text**

*italicized text*

==highlight==

<mark>highlight</mark>
      
</p>
</details>

<details><summary>Stats 1</summary>
<p>
  
Linear regression
```ruby
#linear model
  lm(x ~ y)
#the long way: computing step by step
  #create data:
  y <- c(4,3,5,6,9)
  x1 <- c(3,4,6,8,8)
  x2 <- c(2,6,4,7,7)
  x0 <- c(1,1,1,1,1)
  df1 <- data.frame(y, x0, x1, x2)
  XX <- matrix(1:5, nrow = 5, ncol = 3)
  XX[,1] <- x0
  XX[,2] <- x1
  XX[,3] <- x2
  XT <- as.matrix(t(XX))
#matrix multiplication
  XTXX <- XT %*% XX
  XTY <- XT %*% y
  tXXi <- solve(XTXX) #solve obtains the inverse, similar to 1/x
  hat.beta <- tXXi %*% XTY #obtain the estimates of the coefficients
#get standard residual errors
  #short way:
  summary(fit)
  sqrt(sum(residuals(fit)^2)/(5 - 2 - 1))
  #long way (look at the formula):
  y <- c(4,3,5,6,9)
  X <- matrix(c(1,1,1,1,1,3,4,6,8,8,2,6,4,7,7),nrow=5,ncol=3,byrow=FALSE)
  s2 <- t(y-X%*%solve(t(X)%*%X)%*%t(X)%*%y)%*%(y-X%*%solve(t(X)%*%X)%*%t(X)%*%y)/(5-3)
  sqrt(s2)
#interaction
  score ∼ concentration + time_studied + concentration:time_studied
  #is the same as
  score ∼ concentration*time_studied
#centering
  mtcars[, "hp"] = mtcars[, "hp"] - mean(mtcars[, "hp"])
```
t-test
```ruby
#homogeneity of variances
  leveneTest(d$score1, group = as.factor(d$sex))
  t.test(d$score1[d$sex=='f'],d$score1[d$sex=='m'],alternative='less')
  #alternative would be = "more" if we expect the first group to score higher than the second
#or like this
  t.test(score1 ~ sex, data=d, alternative="less")
#test a two sided hypothesis
  t.test(d$score1, d$score2, alternative="two.sided")
```
Finding the t value and confidence interval
```ruby
#compute t value
  df <- length(math.scores)-1
  t.math <- qt(.975, df = df)
#compute standard error
  se.math <- sd(math.scores)/sqrt(length(math.scores))
#compute margin of error and CI
  moe <- se.math*t.math
  lower.bound <- mean(math.scores) - moe
  upper.bound <- mean(math.scores) + moe
```
Comparing models
```ruby
#Multiple R-squared and AIC
#the lowest AIC = best fit
  summary(fit1)
  AIC(fit1)
  ```
Visualising residuals
```ruby
  library(car)
  residualPlot(fit4)
  res4 <- residuals(fit4)
  hist(res4,border='white',bty='n',col='blue',main='')
  ```
Cross-validation
```ruby
set.seed(2020)
sk <- 5
n <- 30
fold6 <- rep(1:5,6)
fold6 <- sample(fold6,n,replace=FALSE)
mse4 <- c()
mse5 <- c()
for(i in 1:5){
  test <- which(fold6==i)
  train <- which(fold6!=i)
  fit4 <- lm(nrvisits[train] ~ physical[train] + stress[train], data=data.med)
  fit5 <- lm(nrvisits[train] ~ mental[train] + physical[train] + stress[train], data=data.med)
  mse4[i] <-
    sum((nrvisits[test] -
           cbind(rep(1,length(test)), physical[test], stress[test]) %*% coefficients(fit4))^2) / (length(test)-3)
  mse5[i] <-
    sum((nrvisits[test] -
           cbind(rep(1,length(test)),mental[test],physical[test],stress[test])%*%coefficients(fit5))^2)/(length(test)-4)
}

mse4.m <- mean(mse4)
mse5.m <- mean(mse5)
```
MANOVA
```ruby
#assumptions: 
  #independence, linearity, adequate sample size + ...
#h0 = multivariate normality, p<0.05
  library(rstatix)
  mshapiro_test(data)
#h0 = homogeneity of (co)variance matrix, p<0.001
  boxM(Y = df[,1:2], group = df[,3])
```
T squared
```ruby
fit.hotel <- hotelling.test(sleep + light ~ group, data = health)
fit.hotel
str(fit.hotel)
Y1 <- as.matrix(health[health$group==1,c("sleep", "light")],ncol=2)
Y2 <- as.matrix(health[health$group==2,c("sleep", "light")],ncol=2)

# then make the covariance matrices
S1 <- var(Y1)
S2 <- var(Y2)

# make the pooled covariance matrix
#n1 = 34, n2 = 34
Sp <- (33*S1 + 33*S2)/(34+34-2)

#inverse of the matrix
solve(Sp)

# Next we compute the mean vectors for the two groups
m2 <- apply(Y2,2,mean)
m1 <- apply(Y1,2,mean)

# and finally obtain Hotelling's T^2 and F
T2 <- (34*34)/(34+34)*t(m1-m2)%*%solve(Sp)%*%(m1-m2)
F <- ((n1+n2-p-1)/(n1+n2-2)*p)*T2
```
```ruby
#fit the model
  maovfit <- manova(cbind(sleep, light) ~ group, data=health)
  summary(maovfit)
  #which is the same as:
  fitlm <- lm(cbind(sleep,light) ~ group, data = health)
  anova(fitlm)
#if significant, do univariate analysis, either like this:
  summary(fitlm)
  #or:
  fit1 <- aov(sleep ~ group, data = health)
  summary(fit1)
  fit2 <- aov(light ~ group, data = health)
  summary(fit2)
#pairwise comparisons:
  fit_iris <- aov(Sepal.Width ~ Species, data = iris)
  summary(fit_iris)
  library(rstatix)
  tuk <- tukey_hsd(fit_iris)
  View(tuk)
```
Discriminant analysis
```ruby
#first check variances, h0 = equal variances, p<0.001
  box_m(data = health[,1:2], group = health[,3])
#LDA:
  library(MASS)
  model1 <- lda(group ~., data = health)
  model1
#Confusion matrix:
  table(predict(model1, type = "class")$class, health$group)
```
```ruby
#if you want to cross validate it
set.seed(343)
n <- nrow(ocd2)
train <- sample(1:n,n/2)
test <- -train

library(MASS)
fitlda <- lda(Group ~ Actions + Thoughts, data=ocd2[train,])
predlda <- predict(fitlda,newdata=ocd2[test,])
table(predlda$class,ocd2$Group[test])
```
Mixed models: before fitting the models
```ruby
#plot and observe the differences in slopes
  xyplot(frequency ~ time | BST, group=subject, data=sex.l, type='b',pch=16)
  
#transform to wide, but what is the [,-1] at the end
  data_wide <- as.matrix(reshape(data, direction = "wide", idvar = "Rat", timevar = "Time")[,-1])

#make data frame with the time variable names
  idata <- data.frame(Time = as.factor(colnames(data_wide)))

#prep: base model
lmaov <- lm(data_wide ~ 1)
#repeated measures ANOVA
  rmaov <- car::Anova(mod = lmaov, idata = idata, idesign = ~Time, multivariate = FALSE)
  summary(rmaov)
#assumptions:
    #sphericity {kind of like homogeneity}
    #Mauchly's test: H0: there is sphericity (variances of the differences are equal), alpha = 0.05
  #assuming sphericity look at the F statistic
  #assuming no sphericity: look at p[GG] and p[HF]
#repeated measures MANOVA if sphericity is violated
  rmaov <- car::Anova(mod = lmaov, idata = idata, idesign = ~Time)
  summary(rmaov)
  #independent of sphericity, look at Pillai's trace and the linked F
```
Mixed models: fitting the models
```ruby
library(lme4)
  #define factors
  data$Diet <- as.factor(data$Diet)
  data$Time <- as.factor(data$Time)

#mixed intercept model (1|Rat = compute intercept for each rat)
  mixed1 <- lmer(weight ~ Time + Diet + (1|Rat), data = BodyWeight,  REML = FALSE)
  summary(mixed1)
  coef(mixed1)
  #you get personalized coefficients for each participant
  #alternatively using lme (no important differences between the two
  fit1 <- lme(weight ~ time*diet, random = ~ 1|subject, data=BodyWeight, method="ML")
  
  #the number of parameters should be: random and fixed effects intercepts, residual variance (random), and p-1 for each (random/fixed) variable

#mixed intercept + slope (Time|Rat = add a randome slope for Time for each Rat)
  mixed2 <- lmer(weight ∼ Time + Diet + (Time | Rat), data = BodyWeight, REML = FALSE)
  fit2 <- lme(weight ~time*diet, random = ~ time | subject, data =BodyWeight, method = "ML")
```
```ruby
#model fit coefficients
  AIC(mixed1, mixed2)
  BIC(mixed1, mixed2)
#find out if the differences between models are significant
  anova(mixed1, mixed2)
```
        

          
          
</p>
</details>

