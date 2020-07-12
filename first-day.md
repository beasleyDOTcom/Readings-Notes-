# responsive web design  
responsive web design is all about adapting to the trend of mobile first because almost everyone interacts with a phone, while some people may not interact with a desktop much at all.
So companies etc. all want to be able to reach everyone instead of some. 

## Mobile first
Currently the most popular technique lies within responsive web design, favoring design that dynamically adapts to different browser and device viewports, changing layout and content along the way. This solution has the benefits of being all three, responsive, adaptive, and mobile.

## flexible layouts
the flexible layout strategy tackles mobile first via flexible layouts like grid and flex.
then uses @media queries (which require you to write the syntax perfectly or will not work) to set seperate design layouts for each breakpoint (hopefully in between the screen sizes you want to target)
this method will target pixel ranges like 500 px, 700, 900, 1200 mobile larger mobile tablet desktop

## flexible media (pictures etc)
Unfortunately the max-width property doesn’t work well for all instances of media, specifically around iframes and embedded media. When it comes to third party websites, such as YouTube, who use iframes for embedded media this is a huge disappointment. Fortunately, there is a work around.

To get embedded media to be fully responsive, the embedded element needs to be absolutely positioned within a parent element. The parent element needs to have a width of 100% so that it may scale based on the width of the viewport. The parent element also needs to have a height of 0 to trigger the hasLayout mechanism within Internet Explorer.

Padding is then given to the bottom of the parent element, the value of which is set in the same aspect ratio of the video. This allows the height of the parent element to be proportionate to that of it’s width. Remember the responsive design formula from before? If a video has an aspect ratio of 16:9, 9 divided by 16 equals .5625, thus requiring a bottom padding of 56.25%. Padding on the bottom and not the top is specifically used to prevent Internet Explorer 5.5 from breaking, and treating the parent element as an absolutely positioned element.

# all about floats
This article is all about floats haha
It goes into detail about how float originated with print.
Imagine a newspaper add, or picture. They wanted the content (mainly text in newspaper context) to go all around the picture or add. Html does this buy taking it out of the flow of traffic and allows items and allows others to pass on the left or right.

escalator analogy is perfect for this on freecodecamp.

the other half of floats is using 
## clear 
clear says "oh ok enough of that float nonsense" and says "whatever rules you were living by I don't care about anymore" 
you can clear right, left , or both. 
this is a very important part of using floats.