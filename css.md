# CSS - Cascade Style Sheet

[<- Go Back](html.md)

## Intro to CSS

* **CSS** stands for **C**ascading **S**tyle **S**heets and it's a language used to describe the presentation of a document written in HTML
* CSS describes how elements should be rendered on screen, on paper, in speech, or on other media types

  **CSS code example:**
  ```CSS
  span {
    color: white;
  }
  ```

* In this example we define that all span elements will show white text
* Using this code we can see that with CSS we'll select one or many elements & set some property and value to update the way the element should look

  **CSS code example:**
  ```CSS
  element_selector {
    property_name: property_value;
  }
  ```

* By working with CSS we'll be selecting elements and defining how they should look
* We can also define if the style should be applied at the element, document or site level
* [Chrome Devtools](https://developers.google.com/web/tools/chrome-devtools) is a great tool to use when coding CSS and JavaScript
* [Read the MDN CSS reference guide](https://developer.mozilla.org/en-US/docs/Web/CSS/Reference)

## Element Type selectors
* The **type selector** matches elements by node name
* It selects **all** elements of the given type within a document
* Between **{ }** goes CSS code
* [MDN type selecto doc](https://developer.mozilla.org/en-US/docs/Web/CSS/Type_selectors)

  **Selector Example**
  ```css
  /* This selector selects all p elements */
  p {
    /* CSS Code */
  }

  /* This selector selects all div elements */
  div {
    /* CSS Code */
  }

  /* This selector selects all span elements */
  span {
    /* CSS Code */
  }
  ```

### Color
* The **color** CSS property sets the foreground color value of an element's text content and text decorations
* This property accepts any CSS color value:
  * Named color: white, red, blue, green
  * RGB (Red, Green & Blue): rgb(0,0,0)
  * Hexadecimal color: #000000, #ffffff
* [MDN color property](https://developer.mozilla.org/en-US/docs/Web/CSS/color)
* [Wikipedia RGB doc](https://en.wikipedia.org/wiki/RGB_color_model)
* [To learn more about color models](https://developer.mozilla.org/en-US/docs/Web/CSS/color_value)
* [Hexadecimal system](https://en.wikipedia.org/wiki/Hexadecimal)

  **Example:**
  ```css
    /* All p elements are blue */
    p {
      color: blue;
    }

    /* All div elements are red */
    div {
      color: rgb(255, 0, 0);
    }

    /* All span elements are green */
    span {
      color: #00FF00;
    }
  ```

  ```html
  <p>Blue text</p>
  <p>Blue &amp; <span>green</span> text</p> 
  <div>Red text</div>
  <div>Red &amp; <span>green</span> text</div>
  <span>Green text</span>
  ```

## How to apply CSS to a document
* The **style** element contains style information for a document, or part of a document
* By default, the style instructions written inside that element are expected to be CSS
* The **type** attribute is optional and defaults to **text/css** if it is missing
* [MDN style element doc](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/style)

  **Example:**
  ```html
  <!DOCTYPE html>
  <html>
    <head>
      <title>Using CSS in a Document</title>
      <style type="text/css">
        /* We select all the document span elements and apply the color property with a white value */
        span {
          color: white;
        }
      </style>
    </head>
    <body>
      <span>White text</span>
      <span>White text</span>
      <span>White text</span>
    </body>
  </html>
  ```

* We can make our document different by only changing the color value

  **Example:**
  ```html
  <!DOCTYPE html>
  <html>
    <head>
      <title>Using CSS in a Document</title>
      <style type="text/css">
        /* We select all the document span elements and apply the color property with a red value */
        span {
          color: red;
        }
      </style>
    </head>
    <body>
      <span>Red text</span>
      <span>Red text</span>
      <span>Red text</span>
    </body>
  </html>
  ```

#### Practice
[Exercise 1](exercises/css/ex_1.md)

## CSS Styles

* As we know we can apply css in different ways:
  * Document
  * Inline style
  * Site

### Inline style
* We can use the **style** attribute to apply css to only one HTML element
* This attribute accepts a pair of property:value
* To apply more than one style we separate the property:value with a semicolon
  * Example: property:value; other-property: other-value
* We don't need to select the element as we are directly applying the style to it

  **Example:**
  ```html
  <span style="color: white;">White text</span>
  ```

* This is the most singular way to apply CSS to HTML.  The style will apply only to the single element.
* You would need to apply the style attribute to each element if you want more than one element with the same style

  **Example:**
  ```html
  <span style="color: white;">White text</span>
  <span style="color: white;">Other white text</span>
  ```

* This type of selection is usefull if we only need a couple of elements
* It's hard to change values if we have many items
* As it's the last property that the browser reads, it's also the [higher priority one](https://developer.mozilla.org/en-US/docs/Web/CSS/Specificity)
* Because it is the last property read, it's a good option when you need to override styles

#### Practice
[Exercise 2](exercises/css/ex_2.md)

### Site styles
* The **link** element links a HTML document with a CSS one
* The CSS rules that we define in a external CSS file are going to apply for each document that we link
* This is the best way to apply CSS to our sites if we have many documents and we want them to share the same look & feel
* The link tag has the following attributes:
  * **href:** define the document path that you want to link
  * **type:** as we are linking CSS we use the value "text/css"
  * **rel:** as we are linking CSS we use the value "stylesheet"

  **Example:** 

  filename: styles.css
  ```css
  span {
    color: white;
  }
  ```

  filename: index.html
  ```html
  <!DOCTYPE html>
  <html>
    <head>
      <title>Index</title>
      <!-- 
        We link the index.html file with the styles.css one
      -->
      <link href="styles.css" type="text/css" rel="stylesheet" />
    </head>
    <body>
      <span>white text</span>
      <span>white text</span>
      <span>white text</span>
      <span>white text</span>
      <span>white text</span>
    </body>
  </html>
  ```

  filename: contact.html
  ```html
  <!DOCTYPE html>
  <html>
    <head>
      <title>Contact</title>
      <!-- 
        If we have more than one document we can link the same style sheet
        Every rule defined on the external CSS file works here
      -->
      <link href="styles.css" type="text/css" rel="stylesheet" />
    </head>
    <body>
      <span>Other white text</span>
      <span>Other white text</span>
      <span>Other white text</span>
      <span>Other white text</span>
      <span>Other white text</span>
    </body>
  </html>
  ```

* We can change the way spans look in both documents by only changing one CSS value

  **Example:** 
  filename: styles.css
  ```css
  span {
    color: red;
  }
  ```

  filename: index.html
  ```html
  <!DOCTYPE html>
  <html>
    <head>
      <title>Index</title>
      <link href="styles.css" type="text/css" rel="stylesheet" />
    </head>
    <body>
      <span>Red Text</span>
      <span>Red Text</span>
      <span>Red Text</span>
      <span>Red Text</span>
      <span>Red Text</span>
    </body>
  </html>
  ```

  filename: contact.html
  ```html
  <!DOCTYPE html>
  <html>
    <head>
      <title>Contact</title>
      <link href="styles.css" type="text/css" rel="stylesheet" />
    </head>
    <body>
      <span>Other Red Text</span>
      <span>Other Red Text</span>
      <span>Other Red Text</span>
      <span>Other Red Text</span>
      <span>Other Red Text</span>
    </body>
  </html>
  ```

#### Practice
[Exercise 3](exercises/css/ex_3.md)

## CSS Selectors
* To use CSS on our site we need more ways to select elements and apply styles
* By using different types of selector we can select one or many elements at the same time
* For example: 
  * The element selector (tag name) applies the style to all the elements with the same tag name
  * The id selector applies the style to only the element that has the id attribute
* [Read the MDN selectors guide](https://developer.mozilla.org/en-US/docs/Learn/CSS/Introduction_to_CSS/Selectors)

## ID Selector
* To select elements by id we use the **#** character and the element id value
* [MDN ID selectors doc](https://developer.mozilla.org/en-US/docs/Web/CSS/ID_selectors)

  **Example:** 
  ```css
  /* Element with id="main" */
  #main {
    color: red;
  }

  div {
    color: blue;
  }
  ```

  ```html
  <div id="main">Red Main Div</div>
  <div>Blue div</div>
  <div>Blue div</div>
  ```

## Class Selector
* Also we can select all elements with same class name by using a **.** and the element class name
* [MDN Class selectors doc](https://developer.mozilla.org/en-US/docs/Web/CSS/Class_selectors)

  **Example:** 
  ```css
  /* All elements that have class="red" */
  .red {
    color: red;
  }

  div {
    color: blue;
  }
  ```

  ```html
  <div class="red">Red Main Div</div>
  <div>Blue div</div>
  <div class="red">Red Main Div</div>
  ```

* Both **id** and **class** selector can be even more specific by adding the element type before the id or class selector

  **Example:**
  ```css
  /* Only select the div with main id */
  div#main { color: red; }

  /* Only select the paragraph with blue class */
  p.blue { color: blue; }
  ```
  ```html
  <div id="main">Red Text</div>
  <p class="blue">Blue Text</p>
  <p> Text</p>
  <div class="blue">Text</div>
  ```

## Shared CSS code between selectors
* In some cases we need to use the same style for more than one element and we can choose:
  * Create a class and apply it to both elements
  * Or we can add more selectors separated by a comma

  **Example:**
  ```css
  .red{ color: red; }
  ```
  ```html
  <div class="red">Red Text</div>
  <p class="red">Red Text</p>
  ```

* Or

  **Example:**
  ```css
  selector1, selector2 {
    /* CSS code */
  }
  ```

  **Example:**
  ```css
  div, p { color: red; }
  ```
  ```html
  <div>Red Text</div>
  <p>Red Text</p>
  ```
  ## Universal selector
* The `*` universal selector matches elements of any type
* You can use this selector to delete the browser initial styles (Many CSS libraries do it)
* [MDN Universal selectors doc](https://developer.mozilla.org/en-US/docs/Web/CSS/Universal_selectors)

  **Example:**
  ```css
  /* The universal selector will match all the elements and sets the color to white */
  * {
    color: white;
  }
  ```
  ```html
  <div>White div text</div>
  <p>White paragraph text</p>
  <span>White span text</span>
  <a href="#">White link text</a>
  ```

## Attribute selectors
* Selects elements based on the value of the given attribute
* First we select the element
* Then we add brackets
* Between brackets we add the attribute = value
* [MDN Attribute selectors doc](https://developer.mozilla.org/en-US/docs/Web/CSS/Attribute_selectors)

  **Example:**
  ```css
  /* Select all a elements that have a href="#" attribute */
  a[href="#"] { color: pink; }

  /* Select all div elements that have the name main attribute */
  div[name="main"] { color: yellow; }
  ```
  ```html
  <div name="main">Yellow div text</div>
  <a href="#">Pink link text</a>
  <a href="http://www.google.com"></a>
  ```

#### Practice
[Exercise 4](exercises/css/ex_4.md)

## Pseudo-classes selector
* The pseudo-class is a keyword added to a selector that specifies a special state of the selected element(s)
* For example, :hover can be used to change a button's color when the user hovers over it
* For links we can use the following pseudo-classes: **:link, :active, :hover & :visited**
* See a complete Pseudo-classes list on [MDN Pseudo-classes doc](https://developer.mozilla.org/en-US/docs/Web/CSS/Pseudo-classes)

  **Example:**
  ```css
  a:link {
    color: red;
  }

  a:active {
    color: pink;
  }

  a:hover {
    color: gray;
  }

  a:visited {
    color: green;
  }
  ```

## Descendant selectors
* This selector is represented by a single space ( ) character & combines two selectors such that elements matched by the second selector are selected if they have an ancestor element matching the first selector
* It will apply to any element inside other element without being a direct dependency
* [MDN Descendant selectors doc]()https://developer.mozilla.org/en-US/docs/Web/CSS/Descendant_selectors

  **Example:**
  ```css
  div a {
    color: red;
  }
  ```
  ```html
  <div>
    <a href="#">Link inside a div</a>
    <p>
      <a href="#">Link inside a parragraph inside a div</a>
    </p>
  </div>
  ```

## Child selectors
* Using the **>** selector we can select only those elements matched by the second selector that are the direct children of elements matched by the first
* The child combinator **>** is placed between two CSS selectors. 
* Elements matched by the second selector must be the immediate children of the elements matched by the first selector
* This is stricter than the descendant selector
* [Child selectors](https://developer.mozilla.org/en-US/docs/Web/CSS/Child_selectors)

  **Example:**
  ```css
  /* Select the paragraph elements that are direct children from a div element*/
  div > p {
    color: red;
  }
  ```
  ```html
  <p>Black text</p>
  <div>
    <p>Red Text</p>
    <table>
      <tr>
        <td><p>Black Text</p></td>
      </tr>  
    </table>
    <h1>Black text</h1>
  </div>
  ```

* In this example we can see that this selector only affects the div child paragraph

## Pseudo-elements
* A CSS **pseudo-element** is a keyword added to a selector that lets you style a specific part of the selected element(s)
* We use the **::** operator to select **pseudo-element**
* These are the most used **pseudo-element**:
  * ::first-line
  * ::first-letter
  * ::selection
  * ::after
  * ::before
* The pseudo-elements ::after & ::before need to use a special property called **content**
* [MDN Pseudo elements docs](https://developer.mozilla.org/en-US/docs/Web/CSS/Pseudo-elements)

  **Example:**
  ```css
  div::first-line {
    color: red;
  }

  p::first-letter {
    color: blue;
  }

  span::before {
    content: '1';
  }

  span::after {
    content: '2';
  }
  ```

## Adjacent sibling combinator
* The **+** separates two selectors and matches the second element only if it immediately follows the first element, and both are children of the same parent element

**Example:**
```css
p + div {
  color: red;
}
```
```html
<p>Parragraph content</p>
<div>Red text sibling Div</div>
<div>Black sibling Div</div>
```

## General sibling combinator
* The **~** separates two selectors and matches the second element only if it follows the first element (though not necessarily immediately), and both are children of the same parent element

  **Example:**
  ```css
  p ~ div {
    color: red;
  }
  ```
  ```html
  <p>Parragraph content</p>
  <div>Red text sibling Div</div>
  <div>Red text sibling Div</div>
  ```

#### Practice
[Exercise 5](exercises/css/ex_5.md)
  
