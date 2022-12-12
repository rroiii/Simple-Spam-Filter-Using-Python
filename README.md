# Simple Spam Filter Using Python

This is a spam filter based on bayes theorem.

To use  this, we need enter our message that we want to check wether it is a spam or not
```
my_msg = ""
words = my_msg.split()
```
This spam filter has a data set which determine wether the word is ham or spam. so it is necessary to enter data words to determine wether that word ham or spam.

```
arr = [['Ham','Dear'],
       ['Ham','Dear'],
       ['Ham','Dear'],
       ['Ham','Dear'],
       ['Ham','Dear'],
       ['Ham','Dear'],
       ['Ham','Dear'],
       ['Ham','Dear'],
       ['Ham','Friend'],
       ['Ham','Friend'],
       ['Ham','Friend'],
       ['Ham','Friend'],
       ['Ham','Friend'],
       ['Ham','Lunch'],
       ['Ham','Lunch'],
       ['Ham','Lunch'],
       ['Ham','Money'],
       ['Spam','Dear'],
       ['Spam','Dear'],
       ['Spam','Friend'],
       ['Spam','Money'],
       ['Spam','Money'],
       ['Spam','Money'],
       ['Spam','Money']]
```
Besides that there is also a function to calculate posibilites of word in ham or spam category.

```
def check_msg(category : str, msg : str, array: List[List[str]]):
    count = 0
    element = 1
    prob = 0
    for i in range(len(arr)-1):
        for j in range(len(arr[i])-1):
            if(arr[i][0] == category):
    
                count+=1
            
            if(arr[i][0] == category and arr[i][1].lower() == msg.lower()):

                element+=1
    prob = element/count
    return prob
```
This is function to calculate posibilites of ham or spam in data set.
```
def count_spam_ham(category : str,array: List[List[str]]):
    count = 0
    element_spam_ham = 0
    prob = 0
    for i in range(len(arr)):
        for j in range(len(arr[i])-1):
            if(arr[i][0] == category):
                element_spam_ham+=1
    prob = element_spam_ham/len(arr)
    return prob
```
This code is for calculate total probability.
```
for word in words:
    if word in my_msg:
        prob_word = check_msg("Ham",word, arr)
        prob_total_ham = prob_word*prob_total_ham

prob_total_ham = prob_total_ham * prob_ham
print(prob_ham)

for word in words:
    if word in my_msg:
        prob_word = check_msg("Spam",word, arr)
        prob_total_spam = prob_word*prob_total_spam

prob_total_spam = prob_total_spam * prob_spam
print(prob_total_spam)
```
To determine wether spam or not based on total probability of spam and ham
```
if(prob_total_ham > prob_total_spam):
    print("not spam")
else:
    print("spam")
```
References
https://www.youtube.com/watch?v=O2L2Uv9pdDA
