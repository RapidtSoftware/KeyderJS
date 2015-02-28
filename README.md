KeyderJS
======

KeyderJS is a JavaScript event library.

Fast, Easy and Small
--------------------

With the minified version only 10kb KeyderJS is as fast as light, small as an electron and easy as apple pie.

Installation
============

KeyderJS installation is as simple as 123:

Using Bower
-----------

Do the following in your command line:

    bower install keyderjs

Or Adding the `keyder.js` script
-----------------------------

Add the KeyderJS script file to your head section in your HTML file. Example:

	<script src='path/to/keyder.min.js' type='text/javascript'></script>

Usage
=====

Keyder is used as following

	Keyder( element ).eventName( handler [, second_handler] )

The `second_handler` parameter is optional and only supported for the `hover` and `click` events.

The `second_handler` parameter for the click event is used instead of `mouseup` and for the hover event it is used instead of `mouseleave`. See more details in the [examples](#examples) 

The keydown and keyup events are a bit different and used like this:

	Keyder( element ).keydown( keycode/keyname, handler )

Examples
========

Example 1: a simple mousedown event
--

	Keyder( document.getElementById( "my_element" ) ).mousedown( function(){
		console.log( "Mousedown" );
	});
	
Example 2: a click event with two handlers
--

	Keyder( document.getElementById( "my_element" ) ).click( function(){
		console.log( "The mouse button was pressed" );
	}, function(){
		console.log( "The mouse button was released" );
	});
	
Example 3: a simple chained keydown/keyup event
--

	Keyder( document.getElementById( "my_element" ) ).keydown( "shift", function(){
		console.log( "The Shift key was pressed" );
	} ).keyup( "shift", function(){
		console.log( "The Shift key was released" );
	} );

Example 4: a simple handler for multiple events

	Keyder( document.getElementById( "my_element" ) ).on( "click mouseover", function(){
		console.log( "You did: " + e.currentEvent );
	} );

Advanced Features
=====

Prevent autorepeated keydown events
---

Sometimes when the user holds down a key it fires the event repeatedly. To fix this, add a third parameter to the keydown event and set it to `true`. Example:

	Keyder( document.getElementById( "my_element" ) ).keydown( "shift", function(){
		console.log( "The Shift key was pressed, but the event won't be fired repeatedly and the event handler won't be executed repeatedly when you hold down the Shift key!" );
	}, true );

See [this question](http://stackoverflow.com/questions/7686197/how-can-i-avoid-autorepeated-keydown-events-in-javascript) on Stackoverflow to see what I mean.

Get current key name
---

Sometimes when a user pressed a key you would want to get the keyname of the pressed key. That could be easily done by using `event.keyName`, almost like `event.keyCode`, but it gives the name of the pressed key and not the code. Example:

	Keyder( document.getElementById( "my_element" ) ).keydown( "any", function(event){
		console.log( "You pressed the " + event.keyName + "key." );
	} );

Note: if you want to get the last pressed and handled key you would use `Keyder().lastKey`
