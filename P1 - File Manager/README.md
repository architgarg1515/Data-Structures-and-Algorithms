Project 1

Background
Lists are one of the fundamental abstract data types. This project will give you experience in using List operations, writing or modifying List code and using List iteratators in the context of a dynamic disk file allocation system.

Description
One of the fundamental tasks of every operating system is the management of the disk blocks used to store data in files. In this project you will implement a very rudimentary disk file manager. In our hypothetical operating system, the disk is divided into disk blocks. Each disk block is divided into bytes. The file manager is responsible for keeping track of unused (free) disk blocks and all necessary information about every file. The file manager supports the following operations for files

    Create a new file with a specified name and size in bytes
    Delete an existing file, freeing all disk blocks allocated to the file
    Extend an existing file by a specified size in bytes, allocating new disk blocks if necessary
    Shorten (truncate) an existing file by a specified size in bytes, freeing any disk blocks if possible

It is also possible to print all information about the state the file manager including information about each file.

You will implement the classes necessary to implement this project following acceptable OO design principles.

The number of disk blocks in our system and the number of bytes per disk block will be specified as command line arguments.
Tasks

    Use CVS to checkout your repository for this project. Your repository will contain a generic build.xml file that you must modify for this project.
    Implement a linked list class, list node class and list iterator class.
    No Java classes that implement the List interface (LinkedList, ArrayList, etc) may be used. 
    Implement a class that contains main( ) and its supporting methods.
    Implement the classes necessary to support the file manager's functionality.
    Create command file(s) to test your code. Feel free to post your command files and resulting output on blackboard to share with other students.
    Use CVS to commit all of your source files and your build.xml file. DO NOT commit your .class files.
    Use the course cvs utilities to verify that your project will be built and executed correctly by the project grading scripts. 

The Command Line
Your project will be invoked with a command line that consists of three arguments. The first argument specifies the number of disk blocks in our system. The second argument specifies the number of bytes in each disk block. The third argument will be the name of a file that contains a set of operations that must be performed to exercise the file manager. For example

 linux3> java Project1 -Dargs="20000 1024 /path/to/the/command/file"
 

The format of the command file is described in the command file section below.

The Command File
Commands in the file specify operations to be performed by the file manager. Each line in the file represents one command. Blank lines may appear anywhere in the file and should be ignored. Lines in which the first character is '#' are comments and should also be ignored. Invalid commands may appear in the file in which case you should ignore that line in the file and proceed to the next command. Otherwise, you can assume that any line containing a command is syntactically well-formed (e.g. all command arguments are present in the correct order and are of the correct type). We make this assumption so you don't have to spend lots of time making the command file parser bullet proof.

The command file format follows. Note that command names are in UPPERCASE, filenames will not contain spaces and all sizes will be positive.

    CREATE <filename> <size in bytes> — creates a new file with the specified name and size in bytes
    DELETE <filename> — deletes the specified file
    EXTEND <filename> <number of bytes> — increases the size of the file by the specified number of bytes.
    TRUNCATE <filename> <number of bytes> decreases the size of the file by "removing" the specified number of bytes from the end of the file. If the size of the file is zero after truncating, the file should be deleted.
    PRINT -- Prints the state of the file manager and all existing files
    The following information is required for PRINT
        The disk block size in bytes (from the command line)
        The total number of disk blocks (from the command line)
        The number of allocated blocks
        The number of free blocks
        The list of free blocks printed as ranges in sorted order by disk block number (see the sample output)
        All relevant information about each file in sorted order by filename
            Filename
            Actual size in bytes
            Allocated size in bytes
            Number of disk blocks allocated
            List of blocks allocated to the file as ranges in sorted order by disk block number

Sample Output
Sample output can be found here. The sample output was created by this command file.
Project Notes, Hints and Requirements
(R) List iterators must be used to traverse any list (outside of the list class itself).
(R) You must check the command line arguments to ensure that they are valid, e.g. that the command file can be opened and integers are positive. If the command line arguments are not valid, print an appropriate error message and exit.
(R) All commands and their arguments must be echoed to System.out along with a message indicating that the commnd completed successfully or with an appropriate, informative error message.
(R) All file managers errors must be handled with an appropriate exception. The file manager must detect at least the following errors:

    Insufficient disk space when an request to allocate disk blocks cannot be fulfilled because there are not enough free blocks. In this case the file is unchanged and no blocks are allocated.
    No such file whenever an attempt is made to extend, truncate, or delete a non-existing file.
    Duplicate file whenever an attempt is made to create a file that already exists.
    File Underflow whenever an attempt is made to truncate a file by more bytes than are in the file. In this case, the file should remain unchanged and no disk blocks are freed. 

(N) Disk block numbers are integers (starting at zero).
(R) Disk blocks must be assigned in order by disk block number from low to high.
(R) Note in the sample output that disk blocks must be printed as ranges even if there is only one disk block.
(R) Much of the output in this project is in sorted order, so using a sorted linked list is appropriate and therefore required.
