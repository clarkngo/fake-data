Video: Regular Expressions (Regex) Tutorial: How to Match Any Pattern of Text
- https://youtu.be/sa-TUpSx1JA

WebApp: RegexOne - Learn Regular Expressions with simple, interactive exercises.
- https://regexone.com/

## Lesson 1: An Introduction, and the ABCs
- abc

## Lesson 1½: The 123s
- \d
- 123

Explanation:

You can use the expression [cmf]an to match only 'can', 'man' and 'fan' without matching any other line. As you will see in the next lesson, you can also use the inverse expression [^drp]an to match any three letter word ending with 'an' that does not start with 'd', 'r' or 'p'.

## Lesson 2: The Dot
- ...\.

Solution

You can use ...\. to match the first three (wildcard) characters,
and escape the final wildcard meta-character to match the period instead.
This ensures that it will not match the '1' in the fourth line.

## Lesson 3: Matching specific characters
- [cmf]an
- [^drp]an

## Lesson 4: Excluding specific characters
- [^b]og
- [hd]og

Solution

The simplest solution to match any line that ends in 'og' but is not 'bog' would be the expression [^b]og.
Alternatively, you could use what we learned from the previous lesson and use [hd]og to match 'hog' and 'dog'
but not 'bog'. Note that it is slightly more restrictive expression because it limits the strings it can match.

## Lesson 5: Character ranges
-  [A-C][n-p][a-c]


Solution
All the characters are sequential, so you can use the different ranges in the expression [A-C][n-p][a-c] to match only the first three lines.

## Lesson 6: Catching some zzz's
- waz{3,5}up

There are a couple 'z's in the first two lines we have to match, so the expression waz{3,5}up will match all strings with that many 'z's.

## Lesson 7: Mr. Kleene, Mr. Kleene
- aa+b*c+
- a{2,4}b{0,4}c{1,2}
- a{1,}[bc]{1,}

Solution
There are at least two 'a's, zero or more 'b's, and at least one 'c' in each line to match, so you can use the expression 'aa+b*c+' to represent this exactly.

Alternatively, an even more restrictive expression would be a{2,4}b{0,4}c{1,2} which puts both an upper and lower bound on the number of each of the characters.

## Lesson 8: Characters optional
- \d+ files? found\?

Solution
We can use the meta-character '\d' to match the number of files and use the expression \d+ files? found\? to match all the lines where files were found.

Note that the first question mark applies to the preceding 's' character (for plurality), and the actual question mark at the end must be escaped to match the text.

## Lesson 9: All this whitespace
- \d\.\s+abc


Solution
We have to match only the lines that have a space between the list number and 'abc'. We can do that by using the expression \d\.\s+abc to match the number, the actual period (which must be escaped), one or more whitespace characters then the text.

If we had used the Kleene Star instead of the plus, we would also match the fourth line, which we actually want to skip.

##

#1) Anchor Characters: ‘^’ and ‘$’ at the beginning and end of
the pattern are used to anchor the pattern to the start of the line,
and to the end of the line respectively.

#2) Wildcard Character: ‘.’ Is used to match any character.
Example:“^.$” will match all lines with any single character.

#3) MetaCharacters (Need to be escaped):
.[]()\^$|?*+


# Using command in grep
grep `whoami` filename

grep `whoami` sample_files/user.log


# Using environment variables
# would only determine the meaning of the variable HOME
grep "$HOME" filename

grep "$HOME" ../.profile

# Single quotes would not work
# it will search for the pattern $HOME
grep '$HOME' filename


# importance of the right type of quotation marks
