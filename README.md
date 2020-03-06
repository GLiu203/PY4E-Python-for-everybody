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






----------------------------------------------------------------------------------------------------------------------------------------





----------------------------------------------------------------------------------------------------------------------------------------




----------------------------------------------------------------------------------------------------------------------------------------




----------------------------------------------------------------------------------------------------------------------------------------





----------------------------------------------------------------------------------------------------------------------------------------






----------------------------------------------------------------------------------------------------------------------------------------

