# Python - Part 2

## Jupyter Notebooks

- Jupyter notebooks are a special type of file that allows formatted notes to be mixed with Python code.
- These notebooks can be run on SuperMike through OnDemand.
- To open a Jupyter notebook, go to the "Interactive Apps" menu at the top and select "Jupyter Notebook".
- A form will be displayed that asks for some information. For now, please use these options:
    - Account: "hpc_icbio01"
    - Queue: "single"
    - Number of hours: 1
    - Number of nodes: 1
    - Bc Num Cores: 1
- Note that these options will "charge" the account that I've set up for this class (hpc_icbio01). For the purposes of this class, there will never be a need to change the numer of nodes to more than 1. You may later need to increase the number of hours, but please only ask for as many hours as you will be actively working at a time. If you open a notebook during the time you've requested, you won't need to re-enter any of this information. If the time has expired, you will need to make another request for time.
- If you've cloned this week's repository in your HPC account, it includes a file called "ExampleJupyterNotebook.ipynb" that you can open once you've started a Jupyter Notebook Server.
- [OPTIONAL] If you end up wanting to work with Jupyter notebooks on your own computer, you can install it locally. Probably the most popular way to run Jupyter notebooks locally is by installing Anaconda (https://www.anaconda.com).

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
