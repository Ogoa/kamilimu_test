# A Guide To Writing Proper Commit Messages
They say a `git diff` will tell you WHAT happened but only a good `commit` message will tell you why.

Commit messages provide context into what changes were made to one or more files and why.

## Why should you be bothered?
Writing good commits is crucial to preserving context. If you made a change 3 months ago for example, it may be difficult for the person reviewing that change to understand exactly what it was for. Moreover, when working on group projects or contributing to open source, there are conventions that are crucial for uniformity.

Take these two repositories when you run the `git log --oneline -4` command for example:

```
$ git log --oneline -4

a9e34a1 I have added a Submit button to the bottom of the login screen that will enable the user to login into their account using their credentials
2c10b35 Changed the background colour of my website's home page
23e3d4d More changes
9a0b12e Initial commit
```

Compare that to this:

```
$ gitlog --oneline -4

a9b123c Add a submit button to home page
f32a7c5 Change background colour of home page
d89c2a3 Add a navigation rail at the home page
b45a8c9 Create a readme for the parent directory
```

Which of the two log would you rather read?


You should therefore be very keen on mastering the art of writing a good commit message.

## What are these conventions/rules?
There are seven main rules that guide writing a good commit message:
- Limit the subject line to 50 characters
- Capitalise the subject line
- Do not end the subject line with a period
- Separate the subject from the body with a blank line
- Use the imperative mood in the subject line
- Use the body to explain the changes made
- Wrap the body at 72 characters

I will go through each of them and hopefully you will get better insight.


### 1. Limit the subject line to 50 characters
The subject line usually forms the title of the commit. It provides a high-level context of the changes made in a particular commit and they are what you see when you use the command `git log --oneline` as shown above.

Github conventions dictate that you make them as short as 50 characters. Yes, summarising all you changes using roughly 7 seven words can prove a daunting task. If you are struggling to narrow all changes made to just 50 characters, it may mean that you are grouping too many changes together. It may be wise to break the commit down to its `atomic` components.

You can add this subject in two ways.

```
# Using the '-m' flag
$ git commit -m "Change background colour of home page"

# Using the text editor
$ git commit
```

I would recommend using the text editor since it guides you when you cross the 50character limit by changing the colour of the text. It also allows you to type in the body of your commit message.


### 2. Capitalise the subject line
As shown in the examples above, it is good practice to always start your subject with a capital letter.

```
# Do this
Change background colour of home page

# Do not do this
~~change background colour of home page~~
```

### 3. Do not end the subject line with a period
`NEVER` punctuate your subject with a full stop.
```
# Do this
Change background color of home page

# Do not do this
~~Change background colour of home page.~~
```

### 4. Use the imperative mood in the subject line
More often than not, we write things in indicative mood like you are reporting something that has happened. This is an example: `Added background colour to the home page`.

You should always write your subject in an imperative mood; like you are giving out an instruction. This is an example: `Correct deletion of linked list node`.

A tip to always remembering this is asking yourself the question `I am making this change to...` or `If I apply this change it will...`

```
If I apply this change it will Fix the deletion of a linked list node
If I apply this change it will Change the background colour of home page

# Note that this does not work when you use the indicative mode:
If I apply this change it will ~~Changed the colour of the login button~~
```

Git itself uses the imperative when creating a commit on your behalf.

### 5. Use the body to explain the changes made
The body of your commit should explain the `WHY` and `HOW` of your changes.

To put this into context, say you were working on adding a method to a `Node` class that appends a node to the linked list. This is what a proper commit would look like:

```
Correct method to append a node to linked list

Previously, the method used a temporary pointer that would change to NULL after traversing the linked list and reaching its tail. This would result in a segmentation fault when trying to add the new node. The condition to stop traversing was therefore changed from 'while(current_node != NULL)' to 'while(current_node->next != NULL)'
```

You can see that this clearly explains the changes made and answers the questions `How did it change?` as well as `Why did it change?`.


### 6. Separate the subject from the body with a blank line
As shown in rule no. 5, you should always separate the two components with a blank line. This is very useful in some git operations such as `git log --oneline`, `git shortlog` etc.

```
$ git log
commit ...
Author: Hansel
Date: Thu May...

This is the subject of the commit

This is the body of the commit separated from the subject by a blank line...
```


### 7. Wrap the body at 72 characters
Ideally, the body of your commit message should not exceed 72 characters. This, however, can be relaxed (at least that's how I view it :)).


## Conclusion
Your git commit messages are not just a mere formality. They provide context to whoever may be reviewing you work in the future - that may as well be your future self - so strive to always do it correctly.

Happy commiting!!
