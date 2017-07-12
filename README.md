# LearnXquery

## XML

* XML stands for eXtensible Markup Language

* XML is a markup language much like HTML

* XML was designed to store and transport data

* XML was designed to be self-descriptive

* XML is a W3C Recommendation

* XML stores data in plain text format. This provides a software- and hardware-independent way of storing, transporting, and sharing data.

* XML, there is a full separation between data and presentation.

* XML documents form a tree structure that starts at "the root" and branches to "the leaves".

### XML Syntax
* 
``` <root>
  <child>
    <subchild>.....</subchild>
  </child>
</root>
```

* All XML Elements Must Have a Closing Tag
 
* XML Tags are Case Sensitive.

* XML Elements Must be Properly Nested

* XML Attribute Values Must be Quoted

* Some characters have a special meaning in XML.For them use entity reference.(&lt,&gt,&amp,&apos,&quot)

* 
```
<!-- This is a comment -->
```
* White-space is Preserved in XML

* XML Stores New Line as LF

* metadata (data about data) should be stored as attributes, and the data itself should be stored as elements.

### The XMLHttpRequest Object
* The XMLHttpRequest object can be used to request data from a web server.

* The XMLHttpRequest object is a developers dream, because you can:

  * Update a web page without reloading the page
  * Request data from a server - after the page has loaded
  * Receive data from a server  - after the page has loaded
  * Send data to a server - in the background
  * 
```
var xhttp = new XMLHttpRequest();
xhttp.onreadystatechange = function() {
    if (this.readyState == 4 && this.status == 200) {
       // Typical action to be performed when the document is ready:
       document.getElementById("demo").innerHTML = xhttp.responseText;
    }
};
xhttp.open("GET", "filename", true);
xhttp.send();
```


### XML Parser

* The XML DOM (Document Object Model) defines the properties and methods for accessing and editing XML.

* However, before an XML document can be accessed, it must be loaded into an XML DOM object.

* All modern browsers have a built-in XML parser that can convert text into an XML DOM object.

* The XML DOM defines a standard way for accessing and manipulating XML documents. It presents an XML document as a tree-structure.


### XPath

* XPath is a major element in the XSLT standard.

* XPath can be used to navigate through elements and attributes in an XML document.

* XPath is a syntax for defining parts of an XML document

* XPath uses path expressions to navigate in XML documents

* XPath contains a library of standard functions

* XPath is a major element in XSLT and in XQuery

* XPath is a W3C recommendation


