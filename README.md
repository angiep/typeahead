JavaScript Widgets
=======

# Type Ahead #

## Required Files ##
* utilities.js
* typeahead.js
* typeahead.css


## Setup ##

### HTML Structure ###
```html
<div class="typeAhead">
    <input id="test" type="text" />
</div>
```

Don't forget to include the css file! You can make modifications to the css as you see fit.

### Initializing ###
The typeahead widget can take either a list of strings to search through or take a source URL that returns a JSON response according to the current query.

Here is a setup example with just a simple list:
```javascript
var input = document.getElementById("test");
var ta = new TypeAhead(input, {list: ["cat", "dog", "cow", "cattle"]});
```

And a little bit more complicated setup with a source URL:
```javascript
var input = document.getElementById("test");
var ta = new TypeAhead(input, {
    source: '/api/example', 
    property: 'name',
    onSelect: function(item, data) {
        console.log(item);
    }
});
```

## Options
* list: an array of strings to check user input against, an alternative to making AJAX requests
* activeClass: the class to be added to a list item when it is selected (through arrows, hovering or clicking), default is 'highlight'
* source: source URL to check user input against, should return a JSON array
* property: if source is returning objects rather than strings, the property name that should be displayed within the list
* onSelect: a callback function to be called when the user clicks or hits enter on an item, the onSelect method is passed the DOM element and the data object corresponding to the item
* onHover: a callback function to be called when the user hovers over an item, the onHover method is passed the DOM element and the data object corresponding to the item

# Carousel
