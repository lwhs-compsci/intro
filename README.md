# Welcome to Lake Washington High School Computer Science Club #

## Introduction to tooling (Git, C++, CMake) ##

If you are looking for more explanations, the internet is your friend. You should expect to become quite good at finding answers via the internet, as there are many useful resources.

## Git ##

____Git *is* *not* Github nor vis versa. Github is only one public hosting service and *does not* own Git___

Git is a version control system designed for the Linux kernel. It provides a varity of useful things:
+ The ability to see who changed what, when, and where
+ The ability to merge multiple people's changes into one source base

Using git is not terribly difficult if you ignore the insides. Visual Studio provides a GUI interface that is pretty easy to use. Basic operation is as follows for commands run at the shell:

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
+ There is also a `git rm` command to remove files, notably with the option `--cached` to take a file out of a commit
+ You can push your changes to a remote repository with `git push` and pull new changes from the server into a existing repository with `git pull`

	These can be tricky, but you can always message me and will be able to help you

+ Other good resources:
	
	+ [The Offical Git Tutorial](https://git-scm.com/docs/gittutorial)
	+ [Github's Tutorial - Interactive Walkthrough](https://try.github.io/levels/1/challenges/1)

## CMake ##

CMake is a tool that allows for the creation of build files for multiple platforms. This allows us to compile our code on many different platforms. It should stay pretty out of the way.

+ Run cmake from the shell, inside of a new directory like build/

	```
	# The first time you clone the repo
	mkdir build/
	cd build/
	cmake ..
	```


## C++ ##

+ [cplusplus.com tutorial](http://www.cplusplus.com/doc/tutorial/)
	
	I _strongly_ recommend following this tutorial including its installation instructions if you don't have any idea what you are doing

+ [University of Washington C++ Resources from CS557](https://courses.cs.washington.edu/courses/cse557/15au/projects/c++resources.html)

If you find some other tutorials that are helpful, create a pull request that adds them to this document

### A more detailed explanation of the actual compilation process ###

C++ is a compiled language. This means that a program called the compiler transforms your source code into a final executable containing machine code that can be run many times. The basic process is that the compiler takes your source code files (files ending in .cpp usually) and compiles them into something called an object files (.o or .obj). Object files are a intermediary and basically contain the actual machine code for that source file. Another program called the linker then takes these object files and links them together into the final executable (on Windows: .exe). This steps are of course automated (truly one virtue of programmers is their lazyness) using the tools introduced in intro/setup.md and friends. They are, of course, somewhat system dependent.

Due to the somewhat old nature of C++, there is one more twist to how your source code files become an executable. Some code, notably definitions, are sometimes placed in files called headers (.h) which can then be included into multiple source files. This allows you to share the definitions between multiple source files. These files are spliced together via the preprocessor, which runs before the source code is actually compiled. To include a file, you use the `#include` preprocessor command. There are a varity of useful standard headers avaliable as well as the headers for the project that are also in the include path.

