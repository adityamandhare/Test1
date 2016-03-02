## Problem
It is often observed that a web page contains images and references to these images are made at multiple places across the page. In this case the reader has to scroll back and forth through the web page every time he has to refer to an image. This is highly inconvenient. Due to this, the user faces many problems like loss of continuity, comprehension and context. It also puts stress on user’s vision, due to which the user cannot concentrate fully. It also consumes considerable amount of user time. This results in spoiling the user’s reading experience. [aditya](http://adityamandhare.blogspot.com/)

## Solutions
**Solution 1: Displaying image in a pop-up on hovering over its reference**
In this solution first we created a regular expression which searches image references in the web page. A Map has been created which stores key-value pairs wherein the key equals the “alt” argument of the <img/> tag and the value equals the corresponding “src” argument of the <img/> tag. A string replacement method has been created. This method has the task of converting each of the image references into a hyperlink. The hyperlink contains an on-hover functionality which enables the referenced image to pop-up, when the user hovers over it.  

**Solution 2: Display thumbnails of all images in the page in a sidebar**
In this solution, we first scan the page to search for images contained in it. These images are then extracted and converted into thumbnails. A sidebar has been created which holds these thumbnails and scrolls with the page.  Being on the side of the screen, the sidebar is easily accessible (according to Fitts’ law) and the user can click these thumbnails contained in the sidebar. On click the user’s page is automatically scrolled to display the original image in the page. 

**Solution 3: Click on image reference to open image it in a new tab**
The “alt” value of the “img” tag associated with each image is stored in a map. If the page source contains any key from the map, the text is converted to a hyperlink. When the user clicks on this link, a new tab opens with the source image. The user can switch between tabs as and when required and refer the desired images without disrupting his continuity.



## Code 
Example

Show what the library does as concisely as possible, developers should be able to figure out **how** your project solves their problem by looking at the code example. Make sure the API you are showing off is obvious, and that your code is short and concise.



## Motivation


A short description of the motivation behind the creation and maintenance of the project. This should explain **why** the project exists.



## Installation


Provide code examples and explanations of how to get the project.

## API Reference

Depending on the size of the project, if it is small and simple enough the reference docs can be added to the README. For medium size to larger projects it is important to at least provide a link to where the API reference docs live.



## Tests


Describe and show how to run the tests with code examples.

## Contributors

Let people know how they can dive into the project, include important links to things like issue trackers, irc, twitter accounts if applicable.

## License

A short snippet describing the license (MIT, Apache, etc.)
