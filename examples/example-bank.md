# Front-end development guidelines for banking portal <!-- omit in toc -->

## Table of Contents <!-- omit in toc -->

<!-- TOC -->

- [About the project behind these guidelines](#about-the-project-behind-these-guidelines)
- [About the guidelines](#about-the-guidelines)
  - [CONTRIBUTING.md vs README.md](#contributingmd-vs-readmemd)
- [Getting started](#getting-started)
  - [Version control](#version-control)
  - [Project management](#project-management)
  - [Code authoring](#code-authoring)
  - [Design system](#design-system)
- [Browser and device support](#browser-and-device-support)
  - [Internet Explorer 11 and Microsoft Edge](#internet-explorer-11-and-microsoft-edge)
- [HTML](#html)
  - [Elements](#elements)
    - [What elements should I use?](#what-elements-should-i-use)
    - [Important elements for the project](#important-elements-for-the-project)
      - [Heading elements (h1-h6)](#heading-elements-h1-h6)
      - [Sectioning elements (`<article>`, `<aside>`, `<nav>`, `<section>`)](#sectioning-elements-article-aside-nav-section)
      - [Other elements](#other-elements)
  - [Attributes](#attributes)
    - [ARIA attributes](#aria-attributes)
    - [The `class` attribute](#the-class-attribute)
  - [Other accessibility notes](#other-accessibility-notes)
    - [Keyboard navigation](#keyboard-navigation)
    - [Forms, validation and errors](#forms-validation-and-errors)
    - [Skip link](#skip-link)
    - [Managing focus](#managing-focus)
    - [For users with visual impairments](#for-users-with-visual-impairments)
- [CSS](#css)
  - [Methodology and general principles for writing CSS](#methodology-and-general-principles-for-writing-css)
    - [CSS-in-JS](#css-in-js)
    - [Comments and TODOs](#comments-and-todos)
  - [Directory structure](#directory-structure)
  - [CSS Grid & IE11](#css-grid--ie11)
  - [Gradients](#gradients)
  - [Property values](#property-values)
    - [Fonts](#fonts)
  - [Pre- and post-processing](#pre--and-post-processing)
- [JavaScript](#javascript)
  - [Testing and debugging](#testing-and-debugging)
  - [Authoring](#authoring)
- [Media and fonts](#media-and-fonts)

<hr />

## About the project behind these guidelines

These example guidelines were written to help us develop a brand new portal for a Norwegian bank. We have removed identifying links and references so that this example could be made public. If you are a Knowit employee interested in more details about the original project, get in touch with one of its front-end developers:

- <Christian.Grimsgaard@knowit.no> (front-end lead on the project)
- <Maja.Jaakson@knowit.no> (author of the guidelines)

<hr />

<a id="about-the-guidelines"></a>

## About the guidelines

These extensible guidelines exist to help us write more consistent, cohesive code more efficiently, produce a better quality front-end, and to make it easier for developers to get started in this codebase.

The guidelines are a part of the codebase for this project both in order to make changes to the guidelines visible and to make them easier to update.

<a id="guidelinesmd-vs-readmemd"></a>

### CONTRIBUTING.md vs README.md

The project README contains information about how to install, run and configure the application, whereas the guidelines (CONTRIBUTING.md) cover the development practices our team adopts when making changes to the project.

<a id="getting-started"></a>

## Getting started

<a id="version-control"></a>

### Version control

- Git repository (Azure DevOps): <https://dev.azure.com/...>
  - We currently only have a `master` branch and `feature` branches. We expect our version control workflow to change once we start deploying to multiple environments. Suggested future workflow:
    - `master`, `develop`, and `feature` branches, where:
      - `develop` represents active code which auto-deploys to our development environment.
      - `feature` branches are branched from and merged back into `develop` via pull requests.
      - When we are ready to deploy to a test environment, `develop` is merged into `master`, triggering an automatic deploy to the test environment for testing.
      - Any changes (e.g., urgent fixes) made directly to `master` should be merged back in ASAP.
  - `feature` branch naming convention: `feature/VF-561-descriptive-feature-name`
  - Pull Requests/Code Review
    - When your PR is complex, walk through it with your reviewer.
    - For simple PRs, reviewers can just read through on their own.
    - When completing a PR, delete the branch (this is the Azure DevOps default) and squash the commits whenever these make sense.

<a id="project-management"></a>

### Project management

- We use JIRA for managing all issues: <https://link.to.jira.no>
  - Should be opened in Incognito Mode so it doesn't interfere with your Knowit AB login

<a id="code-authoring"></a>

### Code authoring

Everyone working on the project uses the same linter and code formatter to ensure a base level of consistency.

- We use [ESLint](https://eslint.org/) with the [airbnb config](https://www.npmjs.com/package/eslint-config-airbnb), plus some extra rules (see `.eslintrc.js` at the root of the project).
- We use [Prettier](https://prettier.io/) for code formatting with the [ESLint integration](https://prettier.io/docs/en/integrating-with-linters.html).

<a id="design-system"></a>

### Design system

We make use of the bank's design system: <https://designsystem.bank.no/>

- Use the design system's components whenever possible.
- Accessibility guidelines: <https://designsystem.bank.no/...>
- When creating a new component, create a new story for it and import to Storybook.

<a id="browser-and-device-support"></a>

## Browser and device support

- [This device list](https://link.to.confluence.page/) covers all phones and tablets to be supported.
- The smallest phone to support is the iPhone 4S (640x960).
- We (should) support the default browser on all devices.

<a id="internet-explorer-11-and-microsoft-edge"></a>

### Internet Explorer 11 and Microsoft Edge

When installing a new package or adding modern features/functionality, consider whether that package should be transpiled, a new polyfill is needed, or a CSS fallback is required for the site to be viewable in IE11 and Edge. (You can also check [Can I use...](https://caniuse.com/) to see what browsers support HTML/CSS/JS features and to what extent.)

Early and regular testing of the site in IE11 and Edge makes it easier to ensure the site will perform as best it can in those browsers.

<a id="html"></a>

## HTML

By Norwegian law, our site needs to meet 35 of the 61 success criteria detailed in WCAG 2.0, and 27 of these criteria directly concern front-end development. The guidelines below have been written with those requirements in mind and will help us meet them.

<a id="elements"></a>

### Elements

We try to use appropriate semantic HTML5 tags whenever we can. We try to be as precise as we can and use `div` and `span` elements sparingly.

- Here is [a nice example](https://www.w3.org/TR/2016/REC-html51-20161101/grouping-content.html#example-e49943ac) of rewriting some HTML using more specific elements.
- `div` and `span` tags are devoid of meaning; we use them only when we mean just that (e.g., for wrapping content for styling purposes only).
- We do not use `em`, `i`, `strong`, `b`, `br` or `hr` elements purely for styling purposes.
  - See the semantics of `em` and `strong` here: <https://www.w3.org/TR/html4/struct/text.html#h-9.2.1>
  - We prefer styling a span rather than using `b` or `i` tags: <https://www.w3.org/International/questions/qa-b-and-i-tags>
  - Breaks should be added directly to source text. Vertical space can be implemented using padding or a margin.
  - Horizontal lines can be implemented with a border or pseudo-element.

<a id="what-elements-should-i-use"></a>

#### What elements should I use?

[This cheat sheet](https://learn-the-web.algonquindesign.ca/topics/html-semantics-cheat-sheet/) is a nice quick reference for the semantics of some popular tags; see also [this handy checklist](https://learn-the-web.algonquindesign.ca/topics/html-semantics-checklist/) for writing semantic HTML.
See [this W3C page](https://www.w3.org/TR/2016/REC-html51-20161101/dom.html#kinds-of-content) for more extensive documentation about elements used for particular types of content (e.g. heading, sectioning, and interactive elements).

<a id="important-elements-for-the-project"></a>

#### Important elements for the project

<a id="heading-elements-h1-h6"></a>

##### Heading elements (h1-h6)

- Each heading element represents the heading of its section (be this a `<section>` or a section implied by the heading).
- The heading of each section should be unique (i.e., a section starting with an `h1` tag should not include another `h1` tag). 1-6 stand for the rank/importance of the heading and should be used accordingly.
- **Note:** we do not use `h2-h6` elements to markup subheadings, subtitles or taglines unless the element still acts as a heading for a new section/subsection. Please have a look at [the W3C's examples](https://www.w3.org/TR/2016/REC-html51-20161101/common-idioms-without-dedicated-elements.html#subheadings-subtitles-alternative-titles-and-taglines) of suggested markup to use for subheadings (hint: use `<p>` or `<span>` tags).
- We avoid skipping heading levels (e.g., avoid using `<h3>` as the subsection headings for a section with an `<h1>` heading).

<a id="sectioning-elements-article-aside-nav-section"></a>

##### [Sectioning elements](https://www.w3.org/TR/2016/REC-html51-20161101/dom.html#sectioning-content) (`<article>`, `<aside>`, `<nav>`, `<section>`)

- An `aside` element represents a part of the page only indirectly related to the main content, such as a list of related links. Use cases:
  - Right-hand button/link list on dashboard page
  - Category navigation on FAQ article page
- An `article` element represents a complete, self-contained part of the page. It should not contain a `main` element. We identify articles by including an `h1-h6` heading as a child of the `article` element. Use cases:
  - FAQ question and answer block on FAQ article page
- A `section` element represents a generic but thematic grouping of content. As with articles, we identify sections by including an `h1-h6` heading as a child of the `section` element. Use cases:
  - My recent invoices on the Contract page
- A `nav` element represents a set of navigation links. We only wrap link sets with a `nav` element if they constitute a major navigation block (e.g., site or sub-section navigation). We ensure a consistent ordering of the items in menus appearing on multiple pages of the site. Use cases:
  - Main/site navigation in Main Menu component
  - FAQ category navigation on FAQ article page

<a id="other-elements"></a>

##### Other elements

- Times and dates are be expressed using the `time` element. Wrapping human-readable date/time content with this element lets us set a datetime attribute with the date/time in a machine-readable format, allowing for features such as adding a date to a calendar. See usage notes here. Use cases:
  - timeline
  - invoice list
- The content of the `main` element is unique and directly related to the central purpose or topic of the page.
  - The element does not contain site-wide navigation, generic footers, banners, breadcrumbs, or any other content that is repeated across multiple pages.
  - This element indicates to assistive devices that it holds the page's main content.
  - Use the Main component on all pages to wrap the main content (the skip link links to its ID).
- The only children of `<ol>` and `<ul>` elements are `<li>` elements.
- All email addresses and phone numbers should be linked, e.g. `<a href=”tel:+14123815500″>1 (412) 381-5500</a>`.

<a id="attributes"></a>

### Attributes

- No two elements on the page should have the same `id` value.
- Each page should have a meaningful `title` (especially if they have public/search engine-accessible content, e.g. the FAQ page).
- Each label should have the correct `id` as its `for` attribute value. This ensures that e.g. the field/control will be active if the label is clicked and shows screen-reader users the relationship between the label and the field/control.
- The main language for the site is set on the custom Html component in `/pages/_document.js`.
  - In the event that the site design changes and we include non-Norwegian content on the site, we will ensure (screen-reader) [users are informed of the content's language](https://www.w3.org/TR/UNDERSTANDING-WCAG20/meaning-doc-lang-id.html).
  - Images (e.g., logo in header) linking somewhere should have `alt` text regarding the link, not the content of the image.

<a id="aria-attributes"></a>

#### ARIA attributes

When should we use ARIA properties in this project? (The points below are based on MDN's [when-to-use ARIA guidelines](https://developer.mozilla.org/en-US/docs/Learn/Accessibility/WAI-ARIA_basics#When_should_you_use_WAI-ARIA).)

- Only use ARIA when you need to. _We rely on native HTML features_ to provide semantics used by assistive devices and only use ARIA to fill in the gaps.
- The `role` attribute values can help us go beyond HTML5 semantics to provide signposts to different functional areas, e.g `search`, `tabgroup`, `tab`, `listbox`, etc.
- Good semantic HTML will ensure users have _keyboard access to interactive elements_ on the page. However, in cases where it is inappropriate to use e.g. `button` or an `a` with `href`, one can use `tabindex` as a means to place focus on non-interactive elements. See [non-interactive elements under the Other accessibility notes section](#nie) for more details.
- You might need more than good, semantic HTML to communicate how a complex UI feature works to screen-reader users. For example, on the Dine fakturaer page, one might need to use ARIA features to explain the relationship between the filter toggles and the list of invoices. Some useful resources:
  - [The related WCAG 2.0 success criterion](https://www.w3.org/TR/UNDERSTANDING-WCAG20/ensure-compat-rsv.html);
  - [A reference library of accessible controls](https://dequeuniversity.com/library/);
  - Some [MDN content about the accessibility of non-semantic controls](https://developer.mozilla.org/en-US/docs/Learn/Accessibility/WAI-ARIA_basics#Accessibility_of_non-semantic_controls) in a UI, including a nice [example of guiding screen-reader users through a complex (tabular) widget](https://developer.mozilla.org/en-US/docs/Learn/Accessibility/WAI-ARIA_basics#Guiding_users_through_complex_widgets).
- If a button or UI control's action does not follow from its semantics, provide a description using the `aria-describedby` attribute. Use the `withAriaDescription` function in `/utils/renderHelper.js` to wrap your controls 😁

[Read more about the W3C's definitions of ARIA states and properties here](https://www.w3.org/TR/wai-aria-1.1/#state_prop_def).

<a id="the-class-attribute"></a>

#### The `class` attribute

When creating a new component, give it a descriptive class.

- This should be the first class in the list, coming before all Tailwind and other presentation-centric classes.
- _Why?_ Because these descriptive classes won't typically be used as style hooks; we add them in to make it easier to scan/read through our HTML output (hence putting them at the beginning of the list).
- Syntax: Descriptive classes follow the two-dashes BEM naming convention: `component/block-name__elem-name--mod-name--mod-val`
  - Documentation: <https://en.bem.info/methodology/naming-convention/#two-dashes-style>

Descriptive classes can be added to sub-elements of components whenever it improves HTML legibility or the class is needed as a selector (for CSS/JS).

<a id="other-accessibility-notes"></a>

### Other accessibility notes

- We use Windows Narrator and VoiceOver on the Mac for accessibility testing on Windows/OS X. (**NOTE:** this actually changed over time; contact the team for details)
- We use the `sr-only` Tailwind class for screen reader users (e.g., table with data equivalent to a contract timeline). (Using `display: none;` or `visibility: hidden;` will hide the text from all users, including those with screen readers!)
- Difi recommends using the [WAVE web accessibility tool](https://wave.webaim.org/) to evaluate our site's compliance with WCAG 2.0.
- We aim to maximize compatibility with current and future user agents, including assistive technologies.
- According to Difi, if JavaScript is required for using the site, [we need to inform users about this](https://uu.difi.no/krav-og-regelverk/losningsforslag-web/feilhandtering#2_2).
- We always use text instead of images of text.
- Elements with the same functionality should maintain a[ consistent design across the site](https://www.w3.org/TR/UNDERSTANDING-WCAG20/consistent-behavior-consistent-functionality.html).

<a id="keyboard-navigation"></a>

#### Keyboard navigation

Test to ensure that keyboard navigation works on your component in the contexts in which it will appear.

- Testing your component in context will help you ensure users do not fall into [keyboard traps](https://www.w3.org/TR/UNDERSTANDING-WCAG20/keyboard-operation-trapping.html).
- Users should be able to use tab and shift+tab to navigate between all interactive elements of a page (links, buttons, form fields, etc.) in a logical order.
- Any function one can perform with a click or tap should be possible to perform using only the keyboard. In particular, all `nav` menus should be fully navigable by keyboard alone.
- <a id="nie"></a>[Non-interactive elements](https://www.w3.org/TR/2016/REC-html51-20161101/dom.html#kinds-of-content-interactive-content) (such as `<div>`, `<span>`, `<p>`, and `<a>` with no `href` value) are not natively focusable, but they can be made focusable by adding `"tabindex=0"` to allow for interaction. When these elements are given click handlers, they should have at least one keyboard listener, e.g. `onKeyDown`. You can use the `getClickAndKeyEvents` function in `/services/eventService.js` to trigger your `onClick` function when either the enter or space key is pressed.
- Here is a link with more [detailed keyboard accessibility information](https://webaim.org/techniques/keyboard/), including handling focus, tabbing order, tabindex techniques and testing.

<a id="forms-validation-and-errors"></a>

#### Forms, validation and errors

- Before implementing a form, please have a look at [Difi's guidelines and suggestions for implementing forms](https://uu.difi.no/krav-og-regelverk/losningsforslag-web/skjema) and [this detailed MDN example](https://developer.mozilla.org/en-US/docs/Learn/Accessibility/WAI-ARIA_basics#Form_validation_and_error_alerts) of creating an accessible form.
- Ensure your form is keyboard accessible by making sure you can use:
  - the space key to select a radio button or checkbox value;
  - the arrow keys to move between drop-down options;
  - the enter key to trigger the onClick action on buttons.
  - If you use a clickable span or div as part of the form, see the [notes for `onClick` events for non-interactive elements](#nie).
- Provide [labels/instructions for form fields/controls](https://www.w3.org/TR/UNDERSTANDING-WCAG20/minimize-error-cues.html) to minimize the chance of errors. Follow labelling best practices to make the label-control relationship perceivable to users of assistive devices.
- Changing the setting of a [UI component](https://www.w3.org/TR/UNDERSTANDING-WCAG20/consistent-behavior-unpredictable-change.html#user-interface-componentdef) does not automatically cause a [change of context](https://www.w3.org/TR/UNDERSTANDING-WCAG20/consistent-behavior-unpredictable-change.html#context-changedef) (e.g., content change on page or change in focus) unless the user has been advised of the behavior before using the component (e.g., filter toggles).
- An error message should clarify how to fix the related error (see [Difi's error accessibility guidelines](https://uu.difi.no/krav-og-regelverk/losningsforslag-web/feilhandtering)):
  - It should [show where the error occurred, including a textual description](https://www.w3.org/TR/UNDERSTANDING-WCAG20/minimize-error-identified.html);
  - It should [suggest](https://www.w3.org/TR/UNDERSTANDING-WCAG20/minimize-error-suggestions.html) how to fix the error;
  - The message should remain visible while addressing the error (e.g., changing a field's value).
- We ensure `required` is present on required fields.

<a id="skip-link"></a>

#### Skip link

Provide a skip link at the top of each page, allowing the user to bypass things like the homepage and hamburger links and get to the main content of the page in one click/keystroke.
The design system on skip links:

- <https://designsystem.bank.no/...skip-link>
- <https://designsystem.bank.no/...focus-on-first-page>

Our skip link is similar to the one implemented on [WebAIM](https://webaim.org/techniques/skipnav/), which is brought into focus on the first tab keystroke. **NOTE:** the skip link does not work on iOS!

<a id="managing-focus"></a>

#### Managing focus

Ensure that whatever element is currently in focus is visibly marked as such. The following is paraphrased from [the design system](https://designsystem.bank.no/.../focus) and WCAG 2.0:

- On SPA-like pages, set the focus on the `main` element after a navigation action.
- When a menu is opened, set the focus within the menu. Set the focus back on the page's `main` content when the menu is closed.
- When a modal-like menu is open (e.g. main, notifications), preclude focus on the content behind it so the user only can navigate inside the menu.
- Moving focus to an element should not result in an [unexpected action or context change](https://www.w3.org/TR/UNDERSTANDING-WCAG20/consistent-behavior-receive-focus.html).

<a id="for-users-with-visual-impairments"></a>

#### For users with visual impairments

- Test to ensure every page of the site displays properly, without loss of function, on all relevant devices:
  - at 200% zoom;
  - with 200% font size.

Ensure an appropriate contrast level for text and buttons. Chrome has a [WCAG contrast checker extension](https://chrome.google.com/webstore/detail/wcag-contrast-checker/plnahcmalebffmaghcpcmpaciebdhgdf) we can use to help us meet the A-level requirements.

Ensure all links are clearly distinguished from body text in some way.

Ensure tables are accessible – relevant for contract timeline table (which never happened...)

- [Here are the Difi accessibility guidelines for tables](https://uu.difi.no/krav-og-regelverk/losningsforslag-web/tabeller).
- Here is MDN's [Advanced Table Features and Accessibility page](https://developer.mozilla.org/en-US/docs/Learn/HTML/Tables/Advanced).

<a id="css"></a>

## CSS

<a id="methodology-and-general-principles-for-writing-css"></a>

### Methodology and general principles for writing CSS

We are taking a **utility-first approach** to styling and are using the [Tailwind CSS framework](https://tailwindcss.com/). To keep custom CSS to a minimum, please make use of the Tailwind utility classes in your markup whenever sensible. In cases where the utility-first approach does not work, use/create a _descriptive_ class as a selector. See [Classes under the HTML section](#class-attribute) for more information.

If you are unsure as to how a new component should be styled, have a look at similar pre-existing components. If you are still unsure (or no existing component is similar to the one you are implementing), see if your question is addressed by [these CSS guidelines](https://cssguidelin.es/). And if you're still unsure, ask a friend 🥰

<a id="css-in-js"></a>

#### CSS-in-JS

We only use CSS-in-JS when styling SVGs (see `/components/MainMenuItem.js` for an example).

<a id="comments-and-todos"></a>

#### Comments and TODOs

We only write SCSS comments. If you need to revisit a piece of CSS, please leave a TODO so we can remember to fix your issue before it makes its way into master.

<a id="directory-structure"></a>

### Directory structure

Custom styles for individual components are SCSS partials under `/styles/components` with filenames like `_my-new-component.scss`. Import your partial in `/styles/components/components.scss`.

<a id="css-grid--ie11"></a>

### CSS Grid & IE11

We are using a modified version of the [Tailwind CSS Grid plugin](https://github.com/tailwindcss/plugin-examples/tree/master/plugins/css-grid). The configuration is in `/tailwind.config.js` and the plugin source code is in `/styles/plugins/css-grid/index.js`.
We use PostCSS to add prefixes for grid in IE11, but this is only used for the site header. The grid classes actually use `display: flex;` for IE11 because the latter does not support grid-gap and other grid properties we leverage for the layout in modern browsers.

<a id="gradients"></a>

### Gradients

We define custom gradients in `/styles/plugins/gradient/index.js`.

<a id="property-values"></a>

### Property values

We use `px` values for borders, border-radii, shadows, and other similar properties. Following Tailwind CSS, we also use `px` values for media query viewport widths. We size everything else in `rem`.

<a id="fonts"></a>

#### Fonts

We use the classes below, which correspond to the design system's font sizes. (The only exception is the `amount` text on the `NotificationsMenuToggle` component, which has a font-size under 14px.)

- 14px - 0.875rem - .text-sm
- 16px - 1rem - .text-base
- 20px - 1.25rem - .text-lg
- 24px - 1.5rem - .text-xl
- 32px - 2rem - .text-2xl
- 48px - 3rem - .text-3xl

<a id="pre--and-post-processing"></a>

### Pre- and post-processing

- Processing is configured in `postcss.config.js`.
  - [PostCSS](https://postcss.org/) website
  - Sass [Documentation](https://sass-lang.com/documentation) and [Guidelines](https://sass-guidelin.es/)
  - Autoprefixer's grid support for IE11 has been enabled (but is only being used for the site header).

<a id="javascript"></a>

## JavaScript

The project uses **Node v10.14.1**, **Next.js v9**, **React v16.8.3**, and ReactN. Documentation:

- https://nextjs.org/docs
- https://reactjs.org/docs/getting-started.html
- https://www.npmjs.com/package/reactn
  For an up-to-date list of other dependencies, check out `/package.json`.

<a id="testing-and-debugging"></a>

### Testing and debugging

Front-end testing will be done manually; we will not be using any test tools in development. Storybook will be used for testing components; check out <https://storybook.js.org/docs/testing/react-ui-testing/>

Please see `README.md` for information regarding running the project with the Visual Studio Code debugger.

<a id="authoring"></a>

### Authoring

- We are using [JSDoc](https://jsdoc.app/) to annotate our code. This allows us to write documentation directly in the source code, right alongside the code itself. [Visual Studio Code provides IntelliSense](https://code.visualstudio.com/docs/languages/javascript#_jsdoc-support) based on your JSDoc annotations. The JSDoc tool can also [scan your source code and output HTML documentation](https://jsdoc.app/about-getting-started.html#generating-a-website).
- We use function components only with hooks for local state and follow the [Airbnb React/JSX Style Guide](https://github.com/airbnb/javascript/tree/master/react).
- We write models, factories, and services for all data we receive from API requests. We also write models for complex components.

<a id="media-and-fonts"></a>

## Media and fonts

- We do not expect to use non-svg images.
- Fonts are from [the design system's UI library](https://designsystem.bank.no/...), `bank-ui-lib`.
- Favicons generated using https://realfavicongenerator.net/
