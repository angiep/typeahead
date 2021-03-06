# Type Ahead #

A typeahead (or autocomplete) JavaScript widget with no framework dependencies.  The widget displays a list of matching keywords underneath the input field when the user begins typing into the field. 

The widget allows the developer to pass in either a list of keywords or a URL that provides a JSON response with the keywords that are then filtered by the user input.

## Required Files ##
* utilities.js
* typeahead.js
* typeahead.css


## Setup ##

### HTML Structure ###
```html
<div class='type-ahead'>
    <input id='test' type='text' />
</div>
```

Don't forget to include the css file! You can make modifications to the css as you see fit.

### Initializing ###
The typeahead widget can take either a list of strings to search through or take a source URL that returns a JSON response according to the current query.

Here is a setup example with just a simple list:
```javascript
var input = document.getElementById('test');
var ta = new TypeAhead(input, {list: ['cat', 'dog', 'cow', 'cattle']});
```

And a little bit more complicated setup with a source URL:
```javascript
var input = document.getElementById('test');
var ta = new TypeAhead(input, {
    source: '/api/example', 
    property: 'name',
    onSelect: function(item, data) {
        console.log(item);
    }
});
```

When a request is made to the source URL the query parameter 'query' is appended to the end of the URL with it's value being the current search term. Example: api/example?query=museum.

## Options ##
* list: an array of strings to check user input against, an alternative to making AJAX requests
* activeClass: the class to be added to a list item when it is selected (through arrows, hovering or clicking), default is 'highlight'
* source: source URL to check user input against, should return a JSON array
* property: if source is returning objects rather than strings, the property name that should be displayed within the list
* onSelect: a callback function to be called when the user clicks or hits enter on an item, the onSelect method is passed the DOM element and the data object corresponding to the item
* onHover: a callback function to be called when the user hovers over an item, the onHover method is passed the DOM element and the data object corresponding to the item
