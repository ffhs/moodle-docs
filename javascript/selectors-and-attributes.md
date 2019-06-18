# Selectors and Attributes

## Selectors

#### Find nearest element with selector

```javascript
// Assuming option is a menu button
var menuContainer = option.closest('.nav-buttons');
```

#### Find all child elements with a certain class

```javascript
var menuItems = menuContainer.find('.btn');
```

## Attributes

#### Get an attribute value

```javascript
var filter = option.attr('data-filter');
```

#### Set an attribute value

```javascript
option.attr('data-filter','xxx');
```

### Add and remove classes

```javascript
// On a single instance
option.addClass('active');
// On multiple instances
dropdownItems.removeClass('active');

```

