# Welcome to Lake Washington High School Computer Science Club #

This is largly an introduction to tooling and workflow.
If you are looking for more explanations, the internet is your friend. You should expect to become quite good at finding answers via the internet, as there are many useful resources. Of course, the Telegram group chat is also an excellent way to get help.

## C++ ##

+ [cplusplus.com tutorial](http://www.cplusplus.com/doc/tutorial/)
	
	I _strongly_ recommend following this tutorial including its installation instructions if you don't have any idea what you are doing. It will walk you through installing Visual Studio (which you probably want to do if you use Windows) and provides a tutorial to get you familar with the basics of C++. Notably their Visual Studio link is a bit old, go [here](https://www.visualstudio.com/)

+ [University of Washington C++ Resources from CS557](https://courses.cs.washington.edu/courses/cse557/15au/projects/c++resources.html)

+ [The C++ club standards](CXXSTD.md)

	I would hope that these get followed to an extent

If you find some other tutorials that are helpful, create a pull request that adds them to this document

### Introductory Project ###
It is recommended that you start off by trying to implement this project, and then show us the result. We will and can help you out.

*The Project:* Create a reverse polish notation calculator. This is not too difficult and should only support basic arithmetic
Read input lines off out of std input and write out the answer on a following line. Each number or operation should be seperated with a single space.
Example Input/Output:
```
	1 2 +  <-- the input
	3  <-- the answer
	2 3 4 + *
	14
	2 3 + 4 *
	20
```
As a hint: You may want to look into stacks, implemented for you in the <stack> std header
You can always look up std types on the internet, there is good documentation for them

#### Note on Installing Tools ####
If you aren't running Windows, your best bet is to just talk to me over Telegram. I'm expecting that if you do something out of the norm, you know what you are doing
If you want to get something set up on your school laptop (or don't want to install Studio), again, talk to me. You're going to be looking at [MSYS2](http://www.msys2.org/) or [Cygwin](http://cygwin.com/), both of which effectivly make your Windows machine look as much like Unix as possible. (The Windows Subsystem for Unix is another option but probably not on the school laptops)

## Git ##

___Git *is* *not* Github. Github is only one public hosting service and *does not* own Git___

[Git is a version control system](https://git-scm.com/) designed for the Linux kernel. It provides a varity of useful things:
+ The ability to see who changed what, when, and where
+ The ability to merge multiple people's changes into one source base

Using git is not terribly difficult if you ignore the insides. Visual Studio provides a GUI interface that is pretty easy to use and you may want to just stick with that. Basic operation is as follows for commands run at the shell:

+ To 'clone' or download a repository at a remote location

	`git clone <the remote location>`
	ex: `git clone https://github.com/lwhs-compsci/intro`

+ When you change files in your local copy, you will be able to observe the changes by running `git status`
+ Once you have completed part or all of what you had set out to do or want to upload your changes, add the files you wish to commit and  commit your changes:

	```
git add <a file that you want to commit that is changed>
<more git add commands to add the rest of the files. you can add entire directories with their pathes as well>
git commit -m '<include a useful message about this commit>'
	```
+ You can run `git status` before commiting but after adding files to see the intermediate status
+ Try to not commit files that are unnecessary, esp temp files and your `build/` directory. The .gitignore file provides a filter that should catch most things, and if it doesn't please add those file types. This means that if you add an entire directory, git will still filter out stuff that matches in .gitignore
+ There is also a `git rm` command to remove files, notably with the option `--cached` to take a file out of a commit
+ You can push your changes to a remote repository with `git push` and pull new changes from the server into a existing repository with `git pull`

	These can be tricky, but you can always message me and will be able to help you

+ Other good resources:
	
	+ [The Offical Git Tutorial](https://git-scm.com/docs/gittutorial)
	+ [Github's Tutorial - Interactive Walkthrough](https://try.github.io/levels/1/challenges/1)

Using GitHub has a few more additional steps, but they are for an additional document and also vary depending on how we want to develop our projects. It would be a good idea to sign up for GitHub if you haven't already, and message us your username so that we can add you to the LWHS Comp Sci Organization on GitHub. See the [Contribution](CONTRIB.md) for information on how exactly this process would work.

## CMake ##

_You will need to install CMake aside from the other stuff you've installed_
You can get CMake from [here](https://cmake.org/) 

CMake is a tool that allows for the creation of build files for multiple platforms. This allows us to compile our code on many different platforms. It should stay pretty out of the way.
+ Run cmake from the shell, inside of a new directory like build/ (this is known as an out-of-source build, and makes sure your source directories stay clean and free of the intermediaries generated)

	```
	# The first time you clone the repo
	mkdir build/
	cd build/
	cmake ..
	# open whatever build files you end up with 
	```
	For instance, if you are using Visual Studio, running CMake will result in a solution file that you can open inside `build/` and then use like a normal Visual Studio solution. If you're on Linux and using Make, it will generate a makefile and you can then just run `make` in `build/` 

+ If you change the project in some way like adding or removing files or change the CMakeLists.txt file, you need to rerun CMake. Some tools like VS and make will do this for you sometimes, but you can't always rely on it. You just need to run `cmake` from your `build/` directory like the first time, and CMake will update the build files found within.

#### A more detailed explanation of the actual compilation process ####

C++ is a compiled language. This means that a program called the compiler transforms your source code into a final executable containing machine code that can be run many times. The basic process is that the compiler takes your source code files (files ending in .cpp usually) and compiles them into something called an object files (.o or .obj). Object files are a intermediary and basically contain the actual machine code for that source file. Another program called the linker then takes these object files and links them together into the final executable (on Windows: .exe). This steps are of course automated (truly one virtue of programmers is their lazyness) using the tools introduced in intro/setup.md and friends. They are, of course, somewhat system dependent.

Due to the somewhat old nature of C++, there is one more twist to how your source code files become an executable. Some code, notably definitions, are sometimes placed in files called headers (.h) which can then be included into multiple source files. This allows you to share the definitions between multiple source files. These files are spliced together via the preprocessor, which runs before the source code is actually compiled. To include a file, you use the `#include` preprocessor command. There are a varity of useful standard headers avaliable as well as the headers for the project that are also in the include path.

CMake takes care of making sure all of this stuff happens and so we don't have to worry about it.
