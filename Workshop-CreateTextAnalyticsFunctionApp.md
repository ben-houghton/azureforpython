

# Build a Python Based Text Analytics Function App

In this exercise we will build a simple HTTP Trigger Python Function that performs text Analytics, do this in the Azure Portal so that you can get a flavour of the Azure resource structure 

Once you've created this Function and tested in the Azure Portal, try calling the Function from notebooks.azure.com using Python, or try calling it from PostMan.

Here is the request POST body
```
{ 

    "name": "Test App Function App" 

} 

```
Here is the code for the Functions - you'll need to get a Text Analytics Subscription Key

```
 
########### Python 2.7 ############# 
import httplib, urllib, base64 
 

headers = { 
    # Request headers 
    'Content-Type': 'application/json', 
    'Ocp-Apim-Subscription-Key': '[Text Analytics Subscription Key]', 
} 

 

body = 'What a great day' 

params = urllib.urlencode({ 
}) 
 

try: 
    conn = httplib.HTTPSConnection('westus.api.cognitive.microsoft.com') 
    conn.request("POST", "/text/analytics/v2.0/sentiment?%s" % params, body, headers) 
    response = conn.getresponse() 
    data = response.read() 
    print(data) 
    conn.close() 
except Exception as e: 
    print("[Errno {0}] {1}".format(e.errno, e.strerror)) 

#################################### 
 

########### Python 3.2 ############# 
import http.client, urllib.request, urllib.parse, urllib.error, base64 
 

headers = { 
    # Request headers 
    'Content-Type': 'application/json', 
    'Ocp-Apim-Subscription-Key': '408b7ae40d3f434691081e5b18446a82', 
} 

body = 'What a great day' 

 

params = urllib.parse.urlencode({ 
}) 
 

try: 
    conn = http.client.HTTPSConnection('westus.api.cognitive.microsoft.com') 
    conn.request("POST", "/text/analytics/v2.0/sentiment?%s" % params, body, headers) 
    response = conn.getresponse() 
    data = response.read() 
    print(data) 
    conn.close() 
except Exception as e: 
    print("[Errno {0}] {1}".format(e.errno, e.strerror)) 

#################################### 

```
