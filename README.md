# Python - Part 2

## Jupyter Notebooks

- Jupyter notebooks are a special type of file that allows formatted notes to be mixed with Python code.
- These notebooks can be run on SuperMike through OnDemand.
- To open a Jupyter notebook, go to the "Interactive Apps" menu at the top and select "Jupyter Notebook".
- A form will be displayed that asks for some information. For now, please use these options:
    - Account: Leave blank for now
    - Queue: "single"
    - Number of hours: 1
    - Number of nodes: 1
    - Bc Num Cores: 1
- Note that these options will "charge" an account for the time used to run the notebook. For the purposes of this class, there will never be a need to change the numer of nodes to more than 1. You may later need to increase the number of hours, but please only ask for as many hours as you will be actively working at a time. If you open a notebook during the time you've requested, you won't need to re-enter any of this information. If the time has expired, you will need to make another request for time.
- If you've cloned this week's repository in your HPC account, it includes a file called "ExampleJupyterNotebook.ipynb" that you can open once you've started a Jupyter Notebook Server.
- [OPTIONAL] If you end up wanting to work with Jupyter notebooks on your own computer, you can install it locally. Probably the most popular way to run Jupyter notebooks locally is by installing Anaconda (https://www.anaconda.com).

```
Practice Exercise

Follow the procedure above to start a new Jupyter notebook server. Create a new notebook and add both 
some text and some Python code.
```

## String Formatting
  
- Python has a special way to format strings so that the values of variables can be included
- The operator `%` is used to indicate that the values of certain variables should be used to fill in a string
- The parts of the string where the values should go is indicated with placeholders (kinda like wildcards)
- The three most basic placeholders are:
    - `%d` - An integer
    - `%f` - A floating point number (i.e., a decimal)
    - `%s` - A string
- Try this:
    - `faveInt = 7`
    - `faveFloat = 3.14`
    - `faveString = phyleaux`
    - print("Favorite integer is %d, favorite float is %f, and favorite string is %s." % (faveInt,faveFloat,faveString))
- Note how the variables holding the values are provided in the same order inside parentheses after the `%`.

## User Input

- Python has a special function, `input("Message:" )`, to accept input from a user.
- This function reads the user input and returns it. But be sure to store it in a variable!
    - `userStr = input("Input some string: ")`
- You can use the string methods outlined above to standardize user input - like stripping out excess whitespace, changing character case, etc.

```
Practice Exercise

Write a Python script that asks a user to input three different kinds of variables, using three 
separate input() commands. Then use string formatting to print out the values of all three 
variables in one string. Please do this in a Jupyter notebook.
```

## Getting help from Python
  
- If you need help remembering what methods are available for a given object, use `dir(<OBJECT>)`
- Note that methods starting and ending with "__" are not meant for users to call. They are methods to be used by the system.
- Try creating a string variable (e.g., `myStr = "some text"`).
    - Now run `dir(myStr)`
    - Pick a method you haven't used before and see what it does with `myStr`.


## `if` statements

- These are similar in form to bash, but simpler.
- The general form is:

```
if <CONDITION>:
    <DO_THIS>
```
   
- The `if` statement has to finish with a `:`.
- Also, in Python, the code block _inside_ the `if` statement must be indented. You can use either tabs or a certain number of spaces. When using spaces, you must use the __same__ number of spaces throughout your code. The official recommendations for Python style strongly suggest using 4 spaces, rather than tabs.
- Note that the syntax for conditions is pretty intuitive in Python
    - `myStr != "other text"`
- `if` statements can be used on their own, but no code will be executed when the condition is false.


## `if...else` statements

- To include code blocks that should be executed when the condition is false, you'll need to use an if...else statement. These have the general form:

```
if <CONDITION>:
    <DO_THING_WHEN_TRUE>
else:
    <DO_THING_WHEN_FALSE>
```
            
- Sometimes, you'll want to test a series of conditions to decide what to do. In that case you could use a nested set of `if...else` statements:

```
nuc = "A"
if nuc == "A":
    print("Nucleotide is an A.")
else:
    if nuc == "C":
        print("Nucleotide is a C.")
    else:
        if nuc == "G":
            print("Nucleotide is a G.")
        else:
            if nuc == "T":
                print("Nucleotide is a T.")
```
                        
- However, you'll notice that this can get pretty cumbersome pretty quickly. Thankfully, python offers another, more compact, way to write this:

```
nuc = "A"
if nuc == "A":
    print("Nucleotide is an A.")
elif nuc == "C":
    print("Nucleotide is a C.")
elif nuc == "G":
    print("Nucleotide is a G.")
elif nuc == "T"
    print("Nucleotide is a T.")
```
            
- The `elif` statements stand for `else...if` and capture what we tried to do above with the nesting.
- It is important to realize that as we've currently written these statements, nothing would happen if the variable `nuc` didn't have the value `A`, `C`, `G`, or `T`. This can be a big problem when accepting input from a user or file that might provide a nonsensical value. To capture these cases, it's always best to close with a simple `else`:

```
nuc = "A"
if nuc == "A":
    print("Nucleotide is an A.")
elif nuc == "C":
    print("Nucleotide is a C.")
elif nuc == "G":
    print("Nucleotide is a G.")
elif nuc == "T":
    print("Nucleotide is a T.")
else:
    print("This is not a valid nucleotide!")
```

```
Practice Exercise

Write a script that asks a user to enter a string. Use an if...elif...else statement to compare the string
to a series of keywords that you've defined. Print out a statement indicating whether the user's entry
matches any of the keywords or not. Do this in a Jupyter notebook.
```

## Lists

- We've now covered the simple variable types in Python: integers, floats, strings, and bools.
- However, there are several more complex types of variables that allow us to store and access multiple values.
- Perhaps the most versatile and common of these more complex types are lists.
- Lists are always specified using square brackets - `[]`
- Lists can contain an arbitrary number and type of simpler variables, but we often want to use only one type in a list so as not to get confused.
    - `listOfNums = [1,2,3,4]`
    - `listOfFloats = [3.14, 2.0, 12.3]`
    - `listOfStrings = ["Ecology", "Evolution", "Systematics"]`
    - `listOfBools = [True, False, False, True]`
- Even after they are created, lists can be modified. Individual elements can be added using the append method():
    - `listOfNums.append(5)` - Examine list after executing
    - `listOfStrings.append("Neurobiology")`
- Elements can be removed using a few different methods.
    - Try `listOfFloats.pop()` - What is returned? And what does the list look like now?
    - You can remove specific values from a list, regardless of their position, by using the `remove(<VALUE>)` method. What happens when you execute `listOfBools.remove(False)`? How does the list change?
- Lists can contain lists as elements. For instance, try this:
    - `newList = []`
    - `newList.append([1,2,3])`
    - `newList.append([4,5,6])`
    - `newList.append([12,13,14])`
- But you can also add all the _individual elements_ of one list to another. Try this:
    - `newList = [1,2,3]`
    - `newList.extend([4,5,6])`
    - `newList.extend([12,13,14])`
    - How does `newList` differ from what you got when you used `append()`?
- You can view or extract parts of a list by using indices and "slicing" the list (just remember that python starts counting at 0!)
    - `newList[4:7]` - What values are returned? How do these relate to the indices you provided?
- You can also extract every n-th element of a list using notation like this:
    - `newList[::2]` - What values are returned now?
    - `newList[2:8:2]` - How about now?
- You can also alter individual elements of lists by using indices
    - `newList`
    - `newList[2] = 100`
    - `newList`


## `for` loops
  
- One of the nicest things about Python is the relationship between lists and `for` loops
- If you have an existing list, you can quickly iterate across all of its elements using this syntax:

```
for num in newList:
    print("This number is: %d" % num)
```
            
- If you still want to iterate over a series of integers, you can use the range() function.

```
for num in range(10):
    print("This number is: %d" % num)
```

## A note about "copying objects"

- Try this:
    - `firstNum = 2`
    - `secondNum = firstNum`
    - `firstNum = 5`
    - `firstNum`
    - `secondNum`
- Now try this:
    - `firstList = [1,2,3]`
    - `secondList = firstList`
    - `firstList.extend([4,5,6])`
    - `firstList`
    - `secondList`


## Tuples

- Tuples are like lists, but they're not mutable (can't be changed)
- Tuples are instantiated using parentheses - `()`
- Try this:
    - `myTuple = (1,2,3)`
    - `myTuple`
    - `myTuple[1]`
    - `myTuple[1] = 5`


```
Practice Exercise - Generating the Reverse Complement of a DNA sequence

When looking for specific patterns in genome sequences, we often want to make
sure to search for the pattern on both strands. Because the 5'-3' orientation
runs in opposite directions on different strands, and nucleotides pair with
their complement (A-T and G-C), the 5'-3' sequence AGGC on one strand will
look like GCCT if sequenced on the other strand. Since we're generally not
sure which strand we've actually sequenced, we want to look for both of these
patterns. But this requires being able to translate any sequence of interest
into its reverse complement. There are two steps in this process, although
the order of these steps doesn't matter:

  - Reverse the sequence
  - Generate the complement of the sequence

Write a python script that accepts a sequence from the user and prints out
the reverse complement to the screen.
```



## Assignment - Week 8
```
See the Jupyter notebook called "Dispersal_assignment". Fill in the
missing code and answer the questions at the end. Complete this by
Friday, March 13th. Add your completed Jupyter notebook to the assignments
folder in your fork, and submit a pull request.
```

## References

- [Python Style Guide](https://www.python.org/dev/peps/pep-0008/)

