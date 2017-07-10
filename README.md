# LearnXquery

## XML
1. XML stands for eXtensible Markup Language
2. XML is a markup language much like HTML
3. XML was designed to store and transport data
4. XML was designed to be self-descriptive
5. XML is a W3C Recommendation
6. XML stores data in plain text format. This provides a software- and hardware-independent way of storing, transporting, and sharing data.
7. XML, there is a full separation between data and presentation.
8. XML documents form a tree structure that starts at "the root" and branches to "the leaves".

### XML Syntax
1.
``` <root>
  <child>
    <subchild>.....</subchild>
  </child>
</root>
```
2. All XML Elements Must Have a Closing Tag
3. XML Tags are Case Sensitive.
4. XML Elements Must be Properly Nested
5. XML Attribute Values Must be Quoted
6. Some characters have a special meaning in XML.For them use entity reference.(&lt,&gt,&amp,&apos,&quot)
7. 
```
<!-- This is a comment -->
```
8. White-space is Preserved in XML
9. XML Stores New Line as LF
10. metadata (data about data) should be stored as attributes, and the data itself should be stored as elements.

### The XMLHttpRequest Object
The XMLHttpRequest object can be used to request data from a web server.

The XMLHttpRequest object is a developers dream, because you can:

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


