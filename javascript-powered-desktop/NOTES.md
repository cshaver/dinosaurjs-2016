# The Age of the Javascript-Powered Desktop, *Evan Morikawa*

## [@e0m](https://twitter.com/potch) <br>evan@nylas.com

### Electron
- Desktop apps powered by JS

### Chromium
- Browser aka Backend aka Main Process (C++)
  - Spawns:
    - Renderer (tab)
    - Renderer (tab)
    - Renderer (tab) <- our entire world as web devs

### Electron
- Browser aka Backend aka Main Process (**nodejs**)
  - Spawns:
    - Renderer (tab) **nodejs**
    - Renderer (tab) **nodejs**
    - Renderer (tab) **nodejs**

### Nylas N1
- access to whole backend proccess - main.js
- given access to an electron API that opens a tab

### The age of the JS Desktop
1. “Native” experience
    - Pull applications out of “uncanny valley” of native apps
    - Right click menu
    - Menu toolbar
    - Look & feel - CSS. No cross-browser issues - if it works in latest Chrome it’s fine.
    - Styling specific to OSX, Windows, etc
2. Process control
3. Performance
4. Data Storage & Offline
