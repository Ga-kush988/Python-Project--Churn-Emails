

```python
fhand = open('/cxldata/datasets/project/mbox-short.txt')
inp = fhand.read()
fhand.close()
```


```python

```


```python

def number_of_lines():
    f=open('/cxldata/datasets/project/mbox-short.txt')   
    finput=f.read()
    counter=0
    for i in finput:
        if i =='\n':
            counter+=1
    print(counter)  
    return counter
    f.close()
number_of_lines()
```

    1910





    1910




```python
fhand = open('/cxldata/datasets/project/mbox-short.txt')
count = 0
for line in fhand:
    line = line.rstrip() # Remove new line characters from right
    if line.startswith('From:'):
        print(line)
```

    From: stephen.marquard@uct.ac.za
    From: louis@media.berkeley.edu
    From: zqian@umich.edu
    From: rjlowe@iupui.edu
    From: zqian@umich.edu
    From: rjlowe@iupui.edu
    From: cwen@iupui.edu
    From: cwen@iupui.edu
    From: gsilver@umich.edu
    From: gsilver@umich.edu
    From: zqian@umich.edu
    From: gsilver@umich.edu
    From: wagnermr@iupui.edu
    From: zqian@umich.edu
    From: antranig@caret.cam.ac.uk
    From: gopal.ramasammycook@gmail.com
    From: david.horwitz@uct.ac.za
    From: david.horwitz@uct.ac.za
    From: david.horwitz@uct.ac.za
    From: david.horwitz@uct.ac.za
    From: stephen.marquard@uct.ac.za
    From: louis@media.berkeley.edu
    From: louis@media.berkeley.edu
    From: ray@media.berkeley.edu
    From: cwen@iupui.edu
    From: cwen@iupui.edu
    From: cwen@iupui.edu



```python
def count_number_of_lines():
    f=open("/cxldata/datasets/project/mbox-short.txt") 
    count=0
    for line in f:
            line = line.rstrip()
            if line.startswith('Subject:'):
                count=count+1
    return(count)
print(count_number_of_lines()) 
```

    27



```python
def average_spam_confidence():
    f=open("/cxldata/datasets/project/mbox-short.txt") 
    count=0
    sum=0
    for line in f:
            line = line.rstrip()
            if line.startswith('X-DSPAM-Confidence:'):
                sp=line.split(':')
                sum+=float(sp[1])
                count=count+1
    average=float(sum/count)
    return (average)
print(average_spam_confidence())
```

    0.7507185185185187



```python
def find_email_sent_days():
    with open("/cxldata/datasets/project/mbox-short.txt") as f:
        days = [i.split(' ')[2] for i in f if i.startswith('From ')]
        dic = {}
        for day in days:
            dic[day] = days.count(day)        
        return dic
print (find_email_sent_days())
```

    {'Sat': 1, 'Fri': 20, 'Thu': 6}



```python
def count_message_from_email():
    fhand = open('/cxldata/datasets/project/mbox-short.txt')
    ecount={}
    for line in fhand:
        if line.startswith('From:') and '@' in line:
            sp=line.split()
            email=sp[1]
            ecount[email]=ecount.get(email,0)+1
    return ecount

count_message_from_email()
```




    {'stephen.marquard@uct.ac.za': 2,
     'louis@media.berkeley.edu': 3,
     'zqian@umich.edu': 4,
     'rjlowe@iupui.edu': 2,
     'cwen@iupui.edu': 5,
     'gsilver@umich.edu': 3,
     'wagnermr@iupui.edu': 1,
     'antranig@caret.cam.ac.uk': 1,
     'gopal.ramasammycook@gmail.com': 1,
     'david.horwitz@uct.ac.za': 4,
     'ray@media.berkeley.edu': 1}




```python
def count_message_from_domain():
    with open("/cxldata/datasets/project/mbox-short.txt") as f:
        emails = [re.findall('@([^\s]*)',i)[0] for i in f if i.startswith('From ')]
        dic = {}
        for email in emails:
            dic[email] = emails.count(email)        
        return dic
print(count_message_from_domain())
```

    {'uct.ac.za': 6, 'media.berkeley.edu': 4, 'umich.edu': 7, 'iupui.edu': 8, 'caret.cam.ac.uk': 1, 'gmail.com': 1}



```python

```
