# Toolbar
The toolbar is an important part of the editor and you add new items to it as you need it by calling the `extend` function.

So want to add a set of smileys? It's reasonably easy.

```
// Rich.toolbar.extend(name, callback, classes, text, input);

Rich.toolbar.extend('smiley', function() {
    Rich.contenteditable.call('insertHTML', ' :)');
}, ["fa-smile-o"], ":)", false);
```

So the first parameter is what you reference in the toolbar when including it.
The second parameter which usually will call a content editable action on Rich, calling `document.execCommand` manually will mean any polyfills aren't implemented for IE.
The third parameter is the classes applied to the toolbar item.
The fourth is the icon title or in the case of an empty array being passed to the classes the fallback text.
The fifth is whether you are wanting the user to pass some kind of input in, if you do then it is passed through to the callback as a parameter.
