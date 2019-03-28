# Time on Site #

Time measurements in Google Analytics are limited. 
By default, it only tracks time between two pageviews. 
This means that a single page session has a time on site of 0 seconds. 
For every multi-page visit, it only reports the time spent between pages.
It never includes the time spent on the last page. 
Besides that, GTM only allows you to place tags on time on page events.

### The solution ###

Our script solves both the problem with GA and GTM. 
The script tracks time on site based on a cookie. 
If you have spent 5 seconds on page one, and 10 on page two, your time on site will be 15 seconds according to the script.

### When should you use this script? ###

The Data Technology team has investigated the added value of this script.
It has added value, but only for campaigns where the little details matter (e.g. when 30k conversions make a difference with 25k conversions in your optimisation plans).
The solution also uses a cookie. This has impact on cookie statements and privacy statements.
Because of this, implementation can take a long time.


### How to use ###

You can include the `ghg_time_on_site_min.html` file to your tag manager as a custom HTML tag. 
Customise the `ghgTimeOnSiteConfig` to your situation by changing these values:

- `tosCookieName`: the name of the cookie that will be set on the domain.
- `tosCookieDomain`: the domain the cookie should be placed on.
- `tosIntervalSeconds`: the array of intervals in seconds you want to fire events on.

Here's an example:


```

var ghgTimeOnSiteConfig = {
    tosCookieName: 'ghg_tos',
    tosCookieDomain: 'www.domain.com',
    tosIntervalsInSeconds: [10, 20]
}
```

You also need to change the `ghgTosEventFunction` to fire the event in a format that works for the client. Here's an example for a GTM event:

```

function ghgTosEventFunction(time){
	dataLayer.push({
		'event': 'time on site',
		'time_spent_in_seconds': time
	})
}
```
