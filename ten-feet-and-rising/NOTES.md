# 10 Feet and Rising, *Potch, Developer Advocate Mozilla*

## [@potch](https://twitter.com/potch) <br> [potch.github.io/tv-talk](https://potch.github.io/tv-talk)

## [Corsica](https://github.com/mozilla/corsica)

### Dashboards and Stuff

### Corsica
- Websockets and iframes all over the place

#### Regularly Scheduled Programs
- switches every two minutes
- transit times
- what's for lunch?
- open jobs

#### Public Access Programs
- Submitting a pull request or google slides

#### On-Demand Programming
- Tablet as remote, queue up information that they want
- PUPPY BUTTON

#### “How do I get on TV?”
- What kind of content works well on a television?
- Needs to be large print - “10 foot UI”
- Angular occlusion of a television is not that different from a phone close to your face => TVs are far away mobile phones that you can’t touch

###### Viewport Units
- Size of an element on the page in terms of the size of the Viewport
- `1vw` => 1% of viewport width, `1vh` => 1% of viewport height
- `1vmin`, `1vmax` => 1% of whichever is smaller/larger

No viewport-specific media query - more or less impossible to know the difference between a large monitor or a TV. Some solutions are using a TV-specific URL or button to switch to large-view UI.

`@media (min-aspect-ratio)`
`window.matchMedia()`

###### Accessibility
- For everyone!
- `tabIndex` is so important. Sometimes all the user has is a D-pad and an "OK" button
- Keyboard input
- Focus states and active states

### How do I get a browser on my television?
- Built-in browsers are sometimes available but extremely low-capability
- Firefox TV OS with Panasonic
- Chrome Cast has a full API for taking "Chromium Content" (web HTML5 content) and putting it on the television
  - Chrome browser, Google Cast Extension as dependencies
- Amazon FireTV HTML5 app support, similar process to ChromeCast setup
- Still works best today - a computer plugged into a television

### A smarter remote
- WebSockets server
- How to get the initial content to the tv:
  - mDNS (zeroconf, Bonjour)
    - local network discovery for other devices
    - otherdevice.local
  - [FlyWeb](https://wiki.mozilla.org/FlyWeb) (experimental)
    - can discover nearby FlyWeb services
  - DIAL protocol
    - Chromecast, Smart TVs, etc
  - Bluetooth
    - Don’t need to be on the same network!
    - WebBluetooth is still experimental
  - WebRTC
    - Low-latency!
    - Still need a handshake method (third party / server to discover both)
    - Encrypted PTP connection

### Why bother today?
- Need people to experiment with that environment so we can have best practices.
- Nothing better than writing JS/HTML/CSS and seeing that on a television
- Want to make sure that the stuff that is wanted is prioritized

[tv.youtube.com/](http://tv.youtube.com/) - full TV-first experience
