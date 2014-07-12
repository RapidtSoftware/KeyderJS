KeyderJS
======

KeyderJS is a JavaScript event library.

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

Advanced Features
=====

Prevent Autorepeated Keydown
---

Sometimes when the user holds down a key it fires the event repeatedly. To fix this, add a third parameter to the keydown event and set it to `true`. Example:

	Keyder( document.getElementById( "my_element" ) ).keydown( "shift", function(){
		console.log( "The Shift key was pressed, but the event won't be fired repeatedly and the event handler won't be executed repeatedly when you hold down the Shift key!" );
	}, true );
