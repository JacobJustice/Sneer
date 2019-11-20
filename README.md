# Sneer
Generates the "sarcastic spongebob" (aka mocking spongebob) text in the command line 

# History
https://knowyourmeme.com/memes/mocking-spongebob

# Uses
Sneer provides an easy way to make sarcastic comments in your code
, you could also use bash commands to make mocking commit messages

`git commit $(sneer fixed some documentation)`

# Usage
`sneer [-f input_file] [-o output_file] [text to sneer]`

If no arguments or text is provided, sneer will use stdin.

# Functionality
Sneer works with stdin allowing for piping

```
$ cat file | sneer

TeST tEST Test
```

(Originally I made this to leave sarcastic comments using kakoune's built in | command)

The script itself is also modular allowing you
to make you own rules for how to capitalize or lowercase letters.
By default, it randomly uppers and lowers characters individually. But by
writing your own function you can build your own rulesets.

A custom function must take in a word and an index of that word as parameters. The
index tells you which character you want to capitalize and the word allows you to use the context
of the whole word. If you want the character at `index` to be uppercase 
return True, for lowercase return False. 

For example maybe you want to always capitalize vowels 
unless they are adjacent to another vowel you could write:

```python
def sneer_vowels(word, index):
    vowels = ['a','e','i','o','u','A','E','I','O','U',]
    if word[index] in vowels:
        if index-1 >= 0 and word[index-1] not in vowels:
            return True
        elif index+1 < len(word) and word[index+1] not in vowels:
            return True
        else:
            return False
    else:
        return False
```
        
And then replace the `main(sneer_default)` call with `main(sneer_vowels)`

# Examples
```
❰jacob❙~/❱✔≻ sneer testing output

testinG oUTpuT

❰jacob❙~/❱✔≻ sneer testing output

TesTInG OUTPUT

❰jacob❙~❱✔≻ cat file

test test test

1 2 3 4

abcdefghijklmnopqrstuvwxyz

❰jacob❙~❱✔≻ cat file | sneer

tEST tesT tEST

1 2 3 4

AbcdEFgHijkLMNoPqRStuvwxyz

❰jacob❙~❱✔≻ cat file | sneer

teSt Test Test

1 2 3 4

abCdefGhIjKlMnopQrsTUVwxyz
```
