# Time on Site #

Time measurements in Google Analytics are limited. 
By default, it only tracks time between two pageviews. 
This means that a single page session has a time on site of 0 seconds. 
For every multi-page visit, it only reports the time spent between pages.
It never includes the time spent on the last page. 
Besides that, GTM only allows you to place tags on time on page events.

### The solution ###

Our script solves both the problem with GA and GTM. 
The script tracks time on site based on Session Storage. 
If you have spent 5 seconds on page one, and 10 on page two, your time on site will be 15 seconds according to the script.

### When should you use this script? ###

The Digital Analytics team has investigated the added value of this script.
It has added value, but only for campaigns where the little details matter (e.g. when 30k conversions make a difference with 25k conversions in your optimisation plans).
The solution also uses Session Storage. This has impact on privacy statements.
Because of this, implementation can take a long time.


### How to use ###

You can include the main file to your tag manager as a custom HTML tag. 
Read the comments in the code and replace with thing that suit your needs.
For example:

- Tagging: For which tagging you want to reset the timer.
- TimedEvent: On how many ticks/seconds you want to fire an event.
- Event handler onTimedEvent: Add you own event handler, an example for the GTM dataLayer is in the code.
- Default tick is one second and default timeout is 30 minutes.
