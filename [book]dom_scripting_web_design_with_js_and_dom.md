# Selected Exercises of **DOM Scripting**

Following along with exercises in the famous book [DOM Scripting: Web Design with JavaScript and the Document Object Model](http://www.apress.com/9781430233893), and I made some improvements to the code inclueded in the book.

* Gallary_02: an unobstrusive version of ``showPic.js``

# Reading Notes

## 20150616

### Chapter 1: A Brief History of Javascript
* the wars between different browser vendors, esp. Microsoft and Netscape

### Chapter 2: Javascript syntax
* ``<script>`` default: ``<script type="text/javascript">``
* diff between  initializing an ``array`` and a  ``object``
* diff between ``Native objects`` and ``Host objects``

### Chapter 3: The Document Object Model

* The properties and methods of the ``window`` object are often referred to as the ***Browser Object Model(BOM)***
* diff between ``element node``, ``text node``, ``attribute node``
* 3 ways to access element nodes by ID, tag name, and class name
  * ``document.getElementById("purchases")``
  * ``document.getElementsByTagName("*")`` will get all elements in the document
  * ``document.getElementsByClassName("important sale")``

## 20150617 

### Chapter 4: A Javascript Image Gallery

* ***A Javascript image gallery***
  * Put a placeholder image on the same page as the list
  * When the user clicks a link, intercept the default behavior
  * Replace the placeholder image with the image from the link
* ``Pre-DOM`` and ``DOM Level 1``
  * `` element.value = "the new value"`` vs ``element.setAttribute("value", "the new value")``
* ``body_element.childNodes``
  * ``node.firstChild``
  * ``node.lastChild``
* ``alert(body_element.nodeType);``
  * Element nodes have a nodeType value of 1.
  * Attribute nodes have a nodeType value of 2.
  * Text nodes have a nodeType value of 3.
* ``node.nodeValue`` & `` note.nodeValue = "someValue"``

### Chapter 5: Best practices

* Graceful degradation: ensuring that your web pages still work without JavaScript
   ``<a href="http://www.example.com/" onclick="popUp(this.getAttribute('href'); return false;">Example</a> ")"``
* Unobtrusive JavaScript: separating structure from behavior
* Backward compatibility: ensuring that older browsers don’t choke on your scripts
```js 
    if(!getElementById) return false
```
* Performance considerations: making sure that your script is performing at its best

### Chapter 6: The Image Gallery Revisited
* the ***unobtrusive javascript*** improvement
* ***VERY IMPORTANT!!*** if the eventHandler fails, then the default behavior, that is jumping to the link,  kicks off

```js
  links[i].onclick = function(){
    return !showPic(this);
  }
```

* if some attributes doesn't exists, then get an empty string 
```js
var text = whichpic.getAttribute("title")?whichpic.getAttribute("title"):"";
```

* if the node isn't ``<img>``, then ``return false``
```js
  if(placeholder.nodeName != "IMG") return false
```

* the finished functions look like this:
```js
function prepareGallery(){
  if (!document.getElementsByTagName) return false;
  if (!document.getElementById) return false;
  if (!document.getElementById("imagegallery")) return false;

  var gallery = document.getElementById("imagegallery");
  var links = gallery.getElementsByTagName("a");
  for (var i=0; i < links.length; i++) {
    links[i].onclick = function() {
      return showPic(this) ? false : true;
    }
  }
}

function showPic(whichpic) {
  if (!document.getElementById("placeholder")) return false;
  var source = whichpic.getAttribute("href");
  var placeholder = document.getElementById("placeholder");
  if (placeholder.nodeName != "IMG") return false;
  placeholder.setAttribute("src", source);
  if (document.getElementById("description")) {
    var text = whichpic.getAttribute("title")? whichpic.getAttribute("title");
    var description = document.getElementById("description") : "";
    if (description.firstChild.nodeType == 3) {
      description.firstChild.nodeValue = text;
    }
  }
  return false;
}
```

### Chapter 5: Creating Markup on the fly

* Nodes are created and appended in this general order:
```js
window.onload = function() {

  // create a paragraph element node.
  var para = document.createElement("p");
  // create a text node
  var txt = document.createTextNode("Hello World");

  // append this text node to the paragraph
  para.appendChild(txt);

  // append this paragraph to an element node in the document
  var testdiv = document.getElementById("testdiv");
  testdiv.appendChild(para);
}
```