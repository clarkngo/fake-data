Video: Regular Expressions (Regex) Tutorial: How to Match Any Pattern of Text
- https://youtu.be/sa-TUpSx1JA

WebApp: RegexOne - Learn Regular Expressions with simple, interactive exercises.
- https://regexone.com/

## Lesson 1: An Introduction, and the ABCs
- abc
-

## Lesson 1½: The 123s
- \d
- 123
- [123][0-9][0-9]

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

## Lesson 10: Starting and ending
- ^Mission: successful$

Solution
The expression 'Mission: successful' will match anywhere in the text, so we need to use the starting and ending anchors in an expression ^Mission: successful$ to only match the full string that starts with 'Mission' and ends with 'successful'.

## Lesson 11: Match groups
- ^(file.+)\.pdf$

Solution

We only want to capture lines that start with "file" and have the file extension ".pdf" so we can write a simple pattern that captures everything from the start of "file" to the extension, like this ^(file.+)\.pdf$.

## Lesson 12: Nested groups
- (\w+ (\d+))

Solution

This expression requires capturing two parts of the data, both the year and the whole date. This requires using nested capture groups, as in the expression (\w+ (\d+)).

We can alternatively use \s+ in lieu of the space, to catch any number of whitespace between the month and the year.

## Lesson 13: More group work
- (\d\d\d\d)x(\d\d+)
- (\d+)x(\d+)

Solution

This one is pretty clean, we just need to capture the two groups of digits as such (\d+)x(\d+).

## Lesson 14: It's all conditional
- I love (cats|dogs)

Solution

By using the logical or, we can match the first two lines by using the expression I love (cats|dogs). But logs and cogs are pretty cool too.

## Lesson 15: Other special characters
- .*

Solution

This lesson is more of a sandbox for you to play with some sample text. The lazy solution to this, can be the simple expression .* :)

## Problem 1: Matching a decimal numbers
- ^-?\d+(,\d+)*(\.\d+(e\d+)?)?$
- ^-?[0-9]+((,|\.)[0-9]+)*((e[0-9]+)?)?$
- ^-?[0-9]+([,\.][0-9]+)*((e[0-9]+)?)?$
- [^p]$

Solution

The expression for this can be quite complicated when you take into account fractional numbers, exponents, and more.

For the above example, the expression ^-?\d+(,\d+)*(\.\d+(e\d+)?)?$ will match a string that starts with an optional negative sign, one or more digits, optionally followed by a comma and more digits, followed by an optional fractional component which consists of a period, one or more digits, and another optional component, the exponent followed by more digits.

This is not the only solution as there can be many expressions that can match these sets of number strings.

## Problem 2: Matching phone numbers
- ^\(?(\d+)(-|\)| )?(\d+)(-|\)| )?(\d+)(-|\)| )?(\d+)?
- 1?[\s-]?\(?(\d{3})\)?[\s-]?\d{3}[\s-]?\d{4}
- (1\s)?\(?([0-9]{3})(-|\)|\s)?([0-9]{3})(-|\s)?([0-9]{4}

Solution

To grab the area code from the phone numbers, we can simply capture the first three digits, using the expression (\d{3}).

However, to match the full phone number as well, we can use the expression 1?[\s-]?\(?(\d{3})\)?[\s-]?\d{3}[\s-]?\d{4}. This breaks down into the country code '1?', the captured area code '\(?(\d{3})\)?', and the rest of the digits '\d{3}' and '\d{4}' respectively. We use '[\s-]?' to catch the space or dashes between each component.

## Problem 3: Matching emails
- ^([\w\.]*)
- ^([\w\.\+]*)@(\w+)(.eu)?.com

Solution

To extract the beginning of each email, we can use a simple expression ^([\w\.]*) which will match emails starting with alphanumeric characters including the period. It will match up to the point in the text where it reaches an '@' or '+'.

Again, you should probably use a framework to match emails!

## Problem 4: Matching HTML
- <(a|div)\b[^>]*>(.*?)</(a|div)>
- <(a|div)?>?

Solution

It is a best practice to use a proper library to parse html, but to find simple tag names, you can use the expression <(\w+).

You can also capture tag contents >([\w\s]*)<, or even attribute values ='([\w://.]*)' if desired (not the goal of this problem though).

#1) Anchor Characters: ‘^’ and ‘$’ at the beginning and end of
the pattern are used to anchor the pattern to the start of the line,
and to the end of the line respectively.

#2) Wildcard Character: ‘.’ Is used to match any character.
Example:“^.$” will match all lines with any single character.

#3) MetaCharacters (Need to be escaped):
.[]()\^$|?*+

## Problem 5: Matching specific filenames
- (\w+)\.(gif|jpg|png)$
- ([a-z0-9_]+)\.(gif|png|jpg)$

Solution

We are only looking for image files ending with the 'jpg', 'png' and 'gif' file extensions, so we can capture all such filenames using the expression (\w+)\.(jpg|png|gif)$.

## Problem 6: Trimming whitespace from start and end of line
- ^\s*(.*)\s*$

Solution

We can just skip all the starting and ending whitespace by not capturing it in a line. For example, the expression ^\s*(.*)\s*$ will catch only the content.

## Problem 7: Extracting information from a log file
- (\w+)\(([\w\.]+):(\d+)\)
- (E/)\(\s[0-9]{4}\):(\s+[a-z]+.+)+([0-9]{3,4}\))

Solution

This one can be tricky too, but we really just want to capture the method name, filename, and line number. This can be achieved using the expression (\w+)\(([\w\.]+):(\d+)\) in which the first capture group is the method, followed by an escaped parenthesis, followed by the filename, a colon, and finally the line number.

## Problem 8: Parsing and extracting data from a URL
- (\w+)://
- ://([\w\-\.]+)
- (:(\d+))
- (\w+)://([\w\-\.]+)(:(\d+))?

Solution

We have to match each of the three components:

the protocols in our list are all alphanumeric, so they can be matched using (\w+)://
The hosts can contain non-alphanumeric characters like the dash or the period, so we will have to specifically include those characters using ://([\w\-\.]+)
The port is an optional part of the URI and is preceeded with a colon and can be matched using (:(\d+))
To put it all together, we then have the full regular expression (\w+)://([\w\-\.]+)(:(\d+))? to capture all the data we are looking for.

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


## Using regex.txt
email
- grep -E "[A-Za-z0-9+-]+@[a-z]+\.(com|edu|net)" regex.txt
- grep -E "^(http|https)://(www)?\.[a-z]+\.(com|gov)" regex.txt
url
- grep -E "^(https?)://(www)?\.[a-z]+\.(com|gov)" regex.txt
phone
- grep -E "([0-9]{1,3})([\.-])([0-9]{1,3})([\.-])([0-9]{1,4})" regex.txt
- grep -E "([0-9]{1,3})(\.|-)([0-9]{1,3})(\.|-)([0-9]{1,4})" regex.txt


[] - Matches Characters in brackets
[^] - Matches Characters in brackets
() - Group
