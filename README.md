# RobotStageControl
A universal liteweight web based interface to control the behavior of a Pepper robot.

## How to Use the Server

### A. Setup the Server

1. Open the Project in Choregraphe
2. Connect to your Pepper
3. Install the behavior on the robot
4. run the behavior / put it on autostart

* http://doc.aldebaran.com/2-5/software/choregraphe/panels/robot_applications.html


### B. Use the Server

1. open your favorite browser
2. open the address
   ```
   http://<robot.ip>:8000/test.html
   ```
3. enter some text in the box and press "say" or "animated say"
4. the robot now says the text and displays it on its chest


## History
Originally developed for the theater performance "Future Fortune" that involved a robot pepper.
Original code:
https://github.com/BerlinUnited/RoboTheater/tree/master/scenes_for_stage/RemoteStageControl


## Interactive Demo

The interactive demo allowws to manually switch between three intective modes of pepper `static`, `active` and `interactive`.

There are two ways to switch the modes:

### For Testing 

1. open your favorite browser
2. open the address
   ```
   http://<robot.ip>:8000/mode.html
   ```
3. clock buttons to switch modes

> [!WARNING]  
> Don't switch the modes too fast. Give pepper some time (~5s) so change the mode before switching to another.


### For Integration

The modes can also be switched by simply calling (triffering) the following corresponding url's:

```
http://<robot.ip>:8000/mode/static.html
http://<robot.ip>:8000/mode/active.html
http://<robot.ip>:8000/mode/interactive.html
```

This can be done from a static local website that does not require a server. For instance like this:


```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Hidden iframe URL Calls</title>
    <style>
        /* Hide the iframe */
        #hiddenFrame {
            display: none;
        }
    </style>
</head>
<body>
    <!-- Links -->
    <ul>
        <li><a href="#" onclick="callUrl('http://10.0.4.166:8000/mode/static.html'); return false;">Static</a></li>
        <li><a href="#" onclick="callUrl('http://10.0.4.166:8000/mode/active.html'); return false;">Active</a></li>
        <li><a href="#" onclick="callUrl('http://10.0.4.166:8000/mode/interactive.html'); return false;">Interactive</a></li>
    </ul>

    <!-- Hidden iframe -->
    <iframe id="hiddenFrame"></iframe>

    <script>
        function callUrl(url) {
            // Set the iframe's src to the target URL
            const iframe = document.getElementById('hiddenFrame');
            iframe.src = url;

            console.log(`URL called: ${url}`);
        }
    </script>
</body>
</html>
```

> [!WARNING]  
> Replace the robot url with your own.
