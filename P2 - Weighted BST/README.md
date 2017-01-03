Project 2

Objectives
The purpose of this project is to give you significant exposure to Binary Search Trees (BST), tree traversals, and recursive code.
Background
An arbitrary BST is seldom balanced. The left and right subtrees of a node may have different heights or contain different numbers of nodes, potentially leading to O( N ) performance for operations such as insert, find, and remove. There are several techniques for improving performance and insuring O( lg N ) performance by "balancing" the tree. Some of these will be discussed in class.
Description
In this project, you will explore balancing BST based on the weights of its subtrees. Here we define the weight of a BST to be the number of nodes in that tree. A node in a BST is weight-balanced if the weights of its left and right subtrees differ by no more than 1. A weight-balanced BST is a BST in which every node is weight-balanced. An important property of weight-balanced BST is that the value at any node, X, is a median of the values at all nodes in the subtree rooted at X.
How Your Program Works
Your program is invoked with two command line arguments. The first argument is the name of a file of integers (separated by whitespace) to read and insert into your BST. The second argument is the level to which your BSTs should be printed. Recall that the root is at level zero. For example

unix> ant run -Dargs="integers.dat 4"

Your program performs the following steps

    Read the integers found in the file specified on the command line and insert them into an initially empty BST, let's call it T, ignoring duplicates.
    Print the number of integers read from the file (including duplicates).
    Print the number of nodes in T, the height and median value of T and then print the contents of T in level-order up to the level specified on the command line.
    Weight-balance T according to the (admittedly inefficient) algorithm below.

    weightBalance tree T
       find the median of T
       create a new BST, T', with a single node (the root) whose value is the median of T
       retrieve and insert elements of all nodes of T except the median into T'. 
       replace T with T'           // T' has a weight-balanced root
       call this procedure to balance the left and right subtrees of T

    Print the number of nodes in the weight-balanced tree, the height and median of the weight-balance tree and the contents of the tree in level-order up to the level specified on the command line. 

Your Tasks

    Checkout the files from your project 2 repository. Your repository contains build.xml which will require editing, and p2questions.txt which contains questions about your project.
    Design and implement a BST tree class which supports the required operations for this project. 
    Write the code for main in a separate .java file.
    Test your code. Feel free to share your test data files on blackboard.
    Edit the questions file to add your answers.
    Commit build.xml, p2questions.txt and your .java files to your repository to submit your code. Please DO NOT commit any .class files or any files from your doc directory.

Project Requirements, Notes and Hints

    (R) Level-order printing
        If the tree's height is less than the specified number of levels to print, then print the entire tree.
        Tree nodes must be printed as ordered triples of values in the format ( x, y, z ), where x is the value found in the node's parent (print -1 for the root's parent), y is the value found in the node being printed and z is the weight of the tree rooted at that node.
        Your level-order tree print must start with a label on a new line for each level, and print 4 nodes per line if there are more than 4 nodes at a given level.
        The format for printing trees is shown in the sample output below.

    (N) A level-order traversal requires use of a queue. Elements in the queue should contain appropriate data to print the required information.
    (N) You are free to use any classes provided by the Java 6 API.
    (N) The median of a set of values is the value "in the middle". If there are an even number of values, then there are two values "in the middle". In this project you should use the smaller of the two as the median.
    (N) The algorithm given to weight-balance the tree is not the only possible algorithm, but we ask you to use this one so that your project output matches ours.

    (H) Test your code with small files first, using non-random data then move to larger, more complex files.
    (H) Some methods are better implemented as recursive functions, others as iterative functions. Choose your implementation carefully.
    (H) By convention and for ease of coding, define the height of an empty tree as -1.
    (H) Consider adding a new data member to each node which is the weight of the tree rooted at that node. The weight will make it easier to find the median and must be printed with each node. New nodes start with weight = 1. Nodes visited while finding the insertion point for a new node have their weight incremented if the integer being inserted is not a duplicate.
    (H) Use the weight in the tree nodes described above to help find the median value. The median may be found with either a recursive or iterative algorithm.
    (H) Use CVS as a repository to store your files between working sessions, not just as a means of submitting your code. Doing so can prevent you from accidently losing all of your work.
    Use the CVS utilities provided to verify that your code will compile and execute when the grading scripts are used.
    (H) Finding the median
    If the N values in the BST were stored in a sorted array the median would have the index "in the middle" of the array, or if you performed an in-order traversal of the BST, the median would be in the middle position of the output

    In that context, ask yourself these questions...
        What index is "in the middle" of any array of size N?
        How can you use the weight of the tree's root to determine the median's index/position?
        How can you use the weight(s) of the root's left and/or right child(ren) to determine the index/position of the root?
        How can you use the weight(s) of the root's left and/or right child(ren) to determine which subtree contains the median?
        How can you apply B, C, and D above to the appropriate subtree? 
    Finding the median can be performed recursively or iteratively.

SampleOutput
The following output is for format reference only.

unix> ant run -Dargs="integers.dat 4"

245 integers were read from integers.dat

Before balancing
    the tree contains 100 nodes
    the height is 12
    the median is 5436
Tree contents up to level 4
Level 0:
	(-1,5283,100)
Level 1:
	(5283,2086,46)	(5283,8027,53)
Level 2: 
	(2086,1067,17)	(2086,4646,28)	(8027,7673,28)	(8027,9552,24)
Level 3:
	(1067,400,7)	(1067,1287,9)	(4646,2150,19)	(4646,5226,8)
	(7673,5436,24)	(7673,7999,3)	(9552,9182,18)	(9552,9925,5)
Level 4:
	(400,1,2)	(400,666,4)	(1287,1197,1)	(1287,1803,7)
	(2150,2217,18)	(5226,4916,5)	(5226,5237,2)	(5436,5352,2)
	(5436,7565,21)	(7999,7829,2)	(9182,8727,15)	(9182,9336,2)
	(9925,9699,4)


After balancing
    the tree contains 100 nodes
    the height is 6
    the median is 5436

After balancing the level order output is: 

Level 0:
	(-1,5436,100)

Level 1:
	(5436,2794,49)	(5436,7999,50)
Level 2:
	(2794,1323,24)	(2794,4286,24)	(7999,6674,24)	(7999,8862,25)
Level 3:
	(1323,776,11)	(1323,2086,12)	(4286,3436,11)	(4286,5126,12)
	(6674,6049,11)	(6674,7118,12)	(8862,8420,12)	(8862,9518,12)
Level 4:
	(776,400,5)	(776,1197,5)	(2086,1743,5)	(2086,2465,6)
	(3436,2960,5)	(3436,3968,5)	(5126,4891,5)	(5126,5242,6)
	(6049,5692,5)	(6049,6235,5)	(7118,6883,5)	(7118,7568,6)
	(8420,8126,5)	(8420,8563,6)	(9518,9072,5)	(9518,9624,6)


