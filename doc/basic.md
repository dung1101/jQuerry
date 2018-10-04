# 1) jQuery Tutorial
## 1.1) jQuery Syntax
The jQuery syntax is tailor-made for selecting HTML elements and performing some action on the element(s).<br>
Basic syntax is:` $(selector).action()`<br>
A $ sign to define/access jQuery<br>
A (selector) to "query (or find)" HTML elements<br>
A jQuery action() to be performed on the element(s)<br>
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
fadeIn()<br>
fadeOut()<br>
fadeToggle()<br>
fadeTo()<br>
## 2.4) jQuery Sliding Methods
With jQuery you can create a sliding effect on elements.<br>
jQuery has the following slide methods:<br>
slideDown()<br>
slideUp()<br>
slideToggle()<br>
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
$(selector).stop(stopAll,goToEnd);
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
Typical syntax: $(selector).hide(speed,callback);<br>
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
text() - Sets or returns the text content of selected elements<br>
html() - Sets or returns the content of selected elements (including HTML markup)<br>
val() - Sets or returns the value of form fields<br>
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
text() - Sets or returns the text content of selected elements<br>
html() - Sets or returns the content of selected elements (including HTML markup)<br>
val() - Sets or returns the value of form fields<br>
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

The following example demonstrates attr() with a callback function:
