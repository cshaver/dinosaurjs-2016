# Single Page Access

## [@noopcat](https://twitter.com/noopcat)

> “We as developers have a multiplier effect on what we do.”
>
> “We write code to improve people’s lives.”
>
> Rob Deluca @robdel12

### Choice of tools
- Impact on users
- React, Angular, ember
- *(front-end frameworks)* - enormous paradigm shift on how we do work, very powerful, but prevent new challenges that we’re not used to working without
- Are these front-end frameworks accessible?

(Examples in ember)

1. Motor Ability
  - how we use our body to get the computer do what we want it to do
  - keyboard, mouse interface
  - mouse interface is the general assumption
  - motor abilities vary so widely - not everyone can use a mouse. some people predominantly get around by keyboard or only have access to *one button*.
  - Stephen Hawking uses a sensor on his cheek to cycle through elements on a page
  - **Is a mouse necessary for your site?**
  - `ember-template-lint` - actions may only apply to focus-eable eleements
  - `react-a11y`, protractor a11y plugin
  - tl;dr always use buttons and links - semantic HTML is your friend
2. Vision + Motor Ability
  - vision impaired - using a screen reader to navigate. still using a keyboard
  - **Dynamic content** - loss of cursor position
    - `ember-component-focus`
    - `react-focus-trap`
    - angular - custom solution
3. Screenreader Users
  - Problem:<br>
    ✅ server side page loads are announced by screenreaders<br>
    ❗️ client side page loads are not
  - `ember-a11y`, `a11y-announcer` for React
  - `LiveAnnouncer` in Material2 for Angular

tl;dr help users find their way
don't break native browser features

in addition to DOM, rendering tree, there is an accessibility tree. Accessibility inspector that comes with XCode (!!!)

### Takeaways
- Education
  - being aware of guidelines, ARIA spec
- campaign for a11y to be a part of your process
  - *not just bolted on at the end*.
  - Including product managers, CTOs as a part of the conversation
  - Estimate tasks with a11y in mind - e.g. need two days of research time to ensure you're doing it right
  - incorporate a11y testing into your test suite

### why do we program?
- we program to build things for other humans
  - humans are *not* “edge cases”
  - people that need assistive tech go through life feeling like an edge cases
- freedom of speech, freedom of information
- “moving the web forward”
  - new, exciting APIs to use in the browser, JS spec changing and evolving, sugar, language additions.
  - Have a look around outside your ecosystem - are we really moving the web forward if we are still leaving people behind consistently? Moving the web forward is providing more and more people access to information.

> “Computers do exactly what we tell them, and no more.”
>
> -- anonymous

- VoiceOver & Safari
- NVDA & Firefox
- JAWS & IE or Edge
