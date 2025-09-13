# Python Practicals (Q1–Q13)

```python
# 1. Write a program to find the roots of a quadratic equation
a = int(input("Enter coefficient of x^2: "))
b = int(input("Enter coefficient of x: "))
c = int(input("Enter constant: "))
print(f"Your eqn. is: {a}x^2 + {b}x + {c}")
d = (b**2) - (4*a*c)

if (d < 0):
    print("Real roots does not exist")
else:
   x1 = ((-b) + (d**0.5)) / (2 * a)
   x2 = ((-b) - (d**0.5)) / (2 * a)
   print("First sol. is: " , x1)
   print("Second sol. is: " , x2)


# 2. Write a program to accept a number ‘n’ and 
# a. Check if ’n’ is prime 
n = int(input("Enter a number to check prime: "))
if (n<0):
    print("It is a negtaive number")
elif (n==0):
    print("0 is not a prime number")
elif (n==1):
    print("1 is not a prime number")
else:
    l = []
    for i in range(2 , n+1):
        if (n%i == 0):
            l.append(i)

    if (l[0] == n):
        print('It is a prime number')
    else: 
        print("It is not a prime number")

# b. Generate all prime numbers till ‘n’ 
n = int(input("Enter a number till where you want all prime number: "))
z = {}
for i in range(2,n+1):
    for j in range (2,i+1):
        l = []
        if (i%j == 0):
            l.append(j)
            if (l[0]==j):
                z.append(i)

print(z)

# c. Generate first ‘n’ prime numbers This program may be done using functions
def is_prime(x):
    if x<2:
        return False
    for i in range(2,int(x**0.5)+1):
        if x%i==0:
            return False
    return True

def first_n_primes(n):
    primes=[]
    num=2
    while len(primes)<n:
        if is_prime(num):
            primes.append(num)
        num+=1
    return primes

n=int(input("Enter number of primes to generate: "))
print(first_n_primes(n))


# 3. Write a program to create a pyramid of the character ‘*’ and a reverse pyramid
rows = int(input("Enter number of rows: "))

# Pyramid
for i in range(1, rows+1):
    print(" "*(rows-i) + "*"*(2*i-1))

# Reverse Pyramid
for i in range(rows-1, 0, -1):
    print(" "*(rows-i) + "*"*(2*i-1))


# 4. Write a program that accepts a character and performs the following:
# a. print whether the character is a letter or numeric digit or a special character. 
# b. if the character is a letter, print whether the letter is uppercase or lowercase
# c. if the character is a numeric digit, prints its name in text (e.g., if input is 9, output is NINE)
import string
import num2words 
char = input("Enter any char: ")
if (char in string.digits):
    print("It is a digit")
    print(num2words.num2words(char))
elif (char in string.punctuation):
    print("It is a special character")
elif (char in string.ascii_letters):
    print("It is a letter")
    if (char in string.ascii_lowercase):
        print("It is a lowercase letter")
    elif (char in string.ascii_uppercase):
        print("It is a uppercase letter")


# 5. Write a program to perform the following operations on a string 
# a. Find the frequency of a character in a string. 
para = str(input("Enter string: "))
char = str(input("Enter char to be searched: "))
count = 0
for k in para:
   if (k==char):
      count += 1
print("No. of occurence of" , char , "is" , count)

# b. Replace a character by another character in a string. 
para = str(input("Enter string: "))
char1 = str(input("Enter char to be replaced: "))
char2 = str(input("Enter new char you want: "))
print(para.replace(char1 , char2))

# c. Remove the first occurrence of a character from a string. 
para = str(input("Enter string: "))
char = str(input("Enter char whose first occurence to be removed: "))
print(para.replace(char , "" , 1))

# d. Remove all occurrences of a character from a string.
para = str(input("Enter string: "))
char = str(input("Enter char whose first occurence to be removed: "))
print(para.replace(char , ""))


# 6. Write a program to swap the first n characters of two strings.
s1 = input("Enter first string: ")
s2 = input("Enter second string: ")
n = int(input("Enter number of characters to swap: "))

s1_new = s2[:n] + s1[n:]
s2_new = s1[:n] + s2[n:]

print("After swapping:")
print("String 1:", s1_new)
print("String 2:", s2_new)


# 7. Write a function that accepts two strings and returns the indices of all the occurrences of the second string in the first string as a list. If the second string is not present in the first string then it should return -1
def find_all_occurrences(s, sub):
    indices = []
    start = 0
    
    while True:
        index = s.find(sub, start)   
        if index == -1:
            break
        indices.append(index)
        start = index + 1   
    
    return indices if indices else -1

print(find_all_occurrences("banana", "ana"))   


# 8. Write a program to create a list of the cubes of only the even integers appearing in the input list (may have elements of other types also)
# a. 'for' loop 
lst = [1,2,3,4,5,6,"a",8.5]
cubes = []
for i in lst:
    if isinstance(i,int) and i%2==0:
        cubes.append(i**3)
print("Cubes using loop:", cubes)

# b. list comprehension
cubes2 = [i**3 for i in lst if isinstance(i,int) and i%2==0]
print("Cubes using comprehension:", cubes2)


# 9. Write a program to read a file and 
# a. Print the total number of characters, words and lines in the file. 
import string
with open("new.txt") as f:
    data = f.read()
    words = data.split()
    lines = data.split("\n")
    count = 0
    count2 = 0
    count3 = 0
    for i in data:
        if i in string.ascii_letters:
            count+=1
    for j in words:
        count2 +=1 
    for line in lines:
        count3 +=1
    print("No. of characters is " , count)
    print("No. of words is " , count2)
    print("No. of lines is " , count3)

# b. Calculate the frequency of each character in the file. Use a variable of dictionary type to maintain the count. 
with open("new.txt") as f:
    data = f.read()
    dict = {}
    for i in data:
        dict[i] = dict.get(i ,0 ) + 1
print(dict)
    
# c. Print the words in reverse order. 
with open("new.txt") as f:
    data = f.read()
    words = data.split()
    print(words[::-1])

# d. Copy even lines of the file to a file named ‘File1’ and odd lines to another file named ‘File2’.
with open("new.txt", "r") as f, \
     open("file1.txt", "w") as f1, \
     open("file2.txt", "w") as f2:
    for i, line in enumerate(f, start=1):
        if i % 2 == 0:   # even line
            f1.write(line)
        else:            # odd line
            f2.write(line)
print("Lines copied")


# 10. Write a program to define a class Point with coordinates x and y as attributes. Create relevant methods and print the objects. Also define a method distance to calculate the distance between any two point objects.
import math
class Point:
    def __init__(self, x, y):
        self.x = x
        self.y = y
    
    def __str__(self):
        return f"Point({self.x}, {self.y})"
    
    def distance(self, other):
        return math.sqrt((self.x - other.x)**2 + (self.y - other.y)**2)

p1 = Point(2, 3)
p2 = Point(5, 7)
print(p1)
print(p2)
print("Distance:", p1.distance(p2))


# 11. Write a function that prints a dictionary where the keys are numbers between 1 and 5 and the values are cubes of the keys.
def cube_dict():
    d = {i: i**3 for i in range(1,6)}
    print(d)
cube_dict()


# 12. Consider a tuple t1=(1, 2, 5, 7, 9, 2, 4, 6, 8, 10). Write a program to perform following operations: 
t1=(1,2,5,7,9,2,4,6,8,10)
# a. Print half the values of the tuple in one line and the other half in the next line.
half = len(t1)//2
print(t1[:half])
print(t1[half:])
# b. Print another tuple whose values are even numbers in the given tuple.
even_tuple = tuple(i for i in t1 if i%2==0)
print(even_tuple)
# c. Concatenate a tuple t2=(11,13,15) with t1.
t2=(11,13,15)
print(t1+t2)
# d. Return maximum and minimum value from this tuple
print("Max:", max(t1))
print("Min:", min(t1))


# 13. Write a program to accept a name from a user. Raise and handle appropriate exception(s) if the text entered by the user contains digits and/or special characters.
class InvalidNameError(Exception):
    """Custom exception for invalid names"""
    pass

def validate_name(name):
    if not name.isalpha():
        raise InvalidNameError("Name must contain only alphabets (no digits/special characters).")
    return name

try:
    user_input = input("Enter your name: ")
    valid_name = validate_name(user_input)
    print(f"Hello, {valid_name}!")
except InvalidNameError as e:
    print("Error:", e)