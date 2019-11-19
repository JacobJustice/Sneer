#! /usr/bin/python3

import sys

#
# sneer_default
#
# parameters:
# word -word in the input string that the character you are considering to
# 	upper or lower is from
# index-index of the character you are considering to upper or lower
# 
# return:
# boolean (capitalize this character or not)
#
# parameters allow for a wide variety of conditions to make your own sarcastic
# looking text. sneer_default simply flips a coin
# 
# intended to be passed in as an argument to the main function
#

def sneer_default(word, index):
    import random
    return random.choice([True,False])


#
# char_to_words
#
# parameters:
# char_list -	list of chars
#
# return:
# word_list - list of strings
#
# concatenates chars into string, seperated by spaces
#
# in: ['a','p','p','l','e',' ','j','u','i','c','e']
# out: ["apple", "juice"]
#

def char_to_words(char_list):
    word_list = ''.join(char_list)
    word_list =  word_list.split(' ')
    return word_list


#
# main
#
# parameters:
# sneer_function -	function that takes in a word and index, and returns true or false
#
# uses sneer_function to decide whether or not to capitalize a letter
#

def main(sneer_function):
    args = sys.argv[1:]
    if len(args) == 0: #if there are no normal arguments
        args = list(sys.stdin.read()) #check stdin
        args = char_to_words(args) #convert to proper format
        if args[-1][-1] == '\n':
            args[-1] = args[-1][:-1] #remove \n
    if len(args) == 0: #if there are still no normal arguments
        sys.exit() #exit
    else:
        processed_args = []
        for word in args:
            l_word = list(''.join(word))
            for i, letter in enumerate(word):
                if sneer_function(word, i):
                    l_word[i] = l_word[i].upper()
                else:
                    l_word[i] = l_word[i].lower()
            l_word.append(' ')
            processed_args += l_word

        print(''.join(processed_args[0:(len(processed_args)-1)]))

main(sneer_default)
