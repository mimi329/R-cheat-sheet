# R-cheat-sheet

## General
* [import and tidy data](https://github.com/jananiravi/cheatsheets/blob/master/r/tidyverse-data-import-cheatsheet.pdfhttps://github.com/jananiravi/cheatsheets/blob/master/r/tidyverse-data-import-cheatsheet.pdf)
* 

## *Week 1*
### Useful functions
* random
```
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
* check the structure of an object
```
str()
```
* convert a logical vector to a single vector: are they all TRUE, or is any of those TRUE, respectively
```
all(), any() 
```
* remove all duplicates in a vector, returning only the unique elements of a vector
```
unique() 
```
* compute means of each column/row of a matrix or dataframe
```
colMeans(), rowMeans() 
```
* create a string vector
```
a <- paste("studentID", 1:10, sep = "_")
```
* find and replace
```
grep(pattern = "student", data) #find
grepl() #same but logical
gsub("find_me", "replace_with", data) #find and replace
```
* 

### Vectors
* indexing
```
x[4] # take 4th element
x[4:6] # take 4th through 6th elements
x[c(3, 5)] # take 3rd and 5th elements
x[-2] # take all elements except the 2nd element
x[x > 0] # take elements of x greater than 0
```

### Matrices
* creating and binding
```
a <- matrix(ncol = 3, nrow = 3, 1:9) # a matrix filled with the numbers 1 through 9
b <- matrix(ncol = 6, nrow = 3, rnorm(18)) # a matrix filled with 18 normally distributed numbers
cbind(a, b) #c stands for column
cbind(b, a) # change the order of binding
rbind(m, c(1,2,3)) #r stands for row
#create random matrix

set.seed(1234)
NRows <- sample(2:200,1) #Find a random number of rows
NCols <- sample(2:200,1) #Find a random number of columns
MyArray <- matrix(data=seq(1,NRows*NCols), nrow = NRows, ncol=NCols) #Make a matrix (array)
dim(MyArray)
```
* indexing
```
a[, 2] # take 2nd column
a[2, ] # take 2nd row
a[2,2] # take element at 2nd row, 2nd column
a[,-2] # remove the 2nd column
```

### Arrays
```
array(1:12, dim=c(1,2,3))
```

### Lists
```
#to index a list use [[ or $
v1 <-c(5,10,2,13)
l1 <-list(v1=v1, m1=n)
l1$v1
#change the element in a matrix
l1$m1[2,2]<-0
l1$m1
#lists are a popular way of returning data
t.test(1:9)
result <- t.test(1:9)
result$p.value
```

### Data frames
* turn into a data frame
```
df <- data.frame()
```
* create a data frame
```
data.frame(
    FirstVariable = rep(c(),5),
    SecondVariable = c()
    ThirdVariable = variable3
    )
```
## *Week 2*

## *Week 3*

## *Week 4*

### tidyverse
* filter data
* mutate a variable (into a new variable)
* sort data
* *and don't forget to use the pipe again after every line*
```
gapminder %>%
    filter(year == 2007) %>%
    mutate(lifeExpMonths = 12 * lifeExp) %>%
    arrange(desc(lifeExpMonths))
```
### Cleaning and ordering data
* observe data and missing values
```
summary(TPT_scores[,45:50])
dim(TPT_scores)
colSums(is.na(TPT_scores))
```
* create a new variable
```
df$newvariable <- df$extra + df$group
```

* rename a variable
```
colnames(df)[3] <- "New name"
```
* remove several variables
```
new_df <- select(df, !(2:44))
```
* combine data
```
combined_df <- join(df1, df2, by = "Participant", type = "full")
```
* choose a subset of a data frame
```
subset(df, group == 1)
df[df$group == 1]
```

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
