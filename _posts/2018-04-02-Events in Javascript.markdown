---
layout: post
title:  "How to visualize Javascript events in the console"
date:   2018-04-02 17:14:47 +0100 
categories: Javascript
---

> I’ve always learned more about web design by dissecting examples in the wild rather than reading white papers

I got here a trivial example of a Javascript code. I was curious to see what exactly is contained in an event passed on from the Eventlistener in Javascript.
To do this I used a small trick. I inserted these two lines of code giving me out the value of the event parameter in 
different points of the execution. The variable I want to observe will be given the name "r" and I will print this out in the console.log

    var r = event;
    console.log(r);

So open the inspect element of your browser and go to Console. Insert those two lines at every place where you want to understand which value is being passed.

The code below is only showing a button: "start" which will be returning an alert, OK if the ALT taste is pressed at the time of the mouseclick.

    	...
        <title>How to visualize Javascript events in the console</title>
    <script>
    	//this is a standard entry
        window.addEventListener("load", setup); //we add an event listener to the window to know when the page is loaded 
        
         // when the window finished loading we start the function setup as called in the previous argument
        function setup() {
        
        //here we add an EventListener to the button with id "start".
        //this eventListener will listen to the "click" of the mouse and start the function launch  
        document.getElementById("start").addEventListener("click", launch);
        }

        /*All eventhandler give out an event-objekt as first parameter
        which contains all the informations about what is happened
        Really interesting is to realize what Is contained in this event parameter.
        To find out I inserted these two lines of code which define a var p = event 
        and print this variable to the console with a console.log(p)
        */
        function launch(event) { 
        		var r = event;
                console.log(r);
                var t = event.target;
                console.log(t);
                
            /* Here I give out an OK when the ALT key is pressed by the click in the button */
            if (event.altKey) {
                alert("OK");
                var p = event.altKey; //again I want to see what is the content of event.altKey..
                console.log(p); 	  //with this console log. Hint! it is a boolean! Here is "true"
            } else {
                var p = event.altKey;
                console.log(p);		  //And here the result will be "false"			
                alert("Not OK");		
            }
        }
        
        // this code will display a button with id "start"
    <body>
      ...     
        
        
The eventlistener could be as well launched with a mouseover:
    
    document.getElementById("start").addEventListener("mouseover", launch);      

From the eventListener 

    document.getElementById("start").addEventListener("mouseover", launch);

When the event is fired will be passed to the launch function, 
and this is how such an event object looks like:

![MouseEvent](/img/MouseEvent.png){:class="img-responsive"}

The target of my event remains the HTML button though, the event.target:

![target](/img/target.png){:class="img-responsive"}

The contents of the event.target will be:
    
    <button type="button" id="start">start</button>  
    
And the event.AltKey is a boolean, a click without pressing the alt-key will be false :

![eventAltKey](/img/eventAltKey.png){:class="img-responsive"}

otherwise the value will be true.

![eventAltKeyTrue](/img/eventAltKeyTrue.png){:class="img-responsive"}

Check my [codepen](https://codepen.io/multitudes/full/XEOZyR) for the example code.


        