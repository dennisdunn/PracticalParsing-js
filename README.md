Practical Parsing: Examples
===

Example code for my talk "Practical Parsing: Level Up With Parser Combinators". Each of the branches
is this repository parse a grammar for arithmetic expressions with slightly different results.

After cloning the repository, CD into the directory and run ```npm install``` to grab the required dependencies. The example grammar for each branch is exported as the ***start()*** method of the grammar object. Checkout each of the
branches and run ```npm test``` or call ```G.start()``` with your own text stream.

Here is an example nodejs session:

```
> {Stream} = require('@dennisdunn/tiny-parse')
> G = require('./src/grammar')
> s = new Stream('(1 + 2) * 3')
> G.start(s)
```
If you want to use the same stream more than once reset the position with ```s.seek(0)```

### as-parse-tree
The result of the parse is an array-of-arrays that contains all of the textual elements of the source.

### as-token-stream
In this branch, the elements are Token objects and the resulting tree is flattened. The resulting token stream can be passed to the shunting-yard algorithm for evaluation.

### as-abstract-syntax-tree
This grammar returns the parse as an AST_Node instance.
This object is the root of an abstract syntax tree.

### as-computable
The AST nodes have an added ```eval()``` method that computes the value of node and returns it to the caller.  
