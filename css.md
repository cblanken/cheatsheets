# CSS

Capital letters (A, B, C, etc.) are used to indicate when syntax can be applied to essentially any CSS selector.
## Syntax & Common Properties
```css
/* comments */

/* specify CSS rule */
<selector> {
    <rule1>: <value>;
    <rule2>: <value>;
}
```

## Basic Selectors Types
```css
/* any selector */
* {...}

/* id selector */
#idName {...}

/* class selector */
.className {...}

/* tag selector */
tag {...}

/* use ":" to designate a pseudo class
A:pseudo-class {...}
```

## Combinator Selectors
Combine selectors for more specificity
```css
/* descendant selector */
A B {...} /* target all B elements which are inside a A element */

/* adjacent selector */
A + B {...} /* target B elements which are immediately preceded by an A element */

/* direct descendant selector */
A > B {...} /* target B elements which are direct children of A (only children not grandchildren) */

/* sibling selector */
A ~ B {...} /* target B elements which are preceded by an A element (less strict version of "+" selector */
```

## Attribute Selectors
Target elements with the attribute specified in square brackets [...]
```css
A[attribute="value"] {...}

/* some simple regex can be used when selecting on an attribute */
a[href*="google.com"]   /* select any <a> tag with a href attribute containing "google.com" */
a[href^="http"]         /* select any <a> tag with a href attribute beginning with "http" */
a[href$=".com"]         /* select any <a> tag with a href attribute ending with ".com" */

/* custom attributes can be used to apply rules, e.g. to select all anchor tag images */
a[data-filetype="image"] {...}

/* ~ can be used to target attributes with a space-seperated list of values e.g. */
a[data-info~="external"] {...}
```

## Pseudo Selectors
Pseudo selectors can target an element in a certain state
```css
/* Common pseudo-classes */
A:before {...}  /* target the element _before_ an element A */
A:after {...}   /* target the element _after_ an element A */
A:hover {...}   /* target an element on hover */
A:not(B) {...}  /* target all elements EXCEPT for the B selector */

/* Nth child and type selectors */
A:nth-child(n) {...}        /* target the nth child of parent element A */
A:nth-last-child(n) {...}   /* same as above starting from the last child */
A:nth-of-type(n) {...}      /* target the nth element of type A */
A:nth-last-of-type(n) {...} /* same as above starting from the last element A */
A:first-child {...}         /* target the first child of an element A */
A:last-child {...}          /* target the last child of an element A */
A:only-child {...}          /* target elements which are the only child of its parent */
A:only-of-type {...}        /* target elements that don't have any siblings */
A:first-of-type {...}       /* target the first sibling of type A */

/* Link pseudo-classes */
a:link {...}    /* target all anchor tags which have not yet been clicked */
a:visited {...} /* target all anchor tags which have been clicked */

/* target fragments of an element with A::pseudo-element, notice the :: */
A::first-letter {...}   /* target the first letter of an element */
A::first-line {...}     /* target the first line of an element */

/* target a UI element (radio button or checkbox) that has been checked */
input[type="radio"]:checked {...}
```

## Multiple Selectors
```css
/* a css rule can be applied to multiple selectors by using a comma delimited list prior to 
the definition e.g. set backgorund color to blue for h1, h2, and h3 elements */
h1,
h2,
h3 {
    background-color: blue;
}
```

# Flexbox

# CSS Grid

