## Variable Assignment
Assign values to variables with the assignment operator '='. Typing the variable by itself at the prompt will print out the value. Note that another form of assignment operator "<-" is also in use

x = "HI" or X <- "HI"

## Functions
R functions are invoked by its name, then followed by the parenthesis, and zero or more arguments. The following apply the function <b>'c'</b> to combine five numeric values into a vector.

c(1,2,3,4,5)

## Getting Help in R
help(c)

## Extension and Import Package
Invoke the <b>install.packages</b> function at the prompt and follow the instruction.

install.packages("ggplot2")

library(ggplot2)

# Data type
## Numeric
Decimal values are called numerics in R. It is the default computational data type. If we assign a decimal value to a variable x as follows, x will be of numeric type.

x = 3.14

class(x)

-> "numeric"

Furthermore, even if we assign an integer to a variable k, it is still being saved as a numeric value.

k = 1 << integer, but still numeric value

class(k)

-> "numeric"

The fact that k is not an integer can be confirmed with the <b>is.integer</b> function. We will discuss how to create an integer in our next part on the integer type.

is.integer(k)

-> FALSE

## Integer
In order to create an integer variable in R, we invoke the integer function. We can be assured that y is indeed an integer by applying the is.integer function.

y = as.integer(1)

class(y)

-> "integer"

is.integer(y)

-> TRUE

Incidentally, we can coerce a numeric value into an integer with the as.integer function.

as.integer(3.14)

-> 3

On the other hand, it is erroneous trying to parse a non-decimal string.

as.integer("HI") // error

## Logical
A logical value is often created via comparison between variables.

x = 1; y = 1

z = x > y

z

-> FALSE

class(z)

-> "logical"

Standard logical operations are "&"(and), "|"(or), "!"(negation).

x = TRUE; y = FALSE

x & y

-> FASLE

x | y

-> TRUE

!x

-> FALSE

## Character
A character object is used to represent string values in R. We convert object into character values with the <b>as.character()</b> function:

x = as.character(3.14)

class(x)

-> "character"

Two character values can be concatenated with the <b>paste</b> function.

fname = "Jone"; lname = "Smith"

paste(fname,lname)

-> "Jone Smith"

However, it is often more convenient to create a readable string with the <b>sprintf</b> function, which has a C language syntax.

sprintf("%s has %d dollars, fname, 10) << <b>Different from python!!, it seems to be C</b>

-> "Jone has 10 dollars"

To extract a substring, we apply the <b>substr</b> function. Here is an example showing how to extract the substring between the second and tenth positions in a string.

substr("Mary has a little lamb.", start=2, stop=10)

-> "ary has a"

To replace the first occurrence of the word “little” by another word “big” in the string, we apply the <b>sub</b> function.

sub("little", "big", "Mary has a little lamb.")

-> "Mary has a big lamb."

## Vector
A vector is a sequence of data elements of the same basic type. Members in a vector are officially called components. Here is a vector containing three numeric values 1, 2 and 3.

c(1,2,3) // <b>c is not variable, So you can use only c!!</b>

And here is a vector of logical values.

c(TRUE, TRUE, FALSE, TRUE, FALSE)

A vector can contain character strings.

c("Mary", "has", "a", "little", "lamb")

Incidentally, the number of components in a vector is given by the length function.

length(c("Mary", "has", "a", "little", "lamb"))

-> 5

## Combining Vectors
Vectors can be combined via the function c. For examples, the following two vectors x and y are combined into a new vector containing elements from both vectors.

x = c(1,2,3)

y = c("a", "b", "c")

c(x,y)

-> "1" "2" "3" "a" "b" "c" // <b>1,2,3 is not numeric because of y!!!</b>

## Vector Arithmetics

Arithmetic operations of vectors are performed component-by-component. For example, suppose we have two vectors x and y.

x = c(1,2,3,4)

y = c(2,4,6,8)

Then, if we multiply a by 5, we would get x vector with each of its components multiplied by 5.

5*x

-> 5 10 15 20

If we add x and y together, the sum would be a vector whose components are the sum of the corresponding members from x and y.

x + y

-> 3 6 9 12

x-y, x*y, x/y also available.

## Recycling Rule
If two vectors are of unequal length, the shorter one will be recycled in order to match the longer vector. For example, the following vectors x and y have different lengths, and their sum is computed by recycling values of the shorter vector x.

x = c(10, 20, 30)

y = c(1,2,3,4,5)

x + y

-> 11 22 33 14 25 //<b>4 and 5 are added by 10 and 20 !!!</b>

## Vector Index

We retrieve values in a vector by declaring an index inside a single square bracket <b>“[]”</b> operator. For example, the following shows how to retrieve a vector component. Since the vector index is 1-based, we use the index position 2 for retrieving the second component.

x = c("a", "b", "c", "d", "e")

x[2]

-> "b"

## Negative Index

If the index is negative, it would strip the component whose position has the same absolute value as the negative index. For example, the following creates a vector slice with the second component removed.

x[-2]

-> "a" "c" "d" "e" // "b" is removed.

## Numeric Index Vector

A new vector can be sliced from a given vector with a numeric index vector, which consists of component positions of the original vector to be retrieved. Here, it shows how to retrieve a vector slice containing the second and third components of a given vector x.

x = c("a", "b", "c", "d", "e")

x[c(2,3)]

-> "b" "c"

## Range Indexes

To produce a vector slice between two indexes, we can use the colon operator “:”. This can be convenient for situations involving large vectors.

x[c(2:4)]

-> "b" "c" "d"

## Matrix

We reproduce a memory representation of the matrix in R with the matrix function.

A = matrix(
  c(2,4,3,1,5,7),
  nrow=2,
  ncol=3,
  byrow = TRUE)

A

-> 2x3 matrix and aligned by row. if not use byrow, A will be [2,3,5] row and [4,1,7] row.

An element at the m row, n column of A can be accessed by the expression A[m,n].

A[2,3]

-> 7

A[2,]

-> 1 5 7

If we assign names to the rows and columns of the matrix, than we can access the elements by names.

dimnames(A) = list(
  c("row1", "row2"),
  c("col1", "col2", "col3"))
  
## Matrix Construction
### Transpose
We construct the transpose of a matrix by interchanging its columns androws with the function t.

t(A)

### Combining Matrices
cbind(A,B) // number of column is equals to A,B. Then, input column A and column B.
rbind(A,B) // number of row is equals to A,B

## List
n = c(2,3,5)
s = c("aa", "bb", "cc", "dd", "ee")
b = c(TRUE, FALSE, TRUE, FALSE, FALSE)
x = list(n,s,b,3)
### List slicing
x[2]

-> "aa" "bb" "cc" "dd" "ee"

x[c(2,4)]

-> "aa" "bb" "cc" "dd" "ee" , 3 // represent 2nd and 4th elements in x

### Member Reference

x[[2]]

-> "aa" "bb" "cc" "dd" "ee" // equals to x[2], but it seems to be reference 2nd element x, not s

x[[2]][1] = "ta"

x[[2]]

-> "ta" "bb" "cc" "dd" "ee"

s

-> "aa" "bb" "cc" "dd" "ee" // s is unaffected

### Names List members

v = list(bob=c(2,3,5), john=c("aa", "bb"))

v

-> bob 2 3 5, john "aa" "bb"

v["bob"]

-> 2 3 5

### Member Reference
v[["bob"]] or $bob

### Data Frame
x = c(1,2,3)

y = c("a", "b", "c")

z = c(TRUE, FALSE, TRUE)

df = data.frame(x,y,z)

df // df is a data frame

-> x y z

1  1 a TRUE

2  2 b FALSE

3  3 c TRUE
