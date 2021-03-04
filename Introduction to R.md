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
