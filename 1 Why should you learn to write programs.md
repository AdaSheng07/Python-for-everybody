## 1 Why should you learn to write programs

### Computer Hardware Architecture

**Central Processing Unit (CPU)**: the part of the computer constantly asking "what's next?" Have to know how to talk fast to keep up with the CPU. 

**Main Memory**: used to store information that the CPU needs in a hurry. It is nearly as fast as the CPU. But the information stored in the main memory vanishes when the computer is turned off. 

**Secondary Memory**: used to store information, but it is much slower than the main memory. It can store information even when there is no power to the computer. e.g. disk drives or flash memory. 

**Input and Output Devices**: screen, keyboard, mouse, microphone, speaker, touchpad, etc.

**Network Connection**: retrieve information over a network. Think of the network as a very slow place to store and retrieve data that might not always be "up". The network is a slower and at times unreliable form of Secondary Memory. 

**Program**: stored instructions

**Programming**: the act of writing instructions down and getting the instructions to be correct

-------

### Two skills to be a programmer

* Need to know the programming language (Python) - the vocabulary and the grammar, spell the words in this new language properly and know how to construct well-former "sentences" in this new language. 
* Need to "tell a story" - combine words and sentences to convey an idea to the reader. In programming, the program is the "story" and the problem you're trying to solve is the "idea". 

Different programming languages have very different vocabulary and grammar but the problem-solving skills will be the same across all programming languages. 

Start with reading and explaining programs, then write simple programs, and then write increasingly complex programs over time. At some point you'll see the patterns on your own and can see more naturally how to take a problem and write a program that solves that problem. 

-------

"Reserved words" in Python (with special meaning, can't be used as variable names) :

```
and      del      global    not    with
as       elif     if        or     yield 
assert   else     import    pass   
break    except   in        raise 
class    finally  is        return 
continue for      lambda    try 
def      from     nonlocal  while
```

In a sense, when you use a program written by someone else, the conversation is between you and those programmers with Python acting as an intermediary. Python is a way for the creators of programs to express how the conversation is supposed to proceed. 

-------

**Terminology**: Interpreters and Compliers

Python is a high-level language intended to be relatively straightforward for humans to read and write and for computers to read and process. 

Other high-level languages: Java, C++, PHP, Ruby, Basic, Perl, JavaScript, etc. 

The CPU understands none of them. 

The CPU understands a language called machine language. It has a very complex syntax and is far more intricate than Python. That's why translators are built to allow programmers to write in high-level languages and these translators convert the programs to machine language for actual execution by the CPU. Programs written in high-level languages can be moved between different computers by using a different interpreter on the new machine or recompiling the code to create a machine language version of the program for the new machine. 

Programming language translators fall into two general categories: 
1) interpreters
2) compliers

**Interpreter**: read the source code of the program as written by the programmer, parse the source code, and interprets the instructions on the fly. Python is an interpreter. When running Python interactively, type a line of Python (a sentence) and Python processes it immediately and is ready for us to type another line of Python. 

**Variable** is the term we use to refer to the labels we use to refer to this stored data. 
```
>>> x = 6
>>> print(x)
6
>>> y = x * 6
>>> print(y)
36
```
We verify that Python has actually remembered the value using print, then we ask Python to retrieve `x` and multiply it by six and put the newly computed value in `y`. Then we ask Python to print out the value currently in `y`. 

Even though we are using terminals and typing these commands into Python one line at a time, Python is treating them as an ordered sequence of statements with later statements able to retrieve data created in earlier statements. 

It is the nature of an interpreter to be able to have an interactive conversation. 

A **compiler**, however, needs to be handed the entire program in a file, and then it runs a process to translate the high-level source code into machine language and then the complier puts the resulting machine language into a file for later execution. 

In a Windows system, executable machine language programs have a suffix of ".exe" or ".dll" which stated for "executable" and "dynamic line library" respectively. In Linux and Macintosh, there is no suffix that uniquely marks a file as executable. 

The text is totally unreadable if you open an executable file in a text editor, because it is never easy to read or write in machine language. That's why we need interpreter and complier that allow us to write in high-level languages like Python and C. 

The Python interpreter is written in a high-level language called "C". So Python is a program itself and it is compiled into machine code. When you installed Python on your computer (or the vendor installed it), you copied a machine-code copy of the translated Python program onto your system. 

-------

Typing commands into the Python interpreter is a great way to experiment with Python's features, but it is not recommended for solving more complex problems. 

Use a text editor to write the Python instructions into a file, which is called a **script**. Python scripts have names that end with .py. 

To execute the script, you have to tell the Python interpreter the name of the file. In a command window, you should type as follows:
```
$ cat hello.py 
print('Hello world!') 

$ python hello.py 
Hello world!
```
-------

**Program**: at its most basic, it is a sequence of Python statements that have been crafted to do something. It might be easiest to understand what a problem is by thinking about a problem that a program might be built to solve, and then looking at a program that would solve that problem. 

**Example**: how to count the most frequently used words?

It would be quicker to learn Python and write a Python program to count the words than manually scan the words. 

```Python
name = input('Enter file:') 
handle = open(name, 'r') 
counts = dict() 

for line in handle: 
    words = line.split() 
    for word in words: 
        counts[word] = counts.get(word, 0) + 1 

bigcount = None 
bigword = None 
for word, count in list(counts.items()): 
    if bigcount is None or count > bigcount: 
        bigword = word 
        bigcount = count 

print(bigword, bigcount) 

# Code: http://www.py4e.com/code3/words.py
```

-------

### The Building Blocks of Programs

Low-level conceptual patterns to construct programs (not just for Python, but are part of every programming language): 

**input** Get data from the "outside world". This might be reading data from a file, or even some kind of sensor like a microphone or GPS. In our initial programs, our input will come from the user typing data on the keyboard. 

**output** Display the results of the program on a screen or store them in a file or perhaps write them to a device like a speaker to play music or speak text. 

**sequential** execution Perform statements one after another in the order they are encountered in the script. 

**conditional** execution Check for certain conditions and then execute or skip a sequence of statements. 

**repeated execution** Perform some set of statements repeatedly, usually with some variation. 

**reuse** Write a set of instructions once and give them a name and then reuse those instructions as needed throughout your program. 

-------

### Common Types of Error

Communicate very precisely when writing Python code, the smallest deviation or mistake will case Python to give up looking at your program. 

**Syntax errors** 

The first errors you will make and the easiest to fix. It is saying that you have violated the "grammar" rules of Python. Python tries its best to point right at the line and character where it noticed it was confused. Something tricky might happen that the mistake that needs fixing is earlier in the program than where Python noticed it was confused. So, the line and character that Python indicates in a syntax error may be a starting point for you to look for. 

**Logic errors** 

It is when your program has good syntax but there is a mistake in the order of the statements or perhaps a mistake in how the statements relate to one another. e.g. "take a drink from your water bottle, put it in your backpack, walk to the library, and then put the top back on the bottle. "

**Semantic errors** 

It is when your description of the steps to take is syntactically perfect and in the right order, but there is simply a mistake in the program. The program is perfectly correct but it does not do what you intended for it to do. 

-------

### Debugging - the hunt for the cause of the error

When debugging a program, and especially if you are working on a hard bug, there are four things to try: 

**reading** Examine your code, read it back to yourself, and check that it says what you meant to say. 

**running** Experiment by making changes and running different versions. Often if you display the right thing at the right place in the program, the problem becomes obvious, but sometimes you have to spend some time to build scaffolding. 

**ruminating** Take some time to think! What kind of error is it: syntax, runtime, semantic? What information you can get from the error messages, or from the output of the program? What did you change last, before the problem appeared? 

**retreating** At some point, the best thing to do is back off, undoing recent changes, until you get back to a program that works and that you understand. Then you can start rebuilding. 

**Reading your code** - if the problem is a typographical error, but not if the problem is a conceptual misunderstanding. Read your code unless you don't understand what your code is doing. 

**Running experiments** - it helps especially if you run small, simple tests. Run the code without reading might lead you to a pattern called "random walk programming", which is the process of making random changes until the program does the right thing and takes a long time. 

**Take time to think** - debugging is like an experimental science. Have at least one hypothesis about what the problem is. if there are two or more possibilities, try to think of a test that would eliminate one of them. 

**Take a break** - it helps with the thinking and talking. Explain the problem to someone else (or even to yourself). 

The methods above might not work as well if there are too many errors, or the code to fix is too big and complicated. Then the best way to deal with it is to retreat, simplify the program until you get to something that works and that you understand. 

Don't hesitate to delete a line of code when you have to. Save a copy of your original code and then make the changes if it makes you feel better. 

-------

### Glossary

**bug** - an error in a program

**central processing unit** - the heart of any computer; runs the software that we write; also called "CPU" or "the processor"

**compile** - to translate a program written in a high-level language into a low-level language all at once, in preparation for later execution

**high-level language** - a programming language like Python that is designed to be easy for humans to read and write

**interactive mode** - a way go using the Python interpreter by tying commands and expressions at the prompt

**interpret** - to execute a program in a high-level language by translating it one line at a time

**low-level language** - a programming language that is designed to be easy for a computer to execute; also called "machine code" or "assembly language"

**machine code** - the lowest-level language for software; the language that is directly executed by the central processing unit (CPU)

**main memory** - stores programs and data; main memory loses its information when the power is turned off

**parse** - to examine a program and analyze the syntactic structure

**portability** - a property of a program that can run on more than one kind of computer

**print function** - an instruction that causes the Python interpreter to display a value on the screen

**problem solving** - the process of formulating a problem, finding a solution, and expressing the solution

**program** - a set of instructions that specifies a computation

**prompt** - when a program displays a message and pauses for the user to type some input to the program

**secondary memory** - stores programs and data and retains its information even when the power is turned off; generally slower than main memory; e.g. disk drives and flash memory in USB sticks

**semantics** - the meaning of a program

**semantic error** - an error in a program that makes it do something other than what the programmer intended

**source code** - a program in a high-level language

-------

### Exercises

![image](https://user-images.githubusercontent.com/86143164/123505232-7f0b1700-d690-11eb-8118-66e6bf4a2414.png)

c d


![image](https://user-images.githubusercontent.com/86143164/123505239-8af6d900-d690-11eb-9a9a-2f76665a2aa5.png)

Program is a set of instructions that specifies a computation. 

A complier translate high-level language into low-level language all at once in preparation for later execution, while interpreter is executing a program in a high-level language by translating it one line at a time. 


![image](https://user-images.githubusercontent.com/86143164/123505247-9518d780-d690-11eb-97b2-b77463369a28.png)

a


![image](https://user-images.githubusercontent.com/86143164/123505258-a06c0300-d690-11eb-8803-a782ea1b2b91.png)

b


![image](https://user-images.githubusercontent.com/86143164/123505265-a95cd480-d690-11eb-9096-efabb5c7d5f9.png)

b






