# Mobile First Design
<p>Mobile optimization and responsive design are not just buzz words, but really important factors to consider when implementing a mockup. In most cases, clients won't be satisfied unless the application being developed looks consistent amongst the plethora of devices available in the marketplace.  </p>

Even though tools like Twitter Bootstrap exist to make responsive design easy and efficient, often times you might want to build your own responsive design implementationwithout relying on preexisting libraries.   If anything, hand-rolling a responsive design helps to gain a better understanding of the fundamentals of responsive design and allows for more customization than frameworks like Bootstrap.

Here is a list of tools I use when implementing a mobile responsive design:

1.  A meta viewport tag
	- In the \<head> of your document, include this meta tag to ensure your @media queries work correctly (written in Haml):
				
			%meta{ name: "viewport", content: "initial-scale=1, maximum-scale=1" }
1. @media queries
	- The crux of responsive design, media queries "let the presentation of content be tailored to a specific range of output devices without having to change the content itself." Source: [MDN](https://developer.mozilla.org/en-US/docs/Web/Guide/CSS/Media_queries) 
	- Media queries allow for certain blocks of code to apply to devices with specific heights and widths.  
	- An example of a media query used for devices with a width smaller than 480px:
		
			div.archive-container
				@media (max-width: 480px)
					position: initial
					width: 45%
					height: 424px
					min-width: 288px
					margin-left: 0
1.  Use the Chrome "Emulation" tool
	- Whereas one solution might be to simply resize the width of your browser window, Chrome offers a nifty tool to help developers test out their layouts across devices. 
		1. Open Developer Tools cmd + i
		1.  On the bottom of the window, click on "Emulation"
		1.  From the "Device" drop-down menu, pick a device
		1.  Click on Emulate
		1.  You might have to reload the page <br>
		& voila, you can checkout your site's appearance on a mobile device.