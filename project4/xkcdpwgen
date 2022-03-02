#!/usr/bin/python

import getopt
import sys
from random import randint

words = 4
caps = numbers = symbols = 0
password = ""

numberList = ["0", "1", "2", "3", "4", "5", "6", "7", "8", "9"]
symbolList = ["~", "!", "@", "#", "$", "%", "^", "&", "*", ".", ":", ";"]

try:
    opts, args = getopt.getopt(sys.argv[1:], "h:w:c:n:s:", ["help", "words=", "caps=", "numbers=", "symbols="])
except getopt.GetoptError:
    sys.exit(2)

for opt, arg in opts:
    if opt == "-h" or opt == "--help":
        print("usage: xkcdpwgen [-h] [-w WORDS] [-c CAPS] [-n NUMBERS] [-s SYMBOLS]"
              "Generate a secure, memorable password using the XKCD method"
              "optional arguments:"
              "-h, --help                        show this help message and exit"
              "-w WORDS, --words                 WORDS include WORDS words in the password (default=4)"
              "-c CAPS, --caps CAPS              capitalize the first letter of CAPS random words (default=0)"
              "-n NUMBERS, --numbers NUMBERS     insert NUMBERS random numbers in the password (default=0)"
              "-s SYMBOLS, --symbols SYMBOLS     insert SYMBOLS random symbols in the password (default=0)")
        sys.exit()
    elif opt == "-w" or opt == "--words":
        words = int(arg)
        print(words)
    elif opt == "-c" or opt == "--caps":
        caps = int(arg)
        print(words)
    elif opt == "-n" or opt == "--numbers":
        numbers = int(arg)
    elif opt == "-s" or opt == "--symbols":
        symbols = int(arg)

with open('words.txt') as file:
    wordList = file.read().splitlines()

for word in range(words):
    wordIndex = randint(0, len(wordList) - 1)
    wordSelect = wordList[wordIndex]
    if caps < words:
        rand2 = randint(0, 1)
        if rand2 == 1:
            wordSelect = wordSelect[0].upper() + wordSelect[1:]
            caps -= 1
    else:
        wordSelect = wordSelect[0].upper() + wordSelect[1:]
        caps -= 1
    password += wordSelect

for num in range(numbers):
    numIndex = randint(0, len(password) - 1)
    password = password[0:numIndex] + numberList[randint(0, 9)] + password[numIndex:]

for sym in range(symbols):
    symIndex = randint(0, len(password) - 1)
    password = password[0:symIndex] + symbolList[randint(0, 11)] + password[symIndex:]

print(password)