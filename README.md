# scrawl-editor
INTRODUCTION TO xv6
 
The job of an operating system is to share a computer among multiple programs and to provide a more useful set of services than what the hardware alone supports. The operating system manages the low-level hardware, so that, for example, a word processor need not concern itself with which video card is being used. It also multiplexes the hardware, allowing many programs to share the computer and run (or appear to run) at the same time. Finally, operating systems provide controlled ways for programs to interact, so that they can share data or work together.
 
The operating system, xv6, provides the basic interfaces introduced by Ken Thompson and Dennis Ritchie’s Unix operating system, as well as mimicking Unix’s internal design.  
 
The latest xv6 source is available via:
git clone git://github.com/mit-pdos/xv6-public.git
 
Nowadays xv6 can be run using the open-source emulator qemu.
 
User programs can be added to xv6 by adding the source code into its directory and modifying its MakeFile.
 
It has originally 21 system calls, it also allows the addition of user defined system calls.
 
It supports a pre-emptive process scheduler. Round robin scheduling has been implemented in xv6
 
 
 
INTRODUCTION TO SCRAWL
 
 
Xv6 is an educational operating system with very basic functionalities. One of the major requirements of any operating system is a text editor and we found that it doesn’t have one!!
So, we have developed an editor to be integrated into xv6.
 
Scrawl is a sophisticated text editor that can be integrated to xv6. It was developed using C making sure it’s compatible with xv6.
 
Our text editor can be used to create programs from within the operating system itself as it has syntax highlighting feature based on the language used.
 
Using Scrawl, all file formats supported by xv6 can be created or modified within the system itself.
 
With Scrawl present in xv6 the user need not look for other sources to open, edit and create.
 
It is a very sophisticated text editor involving many advanced features such as searching based on keywords, syntax highlighting and fluid cursor movements.
 
It also provides facilities like save, save as, quit without saving and so on and indicates if any changes are made after saving.
 
Scrawl also gives us a live statistic on the file in use which enables the user to keep track of his/her whereabouts in the file.
 
 
MAJOR FEATURES OF SCRAWL
 
It’s not your average editor:
 
​​Scrawl has extremely fluid cursor movements. HOME can be used to travel to the start of a line. Scrawl also recognizes page Up, page Down and all our arrow keys can be used. It also has functionalities of a regular editor such as the usage of the return key for a new line, delete key to delete a character, etc.
 
Search:
 
​Scrawl provides the user with functionality to search for the occurrence of a particular string throughout the file. The found string is highlighted in a different colour for easier recognition.
 
Syntax highlighting:
 
​​Based on the type of file scrawl highlights the contents of a file to improve user readability. This improves the efficiency of the work done by the user to a great extent.
 
Smart Save:
 
​​Scrawl provides the functionality to save a user file permanently so that the work done by the user is not lost. Even if the user initiates the quit sequence Scrawl smartly checks whether the file has been saved or not. If it has not been saved then the user must press quit thrice in order to make sure that quitting without saving a file was not an accident. 
 
 
 
IMPLEMENTATION OF SCRAWL
 
 
Raw mode:
 
By default, your terminal starts in canonical mode, also called cooked mode. In this mode, keyboard input is only sent to your program when the user presses Enter. This is useful for many programs: it lets the user type in a line of text, use Backspace to fix errors until they get their input exactly the way they want it, and finally press Enter to send it to the program. But it does not work well for programs with more complex user interfaces, like text editors. We want to process each keypress as it comes in, so we can respond to it immediately.
 
What we want is raw mode. Unfortunately, there is no simple switch you can flip to set the terminal to raw mode. Raw mode is achieved by turning off a great many flags in the terminal.
This process can be clearly understood from the source code.
 
Raw input and output:
 
In this module, we obtain our input. To do so we first disable all our regular terminal control statements and create our own control statements such ctrl-q to quit. Here we define a ctrl function to define the escape sequence. For each additional character output to the screen the entire terminal is cleared and rendered. The clearing is done using a escape sequence. This can better understood from the source code.
 
 
 
Text viewer and editor:
 
This is an extremely important module, as it determines the size of the terminal which in turn facilitates the cursor movements by giving it certain bounds. Here the arrow keys are mapped for their escape sequence so that it can also be used for cursor control. Both page up and down have been mapped along with the usual home, delete and the backspace. This also involves displaying the file statistics such as the total number of lines used, the current line and also the file name.
 
Search:
 
This module facilitates the user to find any string present in their file contents. This mode can be accessed using the command ctrl-f where the user will be prompted to enter the string to be found in their file. The found string is highlighted in a different colour to facilitate better readability.
 
Syntax highlighting:
 
In this module, based on the type of file, Scrawl highlights the contents of a file to improve user readability. This improves the efficiency of the work done by the user to a great extent. With the appropriate highlighting, if the file is a user program then this greatly helps in debugging.
 
