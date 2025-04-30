# EX 3D Pattern Matching
## DATE:
## AIM:
To write a python program to implement pattern matching on the given string using Brute Force algorithm.



## Algorithm
1. Preprocess the pattern to create two arrays: bad character shift and good suffix shift.
2. Start from the rightmost character of the pattern and compare it with the corresponding character in the text.
3. If a match is found, continue comparing the next characters in the pattern and text from right to left.
4. If a mismatch occurs, use the preprocessed arrays to shift the pattern efficiently.
5. Repeat the process until the pattern is found in the text or the end of the text is reached.  

## Program:
```
/*
Program to implement the Pattern Matching.
Developed by: Sana Fathima H
Register Number:  212223240145
def preprocess_strong_suffix(shift, bpos, pat, m):
    i = m
    j = m + 1
    bpos[i] = j
    while i > 0:
        while j <= m and pat[i - 1] != pat[j - 1]:
            if shift[j] == 0:
                shift[j] = j - i
            j = bpos[j]
        i -= 1
        j -= 1
        bpos[i] = j
def preprocess_case2(shift, bpos, pat, m):
    j = bpos[0]
    for i in range(m + 1):
        if shift[i] == 0:
            shift[i] = j
        if i == j:
            j = bpos[j]
def search(text, pat):
    s = 0
    m = len(pat)
    n = len(text)
    bpos = [0] * (m + 1)
    shift = [0] * (m + 1)
    preprocess_strong_suffix(shift, bpos, pat, m)
    preprocess_case2(shift, bpos, pat, m)
    while s <= n - m:
        j = m - 1
        while j >= 0 and pat[j] == text[s + j]:
            j -= 1
        if j < 0:
            print("pattern occurs at shift = %d" % s)
            s += shift[0]
        else:
            s += shift[j + 1]
if __name__ == "__main__":
    text =input()  #"ABAAAABAACD"
    pat =input() #"ABA"
    search(text, pat)
```

## Output:
![image](https://github.com/user-attachments/assets/c5208506-fc6b-4ec9-9a06-3458ec41a23d)



## Result:
The brute force substring search program executed successfully and returned the starting index of the match or 0 if no match was found.
