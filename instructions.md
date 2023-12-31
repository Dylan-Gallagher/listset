This is part 1 of a two-part lab on linked lists and hash tables.

Linked lists are a versatile way of storing collections of data. In this lab we will write an abstract data type (ADT) to represent sets of strings
using linked lists. Note that the purpose of this lab is to learn to write (and especially debug) linked lists, so you should write the
linked list code yourself.

All the files you need are in the attachment to this lab spec, listset.zip. Download this file, transfer it to the Linux machine where you are doing lab work and unzip it. You can compile the C files contained within with one of:

clang -o listset listset.c listset-main.c

gcc -o listset listset.c listset-main.c

The basic declarations of the linked list set are:

// a linked list node containing a string
struct listnode {
  char * str;
  struct listnode * next;
};

// a linked list data structure
struct listset {
  struct listnode * head;
};

Your list set should support the following operations:

`
// create a new, empty linked list set
struct listset * listset_new();

/* check to see if an item is in the set
   returns 1 if in the set, 0 if not */
int listset_lookup(struct listset * this, char * item);

// add an item, with number 'item' to the set
// has no effect if the item is already in the set.
// New items that are not already in the set should
// be added to the start of the list
void listset_add(struct listset * this, char * item);

// remove an item with number 'item' from the set
void listset_remove(struct listset * this, char * item);

// place the union of src1 and src2 into dest
void listset_union(struct listset * dest, struct listset * src1,
                  struct listset * src2);

// place the intersection of src1 and src2 into dest
void listset_intersect(struct listset * dest, struct listset * src1,
                  struct listset * src2);

// return the number of items in the listset
int listset_cardinality(struct listset * this);

// print the elements of the list set
void listset_print(struct listset * this);
`

The zip file for this lab contains a small C program that tests your abstract data type. The program takes command line parameters as input.
The command line parameters are in pairs, with a command followed by a string. Where a "+" appears as a command line parameter, the string in the next command line parameter should be added to your list set. Where a "-" appears, the following string should be removed from your list set. Finally, where a "="
appears, your program should write out the full contents of your listset.

Thus, at the command line you might write:
./listset + knife + spoon + fork + no - knife + is + there - fork =

The output might be:

there is no spoon

