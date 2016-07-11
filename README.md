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