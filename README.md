# NSSA-220
Collection of useful commands and concepts for NSSA 220 - Task Automation Using Interpretive Languages.

# Commands
## The Basics
### (Man)ual Pages
`man <command of interest>. `

The manual (man)pages are your friend. Use them early and often!

### cp (Copy) – How to copy files/directories
`cp [options] <source> <destination`

The most common option for `cp` is `-r`, which will recursively copy the contents of a directory.

### mv (Move) – Move/rename files/directories
`mv [options] <source> <destination`

The move command is similar to `cp` except that it’s strictly used to “move” files or directories from source to destination. A major advantage of using mv is that you don’t need to use a `-r` option to recursively copy the contents of a directory.

## Permissions, Wildcards, and Filters
### chmod - Change permissions
`chmod [permissions] [path]`

The owner of a file or directory may change the permissions of that file or directory at any time. In terms of security, it’s best to give as few permissions as is reasonably possible, while still allowing the users of the file system to accomplish their work.

| r | w | x | Decimal Value |
|---|---|---|:-------------:|
| 0 | 0 | 0 | 0             |
| 0 | 0 | 1 | 1             |
| 0 | 1 | 0 | 2             |
| 0 | 1 | 1 | 3             |
| 1 | 0 | 0 | 4             |
| 1 | 0 | 1 | 5             |
| 1 | 1 | 0 | 6             |
| 1 | 1 | 1 | 7             |

# Concepts
## File Permissions
Recall that Linux file permissions consist of 9 characters, which are broken into three distinct sets. The characters within each set of file permissions in Linux indicate whatmay be done with a file. 

The possibilities are as follows:
  * **r** (read) – the contents of the file are visible.
  * **w** (write) – the contents of the file may be modified .
  * **x** (execute) –the file may be executed, assuming the file is a script or executable.

Each of the three sets of characters (rwx) indicate who may perform any of the above actions. There are three types of users that are considered:
* **owner** – the user that “owns” the file. Often, this is who created the file, but not always. 
* **group** – a defined collection of at least one user. By default, the owner and group are the same. An example of a group could be something called “users” that consistsof all non-root users ora group of similar users, such as users from the same department or team within an organization.
* **all others** -any user that is not the owner or not part of a group.
## Wildcards
Wildcards allow us to generate a pattern that can referenceseveral files or directories at once. 

Here is a set of wild cards that we’ll begin with:
* **&ast;** - represents zero or more characters.
* **?** – represents to a single character.
* **[]** – represents a range of character.
