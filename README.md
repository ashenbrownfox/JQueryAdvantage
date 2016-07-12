# JQueryAdvantage
## How to Contribute

1. Fork it!
2. Commit.
3. Push.
5. Submit a pull request :)

##What is JQuery?
jQuery is a lightweight JavaScript library that simplifies programming with JavaScript.

According to jQuery.com
jQuery is a fast, small, and feature-rich JavaScript library. It makes things like HTML document traversal and manipulation, event handling, animation, and Ajax much simpler with an easy-to-use API that works across a multitude of browsers. With a combination of versatility and extensibility, jQuery has changed the way that millions of people write JavaScript.

##Advantages of using jQuery over raw JavaScript

The use of JQuery has several benefits over using the raw javascript.
* 1. jQuery is cross-browser
* 2. jQuery is a lot more easy to use than raw javascript
* 3. jQuery is extensible
* 4. jQuery simplifies and has rich AJAX support
* 5. jQuery has large development community and many plugins. Example autocomplete textbox plugin.
* 6. Excellent documentation


##How to use jQuery in a web application

Download the jQuery file from jQuery.com and reference it in your application just like any other JavaScript file.

##What is the difference between jQuery 1.x and 2.x
If you want to support IE6/7/8, then use jQuery 1.x where as if you don't have the need to support IE6/7/8 then use jQuery 2.x. jQuery 2.x is smaller in size than jQuery 1.x.

Example : Adding a click event handler for a button control using raw JavaScript. addEventListener() method is not supported in IE < 9. 

```RegularJavascript.js
<script type="text/javascript">
    window.onload = function ()
    {
        // For all modern browsers
        if (document.addEventListener)
        {
            document.getElementById('button1')
                    .addEventListener('click', clickHandler, false);
        }
        else
        // For Internet Explorer < 9
        {
            document.getElementById('button1')
                    .attachEvent('onclick', clickHandler);
        }

        function clickHandler()
        {
            alert('jQuery Tutorial');
        }
    };
</script>
<input type="button" value="Click Me" id="button1" />
```

Example : Adding a click event handler for a button control using jQuery. With jQuery we have less code to achieve the same thing.We don't have to worry about cross-browser issues, as all this is taken care by jQuery.


```Jquery.js
<script type="text/javascript">
    $('document').ready(function () {
        $('#button1').click(function () {
            alert('jQuery Tutorial');
        });
    });
</script>
<input type="button" value="Click Me" id="button1" />
```

Things to remember :
*1. ready() function ensures that the DOM is fully loaded.
*2. $ is a shortcut for jQuery.
*3. All three of the following syntaxes are equivalent:
```
$( document ).ready( handler )
$().ready( handler ) (this is not recommended)
$( handler ) 
```

##What is Document.ready Function?
$(document).ready is a jQuery event. It fires as soon as the DOM is loaded and ready to be manipulated by script. This is the earliest point in the page load process where the script can safely access elements in the page's html DOM. This event is fired before all the images, css etc.. are fully loaded.

The following example works, because the jquery code that adds the event handler to the button is inside the ready() function, which ensures that the DOM is fully loaded before this piece of code is executed, so the JavaScript can find the button element in the DOM and adds the click event handler.

```
<html>
<head>
    <title></title>
    <script src="Scripts/jquery-1.11.2.js"></script>
    <script type="text/javascript">
        $(document).ready(function () {
            $('#button1').click(function () {
                alert('jQuery Tuorial');
            });
        });
    </script>
</head>
<body>
    <input id="button1" type="button" value="Click Me" />
</body>
</html>
```

In the following example, we have removed the ready() method. When you click the button now, you don't get the alert. This is because the jQuery code is present before the button element, so by the time the jQuery code is executed the button element is not loaded into DOM. 

```
<html>
<head>
    <title></title>
    <script src="Scripts/jquery-1.11.2.js"></script>
    <script type="text/javascript">
        $('#button1').click(function () {
            alert('jQuery Tuorial');
        });
    </script>
</head>
<body>
    <input id="button1" type="button" value="Click Me" />
</body>
</html>
```

To make this example work, you have 2 options

1. Place your jQuery code in $(document).ready function OR

2. Place your script at the bottom of the page just before the closing </body> element

$(window).load event fires when the DOM and all the content on the page (images, css etc) is fully loaded. Since the window load event waits for images, css etc to be fully loaded, this event fires after ready event. 

The following example proves the above point. When you run the page with the following script, notice that the alert in ready function is displayed before the alert in load function.

```
<script type="text/javascript">
    $(window).load(function () {
        alert('Window loaded');
    });

    $(document).ready(function () {
        alert('DOM Loaded and ready');
    });
</script>
```
##Difference between Window Load and Document Ready

In most cases, the script can be run as soon as the DOM hierarchy has been fully constructed. So ready() is usually the best place to write your JavaScript code.

However, in your application there could be scenarios where you should be using $(window).load over $(document).ready. For example, let's say we want to display the actual image dimensions (Height and Width). To get the actual image dimensions, we will have to wait until the image is fully loded, so the jQuery code to get the height and width should be in $(window).load event.

Example : If you use $(document).ready() instead of $(window).load() the height and width will be displayed as 0. 

```
<html>
<head>
    <title></title>
    <script src="Scripts/jquery-1.11.2.js"></script>
    <script type="text/javascript">
        $(window).load(function () {
            $('#div1').html("Height = " + $('#Image1').height()
                + "<br/>" + "Width = " + $('#Image1').width())
        });
    </script>
</head>
<body>
    <div id="div1"></div>
    <img src="Chrysanthemum.jpg" id="Image1" />
</body>
</html>
```
###MOre to Come