# Template: front-end development guidelines <!-- omit in toc -->

<!-- TOC -->

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

This is the KXB Frontiers Guidelines template. It is designed to help you and your team put together front-end development guidelines for your project.

Writing, reading and maintaining your guidelines should help you write more consistent, cohesive code more efficiently, produce a better quality front-end, and to make it easier for developers to get started in this codebase. We recommend making the guidelines a part of your codebase both in order to make changes to the guidelines visible and to make them easier to update.

You can use this section to add any other details about the nature of this document that are specific to your project.

<a id="guidelinesmd-vs-readmemd"></a>

### CONTRIBUTING.md vs README.md

We suggest using your project's README.md file for information about installing, running and configuring the application. The CONTRIBUTING.md file can be used to cover the development practices your team adopts when working on the project.

<a id="getting-started"></a>

## Getting Started

<a id="version-control"></a>

### Version control

In this section, you can include the following:

- Which version control system is used for the front-end codebase (e.g., [Git](https://git-scm.com/), [Subversion](https://subversion.apache.org/), [Mercurial](https://www.mercurial-scm.org/)). Include a link to your remote repository and any relevant information regarding hosting, access and administration.
- Details about the version control workflow your team is adopting. Will you be using Gitflow or feature branching? Will commits be squashed when merging into master?
- Any naming conventions your team is adopting. Will you name your branches using a particular syntax? Does your task management platform integrate with your VCS via prefixed commit messages?
- Details about how your team plans to do code reviews, if applicable.
- Information about deployment/integration to test and production environments. There is a separate section for [deployment](#deployment) towards the end of the template in case this warrants a section of its own.

<a id="project-management"></a>

### Project management

Include project management information in this section, like where issues are being tracked and how one gets access to the system. How should developers and others on the project write/structure bug reports and other issues? Is there anything else one ought to know about the project management workflow?

<a id="tooling"></a>

### Tooling

This section covers different tools you might be using as part of the project. We suggest agreeing on choosing a linter and code formatter that everyone will use in order to ensure a base level of consistency.
You can include information about tools such as:

- task runners (such as [Grunt](http://gruntjs.com/) or [Gulp](http://gulpjs.com/));
- dependency/package managers (such as [npm](https://www.npmjs.com/), [Bower](http://bower.io/) or [Composer](https://getcomposer.org/));
- scaffolding tools (such as [Yeoman](http://yeoman.io/));
- tools used to reinforce style (e.g. [Editor Config](http://editorconfig.org/), a linter such as [ESLint](https://eslint.org/), or a formatter like [Prettier](https://prettier.io/)).

<a id="other-documentation"></a>

### Other documentation

You can use this section for information about any additional documentation (or similar resources) related to the project, such as a design system or pattern library. Note where external documentation lives, who maintains it, and what happens when it is updated.

<a id="browser-and-device-support"></a>

## Browser and Device Support

In this section, you can:

- Include a list explicitly covering all devices and browsers to support and to what extent. This can include details about graded support of specific components when applicable.
- Include suggestions on how to develop against older browsers (e.g. IE11), if applicable.
- Maintain a list of devices and browsers on which developers are expected to test their code as well as how and when such developer testing should take place.
- Document the smallest viewport size to support and any other similar constraints.

<a id="html"></a>

## HTML

### HTML methodology and principles

You can use this section to document the general principles your team follows when writing HTML:

- If your site needs to meet e.g. accessibility requirements due to universal design legislature, specify the success criteria and how to meet them. This can include information about apposite elements and attributes for your particular project and links to external resources that will help developers meet the success criteria (see the **HTML** section in the `/examples/example-bank.md` example guidelines).
- Are there any other standards or best practices your team has adopted or will adopt? If these are documented elsewhere, provide a link. Here are some examples:
  - https://codeguide.co/#html
  - http://manuals.gravitydept.com/code/html
- Does your CSS methodology place any requirements on how your HTML markup is written?

### HTML tools

In this section, you can include the following:

- your HTML preprocessor (if applicable), such as [HAML](http://haml.info/) or [Jade](http://jade-lang.com/);
- your templating engine (if applicable), such as [Mustache](https://mustache.github.io/) or [Handlebars](http://handlebarsjs.com/);
- information about the backend architecture's influence on the frontend markup (if applicable).

### HTML coding style

If you have chosen not to use a common formatter/linter for HTML code, coding style specifications can be made here. You can also specify under what (if any) circumstances are HTML comments acceptable and how such comments will look and e.g. stripped out before going to production.

<a id="css"></a>

## CSS

### CSS Frameworks, bases and resets

If your team is using a framework like [Bootstrap](https://getbootstrap.com/), [Foundation](http://foundation.zurb.com/) or [Bulma](https://bulma.io/), provide a link to the documentation. Be sure to specify any ways in which your team's approach deviates from the standard framework.

You can also use this section to list other external stylesheets, like CSS bases (such as [Normalize](https://necolas.github.io/normalize.css/) or [resets](http://meyerweb.com/eric/tools/css/reset/).

<a id="methodology-and-general-principles-for-writing-css"></a>

### CSS methodology and principles

If your team follows certain principles/guidelines or subscribes to a particular CSS authoring methodology, provide links to the documentation. If your team's methodology and conventions deviate in some way from the external documentation, be sure to document how (and why).

Examples of CSS Guidelines:

- [Harry Roberts' CSS Guidelines](http://cssguidelin.es/)
- [PageUp People CSS Guidelines](http://www.yellowshoe.com.au/standards/#css)
- [Gravity Department CSS Guidelines](http://manuals.gravitydept.com/code/css)
- [Mark Otto's Code Guide](http://codeguide.co/#css)

Examples of CSS-authoring methodologies:

- [SMACSS](https://smacss.com/)
- [BEM](https://en.bem.info/method/)
- [OOCSS](http://oocss.org/)
- [utility first](https://frontstuff.io/in-defense-of-utility-first-css)

You can also provide details about specific CSS techniques or strategies your team uses, such as [critical CSS](https://www.smashingmagazine.com/2015/08/understanding-critical-css/).

### CSS coding style

If you have chosen not to use a common formatter/linter for your CSS, coding style specifications for e.g. spacing can be made here. You can also include more general CSS style guidelines, concerning:

- Ordering of declarations within a rule (e.g., https://smacss.com/book/formatting#grouping)
- Property values (e.g., when to use `px`/`rem`/`em` values)
- Constraints on available spacing and font sizes
- Use of CSS-in-JS
- Your team's commenting strategy
- How your team manages CSS TODOs

<a id="directory-structure"></a>

### Directory structure

- You can use this section to describe the directory structure (and file import) conventions your team follows.

### CSS pre- and post-processing

- If your team using a pre-processor like [Sass](http://sass-lang.com/) or [Less](http://lesscss.org/) provide links to documentation and guidelines (e.g., [Sass Guidelines](https://sass-guidelin.es/) for Sass).

- If your team using a post-processor like [Prefixfree](https://leaverou.github.io/prefixfree/) or [Autoprefixer](https://github.com/postcss/autoprefixer), include a link to the documentation and information regarding things like customization.

<a id="javascript"></a>

## JavaScript

### Third-party JavaScript and tools

- If your project leverages a UI library (like [jQuery](https://jquery.com/), [Vue](https://vuejs.org/) or [React](https://reactjs.org/)) and/or framework (like [Next.js](https://nextjs.org/) or [Nuxt.js](https://nuxtjs.org/)), provide links to the documentation.
- Make note of polyfills/shims used in your project and any relevant documentation.
- Does your team use a module bundler like [Webpack](https://webpack.js.org/) or [Parcel](https://parceljs.org/)? Where can developers get an overview of the project's dependencies?

<a id="testing-and-debugging"></a>

### Testing and debugging

If your team testing tools like [Jasmine](https://jasmine.github.io/), [Jest](https://jestjs.io/), [Karma](https://github.com/karma-runner/karma) or [Selenium](http://docs.seleniumhq.org/), provide documentation links.

You can provide additional testing information as well, such as how to use tools like [Storybook](https://storybook.js.org/docs/testing/react-ui-testing/) for manual testing, debugging in IDEs, etc.

### JavaScript authoring

- Is there a style guide or are there general principles your team should follow when writing JavaScript? Examples:
  - https://github.com/airbnb/javascript
  - https://github.com/rwaldron/idiomatic.js
  - https://github.com/styleguide/javascript
- Are there any further elaborations on JavaScript authoring style?
- Does your team employ a particular methodology for annotating code (e.g. [JSDoc](https://jsdoc.app/))? Are there any relevant tools complimenting it that developers should know about (e.g., [Visual Studio Code's IntelliSense](https://code.visualstudio.com/docs/languages/javascript#_jsdoc-support) based on JSDoc annotations)?

## Accessibility

- What accessibility requirements does the site need to meet?
- What [tools](http://a11yproject.com/resources.html) are you using to check the accessibility of your site?

## Media

- Provide a short description of how your team handles:
  - icons (e.g., inline SVG? Sprite sheet? Icon fonts?)
  - responsive images (e.g., using `srcset` and `<picture />`)
- Is your team using any [tools](https://addyosmani.com/blog/image-optimization-tools/) to optimize and serve images? Is there a DAM?

## Fonts

- How does your project load custom fonts?
- Do you use any tools to help implement web fonts (such as [Font Squirrel](https://www.fontsquirrel.com/))?
- Do you use a service to manage and serve custom fonts (such as [Fonts.com](https://www.fonts.com/) or [Typekit](https://typekit.com/))?

## Performance

- Do you use performance budgets? If so, what [metrics](https://timkadlec.com/2014/11/performance-budget-metrics/) are you using to determine budgets? Where are you keeping track of performance budgets?
- How are you measuring your project's speed (e.g., using a tool like [Pingdom Speed Test](http://tools.pingdom.com/) or [Google PageSpeed](https://developers.google.com/speed/pagespeed/))?
- Do you use techniques decrease file size (such as [Gzip](https://css-tricks.com/snippets/htaccess/active-gzip-compression/) and [Image Optimization](https://developers.google.com/web/fundamentals/performance/optimizing-content-efficiency/image-optimization))?
- Do you use other performance-related tools in your workflow, like [WebPagetest](http://www.webpagetest.org/), [BigRig](https://aerotwist.com/blog/bigrig/) or [Speedcurve](https://speedcurve.com/)?

## Deployment

How is your front-end code integrated into a production environment?

## Localization

If your website is served in different languages, consider what do you need to address when localizing for other languages and use this section to document it.
