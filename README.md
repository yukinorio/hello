```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Dynamic iFrame</title>
    <script type="text/javascript">
        function dynamic_iframe(id, content, width, height, from, to) {
            document.getElementById(id).innerHTML = "<iframe width='" + width + "' height='" + height + "' frameborder='0' src='" + content + "?from=" + from + "&to=" + to + "'></iframe>";
        }
    </script>
</head>
<body>
    <div style="text-align:center;">
        <div id="container"></div>
        <br/>
        <a href="javascript:void(0)" onclick="dynamic_iframe('container', 'http://example.com/path/to/url', 640, 700, 'now-1h', 'now');">Show</a>
    </div>
</body>
</html>
```
