---
layout: post
title:  "Assignment 1: Word Frequencies in Gibbons and Wealth of Nations"
date:   2021-09-20 10:00:00 -0400
categories: jekyll update
---

Amanda Westlake

Digital Humanities

September 10, 2021

This program takes in large texts (in this case, the Wealth of Nations and the Decline and Fall of the Roman Empire) and prints out a list of the most common words present in the texts in order to compare their content.

```

def readFile(fileName):
  #print(fileName)
  file = open(fileName, 'r') # open file 

  index = {}
  for line in file:
    line = file.readline() #save line into string line
    words = line.split() #split line into list of words

    for word in words:
      if (word != '\n') and (word!= ""):
        if word in index:
          index[word] += 1 #increment
          num = index[word]
        else:
          index[word] = 1
  file.close()
  return index



def readFileCapitals(fileName):
  #print(fileName)
  file = open(fileName, 'r') # open file 

  index = {}
  for line in file:
    line = file.readline() #save line into string line
    words = line.split() #split line into list of words

    for word in words:
      if (word != '\n') and (word!= "") and word[0].isupper():
        if word in index:
          index[word] += 1 #increment
          num = index[word]
        else:
          index[word] = 1
  file.close()
  return index


def sortWords(dictionary):
  wordList = sorted(dictionary, key=dictionary.get, reverse=True)
  return wordList

def printWords(wordList, dictionary):
  i = 0
  for word in wordList:
    print(i, ".) ", word, " appears: ", dictionary[word], " times", "\n")
    i += 1
    
    # Uncomment this code to create a top 50 list (or change to any number)
    # if not limited, the number of words makes it difficult to read
    if i == 150:
      break


# Run program here - prints list of all words in descending order

indexDecline = readFile("declineandfall-gut.txt")
indexWealth = readFile("wealthofnations-gut.txt")

print("Decline and Fall of the Roman Empire words: \n")
wordsDecline = sortWords(indexDecline)
printWords(wordsDecline, indexDecline)

print("Wealth of Nation words: \n")
wordsWealth = sortWords(indexWealth)
printWords(wordsWealth, indexWealth)


[jekyll-docs]: https://jekyllrb.com/docs/home
[jekyll-gh]:   https://github.com/jekyll/jekyll
[jekyll-talk]: https://talk.jekyllrb.com/

```
