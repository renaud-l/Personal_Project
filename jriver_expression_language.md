jriver - expression language page

source: https://wiki.jriver.com/index.php/Expression_Language

## Expression Language

Media Center provides a simple programming language that enhances and enriches its overall user interface and usability. This language, commonly called the expression language, is simple to learn, simple to use, and can greatly enhance your experience using Media Center.

Expressions are ubiquitous throughout Media Center, used in areas such as:

The categories in a view
File list expression columns
Theater View
Customized view headers, grouping and sort criteria
The library field manager (fields with data type Calculated data)
File and folder location definitions
Auto-import rules
Custom DLNA titles
The player's display
Captions and thumbnail text
The link manager (expressions help format link URLs)
Rename, Move, & Copy tool
Tag assignment
Complex search queries
An expression is a mixture of ordinary text, pre-defined functions, and a few reserved characters and constructs that have special meaning. An expression is evaluated by Media Center's expression engine and textual output is produced. This output is then used by Media Center to customize the user interface and affect its method of operation

## The Anatomy of an Expression

As mentioned above, an expression is a mixture of text and function calls (and some reserved stuff described shortly). The simplest expression would be some basic, literal text, such as A good movie. The expression engine evaluates this expression, finds nothing special, and then outputs the result: A good movie. Simple.

But simple text only has so much utility. The ability to transform or generate content is much more interesting and useful. And this is when functions are employed. Media Center provides many functions, which when called, produce some output. Most functions require some form of input, called arguments, and most functions generate output. By supplying a function with various arguments, the function will return some output value which is just more text. And this output text can be the used by other functions, and so on. Each function has a unique name, and calling upon a function to do some work requires little more that using its name anywhere in the expression.

A function call looks like this:

functionname(argument 1, argument 2, ...)
The syntax of the function call is the function's case-insensitive name, immediately followed by an opening parenthesis character, one or more comma-separated arguments, and a closing parenthesis character. Whitespace after the commas is optional, but helps readability and formatting. And each argument itself is also just an expression. And some arguments are optional. If an argument is optional, it can be omitted and its default value will be used. If the argument is omitted, a comma-separator will still be required if additional arguments follow. The following example uses the FixCase() function to change its input to Title Case:

fixcase(A good movie)
The result is A Good Movie.

A slightly more complex expression example consists of both text and a nested function call:

Wow! fixcase(replace(A good movie, good, great))
Inner functions are called before outer functions, so the Replace() function is call first:

replace(A good movie, good, great)
and its output is then supplied as the input to the FixCase() function. Replace() does its work substituting good with great, and returns A great movie. This output is then supplied as the argument to FixCase() which sees only the text A great movie (it knows nothing about how it was produced). So the function call:

fixcase(A great movie)
in turn outputs A Great Movie. Now that the functions have produced their output, the final output, including the literal Wow! leading text is

Wow! A Great Movie
