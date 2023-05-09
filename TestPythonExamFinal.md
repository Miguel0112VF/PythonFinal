def get_observed_substrings(string):
    substrings = set()
    for j in range(1, len(string) + 1):
        for i in range(0, len(string) - j + 1):
            substrings.add(string[i:i+j])
    return substrings
#giving this code/seuqnce a name 

def get_possible_substrings(string, k):
    a = 4**k
    b = len(string) - (k-1)
    if a > b:
        return b
    else:
        return a
#giving this code/seuqnce a name 
    
def calculate_linguistic_complexity(string):
    observed_substrings = get_observed_substrings(string)
    possible_substrings = sum([get_possible_substrings(string, k) for k in range(1, len(string) + 1)])
    return len(observed_substrings) / possible_substrings