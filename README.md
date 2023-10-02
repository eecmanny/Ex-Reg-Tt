# Regex Tutorial

This tutorial will explain the concepts of Regex or Regular Expression and will use an Email regex as an example.

## Summary


The regex pattern I provided is designed to match an email address. 

```js
const regex = /^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/
```

This regex is designed to match a complete email address, ensuring that it follows the general format of "username@domain.tld," where the username can contain lowercase letters, digits, underscores, dots, or hyphens, and the domain and TLD can contain lowercase letters, digits, dots, or hyphens. The minimum and maximum length restrictions on the TLD are also enforced.


## Table of Contents

- [Anchors](#anchors)
- [Quantifiers](#quantifiers)
- [Bracket Expressions](#bracket-expressions)
- [Character Classes](#character-classes)
- [OR Operator](#or-operator)
- [Flags](#flags)
- [Grouping and Capturing](#grouping-and-capturing)
- [Greedy and Lazy Match](#greedy-and-lazy-match)
- [Boundaries](#boundaries)
- [Back-references](#back-references)
- [Look-ahead and Look-behind](#look-ahead-and-look-behind)

## Regex Components
A regex is considered a literal (the idea of expressing a non-changing value or fixed value in a computer program's source code), so the pattern must be wrapped in slash characters (/). 


Orginal code for Matching an Email:

```js
const regex = /^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/
```

Below all the code is wrapped inside the slashes

```js
const regex = /XXXXXXXXXXXXXX/
```

### Anchors
The characters ^ and \$ are both considered to be anchors. The ^ anchor signifies a string that begins with the characters that follow it. The \$ anchor signifies a string that ends with the characters that precede it.



Orginal code for Matching an Email:

```js
const regex = /^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/
```

Below all the you add the anchors sigifing the beginning (^) and end ($) of your code.

```js
const regex – /^XXXXXXXXXX$/
```

### Quantifiers
A requirement of the regex is the Quantifiers set the limits of the string that your regex matches (or an individual section of the string). Quantifiers are inherently greedy, meaning they match as many occurrences of particular patterns as possible. They frequently include the minimum and maximum number of characters that your regex is looking for, and will be either a symbol or  wapped around {}. 

> \* = Matches the pattern zero or more times
>
> \+ = Matches the pattern one or more times
>
 >? = Matches the pattern zero or one time
>
 >{} = Curly brackets can provide three different ways to set limits for a match:
>
 >{ n } = Matches the pattern exactly n number of times
>
 >{ n, } = Matches the pattern at least n number of times
>
> { n, x } = Matches the pattern from a minimum of n number of times to a maximum of x number of times

Also worth mnetioning quantifiers can be made lazy by adding the ? symbol after it, meaning it will match as few occurrences as possible (for more info please on Greedy and Lazy please see the Greedy and Lazy section).

Orginal code for Matching an Email:

```js
const regex = /^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/
```

Below are using 3 anchore in 3 seperate locations to match diffent parts of the emsil. The first two are + characters to match the pattern 1 or more times and the second is {2,6} meaning it looking for a match a minimum 2 and a maximum of 6 times.
```js
const regex = /^(xxxx+)x(xxxx+)xx(xxxx{2,6})$/
```

### Bracket Expressions
Anything inside a set of square brackets ([]) represents a range of characters that we want to match. These patterns are known as bracket expressions also known as a positive character group, because they outline the characters we want to include. The "-" used between alphanumeric characters (letters and numbers only) to represent a range of those possible characters. It's important to note that a bracket expression can be turned into a negative character group by adding the ^ symbol to the beginning of the expression inside the brackets. A common example is matching a string that doesn't include any vowels.

Orginal code for Matching an Email:
```js
const regex = /^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/
```

Below we are usung three square brackets:

>The first bracket is looking for matching letter characters a through z all lowercase ([a-z]), and next it's looking for intergers 0 through 9 ([0-9]).  Lastly we are looking for specific to match  "\_" "." "-" ([a-z0-9_\.-]). The \ doesn't get counted becasue the "." is used as a literal so to escpe it you need to add a "\\" in front of it to be able to be used. Overall, this will find a match for the username
>
>[a-z0-9_\.-]
>
>Example:
>[username] = [firstname.lastname_123]

>The second bracket has a character class "\d"	which matches any digit (Arabic numeral). Meaning it's short hand for intergers 0 through 9 ([0-9]). Next, it's matching letter characters a through all lowercase ([a-z]). Lastly we are looking for specific to match "." "-" ([\da-z\.-]). The \ doesn't get counted becasue the "." is used as a literal so to escpe it you need to add a "\\" in front of it to be able to be used. Overall, this will find a match for the domain 
>
>>Example:
>[domain] = [mycompany.usa1]
>
>[\da-z\.-]

>The third bracket is looking for matching letter characters a through z all lowercase ([a-z]), Lastly we are looking for specific to match "." ([a-z\.]). The "\\" doesn't get counted becasue the "." is used as a literal so to escape it you need to add a "\\" in front of it to be able to be used. Overall, this will find a match for the TLD (top-level domain). 
>
>[a-z\.]
>
>[TLD] = [us.com]



```js
const regex = /^([a-z0-9_\.-]+)x([\da-z\.-]+)xx([\da-z\.-]{2,6})$/
```

```js
returns = [firstname.lastname_123]x[mycompany.usa1]xx[us.com]
```

### Character Classes
Character classes are a way to specify a set of characters that can be matched by a regular expression. 

> .	 = Matches any character except line terminators. When s flag set, it also matches line terminators.
>
>\d	= Matches any digit (Arabic numeral).
>
 >\D	= Matches any character that is not a digit (Arabic numeral).
>
 >\w	= Matches any alphanumeric character from Latin alphabet, including underscore.
>
 >\W	= Matches any character that is not an alphanumeric character from Latin alphabet or underscore.
>
 >\s	= Matches any whitespace character (space, tab, newline, non-breaking space, and similar).
>
 >\S	= Matches any character that isn’t a whitespace character.
>
 >\t	= Matches a horizontal tab.
>
 >\r	= Matches a carriage return.
>
 >\n	= Matches a linefeed.
>
 >\v	= Matches a vertical tab.
>
 >\f	= Matches a form-feed.
>
 >[\b]	= Matches a backspace.
>
 >\0	= Matches a NUL character (when not followed by another digit).
>
 >\xnn	= Matches the character code nn (two hexadecimal digits).
>
 >\unnnn	= Matches a UTF-16 code unit with the value nnnn (four hexadecimal digits).
>
> \ (insert special character here) = \ Followed by a special character, means that the character should be matched literally.  
> @ = Is already a literal so this will represent its self.
> 


Also, each of the last three character classes can be changed to perform an inverse match by capitalizing the letter character. For example, \D matches a non-digit character.

As stated in the Bracket expression section /d matches any numeric number.

Orginal code for Matching an Email:
```js
const regex = /^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/
```

Lastly, we add the character classes. If you want to make "." a literal add "\\" infront (\\.). Also, @ is already a literal so it's added as @. What these are doing are seperating the username and Domain with an @ character, also the Domain and TLD are seprated by a period. When the email is checked it will expect these characters.

```js
const regex = /^([a-z0-9_\.-]+)@([\da-z\.-]+).\([\da-z\.-]{2,6})$/
```
```js
returns = [USERNAME]@[DOMAIN].[TLD]
//example
returns = [firstname.lastname_123]@[mycompany.usa1].[us.com]
```
This is how you write an email regular expression.

### OR Operator
Bracket expression does not require the string to meet all of the requirements in the pattern. So, the OR operator in JavaScript regex is used to match one of the given patterns using the OR operator (|).

>Example:
>(ab|cd)
>
>Matches "ab" OR "cd"  


### Flags
Flags are the expection to the rule of regex must be wrapped in  slash "/" characters. Flags are placed at the end of a regex, after the second slash, and they define additional functionality or limits for the regex. 

There are six optional flags:

> g	= Performs a global match, finding all matches rather than just the first.
>
 >i	= Makes matches case-insensitive. Matches both uppercase and lowercase.
>
 >m	= Performs multiline matches. (Changes behavior of ^,$)
>
 >s 	= Allows . to match newline characters.
>
 >u	= Enables Unicode support.
>
 >y	= Matches are sticky, looking only at exact position in the text.

The "g"  and "i" are the flags. The "g" find all the matches and not only the first one. "i" makes matches case-insensitive. Matches both uppercase and lowercase.

>Example:
>
>/apple/gi
>
>Matches:
>'apple', 'apple', 'apple'


### Grouping and Capturing
When grouping we need () to establish groups.

>Example:
>(abcd)

When grouping capturing group groups a subpattern, allowing you to apply a quantifier to the entire group or use disjunctions within it. It memorizes information about the subpattern match, so that you can refer back to it later with a backreference, or access the information through the match results. It will only match exaclty what's in the group.

>Example:
>(abcd)
>
>Matches and captures "abcd" in this specific order so "acdb" won't match. But, "abcde" does match because it has "abcd" in it and each gets captured.

When non-capturing groups a subpattern, allowing you to apply a quantifier to the entire group or use disjunctions within it. It acts like the grouping operator in JavaScript expressions, and unlike capturing groups, it does not memorize the matched text, allowing for better performance and avoiding confusion when the pattern also contains useful capturing groups. To make a group non-campturing add "?:" to group.

>Example:
>(?:abcd)
>
>Matches "abcd" in this specific order so "acdb" won't match. But, "abcde" does match because it has "abcd" in it but non of them get captured because in this method it's used to save memory. 



### Greedy and Lazy Match
Quantifiers are inherently greedy, meaning they match as many occurrences of particular patterns as possible. A lazy qauntfier means it will match as few occurrences as possible. You can also make a greedy regex lazy by adding the ? symbol after it.

>Example:
>
>Consider the regex /".*"/, which is designed to match text within double quotes. In a string like "Hello" and "World", the greedy regex will match the entire string between the first and last double quotes: "Hello" and "World".
>
>Using the same regex".*?"/, the lazy regex will match text within the nearest set of double quotes separately. In the string "Hello" and "World", the lazy regex will first match "Hello", then match "World", treating them as separate matches.

### Boundaries
A boundary in JavaScript regex is a special character that marks the beginning or end of a string.
Anchors are used to match the beginning or end of a string.
Quantifiers are used to specify how many times a character or group of characters can be matched.
Character classes are used to match a set of characters.

The following table shows the different types of boundaries and their syntax:
Boundary	Syntax

>Anchors^ = Match the beginning of a string
>
>\A = Match the beginning of a string	
>
>$ = Match the end of a string	
>
>\Z = Match the end of a string	
>
 >\b = Match a word boundary	
>
 >\B = Match a non-word boundary	
>
 >\d = Match a digit	
>
 >\D = Match a non-digit	
>
 >\s = Match a whitespace character	
>
 >\S = Match a non-whitespace character	
>
 >[abc] = Match any of the characters in the set abc	
>
 >[a-z] = Match any lowercase letter	
>
> [A-Z] = Match any uppercase letter	
>
> [0-9] = Match any digit	
>
> [a-zA-Z] = Match any letter	
>
 >[\w] = Match any word character	
>
> [\W] = Match any non-word character


Orginal code for Matching an Email example Uses character classes too. The \d in ([\da-z\.-]+) is a character class that matches any digit (Arabic numeral) which is the shorthand for [0-9].

```js
const regex = /^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/
```


### Back-references
A backreference is a way to match the same text as previously matched by a capturing group. Capturing groups count from 1, so the first capturing group's result can be referenced with \1, the second with \2, and so on. \0 is a character escape for the NUL character.

>Example:(\w+) \1
>
>(\w+): This is a capturing group that matches and captures one or more word characters.
>: This matches a space.
>\1: This is a back-reference to the first capturing group. It matches the same text that was captured by the first group.


### Look-ahead and Look-behind
Look-ahead is a special type of regular expression that allows you to match a pattern only if it is followed by another pattern and there are Positve and Negative look-aheads.

>Example:
>
>Postive:  Find expression A which has expression B after it.
>A(?=B)
>
>Negative:  Find expression A which does not have expression B after it.
>A(?!B)


Look-behind is a special type of regular expression that is zero-width assertions that ensure a pattern is preceded by another pattern and there are Positve and Negative look-behinds.

>Example:
>
>Postive:  Find expression A which has expression B before it.
>
>(?<=B)A
>>
>Negative:  Find expression A which does not have expression B before it.
>(?<!B)A



## Author
Emmanuel Cordero

https://github.com/eecmanny

https://gist.github.com/eecmanny

https://gist.github.com/eecmanny/289dabf3cf2a8003eaf55ebbbcbc12f2

