- [About the guidelines](#about-the-guidelines)
  - [CONTRIBUTING.md vs README.md](#contributingmd-vs-readmemd)
- [Getting Started](#getting-started)
  - [Version control](#version-control)
  - [Project management](#project-management)
  - [Tooling](#tooling)
  - [Other documentation](#other-documentation)
- [Browser and Device Support](#browser-and-device-support)
- [HTML](#html)
  - [HTML methodology and principles](#html-methodology-and-principles)
  - [HTML tools](#html-tools)
  - [HTML coding style](#html-coding-style)
- [CSS](#css)
  - [CSS Frameworks, bases and resets](#css-frameworks-bases-and-resets)
  - [CSS methodology and principles](#css-methodology-and-principles)
  - [CSS coding style](#css-coding-style)
  - [Directory structure](#directory-structure)
  - [CSS pre- and post-processing](#css-pre--and-post-processing)
- [JavaScript](#javascript)
  - [Third-party JavaScript and tools](#third-party-javascript-and-tools)
  - [Testing and debugging](#testing-and-debugging)
  - [JavaScript authoring](#javascript-authoring)
- [Accessibility](#accessibility)
- [Media](#media)
- [Fonts](#fonts)
- [Performance](#performance)
- [Deployment](#deployment)
- [Localization](#localization)

<hr />

<a id="about-the-guidelines"></a>

## About the guidelines

These guidelines were written to help developers further develop or maintain `Project: Climate`. I have removed identifying links and references so that this example could be made public. If you are a Knowit employee interested in more details about the original project, get in touch with the frontend developer:

- <tord.nylund@knowit.no> (front-end lead on the project)
- <tord.nylund@knowit.no> (author of the guidelines)

<a id="guidelinesmd-vs-readmemd"></a>

### CONTRIBUTING.md vs README.md

We suggest using your project's README.md file for information about installing, running and configuring the application. The CONTRIBUTING.md file can be used to cover the development practices your team adopts when working on the project.

<br />
<a id="getting-started"></a>

## Getting Started

<a id="version-control"></a>

### Version control

- Git repository (Github): <somelink>
    - Repository structure and branch managment:
        - `master / main`
        - `develop`
        - `test` ↻
        - `feature / fix`
    - `master` should always be the last and final version of your content.
    - `feature` and `fix` should be used for new content and branches, containting the ticket `number` and `name`. 
    - When task is complete, create a `PR` (pull request). Someone with insight to your current code should be the one reviewing.
    - When `PR` is complete and approved: merge branch into `test` branch.
    - When `testers` are complete and approve the new content: merge into `develop`.
    - `develop` should then do a `squash-merge` with `master` containing a patch-note list of new features and bug fixes.
    - *Note*: commits should be consistent with this format: `<Change Type>(<fileName>): <Your Change>`
    - *Example:* `fix(HomePage): Tweaked height of left section`


**Example branch:** *feature/my-new-feature-task-T123*

<br />

<a id="project-management"></a>

### Project management

- In the case of this project we used trello, but i do recommend using JIRA.
- Overall structure:
    - `New Requests`
    - `Active Tickets` or `In Progress`
    - `In Review` ↻
    - `In Test` ↻
    - `Complete`
- Every ticket that is not in `New Requests` should always assigned to someone, have detailed description for new features. Fixes and bug reports also require a detailed description of how they arrived at set problem (e.g, pictures, paths, clicks, browsers, screen sizes - the more the better).
- Developers should ideally not be the ones translating og understanding `New Request` tickets.

<a id="tooling"></a>

### Tooling

This section covers different tools you might be using as part of the project. We suggest agreeing on choosing a linter and code formatter that everyone will use in order to ensure a base level of consistency.
You can include information about tools such as:

- task runners (such as [Grunt](http://gruntjs.com/) or [Gulp](http://gulpjs.com/));
- dependency/package managers (such as [npm](https://www.npmjs.com/), [Bower](http://bower.io/) or [Composer](https://getcomposer.org/));
- scaffolding tools (such as [Yeoman](http://yeoman.io/));
- tools used to reinforce style (e.g. [Editor Config](http://editorconfig.org/), a linter such as [ESLint](https://eslint.org/), or a formatter like [Prettier](https://prettier.io/)).

<a id="other-documentation"></a>

### Design and development

If the project does not contain existing components or modules, you should discuss with designer what base values should be for fonts, spacing used, grid layout and agree on a overall standard that can be applied to both the design and the application styling. Try to go through these following points:

- Mobile design
- Tablet design
- Small desktop design / more responsive desktop design
- UU and UX
- Buttons various states (focused, active, etc.)
- Spacing
- Grid layout
- Font sizes
- Font families
- Colors / themes

<br />
<a id="browser-and-device-support"></a>

## Browser and Device Support

A very important note that has to be made and confirmed by project lead and customer; is which platform or device you want your application to be supported on. As mentioned above, it is good practice to always expect a design for smaller devices before you move to larger screens like desktops. This needs to be a collaborative effort in which both the designer, developer and project lead / customer agree on which device should be supported. In the case of this project, I initially developed the application with no mobile or tablet design and the consensus was never to develop for these devices. However, with no well defined points from project lead on these terms, I had to develop for them regardless - which increased the development time substantially.

Also remember to define the version of your browsers or devices, for testing purposes and future reference. 

In short terms:
- Well defined device / browser support
- Always develop with the mindset that things might change
- Make your code modular and easy to change
- Don't expect a polished product if these terms are not met

<br />
<a id="directory-structure"></a>

## Directory

### Structure

The project is currently structured the following:

- `assets`
- `components` (Less complex components / smaller components)
- `data` (Mockdata / language / constants, etc)
- `models` (Commonly used types and interfaces)
- `modules` (Complex components / larger components)
- `pages` 
- `services` (Commonly used helper and async -functionality)
- `styles`
  - `styling` (Commonly used variables, mixins and typography)
  - `app.scss`
  - `index.scss`

<br />
<a id="html"></a>

## HTML

By Norwegian law, our site needs to meet 35 of the 61 success criteria detailed in WCAG 2.0, and 27 of these criteria directly concern front-end development. The guidelines below have been written with those requirements in mind and will help us meet them.

### HTML methodology and principles

When writing new html templates for new components, it is important to remember which of these elements should be interactable or represent something to the user. Semantic representation should always be a priority, that; and various elements that should fulfill UU requirements.

A good idea is to create a specialized version of an element that lies within the same category so to speak: like a `<Text />` component for example. This allows for a singular point of entry if something needs to be adjusted, as well as forcing people to use semantic representation of various text elements, such as `<h1 />`, `<h2 />`, etc. Another neat thing about using defined elements is that you could always cement their ideal default state throughout your application.

### Elements

We try to use appropriate semantic HTML5 tags whenever we can. We try to be as precise as we can and use `div` and `span` elements sparingly.

- Here is [a nice example](https://www.w3.org/TR/2016/REC-html51-20161101/grouping-content.html#example-e49943ac) of rewriting some HTML using more specific elements.
- `div` and `span` tags are devoid of meaning; we use them only when we mean just that (e.g., for wrapping content for styling purposes only).
- We do not use `em`, `i`, `strong`, `b`, `br` or `hr` elements purely for styling purposes.
  - See the semantics of `em` and `strong` here: <https://www.w3.org/TR/html4/struct/text.html#h-9.2.1>
  - We prefer styling a span rather than using `b` or `i` tags: <https://www.w3.org/International/questions/qa-b-and-i-tags>
  - Breaks should be added directly to source text. Vertical space can be implemented using padding or a margin.
  - Horizontal lines can be implemented with a border or pseudo-element.

#### What elements should I use?

[This cheat sheet](https://learn-the-web.algonquindesign.ca/topics/html-semantics-cheat-sheet/) is a nice quick reference for the semantics of some popular tags; see also [this handy checklist](https://learn-the-web.algonquindesign.ca/topics/html-semantics-checklist/) for writing semantic HTML.
See [this W3C page](https://www.w3.org/TR/2016/REC-html51-20161101/dom.html#kinds-of-content) for more extensive documentation about elements used for particular types of content (e.g. heading, sectioning, and interactive elements).

### HTML tools

In this section, you can include the following:

- your HTML preprocessor (if applicable), such as [HAML](http://haml.info/) or [Jade](http://jade-lang.com/);
- your templating engine (if applicable), such as [Mustache](https://mustache.github.io/) or [Handlebars](http://handlebarsjs.com/);
- information about the backend architecture's influence on the frontend markup (if applicable).

### HTML coding style

If you have chosen not to use a common formatter/linter for HTML code, coding style specifications can be made here. You can also specify under what (if any) circumstances are HTML comments acceptable and how such comments will look and e.g. stripped out before going to production.

<br />
<a id="css"></a>

## CSS

### Introduction

In this project I have utilized a large amount of the `sass` library, which involves nested classes, mixins and static variables. As most css, none of these cases actually involve realtime updates based on value changes - but instead are all prebaked styles. However, more advanced / helpful functionality is now available and supported on pretty much every browser or device, such as: `css variables`.

In the case of this project, I have attempted to merge the best of two worlds: `mixins` and `css variables`. This merging of two worlds allows for structured and rule defined styling `"functions"`. Variables can change based on rules set for example in various media queries wrapped in a mixin, that again can be used as a wrapper in other components.

*Notes:*
- `css variables`
- `scss`
- `mixins`

### Structure

#### Global

Like in most projects, I defined a base style for every tag, like font family, size and so forth. This allows for a consistent and easily editable reference point. All components, modules and pages should always import a core reference to the `styling.scss` file, which will allow access to various utilities. If there is an easier way to import (by default) a global style file, then do that instead!

- `styles`
  - `styling`
    - `common`
      - `colors.scss`
      - `helpers.scss`
      - `typography.scss`
      - `variables.scss`
    - `styling.scss` (Core utiliy css file)
  - `app.scss`
  - `index.scss`

#### Components

Most of the more unique styling should always be locked to the component you are creating, for example:

- `button`
  - `Button.tsx`
  - `Button.scss`

However, it is often the case that you want different looks for the same component. If the internal functionality does stray too far from its intended purpose, you could always use the component base styling file as an import file and create a new folder within set component and apply more variations. For exmaple:

- `button`
  - `styles`
    - `ActionButton.scss`
    - `IconButton.scss`
    - `LinkButton.scss`
  - `Button.tsx`
  - `Button.scss` (Import other styles into this one for cleanliness)

#### Mixins & Classes

One of the main principles of this coding practice is to use very few predefined class references for specific styles. Instead you should tie styling to the component and not make copious global and smaller styles like: margins, padding, etc. If you want to avoid having too many boilerplate scenarios for your components, create mixin functionality you can reuse throughout your project (under `helpers.css`). 

I often use these two:

<br />

```scss
  // Helper:
  @mixin componentSize($x: auto, $y: auto, $p: 0, $m: 0) {
    width: $x;
    height: $y;
    padding: $p;
    margin: $m;
  }

  // Use example:
  .myClass {
    @include componentSize(
      20rem,
      10rem,
      1rem,
      0.2rem 0.1rem 0.5rem 0
    );
  }
```
**Illustration (0.1):** *Used when applying graphic scale. Could always apply different values inside this based on your parameter input.*

<br />

```scss
  // Helper:
  @mixin componentFlex($d: row, $jc: center, $ai: center) {
    display: flex;
    flex-direction: $d;
    justify-content: $jc;
    align-items: $ai;
  }

  // Use example:
  .myClass {
    @include componentFlex(column, flex-start, flex-end);
  }
```
**Illustration (0.2):** *Used aligning various thing with a very basic flex-grid*

<br />

However, it is often useful to have class references. If you really communicated properly with your designer and planned how the overall look of your application would be, you could always give every component a [Theme](#component-theme).

<a id="component-theme"></a>

#### Themes & Colors

There are various ways you could implement a theme or color scheme for your application. However, I find that in most cases it is ideal to stick to your own custom form of styling throughout your application. Instead of relying on overly complex libraries which can have their limitations and cause version issues.

1. Define your color scheme
2. Create css color base variables
3. Setup your theme by using each of these colors
4. Feel free to make mixin helpers, e.g:

<br />

```scss
  @mixin color($color-variable: --dark, $type: "color", $opacity: 1) {
    @if ($type == "color") {
      color: rgba(var(#{$color-variable}), $opacity);
    } @else if($type == "background") {
      background-color: rgba(var(#{$color-variable}), $opacity);
    } @else if($type == "border") {
      border-color: rgba(var(#{$color-variable}), $opacity);
    } @else if($type == "stroke") {
      stroke: rgba(var(#{$color-variable}), $opacity);
    } @else if($type == "fill") {
      fill: rgba(var(#{$color-variable}), $opacity);
    } @else {
      color: rgba(var(#{$color-variable}), $opacity);
    }
  }
```
**Illustration (0.3):** *A helper for setting up basic colors to a element*

<br />

Depending on how customizable you want your colors to be, you can create either a specific theme template for each component, specified with a `Dark` and `Light` theme for example. Within those types you could always define color for your text, background, border and icon elements.. etc. 

```jsx
  let themes = {
    Dark: {
      text: "#ffffff",
      background: "#000000",
      border: "#3b3b3b"
    },
  }
```
**Illustration (0.4):** *Very basic theme for a component and its elements.*

<br />

The ideal approach, in the case of this project, would be to feed every component with a base model / `interface` and then extend it based on you needs (follow illustration **0.5**).

```tsx
  // Base Interfaces File

  import { Theme } from "./types";

  export interface IComponentProps {
    theme: Theme
  }

  // New Component File

  interface IProps : IComponentProps {
    text: string,
  }

  export const MyNewComponent = () => {
    const { theme, string } = props;
  }
```
**Illustration (0.5):** *Depicts how you could create a base interface for your component library and then extend it for new property values.*

<br />

You should then have defined a theme object at the base of your application, with the use of the react`<Context />` component. Wrap your application with it and set your theme template like the one depicted in illustration **0.4**. You could always extend the theme object and apply additional functionality if so required.

Another neat thing you could do, instead of defining the colors in both your css files and your theme template, is instead reference the css -variables mentioned earlier (illustration: **0.6**)!

<br />

```tsx
  export const getColorCode = (color: colors, type: colorTypes = "rgb", opacity: number = 1) => {
    switch(type) {
        case "rgba":
            return `rgba(${getComputedStyle(document.documentElement).getPropertyValue(`--${color}`)}, ${opacity})`;
        case "rgb":
            return `rgb(${getComputedStyle(document.documentElement).getPropertyValue(`--${color}`)})`;
        case "hex":
            return `${getComputedStyle(document.documentElement).getPropertyValue(`--hex-${color}`)}`;
        default:
            return `rgb(${getComputedStyle(document.documentElement).getPropertyValue(`--${color}`)})`;
    }
  }
```
**Illustration (0.6):** *Depicts a way to fetch your css variabes instead of defining them in two places.*

<br />

### Dynamic Variables

This project frequently utilizes dynamtic variables that will, in this case, change based on screen size. An important note to add, is that these variables should be discussed with your designer, so that you know their spacing rule (or a `base-spacing`). You could always discuss if there are different spaces used for various scenarios, but should always reference these values when adding spacing throughout your application. *(Illustration 0.7)*

<br/>

```scss

// Place in your variables.scss -file

.base-variables {
    --base-spacing: 2rem;

    @include smallDesktop {
        --base-spacing: 1.5rem;
    }

    @include tablet {
        --base-spacing: 1.5rem;
    }

    @include mobile {
        --base-spacing: 1rem;
    }
}

// Place within your index.scss -file

html {
  @extend .base-variables;
  @extend .theme-main;
  @extend .typography;
}

```
**Illustration (0.7):** *Depicts how you could structure your variables to dynamically change within your scss constraints.*

**Note:** *You can also change these css variables through one of your js -scripts!*

<br />

<a id="javascript"></a>

## JavaScript

### React Code

In this project the code follows a consistent pattern with the use of sections seperating various parts of the code. Every component is also divided into their own categories:

- `component`
- `module`
- `page`

New content / reusable components are put into these categories based on their complexity. The less complex component functions are put into the `components` category, while more complex versions are put in the `modules` category. Pages are overall the most complex beasts you create and can contain both modules and components (same goes for modules). 

Other JavaScript related code, such as utility scripts should always be placed into their own service layer with `helper` functionality and `async` functionality. In other words: global or common functionality.

<br />

**Note: useContext**

When utilizing the `useContext` hook, it is ideal to keep all context handling within a `Page`. `Modules` and `Components` should always be fed data and not attempt to fetch it externally. This way, we can always know where the data-flow is set and avoid any deep dives into several modules and components before you figure out what to do.

Overall context usage:

- In regular / basic `components` (No)
- In `modules` (No)
- For global access (App or top of your hierarchy)
- For limited access (Pages)

The reasoning behind not placing every variable you want to access within the top of your hierarchy is because everytime you change a value - you will trigger a rerender for every child within the parent node.

<br />

*Example:*
- `/services/Utilities.ts / .js`
- `/services/DataService.ts / .js`

When it comes to the internal code structure, it is wise to separate various functions and types of logic into their own region. This will assist you in the future or help newer developers find what they are looking for. In this project each `component`, `module` and `page` follows this structure:

- `imports`
- `local interface` (most cases just `IProps` / component props)
- `component`
    - `Properties` (Static values)
    - `Lifecycle` (Usually: hooks states, useEffects, etc.)
    - `Other` or `Helper Functionality` (Internal helpers and such)
    - `Render Functionality` (Extra render related functionality)
    - `Render` (The return template)
- `export default component`

An additional note is to avoid adding styling or too many class references within a component and rather let the component utilize its own style and other common `styling` references available. If you want multiple styled versions of a component, it is always possible to add new ones by creating additional files. Just remember to let each component have their own unique `componentClass` or `classPrefix` as reference and build on those base values. 

<br />

```jsx

  interface IProps : IComponentBase {
    title: string
  }

  const MyComponent = (props: IProps) => {

    // ************************************
    // Properties
    // ************************************

    const { theme, title } = props;

    // ************************************
    // Render
    // ************************************

    return(
      <article>
        <h2> {title} </h2>
        <section>
          <h3></h3>
          <p></p>
        </section>
      </article>
    );

  }

  export default MyComponent;
  
```
**Illustration (0.8):** *A very basic look at how you could structure your component.*

<br/>

## Accessibility

External tools / references:
- [tools](http://a11yproject.com/resources.html)

## Media

In the case of this project, all icons and images are all svg files. The reason for this that most images requires scaling. In the case of icons, it would be ideal to use a icon-font for easy access and editing via css. However, in most cases this requires the designer to know which icons should be used beforehand and should be available when new icons are required. 

Icons are all retrieved via a `<Icon />` component whilst larger svg images are imported using the internal react component converter.

<br />

```tsx
  import banner from "../../assets/bannerImages/finding-the-path.svg";
```
**Illustration (0.9):** *Basic import of asset inside component*

<br />

```tsx
  import { ReactComponent as VerticalEmissionMeterGraphic } from "../../assets/bannerImages/vertical-emission-meter-graphic.svg";
```
**Illustration (1.0):** *Import asset and convert it to a react component*

<br />

## Fonts

There are multiple ways to setup a font reference, either download and add to your `assets` folder or `import`. In the case of this project it is implemented with the use of the [Google Fonts](https://fonts.googleapis.com). The `typography` file should then handle the distribution of various font families.

<br />

```scss
  @import url('https://fonts.googleapis.com/css2?family=Libre+Franklin:wght@400;700;800&display=swap');
```
**Illustration (1.1):** *Basic import of external font*

<br />

## Performance

This project was not developed with the use of performance measurement tools, but should be relatively performant.

Potential tools:

- Do you use performance budgets? If so, what [metrics](https://timkadlec.com/2014/11/performance-budget-metrics/) are you using to determine budgets? Where are you keeping track of performance budgets?
- How are you measuring your project's speed (e.g., using a tool like [Pingdom Speed Test](http://tools.pingdom.com/) or [Google PageSpeed](https://developers.google.com/speed/pagespeed/))?
- Do you use techniques decrease file size (such as [Gzip](https://css-tricks.com/snippets/htaccess/active-gzip-compression/) and [Image Optimization](https://developers.google.com/web/fundamentals/performance/optimizing-content-efficiency/image-optimization))?
- Do you use other performance-related tools in your workflow, like [WebPagetest](http://www.webpagetest.org/), [BigRig](https://aerotwist.com/blog/bigrig/) or [Speedcurve](https://speedcurve.com/)?

<br />

## Localization

Always develop with the mindset that there can be used multiple languages, create a basic language system and file. Does not take up too much development time and will help you in the long run. This project is developed with norwegian being the only available language. But it is possible to add an additional language file and edit the distributer logic. 