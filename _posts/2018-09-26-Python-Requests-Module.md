---
layout: post
title: Python Requests Module usage and Examples
summary: We'll see how to use requests module in python to send HTTP/S Requests

---

Hi There, In this post we'll see how to send HTPP/S requests using requests module

#### What is Requests 
**Requests** is an Apache2 Licensed HTTP library, written in Python. In programming, a library is a collection or pre-configured selection of routines, functions, and operations that a program can use. These elements are often referred to as modules, and stored in object format.

Requests will allow you to send HTTP/1.1 requests using Python. With it, you can add content like headers, form data, multipart files, and parameters via simple Python libraries. It also allows you to access the response data of Python in the same way.

#### How to Install Requests module for Python

Since **requests** is not a built-in module for python we have to download it, We can install requests module by running below command in Terminal or cmd (on Windows)

{% highlight Bash %}
$ pip install requests
{% endhighlight %}

#### Importing the Requests Module

To work with the Requests module in Python, you must import the appropriate module. You can do this simply by adding the following code at the beginning of your script:

{% highlight Bash %}
import requests
{% endhighlight %}

**Note:** To make sample HTTP requests in this Tutorial we will be using **[httpbin](http://httpbin.org)** website which is a A simple HTTP Request & Response Service.

#### Making a HTTP GET Request

Before making GET request using Python requests we will see how to make GET request using cURL you can know more about cURL **[here](https://curl.haxx.se/)**

##### Making GET request Using Curl:

{% highlight Bash %}
$ curl -s -X GET "Content-Type: application/json" http://httpbin.org/get
{
  "args": {},
  "headers": {
    "Accept": "*/*",
    "Connection": "close",
    "Host": "httpbin.org",
    "User-Agent": "curl/7.43.0"
  },
  "origin": "205.234.19.3",
  "url": "http://httpbin.org/get"
}
$
{% endhighlight %}

In the above example we perfomed a HTTP GET request using cURL now we will see how to make the same GET request using Python **requests**

##### Making GET request Using Python requests:
{% highlight Bash %}
import requests #importing requests module

#Defining headers for the request for you headers may be different
headers = {'Content-Type' : 'application/json', 'Accept' : 'application/json'}
#making a GET http request
response = requests.get(‘http://httpbin.org/get’, headers=headers)
{% endhighlight %}

##### Working with Response Code


Before you can do anything with the response content, it’s a good to check the current status code of the request that we made. 

{% highlight Bash %}
>>> import requests
>>>
>>> headers = {'Content-Type' : 'application/json', 'Accept' : 'application/json'}
>>> response = requests.get('http://httpbin.org/get', headers=headers)
>>> print(response.status_code)
200
>>>
{% endhighlight %}

Here we can see that the response.status_code is 200 which means our GET request is got successful response from the website URL you can learn more about HTTP codes **[here](https://www.tutorialspoint.com/http/http_status_codes.htm)**

After a web server returns a response, you can collect the content you need. This is also done using the get requests function.

##### Get the response content
{% highlight Bash %}
>>> print(response.text)
{
  "args": {},
  "headers": {
    "Accept": "application/json",
    "Accept-Encoding": "gzip, deflate",
    "Connection": "close",
    "Content-Type": "application/json",
    "Host": "httpbin.org",
    "User-Agent": "python-requests/2.19.1"
  },
  "origin": "205.234.19.3",
  "url": "http://httpbin.org/get"
}

>>>
{% endhighlight %}

#### Make a HTTP POST Request

##### Making POST request Using Curl:

{% highlight Bash %}
$ curl -X POST "http://httpbin.org/post" -H "accept: application/json"
{
  "args": {},
  "data": "",
  "files": {},
  "form": {},
  "headers": {
    "Accept": "application/json",
    "Connection": "close",
    "Content-Length": "0",
    "Host": "httpbin.org",
    "User-Agent": "curl/7.43.0"
  },
  "json": null,
  "origin": "205.234.19.3",
  "url": "http://httpbin.org/post"
}
$
{% endhighlight %}

In the above example we perfomed a HTTP POST request using cURL now we will see how to make the same POST request using Python **requests**

##### Making POST request Using Python requests:
{% highlight Bash %}
>>> import requests
>>>
>>> headers = {'accept': 'application/json'}
>>> data = {}
>>> response = requests.post('http://httpbin.org/post', headers=headers, data=data)
>>> print(response.status_code)
200
>>> print(response.text)
{
  "args": {},
  "data": "",
  "files": {},
  "form": {},
  "headers": {
    "Accept": "application/json",
    "Accept-Encoding": "gzip, deflate",
    "Connection": "close",
    "Content-Length": "0",
    "Host": "httpbin.org",
    "User-Agent": "python-requests/2.19.1"
  },
  "json": null,
  "origin": "205.234.19.3",
  "url": "http://httpbin.org/post"
}

{% endhighlight %}

**Note:** Usually for POST request we need to pass some data but here in my case I don't need to pass any data that's why I made data = {} as empty dict


#### Make a HTTP PUT or Update Request

##### Making PUT request Using Curl:

{% highlight Bash %}
$ curl -X PUT "http://httpbin.org/put" -H "accept: application/json"
{
  "args": {},
  "data": "",
  "files": {},
  "form": {},
  "headers": {
    "Accept": "application/json",
    "Connection": "close",
    "Content-Length": "0",
    "Host": "httpbin.org",
    "User-Agent": "curl/7.43.0"
  },
  "json": null,
  "origin": "205.234.19.3",
  "url": "http://httpbin.org/put"
}
$
{% endhighlight %}

In the above example we perfomed a HTTP PUT request using cURL now we will see how to make the same PUT request using Python **requests**

##### Making PUT request Using Python requests:
{% highlight Bash %}
>>> import requests
>>>
>>> headers = {'accept': 'application/json'}
>>> data = {}
>>> response = requests.put('http://httpbin.org/put', headers=headers, data=data)
>>> print(response.status_code)
200
>>> print(response.text)
{
  "args": {},
  "data": "",
  "files": {},
  "form": {},
  "headers": {
    "Accept": "application/json",
    "Accept-Encoding": "gzip, deflate",
    "Connection": "close",
    "Content-Length": "0",
    "Host": "httpbin.org",
    "User-Agent": "python-requests/2.19.1"
  },
  "json": null,
  "origin": "205.234.19.3",
  "url": "http://httpbin.org/put"
}

>>>
{% endhighlight %}


#### Make a HTTP PATCH Request

##### Making PATCH request Using Curl:

{% highlight Bash %}
$ curl -X PATCH "http://httpbin.org/patch" -H "accept: application/json"
{
  "args": {},
  "data": "",
  "files": {},
  "form": {},
  "headers": {
    "Accept": "application/json",
    "Connection": "close",
    "Content-Length": "0",
    "Host": "httpbin.org",
    "User-Agent": "curl/7.43.0"
  },
  "json": null,
  "origin": "205.234.19.3",
  "url": "http://httpbin.org/patch"
}
$
{% endhighlight %}

In the above example we perfomed a HTTP PATCH request using cURL now we will see how to make the same PATCH request using Python **requests**

##### Making PATCH request Using Python requests:
{% highlight Bash %}
>>> import requests
>>>
>>> headers = {'accept': 'application/json'}
>>> data = {}
>>> response = requests.patch('http://httpbin.org/patch', headers=headers, data=data)
>>> print(response.status_code)
200
>>> print(response.text)
{
  "args": {},
  "data": "",
  "files": {},
  "form": {},
  "headers": {
    "Accept": "application/json",
    "Accept-Encoding": "gzip, deflate",
    "Connection": "close",
    "Content-Length": "0",
    "Host": "httpbin.org",
    "User-Agent": "python-requests/2.19.1"
  },
  "json": null,
  "origin": "205.234.19.3",
  "url": "http://httpbin.org/patch"
}

>>>
{% endhighlight %}
