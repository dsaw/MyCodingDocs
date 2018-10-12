

## JQuery Tutorial

* ### Getting Started
	* We can download two versions of Jquery: Production version and Development version. The production version is a minified and gzipped version for fast load times.
	* The development version isn't compressed, so if an error is encountered, you can actually see where in jQuery it happens.
	* We can download the jquery.js file in the same directory as the project and reference it with `<script type="text/javascript" src="jquery-1.5.1.js"></script>`
	* Or include it using another link - Google's CDN & Microsoft CDN
	
* ### Hello World!
	* `$('#divTest').text('Hello world')` - The $ shortcut will access jQuery. The #divTest will select all elements with id divTest and call the text method on it. The text is set to 'Hello world!'.
		* Any selector can be used like '.' and method be called. It is shorter code than doing it in just JS.
	* Typically, wait for the document to be fully *loaded* and ready before jQuery functions are called.
	
* ### Ready event
	* `$(document).ready(function() {...})` - anonymous function is called when the document is loaded and ready.
	* `$( function() {...})` - shorthand version of above line.
		* Event is fired as soon as the page is loaded.
		
* ### Method chaining
	* `$('#divTest').text(str).removeClass("blue").addClass("bold").css("color","blue")` - Methods can be chained on the same object. No need to repeatedly call the same object
	* `$('query')` - Takes the selector query and returns a Jquery object.
		* Selector can select elements based on ID,class,type, attributes, values and so on.
		
* ### Selector types
	* `$("a[target='_blank']").append(" [new window] ")` - selects all links (a) with attribute target equal to '_blank'.
	* `Parent child relation selectors`
		* `$('p > div').css("color","blue")` - selects direct children div element of p
		* `$('a div').css("color","gree")` - selects any descendant div element of a
		
		
* ### Events
	* 	`Fading elements` - Fade objects in and out of visibility
		*   `$('selector').fadeIn(dur, easing)` - Takes three paramaters: duration of effect in ms, name of easing function.
		*   `$('selector').fadeOut(dur, easing)` - same parameters
		*   `$('selector').fadeToggle("slow")` - Fades the objects based on the toggle parameter 
	
	* 	`Sliding elements` - Slide objects up and down of visibility. Animates the height of the respective object
		*   `$('selector').slideIn(dur, easing)` - Takes three parameters: duration of effect in ms, name of easing function.
		*   `$('selector').slideOut(dur, easing)` - same parameters
		*   `$('selector').slideToggle("slow")` - Slides the objects in and out of visibility. It will check the 'display' property of the element, if hidden will be restored to the type. Applies vice versa too. 
	
	* `Animating elements` - Custom animations can be executed
		* `$('selector').animate(property_change, duration, easing,complete);` - Animates the element by performing property change with set duration and an easing function. **Complete** is a function that runs after the animation is complete.
		* `$('selector').stop()` - Stops the animation affecting the selector. Other animations remain running in the queue if the first parameter is given as true.
		
* ### Getting and setting content 
	* `$('selector').text()` - Textual representation of the inner content for all regular elements.
	* `$('selector').val()` - Values for all form elements.
	* `$('selector').html()` - Textual representation of the markup for all regular elements.
	* `$('selector').attr(attrname,val)` - Sets the attrname of selector to val. Can also take in a map
	* `$('selector').addClass('class1').removeClass('class2')` - Adds and removes associated classes to elements
	
* ### Adding and Deleting content
	* `$('selector').remove(elem)` - This method will remove the selected elements. There is an optional elem parameter to filter the specified element. 
	* `$('selector').empty()` - Empty the children of the elements defined by the selector.
	* `$('selector').append(elem)` - Append the elem in the list of selected element. elem could be HTML string, DOM object or a JQuery Object
	* `$('selector').prepend(elem)` - Prepend the elem in the list
	
	* `$('selector').before(elem)` - Adds the element before each element in the selected set of elements. 
		* elem could be a Jquery object, DOM object or HTML String.
	* `$('selector').after(elem)`  -Adds the element after each element in the selected set of elements.
	* Similarly, `insertBefore` and `insertAfter` methods perform the same function. Only the order is switched.
	
	
* ### Event handling
	* Custom code can be attached to events that have been recorded on elements.This code is wrapped inside an event handler.
		The event handler is passed an event object parameter of the event that has triggered the handler.
	* `$(selector).bind(eventname, callback)` - Binds the event handler denoted by callback to the specified element. When the event occurs targeting the specific element, the function is executed to process the event.
	 * NOTE: Deprecated in favor of the on() method in JQuery 3.1
	* `$(selector).unbind(eventname)` - Removes all the event handlers corresponding to the event on element.
	
