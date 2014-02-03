##File Input and Output

I'll pose the same question I posed before:

How often do we have a list of values that we just typed into the computer? 
Not that often, right? We usually have data that we put in a file, or downloaded in a file from offline or were sent by a colleague.

On the course site, you should find this file (insert link). Download it.

Open the file in your text editor. What do you notice about the structure of the file? 

```python
>>> f=open("locations.csv",'r')
>>> f
<open file 'locations.csv', mode 'r' at 0x10045d780>
```

The above command opens a file, called spreadsheet and holds it in memory for our use in a container called f. 
The 'r' mode tells the computer that spreadsheet exists and is ready to be read. 

If we type f, we see that f is open for reading. This line is referencing the file as an object, not the data within it. So let's get that data.

```python
>>> location = f.readlines()
>>> location
```
Look at this output on your screen and in your text editor. Does it look like you expected? What has readlines done?

Let's liberate this data so we can do useful and fun things with it.

```python
>>> for lin in location:
...     print(lin).split()
['Site,Observations,Species,Expenditure']
['Lake_Creek,4,12,18']
['Los_Alamos,3,8,340']
['Big_Bend,4,16,280']
['McDonald,5,20,280']
['Balmorrhea,3,3,174']
```

That looks a little nicer. What's different here? Upon what have we split location? What are these objects? We can find out with type:

```python
>>> type(lin)
<type 'str'>
```

On our file, we used a file method, readlines. Now we've split the output into a bunch of strings. We can now manipulate lin as a string.


```python
>>> for lin in location:
...     print(lin).strip(',')
Site,Observations,Species,Expenditure

Lake_Creek,4,12,18

Los_Alamos,3,8,340

Big_Bend,4,16,280

McDonald,5,20,280

Balmorrhea,3,3,174

>>> type(lin)
<type 'str'>
```

We can put all our data in a list over which we could iterate like so:

```python
>>> loc_list = []
>>> for lin in location:
...     loc_list.append((lin).strip().split(','))
... 
>>> loc_list
[['Site', 'Observations', 'Species', 'Expenditure'], ['Lake_Creek', '4', '12', '18'], ['Los_Alamos', '3', '8', '340'], ['Big_Bend', '4', '16', '280'], ['McDonald', '5', '20', '280'], ['Balmorrhea', '3', '3', '174']]
 >>> for i in loc_list[0:]:
   ...	if len(i[0:]) == 4::
   ...	    print 'yay'
yay
yay
yay

```

In this way, we could, for example, check if any of our rows have too many fields, which will help us locate errors in our input files.

But still, we might want to be able to break our data down into, say information about each site. We can accomplish this by combining what we know about indexing and slicing with a new data type, the dictionary. Dictionaries, like physical dictionaries are key:value pairs. The key is a unique identifier that stores information, the value.

```python
>>> money_dict = {}
>>> for lin in loc_list:
...     money_dict[lin[0]]=lin[3]
... 
>>> money_dict
{'Balmorrhea': '174', 'Lake_Creek': '18', 'McDonald': '280', 'Los_Alamos': '340', 'Site': 'Expenditure', 'Big_Bend': '280'}


```

We can use the keys in the dictionary to look up a value associated with the key:

```python
>>> money_dict['Lake_Creek']
18
```

Let's say we wanted to output our numbers to a different file.

```python
outfile=open("output.txt","w")
```

Python makes it quite easy to write out your data. Also to overwrite old files. When you open output.txt, you need to make sure you aren't overwriting an old file. Everyone i know who does any programming has done this. A lot. 
Also of note is that this command will open a file in the working directory you've specified. If you want to save this somewhere, else, you need to specify that file path.

```python
>>> outfile = open('out.txt', 'w')
>>> for item in money_dict.keys():
...    outfile.write('It cost %s dollars to sample %s location' %(money_dict[item], item) + '\n')
... 
>>> outfile.close()
```

You want to close your file when you're done to prevent accidentally writing to it over and over and because python only allows you to have a certain number open.

Practice time:

+ Open the spreadsheet and read it in.
+ Choose a numerical column. Average it.
+ Write a statement about what mathematical operation you did, how you did it, and the result to a file.






