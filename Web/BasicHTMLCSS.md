
## [Shay Howe's HTML & CSS Guide](http://learn.shayhowe.com/html-css/building-your-first-web-page/) Notes!

* ### What is HTML & CSS?
	* **HTML** - Stands for Hypertext Markup Language, it gives content structure and meaning by defining that content as elements like h2.
	* **CSS** - Stands for Cascading Style Sheets, a presentations language created to style the appearance of content using for example fonts or color.
	  
* ### Syntax of HTML & CSS
	* Elements(<a>), Tags(<a></a>), Attributes(<a href="">).
	* CSS - Selectors, Properties and Values.
		*     p { selector: value;}
		
	* _<link rel="stylesheet" href="main.css">_ - Links the stylesheet file to the html document. 'rel' specifies the relationship of the resource.
	
* ### CSS Resets
	* Each web browser has its own default styles for different elements.
	* To ensure cross **browser compatibility**, resets have been used.
	* CSS resets takes every element with a predefined style and sets common style for the browser. Generally resets clear all margins,paddings,fonts and additional styles.
	* Eric meyer's resets are used as a hard reset. One more popular library used is Normalize.css, that sets common styles for various elements.
	
	
* ### Basics of HTML
	* Semantics in HTML gives the content meaning and structure. It describes the value of content on the page.
	* Block & Inline elements 
		* Block elements : Begin on a new line and occupy the given width. Nestable . Can wrap inline-level elements.
		* Inline level elements : Does not begin on a new line. Falls into the flow of document. Has got a specific width. can wrap inline-level elements but not block-level ones.
		
	* Semantic block elements in HTML5 : <header>, <footer>, <nav>, <aside>, <section>, <article>. Provides intention to elements. 
		* nav - major navigational links bar.
		* article - A content group that is independent and self contained that is relevant even if placed somewhere else.
		* section - A block that is a thematic grouping of content. Used to break up content page.
		* aside - It holds content that is tangentially related to the content surrounding it.
		
	* _<a>_ elements called anchor elements can wrap block level and inline-level elements too in HTML5.
	* While clicking links, we can define the context in which the resource will be opened by defining the 'target' attribute.
		* _<a target="_blank"> </a>_ opens the link in a new window.
	
* ### Basics of CSS
	* Three main types of selectors : type, class and ID selectors.
	* CSS can be used to apply styles over different elements and layer styles with multiple classes.
	
	* **Cascading Property**: The rule sets cascade from top to bottom in the stylesheet.
		* A style declaration styling a particular element that comes after another declaration styling the same element (selector) will be applied. 
		* Similarly, the same property declaration that come afterwards overrules the previous one. Styles are overwritten by the most recent one.
		
	* **Specificity weight** : Every selector in CSS has a specificity weight.
				* Specificity point calculation - <ID selector no. - Class selector no. - Type selector no.>
				* ID selector weight > Class selector weight > Type selector weight.
				* Ex: p a.main {} -> 0-1-2 while #top .main {} -> 1-1-0 so #top.main will have higher specificity weight.
				* Higher the specificity weight, more weightage give to the selector when styling conflicts occur.
				
	* **Combining selectors** : The selectors are read from right to left. The rightmost selector is the _key selector_, which are the elements where the styles will be directly applied.
		* _p #useless {..}_ - the elements with id useless whose atleast one ancestor is a paragraph will be selected.
		* **Spaces matter!** - If there is no space between two selectors, the element is selected with both the class/id/types depending on the kind of selector.
			* _p#useless {..}_ - paragraph element with id useless is selected.
		
		
	* ## CSS Property values
		* **Colors** - keywords, Hexadecimal values, RGB, HSL with transparency /alpha channel(RGBa, HSLa).
		* **Lengths** :
			* **Absolute lengths**- Pixels are fixed to a phyical measurement, but vary across low density and high density vieweing devices. 96 pixels make an inch.
			* **Relative lengths**- % percentage of parent element property. em is the value relative to the current font size of the element or one of the set font sizes of the ancestor elements.
			* Relative lengths provide flexibility.	


* ### Box Model
	* How are elements displayed?
		* We can set the way elements are displayed using the _display_ property.
		* Three common values of display: block, inline, and inline-block.
		* _display : none;_ - hide the element and render its children hidden too.
		* _display : inline-block;_ - An element is set as an inline-block element. It an inline element that behaves like a block element.
			* all _4 directions of margin and padding can be set and width and height_ can be specified just like a block.
			* It will **not** force a line break. Elements will surround it like an inline element.
		* Comparison of properties of inline-block and inline:
			* ##inline - only margin-left, margin-right, padding-left, padding-right. You can set top / bottom of padding, but it will bleed into the surrounding element without affecting them.
			* ##inline-block - width, height, margin, padding - Like a block element.
			
	* Block level elements have a default width of 100%. inline and inline-block elements expand and contract horizontally to accomodate the content.
	    Height is determined by the content of the block.
	* _border: width type color;_ -	common styles of border are double,solid,dashed,dotted and none.
		* _border-radius: 5px_ - makes the border rounded. 
	
	* The box model can be changed by setting the _box-sizing_ property
		* _content-box_ - The default box model where the padding and margin is additive.
		* _padding-box_ - The padding is included in the width and height of box. Margin is additive.
		* _margin-box_ - The margin and padding is included in the width and height of box. Actual width is same as the specified width at all times.
    * The above property may require vendor-specific prefixes for support on newer versions of browsers.
	
* ### Positioning Content in CSS
	* To layout elements and position them, three ways can be used: float elements, inline-block method and unique positioning.
		* ## Floating - Applying the float property will shift the element out of the normal flow of the document. It will make the surrounding element wrap over it.
			* _float: left,right,none_ - Left float will shift the element to the left edge of the containing box or till the border of another floated element.
				Similarly, right float will shift the element to the right edge of the containing block or the edge of another floating element.
			* The width of the element needs to be set and margin so that there is space between the floats.
			* Multiple column layouts can be constructed in this manner.
		* ## Clearing elements
			* Float element was intended to let content flow around images. However, there could be problems where occasionally the proper styles wouldn't render.
				Even the gutter between the float elements could be occupied by the unwanted content.
				To fix such issues, clearing and containing floats are essential to return the page to its normal flow.
			* _clear: left, right, both;_ - Clear the element _after the float group_ from wrapping around floating elements. 
				* Value left will clear left float elements, similarly for right and both kinds of elements too.
			
		* ## Containing float elements
			* Outcome of both are same, but containing the elements will ensure the styles are rendered properly.
			* The float elements need to be contained in a special block. We set the ::before and ::after pseduo-elements as a display of table.
			* _ .group::after { clear: both;}_ - The dynamic pseudo-element will clear the previous float group.
			* _ .group {clear: both; *zoom: 1}_ - Similarly, this will clear any such float elements before this.
				* _zoom_ is a property used as a hack in old versions of IE. Not to be used in production code.
			* This method is called the 'clearfix'.
		* ## Inline Block Method
			* By setting display to boxes in a row to inline-block, we can design layouts. 
			* The properties need to be set are width,height and margin to ensure space between columns.
			* But the last inline block wraps into the new line because of ensuing space between those boxes in the line.
			* To fix it, remove the space between opening tag of the box and closing tag of previous floated box. Comments an be added too between the blocks.
		* Newer methods to look out for - flexbox and grid
		
		
		* ## Unique Positioning - Elements need to be precisely positioned in many cases.
			* Determining _how_ it is positioned is defined by the position property.
			* Position values can be static, relative, absolute and fixed.
			* _Static_ is the default positioning context. A list of div's will be a single column layout, stacking on top of one another.
			* _Relative_ means the element original position is preserved and the other elements flow normally. Space is left for the element and box offset properties
				can be modified with respect to that position.
			* _Absolute_ positioning would completely change the element's context outside its normal flow. 
				Its original position is not preserved. It can be positioned anywhere in the document with respect to the **closest relatively positioned ancestor**. 
					If no such element exists, then it is positioned with respect to the body element.
			* The exact positioned elements are specified using top, bottom, left, right properties. They take pixels, % too.
			* _Fixed_ positioning places the element at one point which is fixed with respect to the viewport. It will remain in the place even after scrolling. 
	
* ### Typography
	* Difference between typography and fonts: Typography is what we see, the artistic impression of how text look, feels and reads.
										Fonts is a file that contains a typeface.
	* Font-based properties - to edit the look and feel of text on a page.
		* _font-family_ - declare which font will be used to display text.
		* _font-size_ - Set the size of text using common length values.
		* _font-style_ - Change text to italic, oblique and inherit.
		* _font-variant_ - Text needs to be set in small-caps too. possible values are normal,small-caps.
		* _font-weight_ - This property can be changed to a specific weight. Can be set to a keyword that includes normal, bold, bolder, light, lighter. 
				The numeric values can be 100 to 900.
		* _line-height_ - Distance between twon lines of text is declared using this property. Best practise of legibility is to set the line-height to 1.5 times the font-size.
		* Font shorthand property - style variant weight size/line-height family.
	* _Pseudo-classes_ - They are keywords that may be added to end of selectors to style an element when it's in a unique state. Eg. :hover
	
	* Text properties - We can align, indent, decorate, transform and space text.
		* _text-align: left, right, center, justify, none_
		* _text-decoration: none, underline, overline, line-through, inherit;_
		* _text-indent: value px;_ - indents the first line value pixels in. Negative values are allowed.
		* _text-transform: capitalize, uppercase, lowercase;_ - It will change the text inline without the need for an alternate typeface.
		* _text-shadow: <horizontal-offset> <vertical-offset> <blur-radius> <color>;_ - Generate a shadow behind the text with values as given. Multiple shadows can be chained to the same element by separating them with a comma.
		* _letter-spacing: 1px_ - positive value will push them apart. Negative will pull them closer.
		* _word-spacing: 2px_ - Spaces between words.
		
	* Embed font-face from the internet using the @font-face at rule.
	
	* Include citation and quotes:
		* <cite> - Used to reference a creative work, author or resource.
		* <q> - Used for short, inline quotations.
		* <blockquote> - Used for longer external quotations.
	
* ### Setting Background & Gradients
		* The way to contribute appearance to a website. They can be a solid color, image, gradient, or a combination of these.
		* _background-image : url(bg.png)_ - Sets the backgroun-image to the url. Could be a local file ot a file in the www.
		* _background-color : #hexval_ - The background-color can be set to hexadecimal value.
		* _background-repeat : repeat-x, repeat-y, no-repeat_ - Specify the direction in which the background image is repeated or not repeated at all.
		* _background-position : <horizontal-offset> <vertical-offset>;_ - Shifts the position of the image relative to the top left corner.
		* _background : <color> <image> <position> <repeat>_ - shorthand version
		
	* ## Background gradients
		* _Linear gradients_ - Developers can generate gradients easily using the CSS3 gradient functions.
			*_background-color: linear-gradient(<direction>, <start-color>, <end-color>)_ - An angle can be specified as direction. String values can be used to point to right bottom, right top, left bottom, left top.
			* Multiple colors can be specified as color stops and stop points specified that will transition from that start color to end color
			* Remember, if the the image is not a square, the gradient will not proceed directly from one corner to another. These rough corners are called "magic corners"
		* _Radial gradients_ - A gradient that works from inside to the outside of the screen. First color will sit in the absolute center of the element, and will transition to the outer corners.
		* ex: _radial-gradient(#ffff33, #542fe3);
		* Multiple color stops can be declared so that browser will transition through all of them.
		* ex: _linear-gradient(to left bottom, color1, color2 45%, color3 60%, color4 )_ - by default first color is at 0% and last color is at 100%.
		
		* Multiple background images can be displayed for the same element by separating background properties with a comma.
		
	* ## CSS3 Background properties
		* _background-size : <width> <height>;_ - Can specify the width and height of the image in terms of the element box.
			* Special values
				* _cover_ - Image will be resized such that the smaller dimension (width or height) will stretch or shrink to cover the whole box. Aspect ratio is preserved.
					Image can be _cropped_ though.
				* _contain_ - Image will be resized such that the larger dimension will fit inside the element. Aspect ratio is preserved as above. 
				* Note that the image can seem distorted so take care in the production environment.
				
		* _background-clip : border-box, padding-box, content-box;_ 
			* _border-box_ - Default value. If a border specified, background is displayed under the border.
			* _padding-box_ - Background image is displayed under the padding and is clipped beyond that in the border.
			* _content-box_ - Background image is displayed under the content and is clipped beyond that in the padding.
		* _background-origin : border-box, padding-box, content-box;_
			* _border-box_ - Image starts from border of element.
			* _padding-box_ - Image starts from directly **within** the border. Default value.
			* _content-box_ - Image is positioned from within the padding.
			
* ### Displaying Lists
	* Lists are ubiquitous in websites. There are three different types of lists unordered, ordered & description.
	 We can mark the list item abandoned.
	 * ## Unordered Lists - List items whose order does not matter. Marked by <li> block level element.
	 * ## Ordered Lists - Items are in a list and order matters. <ol> is used as the main element.
		* we can set _start_ attribute to make the list start from a different number.
		* _value_ attribute can help initiate a different numbering from the applied li element.
	 * ## Description Lists - Used to outline multiple items and their descriptions like a glossary.
		* Creating a description list is accomplished using a block level element called <dl>
		* A description term is <dt> is followed by a description contained by <dd>.
		* Maintaining order is important. Multiple descriptions can be there for one description term.
		* <dd> has a left margin set. Both elements have vertical margin.
	* ## List style item marker
		* _list-style-type: none,disc,square,upper-roman, decimal,georgian_ - It will set the content of the list item marker to be specified item.
		* _list-style-position: inside, outside_ - It affects whether a list item line wraps into new line. Outside is a defaul value while in inside the line goes into a new line.
	* ## Horizontally arrange lists
		* **Inline-block / Inline** - Change the display property of list item to inline-block or inline. Modify margin and padding properties.
		* **Float elements to left** - If the list item marker needs to be retained, then we can float the <li> elements to the left.
	  
* ### Adding Media
	* To add images, we add the <img> element. It is a self-containing image.
		* _src_ attribute and _alt_ attributes are added to make it work. _src_ attribute defines the source of image that will be displayed. _alt_ is the alternate text.
		* Set width and height of given images using _width_ and _height_ properties.
		* Positioning images : The images can be positioned in inline, inline-block and block.
			* _float_ property could be used to float the images and let text wrap around it.
			
			
	* _ <audio>_ - Audio files can be added to the webpage using this HTML5 tag. Various attributes need to be specified.
		* _src_ attribute specifies the audio file to be loaded.
		* _autoplay_ - Audio will start playing as soon as the webpage is loaded.
		* _controls_ - Shows up the controls of the audio including the play/pause button,seek and volume.
		* _preload: none,auto,metadata_ - auto is the default value where the audio is loaded automatically. None does the opposite. Metadata will load the details of the audio like playtime etc.
		* _loops_ - Audio will loop.
		
		* Most popular audio formats are ogg, mp3, wav. Fallbacks are prudent if the browser cannot support a particular file format.
			* To support multiple fallbacks, audio files can be specified in multiple _<source>_ elements. Specify the src and type attributes for the sound samples defined.
		
	* _<video>_ -  Video files can be added to the webpage. The attributes are same as **audio tag**.
		* Width and height is specified to speed up rendering of webpage and reduce bandwidth.
		* _poster_ attribute - Specifies an image to be shown before the video is played.
	* Inline Frames - Embed other webpages inside the main webpage.
		* _<iframe src="google.com">_ - Link could be an absolute URL or relative URL. Any such page can be referenced.
			* The styles on the current page doesn't apply on the iframe.
			* Default styles on iframe are frameborder, height and width.
	* Figures & Figure Captions
		* Figures is used to identify and wrap self-contained content, in the form of media. It surrounds images, audio clips, videos etc.
			More than one item of content can be shown in one figure. These items should be related with each other.
		* _<figure>_ - Semantically identifies such figures.
		* _<figcaption>_ - This caption can be added anywhere in the figure element. Before or after media. 
			Only **one** caption is permitted.

* ### Building Forms
	* Forms are a way to capture content and process requests.
	* To initialize a form,  we'll add a form element that identifies where the page control elements appear.
	* The element <form> has attribute _action_ and _method_.
		* It will wrap all elements in the form.
	* _<input type="text" name="company">_ - It is used to obtain text from users. It is self-contained.
		* HTML5 has introduced new input type values _color_, _date_, _email_, _range_.
	* _<textarea name="comment">_ - Just like an input which span multiple lines.
	* Multiple Choice Inputs & Menus
			* _Radio buttons_ - <input type="radio" name="day" value="Friday" > <input type="radio" name="day" value="Saturday" > 
			* _Checkboxes_ - <input type="checkbox" name="day" value="Sat">
			* Apply checked attribute to keep it checked initially.
			* _Drop down list_ - Offers a way to provide long list of options.
			* _<select name="n" multiple>_ element wraps all the menu options.
			* _<option value="val"> _ are the options that are wrapped.
			* When submitting the form data, the name/value pairs are sent.
	* Form buttons
		* After a user inputs the requested information, button allows the user to put that information into action.
		* _Submit input_ - <input type="submit" name="submit" value="send">
		* _Submit button_ - Same as input, just has an opening and closing tag. Text can be put in a button.
	* Other cases 
		* _Hidden input_ - A way to pass data to the server without displaying it to users. Hidden inputs are typically used for tracking codes, keys or other information that is sent.
		* _File upload_ - <input type="file" name="file> 
	* Organizing form elements
		* Labels, fieldsets and legends.
			* Labels provide caption or heading for form controls, tying them to the input.
			* _<label for="id"> text </label>_ - Label for related form control.
			* Fieldset group form controls and labels into organized sections  like a section element.
			* They are a block-level element that wrap related elements in it and have a default border around it.
			* Used within a <form> box.
			* Legend provides the caption or heading for the <fieldset> element. Wraps text describing the form control. 
		* Disabled attribute - applying it will disable the form control from input. It would not be sent for processing.
		* Placeholder attribute - to give a hint to textarea and input element of what to enter. Will dissappear once the control is clicked in.
		* Required attribute - enforces the given input element to be compulsory. if the form control does not have a value, an error message is displayed.
			* validation also occurs specific to a control's type.


* ### Building Tables
	* Use <table> to initialise the element on the page.
	* <tr> table row may be added using this element
	* <td> Data cells are added to this table 
	* <th> is like <td> except it has semantic value as a table header
		* the _scope_ attribute immensely helps screen readers and assistive technologies.
	*  <caption>, <thead>, <tbody>, and <tfoot>
	* Two properties for tables border-collapse, border-spacing.
	
	
	* Align text vertically in inline or table-cell elements using _vertical-align_ property. We set it to top, bottom, middle 
	*
