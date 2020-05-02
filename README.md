# Randomness-Accuracy
A way to know how accurate random function is

*****

import random
import math

a = []  # a list of multiplication table results for numbers between 2 and 40
for i in range(2, 40):
    for j in range(2, 40):
        d = i * j
        if d not in a:  # avoiding repetitive numbers
            a.append(d)
a = sorted(a)  # sorting a (not necessary)


def test(x):  # creating a function returning the number of times a random number has been equal to one of a set
    # members through 100 tries
    count = 0
    for k in range(100):  # 100 random numbers = 100 tries
        ran = random.randrange(0, max(x) + 1)
        for item in x:
            if ran == item:
                count += 1
    return count


result = []  # a list for each test of randomness
for q in range(1000):  # The more range it be the more accurate this test will become
    result.append(test(a))
avg = sum(result) / len(result)  # average number of equal times in 100 try for 1000 test
ss = (len(a) / max(a)) * 100  # The percentage which shows a set's part from state space which is 0 to 39 * 39

print("Maximum equal results: {0}\nMinimum equal results: {1}\nAverage: {2}".format(max(result), min(result), avg))
print("Set a's part from state space: " + str(ss))
print("Random function accuracy: " + str((100 - (abs(avg - ss) / ss) * 100)))

*****

Add whatever you think will improve the code above
