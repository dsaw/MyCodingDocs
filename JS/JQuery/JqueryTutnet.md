

## JQuery Tutorial

* ### Getting Started
	* We can download two versions of Jquery: Production version and Development version. The production version is a minified and gzipped version for fast load times.
	* The development version isn't compressed, so if an error is encountered, you can actually see where in jQuery it happens.
	* We can download the jquery.js file in the same directory as the project and reference it with _<script type="text/javascript" src="jquery-1.5.1.js"></script>_
	* Or include it using another link - Google's CDN & Microsoft CDN
	
* ### Hello World!
	* _$('#divTest').text('Hello world')_ - The $ shortcut will access jQuery. The #divTest will select all elements with id divTest and call the text method on it. The text is set to 'Hello world!'.
		* Any selector can be used like '.' and method be called. It is shorter code than doing it in just JS.
	* Typically, wait for the document to be fully *loaded* and ready before jQuery functions are called.
	
* ### Ready event
	* _$(document).ready(function() {...})_ - anonymous function is called when the document is loaded and ready.
	* _$( function() {...})_ - shorthand version of above line.
		* Event is fired as soon as the page is loaded.
		
* ### Method chaining
	* _$('#divTest').text(str).removeClass("blue").addClass("bold").css("color","blue")_ - Methods can be chained on the same object. No need to repeatedly call the same object
	* _$('query')_ - Takes the selector query and returns a Jquery object.
		* Selector can select elements based on ID,class,type, attributes, values and so on.
		
* ### Selector types
	* _$("a[target='_blank']").append(" [new window] ")_ - selects all links (a) with attribute target equal to '_blank'.
	* _Parent child relation selectors_
		* _$('p > div').css("color","blue")_ - selects direct children div element of p
		* _$('a div').css("color","gree")_ - selects any descendant div element of a
		
		
* ### Events
	* 	_Fading elements_ - Fade objects in and out of visibility
		*   _$('selector').fadeIn(dur, easing)_ - Takes three paramaters: duration of effect in ms, name of easing function.
		*   _$('selector').fadeOut(dur, easing)_ - same parameters
		*   _$('selector').fadeToggle("slow")_ - Fades the objects based on the toggle parameter 
	
	* 	_Sliding elements_ - Slide objects up and down of visibility. Animates the height of the respective object
		*   _$('selector').slideIn(dur, easing)_ - Takes three parameters: duration of effect in ms, name of easing function.
		*   _$('selector').slideOut(dur, easing)_ - same parameters
		*   _$('selector').slideToggle("slow")_ - Slides the objects in and out of visibility. It will check the 'display' property of the element, if hidden will be restored to the type. Applies vice versa too. 
	
	*  _Animating elements_ - Custom animations can be executed
		* _$('selector').animate(property_change, duration, easing,complete);_ - Animates the element by performing property change with set duration and an easing function. **Complete** is a function that runs after the animation is complete.
		* _$('selector').stop()_ - Stops the animation affecting the selector. Other animations remain running in the queue if the first parameter is given as true.
		
* ### Getting and setting content 
	* _$('selector').text()_ - Textual representation of the inner content for all regular elements.
	* _$('selector').val()_ - Values for all form elements.
	* _$('selector').html()_ - Textual representation of the markup for all regular elements.
	* _$('selector').attr(attrname,val)_ - Sets the attrname of selector to val. Can also take in a map
	* _$('selector').addClass('class1').removeClass('class2')_ - Adds and removes associated classes to elements
	
* ### Adding and Deleting content
	* _$('selector').remove(elem)_ - This method will remove the selected elements. There is an optional elem parameter to filter the specified element. 
	* _$('selector').empty()_ - Empty the children of the elements defined by the selector.
	* _$('selector').append(elem)_ - Append the elem in the list of selected element. elem could be HTML string, DOM object or a JQuery Object
	* _$('selector').prepend(elem)_ - Prepend the elem in the list
	
	* _$('selector').before(elem)_ - Adds the element before each element in the selected set of elements. 
		* elem could be a Jquery object, DOM object or HTML String.
	* _$('selector').after(elem)_  -Adds the element after each element in the selected set of elements.
	* Similarly, _insertBefore_ and _insertAfter_ methods perform the same function. Only the order is switched.
	
	
* ### Event handling
	* Custom code can be attached to events that have been recorded on elements.This code is wrapped inside an event handler.
		The event handler is passed an event object parameter of the event that has triggered the handler.
	* _$(selector).bind(eventname, callback)_ - Binds the event handler denoted by callback to the specified element. When the event occurs targeting the specific element, the function is executed to process the event.
	 * NOTE: Deprecated in favor of the on() method in JQuery 3.1
	* _$(selector).unbind(eventname)_ - Removes all the event handlers corresponding to the event on element.
	
