# jqMobi - a HTML5 targeted Javascript Framework

jqMobi is a Javascript framework targeted at HTML5 browsers with a blazingly fast query selector library that supports W3C queries.  

It is comprised of three parts.

1) jqMobi  - query selector library

2) jqUi - UI/UX library for mobile applications in a webkit browser or W8/WP8.  Please see the Kitchen Sink folder for a demo

3) jqPlugins - plugins for mobile applications in a webkit browser or W8/WP8.


# About jqMobi


We started talking to our development community and asked them what they wanted.  The key features were

1. Fast performance

2. Small code base

3. Only needs to support a small subset of commands

Rather then try to improve another library, we found it easier to build one from the ground up, but recognizing the groundwork other frameworks laid out.  By doing this, we were able to identify simple ways to increase speed performance.  Our tests repeatedly showed we were 2x or more faster at single operation commands. 
 
All the libraries performed similar when operations were performed on a group of elements.


# Using jqMobi

To use jqMobi, include the script in your html file.  You can use the pre-built minified version.

``` js
<script src="jq.mobi.min.js"></script>
```

This will then create two objects that you can work with.  It will NOT override a pre-existing $ object.
``` js
$("#main")
jq("#main")
```

# Query Selector

W3C spec'ed queries are supported.  What this means is you can do the following

``` js
$("input[type='text']")
```

You can NOT do the following, as it's not supported by the browsers.

``` js
$("input:text")
```

In some functions, an additional selector can be used.  This can be a string, array, or a jqMobi object.  We currently do not support functions



# Syntax:

Basic call

``` js
$("#id").hide()
```

You can specify a Dom element, selector, list of nodes, or HTML string.	

``` js
$("span").bind("click",function(){console.log("clicked");}); // -> find all span elements and attach a click event
```
You can pass in an HTML string and it will create the object for you.

``` js
var myDiv=$("<div id='foo'>") //Creates a div object and returns it
```

# jqMobi API functions - Please see http://http://app-framework-software.intel.com/api for all functions


# jqMobi Ajax calls

``` js

.get(url,callback) //Makes an Ajax request to the URL and executes the callback funtion with the result
.post(url,data,callback,dataType) //Makes an Ajax POST request to the URL with the data and executes the callback with the result.  An optional dataType can be passed in, as some webservices require the header
.getJSON(url,data,callback) //Makes an ajax request with the data and executes callback function passing in a JSON object from the Ajax response into the callback function.
```
If you need more access, you can use the following.

``` js
.ajax {
   type:'POST', //defaults to GET
   url:'/api/getinfo', //defaults to window.location
   contentType:'application/json', //defaults to application/x-www-form-urlencoded
   headers:{},
   dataType:'application/json', //defaults to text/html
   data:{username:foo}, //Can be a Key/Value pair string or object.  If it's an object, $.serialize is called to turn it into a Key/Value pair string
   success:function(data){}, //function to call on successful Ajax request
   error:function(data){}, //function to call when an error exists in the Ajax request
}
```

If the url contains the pattern =? in it, a jsonP request will be made.  These can ONLY be GET requests

# jqMobi Helper calls
``` js
.param() //Serialize a JSON object into KVP for a querystring
.parseJSON(string) //Backwards compatability JSON parsing call.  Uses the browsers native JSON parser
.parseXML(string) //Parses a string and returns a XML document version
```

# jqMobi OS detectors

``` js
$.os.webkit     //True if webkit found in the user agent
$.os.android    //True if anroid useragent
$.os.ipad       //True if iPad useragent
$.os.iphone     //True if iPhone user agent
$.os.webos      //True if WebOS detected
$.os.touchpad   //True if WebOS and Touchpad user agent
$.os.ios        //True if iPad or iPhone
$.os.blackberry //True if Blackberry PlayBook or OS >=6
```

# Plugins

jqMobi is built with the extendability to add plugins.  To create a plugin, you will most likely extend the $.fn object by passing a reference of the main jqMobi object

``` js

(function($){
  $.fn['foo']=function(){
     alert("bar");
  }
})(jq);

```

# Contribute

You can contribute to the core code by forking it and make a pull request.  Please keep in mind we do not want to add functionality that is a one-off case.  These are best dealt with via plugins.


# Bugs

Please use github issues and file any bugs with the following

1. Any error messages from the console

2. Line numbers of offending code

3. Test cases

4. Description of the Error

5. Expected result

6. Browser/Device you are testing on


# License

App Framework is is licensed under the terms of the MIT License, see the included license.txt file.

jqMobi uses code from the following software:
1) Zepto.js - Thomas Fuchs (MIT X11 License)
2) qUnit - jQuery Foundation (MIT X11 License)
