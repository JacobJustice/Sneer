# Sneer
Generates the "sarcastic spongebob" (aka mocking spongebob) text in the command line 

# History
https://knowyourmeme.com/memes/mocking-spongebob

# Uses
Sneer provides an easy way to make sarcastic comments in your code
, you could also use bash commands to make mocking commit messages

`git commit $(sneer fixed some documentation)`

# Functionality
Sneer works with stdin allowing for piping

`$ cat file | sneer

TeST tEST Test`

(Originally I made this to leave sarcastic comments using kakoune's built in | command)

The script itself is also modular allowing you
to make you own rules for how to capitalize or lowercase letters.
By default, it randomly uppers and lowers characters individually. But by
writing your own function you can build your own rulesets.

A custom function must take in a word and an index of that word as a parameter. The
index tells you which character you want to capitalize and the word allows you to use the context
of the whole word. For example maybe you want to always capitalize vowels but never capitalize 
adjacent vowels. You could write:

`def sneer_vowels(word, index):
    vowels = ['a','e','i','o','u','A','E','I','O','U',]
    if word[index] is in vowels:
        return true
    else:
        return false`
        
And then replace the `main(sneer_default)` call with `main(sneer_vowels)`

# Examples
`❰jacob❙~/❱✔≻ sneer testing output`

`testinG oUTpuT`

`❰jacob❙~/❱✔≻ sneer testing output`

`TesTInG OUTPUT`

`❰jacob❙~❱✔≻ cat file`

`test test test`

`1 2 3 4`

`abcdefghijklmnopqrstuvwxyz`

`❰jacob❙~❱✔≻ cat file | sneer`

`tEST tesT tEST`

`1 2 3 4`

`AbcdEFgHijkLMNoPqRStuvwxyz`

`❰jacob❙~❱✔≻ cat file | sneer`

`teSt Test Test`

`1 2 3 4`

`abCdefGhIjKlMnopQrsTUVwxyz`
