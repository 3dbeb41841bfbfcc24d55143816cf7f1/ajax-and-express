# Ajax #

### :bar_chart: I do
### :bar_chart: We do
### :bar_chart: You do

## Outline ##
* [Introduction](#introduction)
  - Learning objectives
  - Topics so far
* [APIs](#apis)
  - What is an API?
  - Where to find APIs
* [Asynchronous requests](#asynchronous-requests)
  - T&T: Google Maps
* [Ajax](#ajax)

## Introduction ##
### Learning objectives
- Send and handle Ajax requests
  - using vanilla JavaScript `XMLHttpRequest()`
  - using jQuery
- Use Ajax technologies to implement a client for a RESTful web API
- Describe what an API is, specifically in the context of web development
- Explain the advantages asynchronous requests
- Define Ajax, and understand common formats for serialized data

### Topics so far
Let's list out some technologies we've learned in this class thus far.

TODO: HTTP requests, RESTful routes, CRUD, client-server architecture, MVC and separation of concerns

That is a tremendous amount of stuff. In the first couple of weeks we learned how to style a semantically structured HTML site with the ability to manipulate the DOM. In the past couple weeks or so, we've been learning a lot about server-side requests and responses. Today we'll be tying these concepts together. Currently we know how to create applications with full CRUD on models in our database, and that's great. When we do that CRUD, however, it requires a page reload of some kind. It would be really nice if had some functionality on the client side of our application but still communicate with the backend without a page refresh. If only we had a client side language that was non blocking and asynchronous...

(ST-WG) Think back to the first couple weeks of class, whats the difference between synchronous and asynchronous program execution? More importantly, what kind of things can we do with non blocking asynchronous program execution?

### RESTful routes chart

 | Request action | Path format            | Path example  | Description                      |
 | -------------- | ---------------------- | ------------- | -------------------------------- |
 | `GET`          | `/path/to/resource`    | `/cars/:id`   | Retrieve a resource              |
 | `GET`          | `/path/to/container/`  | `/cars/`      | List of resources in a container |
 | `POST`         | `/path/to/parent/`     | `/cars/`      | Create new resource in container |
 | `PUT`          | `/path/to/resource`    | `/cars/:id`   | Replace a resource               |
 | `PATCH`        | `/path/to/resource`    | `/cars/:id`   | Update a resource                |
 | `DELETE`       | `/path/to/resource`    | `/cars/:id`   | Delete a resource                |

## APIs ##
### What is an API?
API stands for Application Programming Interface, but what does that mean?

##### Generic API definition
> An Application Programming Interface (API) is a set of functions, procedures, methods or classes used by computer programs to request services from the operating system, software libraries or any other service providers running on the computer. A computer programmer uses the API to make application programs.

###### --Wikipedia contributors, [Application programming interface](https://simple.wikipedia.org/wiki/Application_programming_interface)

Technically, APIs are _everywhere_ in software development. The DOM and jQuery are actually examples of APIs! Since the explosion of information technology, however, the term now commonly refers to web URLs that can be accessed for raw data.

Since we are web developers, we have a more specific notion of APIs and how they are implemented and used by web apps.

This definition is closer to our web development concept of APIs:
##### Web dev API definition
> An API is the tool that makes a website's data digestible for a computer. Through it, a computer can view and edit data, just like a person can by loading pages and submitting forms.

###### --Brian Cooksey, [Introduction to APIs](https://zapier.com/learn/apis/chapter-1-introduction-to-apis/)

Also theck out the image below that quote on the blog, let's extend it by adding our parts in there.

![alt-txt](https://zapier.cachefly.net/static/CpTucd/images/learn/apis/communicating-with-server.jpg)


### Where to find APIs
#### API Exploration

APIs are published everywhere. Chances are good that most major content sources you follow online publish their data in some type of serialized format. Heck, [even Marvel publishes an API](http://developer.marvel.com/documentation/getting_started). Look around for a "Developers" section on major websites.


| API | Sample URL |
|-----|------------|
| **[Giphy](https://github.com/Giphy/GiphyAPI)** | `http://api.giphy.com/v1/gifs/search?q=funny+cat&api_key=dc6zaTOxFJmzC` |
| **[Marvel](http://developer.marvel.com/documentation/getting_started)** | `http://developer.marvel.com/documentation/getting_started` |
| **[OMDB API](http://www.omdbapi.com/)** | `http://www.omdbapi.com/?t=Game%20of%20Thrones&Season=1` |
| **[StarWars](http://swapi.co/)** | `http://swapi.co/api/people/3` |
| **[Stocks](http://dev.markitondemand.com/MODApis/)** | `http://dev.markitondemand.com/Api/Quote/xml?symbol=AAPL` |
| **[This for That](http://itsthisforthat.com/)** | `http://itsthisforthat.com/api.php?json` |

**Where to find even more APIs**

Try the [Programmable Web API Directory](http://www.programmableweb.com/apis/directory) or the [Public APIs Directory](http://www.publicapis.com/).

## Asynchronous requests ##
### :information_desk_person: Turn and talk: Google maps
Let's visit [Google Maps](https://www.google.com/maps). How would this site work with things not happening asynchronously?

Turn to your neighbor, and chat with them about how Google Maps would function without async requests. Hint: recall how we get a page reload on the client side every time the server sends a response. What if this happened every time the user changed something in the Google Maps UI?

## Ajax ##
### What is Ajax?

Ajax is the name of a set of technologies in web development that allow for asynchronous client-server communication. Ajax techniques emerged around the year 2005. Check out the original article that sets up the foundations of Ajax:

> ##### DEFINING AJAX
> Ajax isn’t a technology. It’s really several technologies, each flourishing in its own right, coming together in powerful new ways. Ajax incorporates:
>
> * standards-based presentation using XHTML and CSS;
> * dynamic display and interaction using the Document Object Model;
> * data interchange and manipulation using XML and XSLT;
> * asynchronous data retrieval using XMLHttpRequest;
> * and JavaScript binding everything together.

-- Jesse James Garrett, ["Ajax: A New Approach to Web Applications"](http://adaptivepath.org/ideas/ajax-new-approach-web-applications/)

###### You can tell we are time travelling, since the blog praises the design of the **iPod**.

Ajax (Asynchronous JavaScript and XML) is a method of building interactive applications for the Web that processes user requests immediately, without re-rendering a whole page.

**Example:** A weather forecasting site could display local conditions on one side of the page as soon as a user finishes typing in a zip code. The temperature could refresh every minute, without the user having to hit a refresh button.

In general the process looks like this – use JavaScript on the client side to hit an API (without reloading a page), then use the _data_ you get back to manipulate the DOM somehow if you need to. This DOM manipulation can take the form of rendering a template or just changing a number on the page.

##### Minimalistic definition of Ajax
> Client-side technologies / techniques that allow two-way communication between the client and the server.

###### &mdash; Chris Shiflett, ["Ajax Is Not an Acronym"](http://shiflett.org/blog/2007/apr/ajax-is-not-an-acronym)

##### Advantages

- __Faster__ - This is the most obvious reason for using to Ajax on your frontend: Ajax allows easier and quicker interaction between user and website as pages are not reloaded for content to be displayed.  The server doesn't have to get data, render HTML, and then spit it out, it just has to get data and your already-loaded frontend does the rest.

- __Compact__ - With Ajax, several application features can be handled using a single web page. That means we modularize our app into smaller bits, and it becomes easier to work on.

- __Backend Separated from Frontend__ - Applications that use Ajax-heavy frontends means developers don't have to work on both sides of the stack at the same time. Some developers can be dedicated to building an API that just serves data, and others can focus on consuming that data and building interfaces.

##### Disadvantages

- __The back and refresh button are rendered useless__ - Since things are loaded dynamically on a page, without that page reloading (or more importantly a URL being changed), clicking the back or refresh button don't work the way you're used to. That's actually a pretty big deal – UX designers are very familiar with the fact that users are _accustomed_ to being able to hit back when they need to. Some advanced front-end frameworks have tried to solve this issue with clever workarounds, but that's not always the case and not always accurate.

- __Javascript can be disabled__ - While javascript is secure and has been heavily used by websites for a long period of time, a percentage of website surfers prefer to turn javascript functionality off on their browser, rendering the Ajax application totally useless. That's not always the best thing to design for, and more often than not, you'll find yourself assuming users have JS on, but it's important to know your whole site could be useless in some situations.

- __You have to consider the UX even more__ - While UX is crucial for _any_ application, the fact that a page doesn't refresh means you have to be even more considerate of what a user is experiencing. If something in your JavaScript goes wrong, your Ajax breaks, and you don't have failsafes thoughtfully built in, your user might be clicking a button and seeing absolutely nothing happen. Most common users won't have their consoles open to notice any errors.

##### Why are we learning it?
As you're learning how to build APIs on the server side, you need to start learning how to consume your APIs on the client side.

While we're going to be tackling some advanced front-end frameworks in the next unit, you, as a junior full-stack developer, need to be able to do something awesome with the APIs you're learning to make. So we're going to tackle the basics and build on them even further, later.


#### **Example: `XMLHttpRequest` GET**

```javascript
function reqListener () {
  console.log(this.responseText);
}

var oReq = new XMLHttpRequest();
oReq.addEventListener("load", reqListener);
oReq.open("GET", "https://www.omdbapi.com/?t=Moneyball");
oReq.send();
```

Let's walk through this for a second. We're doing Ajax, using the JavaScript `XMLHttpRequest` function to send an HTTP request and wait for some response. Here, we're going to open a new request and tell it which verb we need and the URL.

According to the documentation, the XMLHttpRequest `open()` method requires 2 arguments:

* `method` matches an HTTP action (`"GET"`, `"POST"`, `"DELETE"`, etc.)
* `url` is the full URI path where we are sending the request. Its format is dependent on the API in use.

The `open()` method can also take a few optional arguments, including `async`.

* `async` is an **optional** boolean value that indicates the nature of the request. **By default, all requests are async.**

#### **Example: `XMLHttpRequest GET`, annotated**

```javascript
function reqListener () {
  console.log(this.responseText);
}

// create a new request object
var oReq = new XMLHttpRequest();

// add an event listener to call the function reqListener on load
oReq.addEventListener("load", reqListener);

// specify the HTTP method and URL for the request
oReq.open("GET", "https://www.omdbapi.com/?t=Moneyball");

// send the request
oReq.send();
```

#### **Example: `jQuery.ajax()` GET**

```javascript
$.ajax({
  method: "GET",
  url: "https://www.omdbapi.com/?t=Moneyball"
})
.done(function( msg ) {
  console.log("Response text: " + msg);
});
```



## everything else ##
### bonus: APIs that require a key
### GET Examples
#### Standard Example
	
	```javascript
	$.ajax({
	  url: 'http://localhost:8000/animals',
	  type: 'POST',
	  dataType: 'json',
	  data: {"animal":
	  {"name": animal,
	  "sound": sound}
	}})
	```
	
	#### OMDBI Example
	
	```javascript
	$.ajax({
		url: 'http://www.omdbapi.com/?t=Star+Wars&y=&plot=short&r=json',
		type: "GET",
		dataType: 'json',
		success: function(data) {
			$('body').append(data.Title + " was released in " + data.Year + "<hr><br>");
		}
	});
	```
	
	#### Shake-it-speare
	```javascript
	$.ajax({
		url: 'http://shakeitspeare.com/api/poem',
		type: "GET",
		dataType: 'json',
		success: function(data) {
			var data = data;
			//console.log(data);
			$('body').append(data.poem);
			//alert("huzzah! we did it guys!");
		},
		fail: function(error) {
			console.log(error);
		}
	});
	```
	
	### POST examples
	
	```javascript
	 var animal = $("#animalName").val();
	    var sound = $("#animalSound").val();
	
	    // alert(animal);
	
	    $.ajax({
	      url: 'http://localhost:8000/animals',
	      type: 'POST',
	      dataType: 'json',
	      data: {"animal":
	      {"name": animal,
	      "sound": sound}
	    }})
	```

</details>


#### Conclusion (5 mins)
- What's the main use case of Ajax? Why would anyone use it?
- How do you do a simple GET request in vanilla JS?
- How do you do a GET request with jQuery?
- How do you do a PUT, POST, or DELETE request in jQuery?

#### Extra Reading

- [You Might not Need jQuery](http://youmightnotneedjquery.com/)
- [`No 'Access-Control-Allow-Origin' header is present on the requested resource` – WTF?](https://jvaneyck.wordpress.com/2014/01/07/cross-domain-requests-in-javascript/)
- [What is Cross Origin Resource Sharing (CORS)?](https://www.maxcdn.com/one/visual-glossary/cors/)
- [Using CORS with Express](http://enable-cors.org/server_expressjs.html)
- [YouTube - Ajax using $.getJSON](https://www.youtube.com/watch?v=dIdrhawUe6k)
#### Screencasts (via https://github.com/ga-wdi-lessons/js-ajax/)
- [ajax 1](https://youtu.be/K4zRqJm7sXU)
- [ajax 2](https://youtu.be/WoA5LnPXWB8)
- [ajax 3](https://youtu.be/3xUy5QmrBuc)


#### Let's look at the web's plumbing - (5 mins)

The core of it a web client (which may be a browser) makes a request to a web server. A web server makes a response. Let's take a closer look...

**YOU DO**

- Go to Chrome 
- Open the Javascript console 
- Choose the Network tab, make sure the red "record" button is red and "Preserve log" is checked.
- Then go to your favorite website.

Down the left side of the screen you see all the requests that went into assembling that webpage. Click on one line, and you can look at all the data that went back and forth for that one request.

---



## Notes

### :heavy_exclamation_mark: clarify specific goal / desired outcome 
* After this, we will be able to answer the question, "what is Ajax"
* goal: Understand and implement Ajax client-side rendering.

### :heavy_exclamation_mark: attention grabber (story, question,)
google maps t&t exercise

### :heavy_exclamation_mark: need, create interest by exposing need (matter of self-interest)
When does the server run our stuff? Only in response to q request.
We can visit URLs, submit forms, use other tools like httpie
We can redirect using Express routes, but the server only has one chance to respond.
Our content is assembled server-side and sent over, which we know because we wrote EJS templates that got converted to regular HTML.
The server is where that magic happens, then the response gets dropped in the tube and whisked away to a client. It's built, it's shipped, it's gone.

### :heavy_exclamation_mark: satisfaction, show how need is met, address objections

### :heavy_exclamation_mark: viz, dramatic picture / benefits, create desire

### :heavy_exclamation_mark: action, ask for decision or action

