<hr />

## About the handbook : React & TypeScript

<hr />
<br />

This document will contain various code snippets and examples that can point you in the right direction when it comes to structured, neat and clean code. The idea is to have an easy way figuring out how you could solve various issues, and keep your project relatively clean without too much bloating. This document will show you various examples regarding the use of React and TypeScript.

<a id="about-the-guidelines"></a>

<br />
<hr />

## Why React?

<hr />
<br />

### Why

React is a very common JavaScript library that allows for easy setup, calls and general management of elements, data and logic. The implementation of hooks and general use of functional components allows for a more intuitive setup and usage. This example bases itself on the `Component Library` system, where you have one dedicated collection of generic components and modules that can be exported and used within a seperate web application instance. 

### Tools of use
- `typeScript` (for strict typing)
- `sass` (no predefined styling library)
- `classnames` (for easy class implementations)
- `lodash` (for more advanced algorithmic functionality)
- `uuid` (for generated unique ids)

<br />
<hr />

## File Structure

<hr />
<br />

Lets start with the basics, how would you structure your react project? As there are various ways to structure one, this handbook will try to limit it to one commonly used and clean variation. 

<br />

### Overall

<br />

```
⌵ src
    > assets
    > components
    > modules
    > pages
    > stories
    > utility
        > models
        > services
        > data
    > styling
```
**Illustration (0.1):** *Another way to structure base file*

<br />

```
⌵ src
    > assets
    > components
    > data
    > models
    > modules
    > pages
    > stories
    > services
    > styling

```
**Illustration (0.2):** *One way to structure your base files*

<br />

### Assets

<br />

```
⌵ assets
    > images
    > icons
    > fonts
    ...etc
```
**Illustration (0.3):** *Structure here is not paramount, but it is always nice to have some consistency*

<br />

### Components & Modules & Pages

<br />

```
⌵ components
    ⌵ button
        ⌵ variations
            ActionButton.scss
            ...etc
        Buttons.scss
        Button.tsx
    ...etc

⌵ modules
    ⌵ myModule
        ⌵ variations
            StyleTwo.scss
            ...etc
        MyModule.scss
        MyModule.tsx
    ...etc

⌵ pages
    ⌵ myPage
        ⌵ variations
            StyleTwo.scss
            ...etc
        MyPage.scss
        MyPage.tsx
    ...etc
```
**Illustration (0.4):** *One way to structure a react component folder*

<br />

```
⌵ components
    ⌵ button
        ⌵ variations
            ActionButton.scss
            ...etc
        Buttons.scss
        index.tsx
    ...etc
```
**Illustration (0.5):** *Another way to structure a react component folder*

<br />

### Stories

<br />


```
⌵ stories
    ⌵ styling
        Stories.scss
    myComponent.stories.tsx
    myModule.stories.tsx
    myPage.stores.tsx
    ...etc

```
**Illustration (0.6):** *One way to structure a story folder*

**Note:** *The stories style file should implement your core styling, as stories are a seperate instance*

<br />

### Utility

<br />

```
⌵ utility
    ⌵ services
        ⌵ asyncServices
            MyAsyncService.ts
            ...etc
        ⌵ helperServices
            MyHelperService.ts
            ...etc
        ...etc
        MyServicesHandler.ts
    ⌵ models
        ⌵ common
            > interfaces
            > types
            > enums
        > myUniqueModel
        ...etc
        ModelHandler.ts
    ⌵ data
        ⌵ content
            Constants.ts
            Language.ts
            PagesContent.ts
            ModulesContent.ts
            ...etc
        DataHandler.ts
```
**Illustration (0.7):** *One way to structure your utility folder*

**Note:** *This structure might vary from project to project, but this is a potentialt general use structure*

<br />

### Styling

<br />

```
⌵ styling
    ⌵ base
        Typography.scss
        Variables.scss
        Colors.scss
        Helpers.scss
    index.scss
    Styling.scss
```
**Illustration (0.8):** *One way to structure your styling folder*

<br />
<hr />

## Code Structure

<hr />
<br />

In this bit I will go over various basic code examples and structures that would be wise to utilise for future development or potentialt code improvement. 

<br />

### Component, Module and Page Structure

An important note regarding the creation of `components` and `modules` is the data handling. Components should be minimalistic and not require a lot of data handling, instead they should only be fed data and not fetch it internally. The same principle is to a degree applied to `modules` as well, they are however more complex components and can therefore contain more logic and in rare cases internal fetching of data. The idea is to leave all fetching and distribution of data to the `useContext` references or `page` components.

<br />

```tsx

import React, { useState, useEffect } from "React"; 
import { IComponent } from "../utility/Models/ModelHandler"; // Contains base properties defined within your models files
import "./MyComponent.scss"; // The style for your component

interface IProps extends IComponent {
    // Add unique properties here
}

const MyComponent = (props: IProps) => {

    // ************************************
    // Properties
    // ************************************

    const classPrefix = "my-component";
    const { 
        id, 
        className, 
        focused, 
        active, 
        disabled, 
        etc... 
    } = props;

    // ************************************
    // Lifecycle
    // ************************************

    const [myState, setMyState] = useState<any>();

    useEffect(() => {
        // Do something here everytime your state changes
    }, [myState]);

    // ************************************
    // Helper & Other
    // ************************************

    const myHelperFunction = () => { }

    // ************************************
    // Render Functionality
    // ************************************

    const getElemenet = () => {
        return <></>;
    }

    // ************************************
    // Render
    // ************************************

    return(
        <semanticTag
            className={classnames(classPrefix)}
        >
            { getElemenet() }
        </semanticTag>
    );
}

export default MyComponent;

```
**Illustration (0.9):** *One way to structure your react components, modules and pages*

<br />

#### Tips & Tricks

An important note regarding illustration `(0.9)` is the use of sections and consistant placement of your functionality. It might not seem that important to you at the time, but it will definitely help as you progress and expand your application. It will also make it easier for other developers to find their way to various things - or help you in the same manner. 

Instead of duplicating components, try instead to generate them with a render function and array of data.

<br />

```tsx
import classnames from "classnames";
import { IComponent } from "../utility/Models/ModelHandler";
import "./MyComponent.scss";

interface IProps extends IComponent { }

const MyComponent = (props: IProps) => {

    // ************************************
    // Properties
    // ************************************

    const classPrefix = "my-component";
    const { 
        id, 
        className,
        theme,
        focused, 
        active, 
        disabled,
    } = props;

    // ************************************
    // Render
    // ************************************

    return(
        <semanticTag
            className={classnames(classPrefix, {
                [`${className}`]: className,
                [`${classPrefix}-${theme}`]: theme,
                [`${classPrefix}-active`]: active,
                [`${classPrefix}-disabled`]: disabled,
                [`${classPrefix}-focused`]: focused,
            })}
        >
            { getElemenet() }
        </semanticTag>
    );
}

export default MyComponent;
```
**Illustration (1.0):** *Use of classnames*

<br />

### Data & Models

When it comes to data and model handling, you could always structure it as is `(0.7)`. However, it would perhaps be wise to define your data in a json format - this will allow for easier implementation of async functionality when you want to fetch it from an external source. 

<br />

```
⌵ utility
    ⌵ models
        ⌵ common
            ⌵ interfaces
                IComponent.tsx
                IModule.tsx
                IPage.tsx
            > types
            > enums
        > myUniqueModel
        ...etc
        ModelHandler.ts
```

```tsx
interface IComponent {
    id?: string,
    className?: string,
    children?: React.ReactNode | string | number,
    theme?: Theme,
    tooltip?: string,
    focused?: boolean,
    disabled?: boolean,
    active?: boolean,
    render?: boolean,
}

interface IModule extends IComponent { }

interface IPage extends IComponent { }
```
**Illustration (1.1):** *How you could structure your model files*

<br />
<hr />

## Styling Structure

<hr />
<br />

This react version bases itself on custom setup of styling and little to no use of external styling libraries. With that said, it is often the case that you need to use external styling libraries or custom renders of complex components. The idea with the styling folder is to setup all your common styles like typography, commonly used variables and colors as well as your best friend: helpers. These helpers or `mixins` can reduce a lot of development time and code clutter within your style files.

<br />

### Helper Examplers

<br />

```scss

@mixin size($x: auto, $y: auto, $p: 0, $m: 0) {
  width: $x;
  height: $y;
  padding: $p;
  margin: $m;
}

```
**Illustration (1.2):** *Mixin helper example for consistent sizing*

<br />


```scss

@mixin flex($d: row, $jc: center, $ai: center) {
  display: flex;
  flex-direction: $d;
  justify-content: $jc;
  align-items: $ai;
}

```
**Illustration (1.3):** *Mixin helper example for basic flex grid layout*

<br />

```scss

@mixin position($x: 0, $y: 0, $z: auto, $type: "default", $anchorPoint: "top-left") {
  @if($type == "default") {
    @if($anchorPoint == "top-left") {
      left: $x;
      top: $y;
      z-index: $z;
    } @else if($anchorPoint == "bottom-right") {
      right: $x;
      bottom: $y;
      z-index: $z;
    }
  } @else if($type == "transform") {
    transform: translate($x, $y);
    z-index: $z;
  } @else if($type == "transform3d") {
    transform: translate3d($x, $y, $z);
  }
}

```
**Illustration (1.4):** *Mixin helper example for consistent positioning*

<br />

```scss

@mixin mobile {
  @media screen and (max-width: $first-breakpoint-value - 1) {
    @content;
  }
}

@mixin tablet {
  @media screen and (max-width: $second-breakpoint-value - 1) {
    @content;
  }
}

@mixin smallDesktop {
  @media screen and (max-width: $third-breakpoint-value - 1) {
    @content;
  }
}

```
**Illustration (1.5):** *Mixin helper example for reponsive styling*

<br />

```scss

@function hexToRGB($hex) {
  @return red($hex), green($hex), blue($hex);
}

```
**Illustration (1.6):** *Mixin helper example for converting hex to rgb*

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
**Illustration (1.7):** *Mixin helper example consistent coloring*

<br />

```scss
@import "../../styling/Styling.scss";

.my-component-class-prefix {
    @include size(100%, 100%);

    position: relative;
    max-width: 100vw;
    min-width: 100vw;

    &__image {
        @include size(100%);

        object-fit: cover; /*magic*/
        object-position: center center;
    }

    &__text-grid {
        @include size(auto, auto, calc(var(--base-spacing)*2));

        position: absolute;
        bottom: 55%;
        left: 5%;
        transform: translate(0, 0);
        z-index: 999;
        border-radius: var(--base-spacing);
        max-width: calc(100vw / 2);

        @include color(--background-dark, "background", 0.8)
    }
}
```
**Illustration (1.8):** *How you could structure you component styling*

<br />

```scss

$my-static-variable: 20px; // Static variables that cannot be edited runtime
--my-css-variable: 20px; // Variables that can be referenced externally and edited runtime (please use these instead)

@extend .someClass; // Extend with a existing class
@mixin myFunc(); // Custom functionality
@include (); // Call and use of mixins (custom functionality)

```
**Illustration (1.9):** *Sass functionality*

<br />



<br />
<hr />

## Storybook

<hr />
<br />

The use of storybook is a great addition to your application. It allows for displaying all your components and their variations. You can also live edit your component parameters, allowing for testing and showcases to customers.

The main feature however, is the possibility to setup stories with your own mockdata - a fast way for prototyping your application with your existing components.

<br />

### Setup - base styling

When you install your storybook library, you will be handed a `stories` folder where all you story related things go. In here, add your own `styling` folder and reference your external one for consistent styling.

<br />

```

⌵ stories
    ⌵ styling
        Stories.scss
    > components
    > modules
    > pages

```
**Illustration (2.0):** *Example of a storybook folder structure*

<br />

```tsx

import { ComponentStory, ComponentMeta } from '@storybook/react';
import Button from '../components/button/Button';
import Text from '../components/text/Text';
import "./styling/Stories.scss";

// ************************************
// Story: Button : Template
// ************************************

const TemplateButton : ComponentStory<typeof Button> = (args) => {
    return(
        <Button {...args} >
            <Text
              type="label"
              text="Button"
            />
        </Button>
    );
}

export const DemoButton = TemplateButton.bind({});

// ************************************
// Story: Button : Default Args
// ************************************

DemoButton.args = {
  type: "action",
  theme: "dark"
}

// ************************************
// Story: Button : Default Export
// ************************************

export default {
    title: "Demos/Components",
    component: Button,
    subcomponents: { Text }
} as ComponentMeta<typeof Button>;

```
**Illustration (2.1):** *Example of a button component story that can be live edited*