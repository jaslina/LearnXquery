# XML XPath and XQuery

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


### XSLT -eXtensible Stylesheet Language Transformations

* With XSLT you can transform an XML document into HTML.

* XSLT (eXtensible Stylesheet Language Transformations) is the recommended style sheet language for XML.

* XSLT is far more sophisticated than CSS. With XSLT you can add/remove elements and attributes to or from the output file. You can also  rearrange and sort elements, perform tests and make decisions about which elements to hide and display, and a lot more.

* XSLT uses XPath to find information in an XML document.


### XLink and Xpointer

* XLink is used to create hyperlinks in XML documents.

* Any element in an XML document can behave as a link

* With XLink, the links can be defined outside the linked files

* There is no browser support for XLink in XML documents. However, all major browsers support XLinks in SVG.

### DTD Schema

* An XML document with correct syntax is called "Well Formed".

* An XML document validated against a DTD is both "Well Formed" and "Valid".

* DTD description of an XML, rules etc

* An XML Schema describes the structure of an XML document, just like a DTD.

* XML Schema is an XML-based alternative to DTD:

## XPath

* XPath is a major element in the XSLT standard.

* XPath can be used to navigate through elements and attributes in an XML document.

* XPath is a syntax for defining parts of an XML document

* XPath uses path expressions to navigate in XML documents

* XPath contains a library of standard functions

* XPath is a major element in XSLT and in XQuery

* XPath is a W3C recommendation

* XPath expressions can be used in JavaScript, Java, XML Schema, PHP, Python, C and C++, and lots of other languages.


* In XPath, there are seven kinds of nodes: element, attribute, text, namespace, processing-instruction, comment, and document nodes.

* XML documents are treated as trees of nodes. The topmost element of the tree is called the root element.

* XPath uses path expressions to select nodes or node-sets in an XML document. The node is selected by following a path or steps.
```
nodename	: Selects all nodes with the name "nodename"
/	        : Selects from the root node
//	      : Selects nodes in the document from the current node that match the selection no matter where they are
.	        : Selects the current node
..	      : Selects the parent of the current node
@	        : Selects attributes
*	        : Matches any element node
@*	      : Matches any attribute node
node()	  : Matches any node of any kind
```

#### Predicates

* Predicates are used to find a specific node or a node that contains a specific value.

* Predicates are always embedded in square brackets.

#### Selecting several paths

``` 
//book/title | //book/price	    :Selects all the title AND price elements of all book elements
//title | //price	              :Selects all the title AND price elements in the document
/bookstore/book/title | //price	: Selects all the title elements of the book element of the bookstore element AND all the price elements in the document
```

#### XPath Axes

* An axis defines a node-set relative to the current node.

``` 
ancestor	          Selects all ancestors (parent, grandparent, etc.) of the current node
ancestor-or-self	  Selects all ancestors (parent, grandparent, etc.) of the current node and the current node itself
                     attribute	Selects all attributes of the current node
child	              Selects all children of the current node
descendant	        Selects all descendants (children, grandchildren, etc.) of the current node
descendant-or-self  Selects all descendants (children, grandchildren, etc.) of the current node and the current node itself
following	          Selects everything in the document after the closing tag of the current node
following-sibling	  Selects all siblings after the current node
namespace	          Selects all namespace nodes of the current node
parent	            Selects the parent of the current node
preceding	          Selects all nodes that appear before the current node in the document, except ancestors, attribute nodes and                              namespace nodes
preceding-sibling	  Selects all siblings before the current node
self	              Selects the current node

```

#### Location Path Expression
A location path can be absolute or relative.

An absolute location path starts with a slash ( / ) and a relative location path does not. In both cases the location path consists of one or more steps, each separated by a slash:

The syntax for a location step is:

axisname::nodetest[predicate]


#### Example :

```
<!DOCTYPE html>
<html>
<body>

<p id="demo"></p>

<script>
var xhttp = new XMLHttpRequest();
xhttp.onreadystatechange = function() {
    if (this.readyState == 4 && this.status == 200) {
        showResult(xhttp.responseXML);
    }
};
xhttp.open("GET", "books.xml", true);
xhttp.send(); 

function showResult(xml) {
    var txt = "";
    path = "/bookstore/book[@category=\"cooking\"]/title"
    if (xml.evaluate) {
        var nodes = xml.evaluate(path, xml, null, XPathResult.ANY_TYPE, null);
        var result = nodes.iterateNext();
        while (result) {
            txt += result.childNodes[0].nodeValue + "<br>";
            result = nodes.iterateNext();
        } 
    // Code For Internet Explorer
    } else if (window.ActiveXObject || xhttp.responseType == "msxml-document") {
        xml.setProperty("SelectionLanguage", "XPath");
        nodes = xml.selectNodes(path);
        for (i = 0; i < nodes.length; i++) {
            txt += nodes[i].childNodes[0].nodeValue + "<br>";
        }
    }
    document.getElementById("demo").innerHTML = txt;
}
</script>

</body>
</html>
```

## XQuery

* XQuery is to XML what SQL is to databases.

* XQuery was designed to query XML data.

``` 
for $x in doc("books.xml")/bookstore/book
where $x/price>30
order by $x/title
return $x/title
```

* XQuery is built on XPath expressions

* XQuery is supported by all major databases

#### XQuery - Examples of Use

XQuery can be used to:

* Extract information to use in a Web Service
* Generate summary reports
* Transform XML data to XHTML
* Search Web documents for relevant information

#### functions

XQuery uses functions to extract data from XML documents.

The doc() function is used to open the "books.xml" file:

```
doc("books.xml")
```

#### Path Expressions

XQuery uses path expressions to navigate through elements in an XML document.

The following path expression is used to select all the title elements in the "books.xml" file:

``` 
doc("books.xml")/bookstore/book/title
```

#### Predicates

XQuery uses predicates to limit the extracted data from XML documents.

``` 
doc("books.xml")/bookstore/book[price<30]
```

#### XQuery FLWOR Expressions

For      - selects a sequence of nodes
Let      - binds a sequence to a variable
Where    - filters the nodes
Order by - sorts the nodes
Return   - what to return (gets evaluated once for every node)

Path Expression : 
```
doc("books.xml")/bookstore/book[price>30]/title
```

With FLWOR
```
for $x in doc("books.xml")/bookstore/book
where $x/price>30
return $x/title
```

with flwor and html

``` 
<ul>
{
for $x in doc("books.xml")/bookstore/book/title
order by $x
return <li>{data($x)}</li>
}
</ul>
```

#### XQuery Syntax

* XQuery is case-sensitive
* XQuery elements, attributes, and variables must be valid XML names
* An XQuery string value can be in single or double quotes
* An XQuery variable is defined with a $ followed by a name, e.g. $bookstore
* XQuery comments are delimited by (: and :), e.g. (: XQuery Comment :)

Condtional
```
for $x in doc("books.xml")/bookstore/book
return if ($x/@category="CHILDREN")
then <child>{data($x/title)}</child>
else <adult>{data($x/title)}</adult>
```

#### User Defined Functions
```
declare function prefix:function_name($parameter as datatype)
as returnDatatype
{
 ...function code here...
};
```

* Use the declare function keyword
* The name of the function must be prefixed
* The data type of the parameters are mostly the same as the data types defined in XML Schema
* The body of the function must be surrounded by curly braces
