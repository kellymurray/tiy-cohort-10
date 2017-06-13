# AJAX

## To Read

* [What is an API? In English, please.](https://medium.freecodecamp.com/what-is-an-api-in-english-please-b880a3214a82)

* [JavaScript.info async tutorial](http://javascript.info/async)

* [CopterLabs](http://www.copterlabs.com/json-what-it-is-how-it-works-how-to-use-it/)

Now, you'll notice that some of these examples discuss using [jQuery AJAX](http://api.jquery.com/jquery.ajax/) to make calls. While this is still the *easiest* method, it is not *essential*, and can actually cause slight performance issues if you aren't already using jQuery in your project. 

## What's AJAX?

- Asynchronous JavaScript and XML
- Loads data quickly and asynchronously in the background without delaying the page rendering
- Allows JavaScript to ask a server for data without doing a page refresh

## What's JSON?

JavaScript Object Notation (JSON) is a way to store information in an organized, easy-to-access manner. It's very readable by human eyes.

```javascript
{
	"name": "kipling",
	"age": "5",
	"hometown": "Raleigh NC",
	"species": "cat"
}
```

This creates an object with values we can access using the variable `kipling`.

```javascript
document.write("Kipling is " kipling.age);
```

[CopterLabs](http://www.copterlabs.com/json-what-it-is-how-it-works-how-to-use-it/) has a great write-up on JSON that you should spend some time with this week.

## HTTP Methods

- POST is usually used to create new records
- PUT is usually used to overwrite records
  - Is sometimes used for creation and/or update (also called upserting)
- DELETE is used to delete records and doesn't send data
- GET is used to get records and doesn't send data

## Authenticating

Some APIs require users to be authenticated before you can call them.

There are a few ways to make this happen

- If you're calling an API in your own domain, you can just use cookies
- If you're calling an API on another domain, the API may handle auth in a few ways:
- OAuth
  - a complex handshake process
  - allows users to authorize your app with the remote domain
  - your app never actually sees the user's username and/or password
- Basic authentication
  - a simple authentication process
  - your app collects a username/password and sends it to the remote API

## Old APIs

In the past, due to security issues, browsers didn't allow cross-origin calls.

That is, scripts running on `mydomain.com` could not make AJAX calls to
 `yourdomain.com`.

This has been fixed by CORS:

- Cross Origin Resource Sharing
- Old APIs and/or browsers still don't support this

## JSONP

Before CORS (and even now with sites like Etsy), you had to do something
called JSONP (JSON with Padding).

Essentially, this involved adding a script tag to your page:

`<script src="http://otherdomain.com/foo?callback=doSomething"></script>`

The server at otherdomain.com would send you back a script that looked like
this:

```javascript
doSomething({ name: 'Joe Shmo' });
```

So, as long as you had a `doSomething` function defined somewhere, it would
get called and passed the object `{ name: 'Joe Shmo' }`


## JSONP drawbacks

- Can't send authentication credentials
- Can't handle timeouts or networking errors gracefully (silently fails)
- Requires having global callbacks!
