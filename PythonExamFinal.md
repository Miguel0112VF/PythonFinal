string = 'ATTTGGATT'

for j in range(1, len(string) + 1): #this is looking at the range from 1 to the full length of the string. The +1 is because it is non inclusive at the beckend. 
    for i in range(0, len(string) - j + 1): #j is the k value here that goes up per each loop. i is the position of the base in the string. 
        print(string[i:i+j]) 
#this is a generalized version of what I have coded for the string specific ones above. 


string = "ATTTGGATT"

for k in range(1, len(string)+1): #the range of 1, len(string)+1 because the backend is non-inclusive
    unique_substrings = set() #unique_substrings is to collect tghe number fo unique characters in eaach substring length. set() is an empty set 
    for i in range(0, len(string)-k+1): #this and the line below are the exact same as what I did above. The lettering is different, which is probably(definitely) not good. I'll work on that in the future, but not for this becuase I just want this assignment to be over. 
        substring = string[i:i+k]
        if len(substring) == k and not substring.endswith(" "): #this is to remoev any incomplete substrings. 
            unique_substrings.add(substring) #this just adds the outputs to the list. 
    print("Number of observed", k, "-length substrings:", len(unique_substrings))
#This is to get the observed substring counts for each k length. Again, a general version for all of the garbage above. 

for k in range(1, 9+1):
    string = "ATTTGGATT"[:k] #this is the string sequence 
    a = 4**k #a is the first possible equation
    b = len("ATTTGGATT") - (k-1) #b is the second possible equation
    if a > b: 
        print(k, b) #if a is greater than b use the equation b 
    else:
        print(k, a) #if b is greater than a use the equation a 
#basically, just use the equation that results in a smaller number 

def get_observed_substrings(string):
    substrings = set()
    for j in range(1, len(string) + 1):
        for i in range(0, len(string) - j + 1):
            substrings.add(string[i:i+j])
    return substrings
#giving this code/seuqnce a name. This has already been commented on 

def get_possible_substrings(string):
    for k in range(1, 9+1):
        sub = string[:k]
        a = 4**k
        b = len(string) - (k-1)
        if a > b:
            print(k, b)
        else:
            print(k, a)
#giving this code/sequence a name. This has already been commented on 

def get_observed_substrings(string):
    substrings = set()
    for j in range(1, len(string) + 1):
        for i in range(0, len(string) - j + 1):
            substrings.add(string[i:i+j])
    return substrings
#giving this code/sequence a name. This has already been commented on 

def get_possible_substrings(string, k):
    a = 4**k
    b = len(string) - (k-1)
    if a > b:
        return b
    else:
        return a
#giving this code/sequence a name. This has already been commented on 
    
def calculate_linguistic_complexity(string):
    observed_substrings = get_observed_substrings(string)
    possible_substrings = sum([get_possible_substrings(string, k) for k in range(1, len(string) + 1)])
    #the code above is to get the sum of the get_possible_substrings. Why do I need to do this for possible and not obseved? Only God knows 
    return len(observed_substrings) / possible_substrings #this is just the equation for linguistic complexity based off of the example on the assignment. 

string = "ATTTGGATT"
linguistic_complexity = calculate_linguistic_complexity(string)
print("Linguistic complexity:", linguistic_complexity)

import sys 

import pathlib #importing the datafile through pathlib. This is just the string I made up 

file_name = "SequenceDataFile.txt"
file_path = pathlib.Path.cwd() / file_name
g = file_path.read_text()

k = 2

observed_substrings = get_observed_substrings(g)
possible_substrings = sum([get_possible_substrings(g, k) for k in range(1, len(g) + 1)])
linguistic_complexity_fortxt = calculate_linguistic_complexity(g)
print("Observed count:", len(observed_substrings))
print("Possible count:", possible_substrings)
print("Linguistic complexity:", linguistic_complexity_fortxt) #this is everythng done before, but for the new string I made. 