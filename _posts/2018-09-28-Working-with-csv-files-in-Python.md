---
layout: post
title: Python Working with csv files 
summary: We'll see how to Read/Write CSV files in Python

---

Hi There, In this post we'll see how to work with **CSV** (Comma Separated Values) using Python.

In Programming we need to get information into and out of your programs to acomplich some specific tasks, Exchanging information through text files is a common way to share information between programs. One of the most popular formats for exchanging data is the CSV format.


#### What Is a CSV File?

CSV (Comma Separated Values) is a file format for data storage which looks like a text file. A comma-separated values (CSV) file is a delimited text file that uses a comma to separate values. A CSV file stores tabular data (numbers and text) in plain text. Each line of the file is a data record. Each record consists of one or more fields, separated by commas. The use of the comma as a field separator is the source of the name for this file format.

Here’s how does CSV structure looks like:

##### sample.csv

{% highlight Bash %}
name, age, email
Mark, 25, mark@gmail.com
Robin, 26, robin@outlook.com
Sara, 27, sara@gmail.com
{% endhighlight %}

Notice how each piece of data is separated by a comma. Normally, the first line identifies each piece of data—in other words, the name of a data column. Every subsequent line after that is actual data

#### Importing the Requests Module

To work (Read/Write) with the CSV files in Python, First we must import the **csv** module. As csv is a built-in module for python we don't need to install it. You can import csv simply by adding the following code at the beginning of your script:

{% highlight Bash %}
import csv
{% endhighlight %}

#### Reading CSV File With Python

##### read_csv.py

{% highlight Bash %}
# importing csv module
import csv

# reading csv file
with open('sample.csv', 'r') as csv_file:
    # creating a csv reader object
    read_csv = csv.reader(csv_file)

    # extracting field names through first row
    fields = next(read_csv)
    print(f'Column names are: {", ".join(fields)}')
    # extracting each row one by one
    for row in read_csv:
        print(f'Row details: {", ".join(row)}')
{% endhighlight %}

In the above code **read_csv.py** we are reading sample.csv and printing each row one by one by skipping the column headings row. The output for the above code will be as follows

##### output of read_csv.py

{% highlight Bash %}
Column names are: name,  age,  email
Row details: Mark,  25,  mark@gmail.com
Row details: Robin,  26,  robin@outlook.com
Row details: Sara,  27,  sara@gmail.com
{% endhighlight %}


#### Writing CSV Files With Python

##### writer_csv.py

{% highlight Bash %}
# importing csv module
import csv

#New list to add
new_line = ['Rob', '28', 'rob@hotmail.com']
# open file in appending mode
with open('sample.csv', 'a') as csv_file:
    # creating a csv writer object
    write_csv = csv.writer(csv_file, dialect='excel')
    # Appending the newlist to csv file
    write_csv.writerow(new_line)
{% endhighlight %}

In the above writer_csv.py we are writing a new list `new_line = ['Rob', '28', 'rob@hotmail.com']` into `sample.csv` file.

I hope this post is useful for you, Thanks for reading..
