# HTML Specs

## HTML5

HTML5 is a new version of HTML and XHTML. The [HTML5 draft](http://whatwg.org/specs/web-apps/current-work/) specification defines a single language that can be written in HTML and XML. It attempts to solve issues found in previous iterations of HTML and addresses the needs of Web Applications, an area previously not adequately covered by HTML. ([source](http://html5.org/))

### doctype
A nice aspect of HTML5 is that it streamlines the amount of code that is required. Meaningless attributes have been dropped, and the DOCTYPE declaration has been simplified significantly. Additionally, there is no need to use CDATA to escape inline JavaScript, formerly a requirement to meet XML strictness in XHTML.

### IE compatibility mode
Internet Explorer supports the use of a document compatibility ```<meta>``` tag to specify what version of IE the page should be rendered as. Unless circumstances require otherwise, it's most useful to instruct IE to use the latest supported mode with edge mode.

For more information, [read this awesome Stack Overflow article](http://stackoverflow.com/questions/6771258/whats-the-difference-if-meta-http-equiv-x-ua-compatible-content-ie-edge-e).


## HTML Validation
All HTML pages should be verified against the [W3C validator](http://validator.w3.org/), to ensure that the markup is well formed. This in and of itself is not directly indicative of good code, but it helps to weed out problems that are able to be tested via automation. It is no substitute for manual code review.

## HTML5 Semantic Markup
The markup that you write should always be as semantic as possible. Easily readable and understandable by both humans and Bots( site crawlers ). This even helps the SEO of the site.
<br />Here is an awesome article that will help you understand the sematics in depth : ([ lets-talk-about-semantics ](http://html5doctor.com/lets-talk-about-semantics/))
<br/>You can learn about the Semantic elements in HTML5 over here : ([ html5 Semantic Elements ](http://www.w3schools.com/html/html5_semantic_elements.asp) )

## Self-closing Elements
Though we are using [HTML5](http://dev.w3.org/html5/spec/Overview.html), which allows for either HTML or XHTML style syntax, we prefer the strictness of XHTML. Therefore, all tags must be properly closed. For tags that can wrap nodes such as text or other elements, termination is a trivial enough task. For tags that are self-closing, the forward slash should have exactly one space preceding it ```
<br />``` vs. the compact but incorrect ```
<br/>```. The W3C specifies that a single space should precede the self-closing slash ([source](http://w3.org/TR/xhtml1/#C_2)).

## Tags & Attributes
All tags and attributes must be written in lowercase. Additionally, we prefer that any attribute values also be lowercase, when the purpose of the text therein is only to be interpreted by machines. For instances in which the data needs to be human readable, proper title capitalization should be followed, such as:

For machines:
```
<meta http-equiv="content-type" content="text/html; charset=utf-8" />```

For humans:

```
<a href="http://example.com/" title="Description Goes Here">Example.com</a>```

## Quotes
In keeping with the strictness of XHTML code conventions, according to the W3C, all attributes must have a value, and must use double-quotes ([source](http://w3.org/TR/xhtml1/#h-4.4)). The following are examples of proper and improper usage of quotes and attribute/value pairs.

Correct:
```
<input type="text" name="email" disabled="disabled" />```

Incorrect:
```
<input type=text name=email disabled>```

**Checkout some more links about HTML Coding Standards:**

https://make.wordpress.org/core/handbook/coding-standards/html/
http://developer.fellowshipone.com/patterns/code.php#_63_html5
http://codeguide.co/#html
https://google-styleguide.googlecode.com/svn/trunk/htmlcssguide.xml#HTML_Style_Rules

## Useful links

[WordPress coding standard for HTML](https://make.wordpress.org/core/handbook/coding-standards/html/)

