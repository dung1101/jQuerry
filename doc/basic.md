# 1) jQuery Tutorial
## 1.1) jQuery Syntax
The jQuery syntax is tailor-made for selecting HTML elements and performing some action on the element(s).<br>
Basic syntax is:` $(selector).action()`<br>
- A $ sign to define/access jQuery<br>
- A (selector) to "query (or find)" HTML elements<br>
- A jQuery action() to be performed on the element(s)<br>
Examples:<br>
```
$(this).hide() - hides the current element.
$("p").hide() - hides all <p> elements.
$(".test").hide() - hides all elements with class="test".
$("#test").hide() - hides the element with id="test".
```
### The Document Ready Event
```
$(document).ready(function(){
   // jQuery methods go here...
});
```
This is to prevent any jQuery code from running before the document is finished loading (is ready).<br>
It is good practice to wait for the document to be fully loaded and ready before working with it. This also allows you to have your JavaScript code before the body of your document, in the head section.<br>
The jQuery team has also created an even shorter method for the document ready event:<br>
```
$(function(){
   // jQuery methods go here...
});
```
## 1.2) jQuery Selectors
[jQuery Selectors](https://www.w3schools.com/jQuery/jquery_ref_selectors.asp)
```
$("*")	Selects all elements	
$(this)	Selects the current HTML element	
$("p.intro")	Selects all <p> elements with class="intro"	
$("p:first")	Selects the first <p> element	
$("ul li:first")	Selects the first <li> element of the first <ul>	
$("ul li:first-child")	Selects the first <li> element of every <ul>	
$("[href]")	Selects all elements with an href attribute	
$("a[target='_blank']")	Selects all <a> elements with a target attribute value equal to "_blank"	
$("a[target!='_blank']")	Selects all <a> elements with a target attribute value NOT equal to "_blank"	
$(":button")	Selects all <button> elements and <input> elements of type="button"	
$("tr:even")	Selects all even <tr> elements	
$("tr:odd")	Selects all odd <tr> elements
```

## 1.3) jQuery Event Methods
[jQuery Event Methods](https://www.w3schools.com/jQuery/jquery_ref_events.asp)

|Mouse Events|	Keyboard Events|	Form Events|	Document/Window Events|
|------------|-----------------|---------------|--------------------------|
|click|	keypress|	submit|	load|
|dblclick|	keydown|	change|	resize|
|mouseenter|	keyup|	focus|	scroll|
|mouseleave|	 	|blur|	unload|

### click()
The click() method attaches an event handler function to an HTML element.<br>
The function is executed when the user clicks on the HTML element.<br>

### dblclick()
The dblclick() method attaches an event handler function to an HTML element.<br>
The function is executed when the user double-clicks on the HTML element.<br>

### The on() Method
The on() method attaches one or more event handlers for the selected elements.<br>
Attach multiple event handlers to a <p> element:<br>
```
$("p").on({
    mouseenter: function(){
        $(this).css("background-color", "lightgray");
    }, 
    mouseleave: function(){
        $(this).css("background-color", "lightblue");
    }, 
    click: function(){
        $(this).css("background-color", "yellow");
    } 
});
```


# 2) jQuery Effects
[jQuery Effects Reference](https://www.w3schools.com/jQuery/jquery_ref_effects.asp)

## 2.1) jQuery hide() and show()
With jQuery, you can hide and show HTML elements with the hide() and show() methods:<br>
Syntax:<br>
```
$(selector).hide(speed,callback);
$(selector).show(speed,callback);
```
The optional speed parameter specifies the speed of the hiding/showing, and can take the following values: "slow", "fast", or milliseconds.<br>
The optional callback parameter is a function to be executed after the hide() or show() method completes (you will learn more about callback functions in a later chapter).<br>
The following example demonstrates the speed parameter with hide():<br>
```
$("button").click(function(){
    $("p").hide(1000);
});
```

## 2.2) jQuery toggle()
With jQuery, you can toggle between the hide() and show() methods with the toggle() method.<br>
Shown elements are hidden and hidden elements are shown:<br>
```
$(selector).toggle(speed,callback);
```
## 2.3) jQuery Fading Methods
With jQuery you can fade an element in and out of visibility.<br>
jQuery has the following fade methods:<br>
- fadeIn()<br>
- fadeOut()<br>
- fadeToggle()<br>
- fadeTo()<br>
## 2.4) jQuery Sliding Methods
With jQuery you can create a sliding effect on elements.<br>
jQuery has the following slide methods:<br>
- slideDown()<br>
- slideUp()<br>
- slideToggle()<br>
## 2.5) jQuery Animations - The animate() Method
The jQuery animate() method is used to create custom animations.<br>
Syntax:<br>
```
$(selector).animate({params},speed,callback);
```
The required params parameter defines the CSS properties to be animated.<br>
The optional speed parameter specifies the duration of the effect. It can take the following values: "slow", "fast", or milliseconds.<br>
The optional callback parameter is a function to be executed after the animation completes.<br>
```
$("button").click(function(){
    $("div").animate({left: '250px'});
}); 
```
Notice that multiple properties can be animated at the same time:<br>
```
$("button").click(function(){
    $("div").animate({
        left: '250px',
        opacity: '0.5',
        height: '150px',
        width: '150px'
    });
}); 
```
It is also possible to define relative values (the value is then relative to the element's current value). This is done by putting += or -= in front of the value:<br>
```
$("button").click(function(){
    $("div").animate({
        left: '250px',
        height: '+=150px',
        width: '+=150px'
    });
}); 
```
You can even specify a property's animation value as "show", "hide", or "toggle":<br>
```
$("button").click(function(){
    $("div").animate({
        height: 'toggle'
    });
}); 
```
**Uses Queue Functionality**
By default, jQuery comes with queue functionality for animations.<br>
This means that if you write multiple animate() calls after each other, jQuery creates an "internal" queue with these method calls. Then it runs the animate calls ONE by ONE.<br>
So, if you want to perform different animations after each other, we take advantage of the queue functionality:<br>
```
$("button").click(function(){
    var div = $("div");
    div.animate({height: '300px', opacity: '0.4'}, "slow");
    div.animate({width: '300px', opacity: '0.8'}, "slow");
    div.animate({height: '100px', opacity: '0.4'}, "slow");
    div.animate({width: '100px', opacity: '0.8'}, "slow");
}); 
```
The example below first moves the <div> element to the right, and then increases the font size of the text:<br>
```
$("button").click(function(){
    var div = $("div");
    div.animate({left: '100px'}, "slow");
    div.animate({fontSize: '3em'}, "slow");
}); 
```

## 2.6) jQuery stop() Method
The jQuery stop() method is used to stop an animation or effect before it is finished.<br>
The stop() method works for all jQuery effect functions, including sliding, fading and custom animations.<br>
Syntax:<br>
`$(selector).stop(stopAll,goToEnd);`
The optional stopAll parameter specifies whether also the animation queue should be cleared or not. Default is false, which means that only the active animation will be stopped, allowing any queued animations to be performed afterwards.<br>
The optional goToEnd parameter specifies whether or not to complete the current animation immediately. Default is false.<br>
So, by default, the stop() method kills the current animation being performed on the selected element.<br>
The following example demonstrates the stop() method, with no parameters:<br>
```
$("#stop").click(function(){
    $("#panel").stop();
});
```
## 2.7) jQuery Callback Functions
JavaScript statements are executed line by line. However, with effects, the next line of code can be run even though the effect is not finished. This can create errors.<br>
To prevent this, you can create a callback function.<br>
A callback function is executed after the current effect is finished.<br>
Typical syntax: `$(selector).hide(speed,callback);`<br>
Examples<br>
The example below has a callback parameter that is a function that will be executed after the hide effect is completed:<br>
```
$("button").click(function(){
    $("p").hide("slow", function(){
        alert("The paragraph is now hidden");
    });
});
```
## 2.8) jQuery Method Chaining
Until now we have been writing jQuery statements one at a time (one after the other).<br>
However, there is a technique called chaining, that allows us to run multiple jQuery commands, one after the other, on the same element(s).<br>
Tip: This way, browsers do not have to find the same element(s) more than once.<br>
To chain an action, you simply append the action to the previous action.<br>
The following example chains together the css(), slideUp(), and slideDown() methods. The "p1" element first changes to red, then it slides up, and then it slides down:<br>
```
$("#p1").css("color", "red").slideUp(2000).slideDown(2000);
```
# 3 jQuery HTML 
[jQuery HTML Reference](https://www.w3schools.com/jQuery/jquery_ref_html.asp)
## 3.1) jQuery - Get Content and Attributes
One very important part of jQuery is the possibility to manipulate the DOM.<br>
jQuery comes with a bunch of DOM related methods that make it easy to access and manipulate elements and attributes.<br>
```
DOM = Document Object Model
The DOM defines a standard for accessing HTML and XML documents:
"The W3C Document Object Model (DOM) is a platform and language-neutral interface that allows programs and scripts to dynamically access and update the content, structure, and style of a document."
```
### Get Content - text(), html(), and val()
Three simple, but useful, jQuery methods for DOM manipulation are:<br>
- text() - Sets or returns the text content of selected elements<br>
- html() - Sets or returns the content of selected elements (including HTML markup)<br>
- val() - Sets or returns the value of form fields<br>
The following example demonstrates how to get content with the jQuery text() and html() methods:<br>
```
$("#btn1").click(function(){
    alert("Text: " + $("#test").text());
});
$("#btn2").click(function(){
    alert("HTML: " + $("#test").html());
});
```
### Get Attributes - attr()
The jQuery attr() method is used to get attribute values.<br>
The following example demonstrates how to get the value of the href attribute in a link:<br>
```
$("button").click(function(){
    alert($("#w3s").attr("href"));
});
```
## 3.2) jQuery - Set Content and Attributes
### Set Content - text(), html(), and val()
We will use the same three methods from the previous page to set content:<br>
- text() - Sets or returns the text content of selected elements<br>
- html() - Sets or returns the content of selected elements (including HTML markup)<br>
- val() - Sets or returns the value of form fields<br>
The following example demonstrates how to set content with the jQuery text(), html(), and val() methods:<br>
```
$("#btn1").click(function(){
    $("#test1").text("Hello world!");
});
$("#btn2").click(function(){
    $("#test2").html("<b>Hello world!</b>");
});
$("#btn3").click(function(){
    $("#test3").val("Dolly Duck");
});
```
### A Callback Function for text(), html(), and val()
All of the three jQuery methods above: text(), html(), and val(), also come with a callback function. The callback function has two parameters: the index of the current element in the list of elements selected and the original (old) value. You then return the string you wish to use as the new value from the function.<br>
The following example demonstrates text() and html() with a callback function:<br>
```
$("#btn1").click(function(){
    $("#test1").text(function(i, origText){
        return "Old text: " + origText + " New text: Hello world!
        (index: " + i + ")"; 
    });
});

$("#btn2").click(function(){
    $("#test2").html(function(i, origText){
        return "Old html: " + origText + " New html: Hello <b>world!</b>
        (index: " + i + ")"; 
    });
});
```
### Set Attributes - attr()
The jQuery attr() method is also used to set/change attribute values.<br>
The following example demonstrates how to change (set) the value of the href attribute in a link:<br>
```
$("button").click(function(){
    $("#w3s").attr("href", "https://www.w3schools.com/jquery/");
});
```
The attr() method also allows you to set multiple attributes at the same time.<br>
The following example demonstrates how to set both the href and title attributes at the same time:<br>
```
$("button").click(function(){
    $("#w3s").attr({
        "href" : "https://www.w3schools.com/jquery/",
        "title" : "W3Schools jQuery Tutorial"
    });
});
```
##A Callback Function for attr()
The jQuery method attr(), also come with a callback function. The callback function has two parameters: the index of the current element in the list of elements selected and the original (old) attribute value. You then return the string you wish to use as the new attribute value from the function.<br>

The following example demonstrates attr() with a callback function:<br>
```
$("button").click(function(){
    $("#w3s").attr("href", function(i, origValue){
        return origValue + "/jquery/"; 
    });
});
```
## 3.3) jQuery - Add Elements
### Add New HTML Content
We will look at four jQuery methods that are used to add new content:<br>
- append() - Inserts content at the end of the selected elements
- prepend() - Inserts content at the beginning of the selected elements
- after() - Inserts content after the selected elements
- before() - Inserts content before the selected elements

## 3.4) jQuery - Remove Elements
With jQuery, it is easy to remove existing HTML elements.<br>
Remove Elements/Content<br>
To remove elements and content, there are mainly two jQuery methods:<br>
- remove() - Removes the selected element (and its child elements)
- empty() - Removes the child elements from the selected element

### Filter the Elements to be Removed
The jQuery remove() method also accepts one parameter, which allows you to filter the elements to be removed.<br>
The parameter can be any of the jQuery selector syntaxes.<br>
The following example removes all <p> elements with class="test"<br>
`$("p").remove(".test");`<br>

## 3.5) jQuery - Get and Set CSS Classes
### jQuery Manipulating CSS
jQuery has several methods for CSS manipulation. We will look at the following methods:<br>
- addClass() - Adds one or more classes to the selected elements
- removeClass() - Removes one or more classes from the selected elements
- toggleClass() - Toggles between adding/removing classes from the selected elements
- css() - Sets or returns the style attribute

**jQuery css() Method**
The css() method sets or returns one or more style properties for the selected elements.<br>
Return a CSS Property<br>
To return the value of a specified CSS property, use the following syntax:<br>
```
css("propertyname");
```
The following example will return the background-color value of the FIRST matched element:<br>
```
$("p").css("background-color");
```
Set a CSS Property<br>
To set a specified CSS property, use the following syntax:<br>
```
css("propertyname","value");
```
The following example will set the background-color value for ALL matched elements:<br>
```
$("p").css("background-color", "yellow");
```
Set Multiple CSS Properties<br>
To set multiple CSS properties, use the following syntax:<br>
```
css({"propertyname":"value","propertyname":"value",...});
```
The following example will set a background-color and a font-size for ALL matched elements:
```
$("p").css({"background-color": "yellow", "font-size": "200%"});
```
## 3.6) jQuery - Dimensions
### jQuery Dimension Methods
jQuery has several important methods for working with dimensions:<br>
- width()
- height()
- innerWidth()
- innerHeight()
- outerWidth()
- outerHeight()

### jQuery Dimensions
![](https://www.w3schools.com/jquery/img_jquerydim.gif)

# 4) jQuery Traversing
[jQuery Traversing Reference](https://www.w3schools.com/jquery/jquery_ref_traversing.asp)
## 4.1) What is Traversing?
jQuery traversing, which means "move through", are used to "find" (or select) HTML elements based on their relation to other elements. Start with one selection and move through that selection until you reach the elements you desire.<br>
The image below illustrates an HTML page as a tree (DOM tree). With jQuery traversing, you can easily move up (ancestors), down (descendants) and sideways (siblings) in the tree, starting from the selected (current) element. This movement is called traversing - or moving through - the DOM tree.<br>
![](https://www.w3schools.com/jquery/img_travtree.png)

Illustration explained:
```
The <div> element is the parent of <ul>, and an ancestor of everything inside of it
The <ul> element is the parent of both <li> elements, and a child of <div>
The left <li> element is the parent of <span>, child of <ul> and a descendant of <div>
The <span> element is a child of the left <li> and a descendant of <ul> and <div>
The two <li> elements are siblings (they share the same parent)
The right <li> element is the parent of <b>, child of <ul> and a descendant of <div>
The <b> element is a child of the right <li> and a descendant of <ul> and <div>
```
## 4.2) jQuery Traversing - Ancestors
### Traversing Up the DOM Tree
Three useful jQuery methods for traversing up the DOM tree are:
- parent()
- parents()
- parentsUntil()

### jQuery parent() Method
The parent() method returns the direct parent element of the selected element.<br>
This method only traverse a single level up the DOM tree.<br>
The following example returns the direct parent element of each <span> elements:<br>
```
$(document).ready(function(){
    $("span").parent();
});
```
### jQuery parents() Method
The parents() method returns all ancestor elements of the selected element, all the way up to the document's root element `(<html>)`.<br>
The following example returns all ancestors of all <span> elements:
```
$(document).ready(function(){
    $("span").parents();
});
```
You can also use an optional parameter to filter the search for ancestors.<br>
The following example returns all ancestors of all `<span>` elements that are `<ul>` elements:
```
$(document).ready(function(){
    $("span").parents("ul");
});
```
### jQuery parentsUntil() Method
The parentsUntil() method returns all ancestor elements between two given arguments.<br>
The following example returns all ancestor elements between a `<span>` and a `<div>` element:
```
$(document).ready(function(){
    $("span").parentsUntil("div");
});
```
## 4.3) jQuery Traversing - Descendants
### Traversing Down the DOM Tree
Two useful jQuery methods for traversing down the DOM tree are:
- children()
- find()

### jQuery children() Method
The children() method returns all direct children of the selected element.<br>
This method only traverses a single level down the DOM tree.<br>
The following example returns all elements that are direct children of each <div> elements:
```
$(document).ready(function(){
    $("div").children();
});
```
You can also use an optional parameter to filter the search for children.<br>
The following example returns all `<p>` elements with the class name "first", that are direct children of `<div>`:
```
$(document).ready(function(){
    $("div").children("p.first");
});
```
### jQuery find() Method
The find() method returns descendant elements of the selected element, all the way down to the last descendant.<br>
The following example returns all `<span>` elements that are descendants of `<div>`:
```
$(document).ready(function(){
    $("div").find("span");
});
``
The following example returns all descendants of `<div>`:
``
$(document).ready(function(){
    $("div").find("*");
});
```
## 4.4) jQuery Traversing - Siblings
Traversing Sideways in The DOM Tree<br>
There are many useful jQuery methods for traversing sideways in the DOM tree:
- siblings()
- next()
- nextAll()
- nextUntil()
- prev()
- prevAll()
- prevUntil()

### jQuery siblings() Method
The siblings() method returns all sibling elements of the selected element.<br>
The following example returns all sibling elements of `<h2>`:
```
$(document).ready(function(){
    $("h2").siblings();
});
```
You can also use an optional parameter to filter the search for siblings.<br>
The following example returns all sibling elements of `<h2>` that are `<p>` elements:
```
$(document).ready(function(){
    $("h2").siblings("p");
};
```
### jQuery next() Method
The next() method returns the next sibling element of the selected element.<br>
The following example returns the next sibling of `<h2>`:
```
$(document).ready(function(){
    $("h2").next();
});
```
### jQuery nextAll() Method
The nextAll() method returns all next sibling elements of the selected element.<br>
The following example returns all next sibling elements of `<h2>`:
```
$(document).ready(function(){
    $("h2").nextAll();
});
```
### jQuery nextUntil() Method
The nextUntil() method returns all next sibling elements between two given arguments.<br>
The following example returns all sibling elements between a `<h2>` and a `<h6>` element:
```
$(document).ready(function(){
    $("h2").nextUntil("h6");
});
```
### jQuery prev(), prevAll() & prevUntil() Methods
The prev(), prevAll() and prevUntil() methods work just like the methods above but with reverse functionality: they return previous sibling elements (traverse backwards along sibling elements in the DOM tree, instead of forward).<br>
## 4.5) jQuery Traversing - Filtering
### The first(), last(), eq(), filter() and not() Methods
The most basic filtering methods are first(), last() and eq(), which allow you to select a specific element based on its position in a group of elements.<br>
Other filtering methods, like filter() and not() allow you to select elements that match, or do not match, a certain criteria.<br>

### jQuery first() Method
The first() method returns the first element of the specified elements.<br>
The following example selects the first `<div>` element:
```
$(document).ready(function(){
    $("div").first();
});
```
### jQuery last() Method
The last() method returns the last element of the specified elements.<br>
The following example selects the last `<div>` element:
```
$(document).ready(function(){
    $("div").last();
});
```
### jQuery eq() method
The eq() method returns an element with a specific index number of the selected elements.<br>
The index numbers start at 0, so the first element will have the index number 0 and not 1. The following example selects the second `<p>` element (index number 1):<br>
```
$(document).ready(function(){
    $("p").eq(1);
});
```
### jQuery filter() Method
The filter() method lets you specify a criteria. Elements that do not match the criteria are removed from the selection, and those that match will be returned.<br>
The following example returns all <p> elements with class name "intro":
```
$(document).ready(function(){
    $("p").filter(".intro");
});
```
### jQuery not() Method
The not() method returns all elements that do not match the criteria.<br>
Tip: The not() method is the opposite of filter().<br>
The following example returns all <p> elements that do not have class name "intro":
```
$(document).ready(function(){
    $("p").not(".intro");
});
```
# 5) jQuery - AJAX Introduction
[AJAX tutorial](https://www.w3schools.com/xml/ajax_intro.asp)
[AJAX reference](https://www.w3schools.com/jquery/jquery_ref_ajax.asp)
## 5.1) jQuery load() Method
The jQuery load() method is a simple, but powerful AJAX method.<br>
The load() method loads data from a server and puts the returned data into the selected element.<br>
Syntax:
```
$(selector).load(URL,data,callback);
```
The required URL parameter specifies the URL you wish to load.<br>
The optional data parameter specifies a set of querystring key/value pairs to send along with the request.<br>
The optional callback parameter is the name of a function to be executed after the load() method is completed.<br>
Here is the content of our example file: "demo_test.txt":<br>
The following example loads the content of the file "demo_test.txt" into a specific <div> element:
```
$("#div1").load("demo_test.txt");
```
It is also possible to add a jQuery selector to the URL parameter.<br>
The following example loads the content of the element with id="p1", inside the file "demo_test.txt", into a specific <div> element:
```
$("#div1").load("demo_test.txt #p1");
```
The optional callback parameter specifies a callback function to run when the load() method is completed. The callback function can have different parameters:
- responseTxt - contains the resulting content if the call succeeds
- statusTxt - contains the status of the call
- xhr - contains the XMLHttpRequest object

The following example displays an alert box after the load() method completes. If the load() method has succeeded, it displays "External content loaded successfully!", and if it fails it displays an error message:
```
$("button").click(function(){
    $("#div1").load("demo_test.txt", function(responseTxt, statusTxt, xhr){
        if(statusTxt == "success")
            alert("External content loaded successfully!");
        if(statusTxt == "error")
            alert("Error: " + xhr.status + ": " + xhr.statusText);
    });
});
```
## 5.2) jQuery - AJAX get() and post() Methods
The jQuery get() and post() methods are used to request data from the server with an HTTP GET or POST request.<br>
HTTP Request: GET vs. POST<br>
Two commonly used methods for a request-response between a client and server are: GET and POST.<br>
```
GET - Requests data from a specified resource<br>
POST - Submits data to be processed to a specified resource<br>
GET is basically used for just getting (retrieving) some data from the server. Note: The GET method may return cached data.
POST can also be used to get some data from the server. However, the POST method NEVER caches data, and is often used to send data along with the request
```
### jQuery $.get() Method
The $.get() method requests data from the server with an HTTP GET request.<br>
Syntax:
```
$.get(URL,callback);
```
The required URL parameter specifies the URL you wish to request.<br>
The optional callback parameter is the name of a function to be executed if the request succeeds.<br>
The following example uses the $.get() method to retrieve data from a file on the server:<br>
```
$("button").click(function(){
    $.get("demo_test.asp", function(data, status){
        alert("Data: " + data + "\nStatus: " + status);
    });
});
```
### jQuery $.post() Method
The $.post() method requests data from the server using an HTTP POST request.<br>
Syntax:
```
$.post(URL,data,callback);
```
The required URL parameter specifies the URL you wish to request.<br>
The optional data parameter specifies some data to send along with the request.<br>
The optional callback parameter is the name of a function to be executed if the request succeeds.<br>
The following example uses the $.post() method to send some data along with the request:
```
$("button").click(function(){
    $.post("demo_test_post.asp",
    {
        name: "Donald Duck",
        city: "Duckburg"
    },
    function(data, status){
        alert("Data: " + data + "\nStatus: " + status);
    });
});
```
# 6) jQuery Misc
[jQuery Misc Reference](https://www.w3schools.com/jquery/jquery_ref_misc.asp)

## 6.1) The jQuery noConflict() Method
The noConflict() method releases the hold on the $ shortcut identifier, so that other scripts can use it.<br>
You can of course still use jQuery, simply by writing the full name instead of the shortcut:
```
$.noConflict();
jQuery(document).ready(function(){
    jQuery("button").click(function(){
        jQuery("p").text("jQuery is still working!");
    });
});
```
You can also create your own shortcut very easily. The noConflict() method returns a reference to jQuery, that you can save in a variable, for later use. Here is an example:
```
var jq = $.noConflict();
jq(document).ready(function(){
    jq("button").click(function(){
        jq("p").text("jQuery is still working!");
    });
});
```
If you have a block of jQuery code which uses the $ shortcut and you do not want to change it all, you can pass the $ sign in as a parameter to the ready method. This allows you to access jQuery using $, inside this function - outside of it, you will have to use "jQuery":
```
$.noConflict();
jQuery(document).ready(function($){
    $("button").click(function(){
        $("p").text("jQuery is still working!");
    });
});
```
