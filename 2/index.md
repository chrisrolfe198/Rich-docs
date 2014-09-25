# Rich
Rich was born from the trouble with finding a simple to configure lightweight rich text editor.
Many out there looked promising but forced you to follow certain patterns or conditions.
Rich gives you the freedom to handle things such as dependencies in your own way, this shouldn't be our decision.

Rich aims to offer some polyfilled functionality to IE with a long term aim of supporting IE9.
We are also looking at standardising the output of content editable throughout browsers.

If this sounds like the text editor you are after then lets get started.

## Install
To install you should download the dist file from the [github repo](https://github.com/christopherrolfe198/Rich) and then place it within your project.
You will then need to set up your configuration file.
The configuration file is simple to set up and is just a JSON object, you can see an example [here](https://raw.githubusercontent.com/christopherrolfe198/Rich/master/example/RichConfig.js).

### The config file
So the example config file does `Rich = window.Rich || {};` this is to check Rich is loaded.
In version 2 the configuration needs to be loaded after the main file, this is so you can extend the toolbar and make your own changes.

Once you've checked for Rich you then define configuration.

```
Rich.config = {
    toolbars : {
        default: ["bold", "italic"],
        nested: [["bold", "italic"], ["link"]]
    },
    classes: ["class-1", "class-2"],
    classGroup: ["foo"]
}
```

So toolbars are pretty straight forward, you can create as many toolbars as you like in the config and then add a data attribute on the textarea to let Rich know which to use.
You should always provide a default toolbar as when none is specified that is what Rich will look for.
The `classes` array lets you apply custom classes to all toolbar items.

You can use nest toolbar items 1 level to group them together, this can make for a slightly nicer user experience.
The `classGroup` array lets you specify classes for the group containers.
If you are using [Bootstrap](http://getbootstrap.com) you could add in the `btn-group` class here to make the buttons look connected.

Once you have defined the config you could add any further toolbar icon extensions or patches to contenteditable.

Once you've finished you then just need to call init on the editor with `window.Rich.editor.init();`.
