# NSSA-220
Collection of useful commands and concepts for NSSA 220 - Task Automation Using Interpretive Languages.

# Commands
## The Basics
### (Man)ual Pages
`man <command of interest> `

The manual (man) pages are your friend. Use them early and often!

### cp (Copy) – how to copy files/directories
`cp [options] <source> <destination>`

The most common option for `cp` is `-r`, which will recursively copy the contents of a directory.

### mv (Move) – move/rename files/directories
`mv [options] <source> <destination>`

The move command is similar to `cp` except that it’s strictly used to “move” files or directories from source to destination. A major advantage of using mv is that you don’t need to use a `-r` option to recursively copy the contents of a directory.

## Permissions
### chmod - change permissions
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

## Filters
Filters are a way to take data stored in a human readable text file or output from a program/other command, and manipulate it. There’s a large number of filters in Linux that are usually used in tandem.

### head – display the first few lines of a file
`head [-number of lines] [file]`

The `head` command prints some number of lines from a file to the console. By default, this number is 10.

### tail – display the last few lines of a file
`tail [-number of lines] [file]`

The `tail` command operates exactly the same way as `head`, except that it starts from the end of the file and works its way upwards.

One extremely useful option in the `tail` command is `-f`. The `-f` option allows you to “follow” the file. This comes in handy if a program produces an output file that grows over time, such as a packet capture or an analysis program that generates solutions to a problem every so often.

### nl – number lines in a files
`nl [-options] [file]`

 The `nl` command provides line numbers to every line in a file without modifying the contents of a file.
 
### cut – remove fields from a well formatted file
`cut [-options] [file]`

The `cut` command separates well formatted data into fields and returns only the fields of interest.

The `-f` option allows us to specify which fields are of interest to us (seperated by commas). So that `cut` knows how the data is formatted, specify the delimiter in quotes in conjunction with `-d`.

### sed (Stream Editor) – search and replace on data
`sed <expression> [file]`

The stream editor, `sed`, is an extremely expressive and powerful program. The format may appear simple, but this program offers seemingly unlimited possibilities. 

The expression argument is required and has the following format: `s/search/replace/g`.

### awk - pattern scanning and processing language
`awk <search pattern> [file]`

The `awk` program is a much more powerful version of `cut` that has a huge number of options and capabilities.

Fields are indicated by `$`, and actions to perform are surrounded in `{}`.

### sort – arrange lines of a file alphabetically 
`sort [-options] [file]`

Often times, you’ll want to sort data by things like a timestamp, item number, or last name. This can be easily accomplished using the `sort` command.

Use the `-k` option to sort on a certain column.

### uniq – remove duplicate lines
`uniq [options] [file]`

The `uniq` command will remove duplicate lines from a file, but only if the duplicates are right next to each other in the file.

## Searching
Linux has a very powerful search command known as `grep` that lets us search the contents of one or more files for certain data contained there in.

### egrep - extended regex version of grep
`egrep [command line options] <pattern> [path]`

A couple other useful options are `-n` (show the line number along with the string matchedline) and `-c` (display how many lines in the file that the string match appears).

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

## Regex
A regular expression, regex or regexp is a sequence of characters that define a search pattern. Usually this pattern is used by string searching algorithms for "find" or "find and replace" operations on strings, or for input validation.

Here is a fairly comprehensive set of regex that you should be aware of (yes, there are others):
* **.** (dot) – a single character
* **?** – the preceding character matches *only* 0 or 1 times
* **&ast;** - the preceding character matches 0 or more times
* **+** - the preceding character matches 1 or more times
* **{n}** – the preceding character matches exactly n times
* **{n,m}** – the preceding character matches at least ntimes and no more than mtimes
* **[agd]** – the character is one of the characters within the square brackets
* **[^agd]** – the character is not one of the characters within the square brackets
* **[c-f]** – the dash defines a range of characters
* **|** (pipe) – logical OR operator
* **^** -matches the beginning of a line
* **$** -matches the end of a line

## Redirection
All programs that run on the command line have three types of data streams associated with them:
* **STDIN (0)** – Standard input fed into the program (from the command line or other programs)
* **STDOUT (1)** – Standard output printed by the program (to the terminal by default)
* **STDERR (2)** – Standard error for program errors (to the terminal by default)
