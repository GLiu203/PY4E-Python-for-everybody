# Python-for-everybody-Coursera-


I'm taking the Michigan University 'Python for everybody' course. This repo will include my homework codes. 


----------------------------------------------------------------------------------------------------------------------------------------
8.4 Open the file romeo.txt and read it line by line. For each line, split the line into a list of words using the split() method. The program should build a list of words. For each word on each line check to see if the word is already in the list and if not append it to the list. When the program completes, sort and print the resulting words in alphabetical order.

You can download the sample data at http://www.py4e.com/code3/romeo.txt


fname = input("Enter file name: ")

fh = open(fname)

lst = list()

for line in fh:

    line = line.rstrip().split()
    
    for i in line: 
    
        if i not in lst:
        
            lst.append(i)
            
lst.sort()

print(lst)


----------------------------------------------------------------------------------------------------------------------------------------
8.5 Open the file mbox-short.txt and read it line by line. When you find a line that starts with 'From ' like the following line:
From stephen.marquard@uct.ac.za Sat Jan  5 09:14:16 2008
You will parse the From line using split() and print out the second word in the line (i.e. the entire address of the person who sent the message). Then print out a count at the end.
Hint: make sure not to include the lines that start with 'From:'.

You can download the sample data at http://www.py4e.com/code3/mbox-short.txt



fname = input("Enter file name: ")

if len(fname) < 1 : fname = "mbox-short.txt"

fh = open(fname)

count = 0

for line in fh:

    line = line.strip()
    
    if not line.startswith('From:'):
    
        continue
        
    list = line.split()
    
    print(list[1])
    
    count += 1
    

print("There were", count, "lines in the file with From as the first word")

----------------------------------------------------------------------------------------------------------------------------------------
9.4 Write a program to read through the mbox-short.txt and figure out who has sent the greatest number of mail messages. The program looks for 'From ' lines and takes the second word of those lines as the person who sent the mail. The program creates a Python dictionary that maps the sender's mail address to a count of the number of times they appear in the file. After the dictionary is produced, the program reads through the dictionary using a maximum loop to find the most prolific committer.

name = input("Enter file:")

if len(name) < 1 : name = "mbox-short.txt"

handle = open(name)

list = list()

dict = dict()

count = 0

for line in handle:

    if line.startswith('From') and not line.startswith('From:'):
    
      wds = line.split()[1]
      
      if wds in dict:
      
          dict[wds] = dict[wds] + 1
          
      else:
      
          dict[wds] = 1
          
print(wds, dict[wds])
         
----------------------------------------------------------------------------------------------------------------------------------------
10.2 Write a program to read through the mbox-short.txt and figure out the distribution by hour of the day for each of the messages. You can pull the hour out from the 'From ' line by finding the time and then splitting the string a second time using a colon.
From stephen.marquard@uct.ac.za Sat Jan  5 09:14:16 2008
Once you have accumulated the counts for each hour, print out the counts, sorted by hour as shown below.


name = input("Enter file:")

if len(name) < 1 : name = "mbox-short.txt"

handle = open(name)

lst = list()

for line in handle:

    if line.startswith('From') and not line.startswith('From:'):
    
        line = line[-14:-12]
        
        lst.append(line)
        
lst.sort()

#print(lst)

counts = dict()

hours = lst

for hour in hours:

    if hour not in counts:
    
        counts[hour] = 1
        
    else:
    
        counts[hour] = counts[hour] +1

for k,v in counts.items():

    print(k,v)
    
----------------------------------------------------------------------------------------------------------------------------------------
11. Finding Numbers in a Haystack

In this assignment you will read through and parse a file with text and numbers. You will extract all the numbers in the file and compute the sum of the numbers.

Data Files
We provide two files for this assignment. One is a sample file where we give you the sum for your testing and the other is the actual data you need to process for the assignment.

import re

handle = open('actual.txt')

numlist = list()

for line in handle:

    line = line.rstrip()
    
    stuff = re.findall('[0-9]+', line)
    
    if len(stuff)<1: continue
    
    else:
    
        for i in stuff:
        
            numlist.append(i)
            
#print(numlist)

sum = 0

for num in numlist:

    sum += int(num)

print(sum)


----------------------------------------------------------------------------------------------------------------------------------------
13. Extracting Data from XML

In this assignment you will write a Python program somewhat similar to http://www.py4e.com/code3/geoxml.py. The program will prompt for a URL, read the XML data from that URL using urllib and then parse and extract the comment counts from the XML data, compute the sum of the numbers in the file.

import urllib.request as UR

import xml.etree.ElementTree as ET


url = input('URL: ')

print('Retrieving', url)

xml = UR.urlopen(url).read()

print('Retrieved', len(xml), 'characters')

count = 0

sum = 0

tree = ET.fromstring(xml)

counts = tree.findall('.//count')

for i in counts:

    count += 1
    
    sum += int(i.text)

print('Count:', count)

print('Sum:', sum)

----------------------------------------------------------------------------------------------------------------------------------------




----------------------------------------------------------------------------------------------------------------------------------------
12.1 Scraping Numbers from HTML using BeautifulSoup In this assignment you will write a Python program similar to http://www.py4e.com/code3/urllink2.py. The program will use urllib to read the HTML from the data files below, and parse the data, extracting numbers and compute the sum of the numbers in the file.

from urllib.request import urlopen

from bs4 import BeautifulSoup

import ssl



ctx = ssl.create_default_context()

ctx.check_hostname = False

ctx.verify_mode = ssl.CERT_NONE

url = input('Enter - ')

html = urlopen(url, context=ctx).read()

soup = BeautifulSoup(html, "html.parser")



count = 0

sum = 0

tags = soup('span')

for tag in tags:

    # Look at the parts of a tag
    
    print('TAG:', tag)
    
    print('URL:', tag.get('href', None))
    
    print('Contents:', tag.contents[0])
    
    print('Attrs:', tag.attrs)
    
    count += 1
    
    sum += int(tag.contents[0])
    
print(count)

print(sum)
----------------------------------------------------------------------------------------------------------------------------------------






----------------------------------------------------------------------------------------------------------------------------------------

