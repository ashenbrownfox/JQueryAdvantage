
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

## What are jQuery selectors

One of the most important concept in jQuery is selectors. jQuery selectors allow you to select and manipulate HTML elements. 

Different selectors in jQuery

jQuery selectors allow you to select html elements in the DOM by

1. Element ID
2. Element Tag Name
3. Element Class Name
4. Element attribute
5. Element Attribute values and many more 

Id selector in jquery
To find an HTML element by ID, use the jQuery #id selector 

Example : The following example finds button with ID button1 and attaches the click event handler.
```
<html>
<head>
    <title></title>
    <script src="jquery-1.11.2.js"></script>
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

Changes the background colour of the button to yellow
$(document).ready(function () {
    $('#button1').css('background-color', 'yellow');
});
```

###Important points to remember about jQuery #id selector 

1. jQuery #id selector uses the JavaScript document.getElementById() function 

2. jQuery #id selector is the most efficient among all jQuery selectors. If you know the id of an element that you want to find, then always use the #id selector. 

3. HTML element IDs must be unique on the page. jQuery #id selector returns only the first element, if you have 2 or more elements with the same ID.

```
<html>
<head>
    <title></title>
    <script src="jquery-1.11.2.js"></script>
    <script type="text/javascript">
        $(document).ready(function () {
            $('#button1').css('background-Color', 'yellow');
        });
    </script>
</head>
<body>
    <input id="button1" type="button" value="Click Me" />
    <input id="button1" type="button" value="Click Button" />
</body>
</html>
```

4. JavaScript's document.getElementById() function throws an error if the element with the given id is not found, where as jQuery #id selector will not throw an error. To check if an element is returned by the #id selector use length property. 

```
<html>
<head>
    <title></title>
    <script src="jquery-1.11.2.js"></script>
    <script type="text/javascript">
        $(document).ready(function () {
            if ($('#button1').length > 0) {
                alert('Element found')
            }
            else {
                alert('Element not found')
            }
        });
    </script>
</head>
<body>
    <input id="button1" type="button" value="Click Me" />
</body>
</html>
```

5. JavaScript's document.getElementById() and jQuery(#id) selector are not the same. document.getElementById() returns a raw DOM object where as jQuery('#id') selector returns a jQuery object that wraps the DOM object and provides jQuery methods. This is the reason you are able to call jQuery methods like css(), click() on the object returned by jQuery. To get the underlying DOM object from a jQuery object write $('#id')[0]

6. document.getElementById() is faster than jQuery('#id') selector. Use document.getElementById() over jQuery('#id') selector unless you need the extra functionality provided by the jQuery object. 


##Jquery Element Seletor

Syntax : $(element)

$('td') // Selects all td elements
$('div a') // Select all anchor elements that are descendants of div element
$('div, span, a') // Selects all div, span and anchor elements

Alerts the total count of td elements on the page
```
<html>
<head>
    <title></title>
    <script src="jquery-1.11.2.js"></script>
    <script type="text/javascript">
        $(document).ready(function () {
            alert($('td').length);
        });
    </script>
</head>
<body>
    <table style="border:1px solid black; border-collapse:collapse">
        <tr>
            <td>C#</td>
            <td>ASP.NET</td>
            <td>SQL Server</td>
        </tr>
        <tr>
            <td>ADO.NET</td>
            <td>jQuery</td>
            <td>JavaScript</td>
        </tr>
        <tr>
            <td>AJAX</td>
            <td>CSS</td>
            <td>HTML</td>
        </tr>
        <tr>
            <td>VB</td>
            <td>Dot NET</td>
            <td>Visual C++</td>
        </tr>
        <tr>
            <td>Oracle</td>
            <td>Java</td>
            <td>J2EE</td>
        </tr>
    </table>
    <br /><br />
    <div>
        DIV 1
        <br />
        <a href="http://pragimtech.com">PragimTech</a>
    </div>
    <br /><br />
    <a href="http://google.com">Google</a>
    <br /><br />
    <div>DIV 2</div>
    <br /><br />
    <span>SPAN 1</span>
    <br /><br />
    <div>DIV 3</div>
</body>
</html>
```

Selects all the tr elements on the page and changes their background colour to red
```
<script type="text/javascript">
    $(document).ready(function () {
        $('tr').css('background-Color', 'red');
    });
</script>

Alerts the HTML content of the table
<script type="text/javascript">
    $(document).ready(function () {
        alert($('table').html());
    });
</script>

Alerts the HTML content of each table row
<script type="text/javascript">
    $(document).ready(function () {
        $('table tr').each(function () {
            alert($(this).html());
        });
    });
</script>
```

Select and changes the background colour of all the div, span and anchor elements
```
<script type="text/javascript">
    $(document).ready(function () {
        $('div, span, a').css('background-Color', 'yellow');
    });
</script>
```
Select all anchor elements that are descendants of div element
```
<html>
<head>
    <title></title>
    <script src="jquery-1.11.2.js"></script>
    <script type="text/javascript">
        $(document).ready(function () {
            $('div a').css('background-Color', 'yellow');
        });
    </script>
</head>
<body>
    <div>
        <a href="http://pragimtech.com">PragimTech</a>
    </div>
    <br />
    <a href="http://microsoft.com">Microsoft</a>
</body>
</html>
```
Changes the background color of even rows to gray and odd rows to yellow on both the tables.
```
<html>
<head>
    <title></title>
    <script src="jquery-1.11.2.js"></script>
    <script type="text/javascript">
        $(document).ready(function () {
            $('tr:even').css('background-Color', 'gray');
            $('tr:odd').css('background-Color', 'yellow');
        });
    </script>
</head>
<body>
    <table id="table1" border="1">
        <tr>
            <td>C#</td>
            <td>ASP.NET</td>
            <td>SQL Server</td>
        </tr>
        <tr>
            <td>ADO.NET</td>
            <td>jQuery</td>
            <td>JavaScript</td>
        </tr>
        <tr>
            <td>AJAX</td>
            <td>CSS</td>
            <td>HTML</td>
        </tr>
        <tr>
            <td>VB</td>
            <td>Dot NET</td>
            <td>Visual C++</td>
        </tr>
        <tr>
            <td>Oracle</td>
            <td>Java</td>
            <td>J2EE</td>
        </tr>
    </table>
    <br />
    <table id="table2" border="1">
        <tr>
            <td>Mark</td>
            <td>Mary</td>
            <td>Mike</td>
        </tr>
        <tr>
            <td>John</td>
            <td>Jade</td>
            <td>Joy</td>
        </tr>
        <tr>
            <td>Rob</td>
            <td>Roy</td>
            <td>Rachel</td>
        </tr>
        <tr>
            <td>Sam</td>
            <td>Sara</td>
            <td>Smith</td>
        </tr>
        <tr>
            <td>Todd</td>
            <td>Tom</td>
            <td>Theo</td>
        </tr>
    </table>
</body>
</html>
```
To change the background color of even rows to gray and odd rows to yellow just for one of the table, use #id selector along with element selector.
```
<script type="text/javascript">
    $(document).ready(function () {
        $('#table1 tr:even').css('background-Color', 'gray');
        $('#table1 tr:odd').css('background-Color', 'yellow');
    });
</script>
```