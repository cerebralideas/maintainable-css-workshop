# Welcome to the Maintainable CSS Workshop

## Instructions

1. Please fork from https://github.com/cerebrl/maintainable-css-workshop
2. Clone to your local computer
3. Go to www.jsbin.com or your favorite live code editor
4. Copy the starter code from here to the editor and follow the instructions

## Ready? Okay, let's get started!

### Selector specificity

Selector specificity is defined by:

> Specificity is the means by which a browser decides which CSS property values are the most relevant to an element and therefore will be applied. Specificity is only based on the matching rules which are composed of css selectors of different sorts.
> – Mozilla Docs

It's calculated in a very weird way. See Specifishity for more details: http://www.standardista.com/css3/css-specificity.

Specificity is one of the major reasons for CSS complexity. Continuously increasing specificity to overcome this and that for CSS style overrides is a mess. Luckily, there's a solution:

TCEM: a way to author classes in a structured way in order to reduce the need for decendent selectors or nesting. TCEM docs are here: https://github.com/cerebrl/tcem-css.

#### Start the specificity challenge and use TCEM to simplify!

**Pro tip**: doubling up on selectors that you have no recourse to simplify is a trick that keeps your selector at a single level, but ups the specificity. E.g.:

```
.myComponent.myComponent {}
```

### Basic Layout

Laying out an application can be a daunting task, especially if you want it to be rock-solid, yet flexible/fluid. The secret is not to use any properties that alters the element in relation to the document flow.

The normal document flow is the natural way elements interact relationally on the page. Inline elements are horizontally placed next to each other, while block elements take up the full width and stack vertically. This is the most predictable and resilient state of a layout.

That's because as the viewport changes or elements grow and shrink, all the neighboring elements will adjust accordingly in a very predictable manner. Only break this when you absolutely have to!

What breaks document flow:

- The `float` property
- The `position` property: absolute, fixed and sticky

#### Start the basic layout challenge using `inline-block` as the layout property!

**Pro tip**: `inline-block` has one side-effect, and that's the unwanted whitespace between elements. There are solutions:

- On the "containers" for the elements, use `font-size: 0;`, and then go back to `font-size: 1rem;` on the `inline-block` element
- Don't put whitespace in the HTML between the elements
- Use HTML comments to remove the whitespace and still preserve your carraige returns 

### Advanced Layout

At time, you need to do some tricky things with layout:

- Horizontal and vertical centering
- Equal height columns with different content heights
- Fixed widths combined with fluid widths

Of course, there's `flexbox`, and it solves many of your issues, but some can't use it. So, here's a bulletproof way to do this with support all the way back to IE8.

`display: table` for the win! No, it's perfectly accessible and is NOT layout with HTML tables.

#### Start the advanced layout challenge using `display: table` and `display: table-cell`!

**Pro tip**: applying style properties to the elements with table properties can get a bit weird, like negative margins (it just won't work).

### Stacking Context

> Stacking context is the three-dimensional conceptualization of HTML elements along an imaginary z-axis relative to the user who is assumed to be facing the viewport or the webpage. HTML elements occupy this space in priority order based on element attributes.
> Mozilla Docs

Stacking context seems to be a pretty big mystery to many, and the one thing that many may not understand is there can be more than one stacking context. If you have more than one, an element with `z-index` will never be able to move relative to an element in another stacking context.

Here's a simple example of two stacking contexts:

Stacking context A:
	1. Element 1
	2. Element 2
	
Stacking context B:
	1. Element 1
	2. Element 2
	
The idea here is only context A and B can move forward or backward, but A:1 cannot move independently in front of B:1. Here are things that trigger a stacking context:

- `position`: `absolute` or `relative`
- `overflow`: `hidden`
- `opacity` < 1
- `transform`
- `filter`
- `will-change`

#### Start the stacking context challenge now: fix the bug that prevents the modal background from being in front of the header.

### Questions?
