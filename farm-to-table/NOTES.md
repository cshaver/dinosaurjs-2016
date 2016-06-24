How the internet works
@zeigenvector
http://jenna.is/at-dinosaurjs

1. IP Address lookup
  - Assuming that caching never works
  - Host name lookup (local hosts file, `/etc/hosts`)
  - Request to local DNS server (ISP, any DNS server, googles is 8.8.8.8)
  - goes through local router that checks cache also (LANsplaining)
  - Hits DNS server, using UTP - lowest level of protocol but delivery isn’t guaranteed at all, like throwing frisbees at people
  - DNS server receives request and checks its cache, looks up address by recursively looking up other server friends (while client waits for answer)
  - "No, but mabye ask '.com'?"
  - to google.com name server => do you know where www.google.com is ? DNS server will cache response from nameserver
  - Your computer caches that answer
  - `dig www.google.com`

2. Opening a socket
  - dont normally see port numbers on urls - http defaults to :80, https defaults to :4443
  - TCP is a reliable stream, very important as it underlies HTTP, SSH, FTP, email
  - Client establishes communication with webserver
    - "will you talk to me" / SYN
    - "sure" / SYN-ACK. -> derivation and some new info
    - "awesome" / ACK. -> derivation of SYN-ACK and some added info
  - more than one connection is going to be opened
  - TCP has congestion control - the size will start small and ramp up to make sure all the information is received and accounted for
  - TCP is constrained by speed of light, so distance between computers plays a significant role with latency
  - CDNs => put assets as close to users as possible `tcpdumb`

3. Security Stuff
  - TLS, handshake that’s more complicated. (predecessor was SSH)
  - "hello"
  - "hello here's some "
  - "secret stuff"
4. HTTP request
  - HTTP 1.1
  - GET, request, headers
  - uses HTTP daemon such as apache or ngx
  - server breaks down request to get params
    - request method (get post delete options etc), URL is `GET`
    - domain from request `google.com`
    - path => `/`

 5. HTTP Response
  - Respond with HTML based on cache
  - ```
  HTTP/1.1200 OK
  [other headers]
  <
  <doctype !html><html>...</html>
  ```
   - Could get 400 (client went wrong), 500 (server went wrong)
   - Can use `curl` to get HTTP responses
 - gzip takes repeated substring and replaces them with references => reduces by ~70%
 - As soon as the browser starts receiving bytes, its starts to parse it.
5. HTML Parsing
  - Speculative or look-ahead preparser (JS, CSS, images) to get from server immediately
  - If it finds external resources, it uses request from same host or does DNS dance again
  - Translate into characters based on specified encoding (UTF8), to DOM tree
  - Unlike most parsers, HTML parser is not context free because the html spec requires that HTML be forgiving. **fault tolerant** - you never see an HTML syntex error. a lot of code in the parser goes into fixing author mistakes. (browsers are a LOT of code to fix mistakes)
  - Size correlates to how long it takes to download them - gzip, compress, minify, optimize images
  - Browsers impose limits on how many parallel downloads - this is a bottleneck. get around this by serving from multiple hostnames. or combine files together - concat JS, CSS, image sprites, caching
  - Parser runs into JS include and STOPS
    - javascript is 'blocking'. It can manipulate the dom - any HTML that gets added gets added to the main parser. while the script is downloading the browser won't stard any other downloads, even from other host names. this explains the "js at the bottom of the page" optimization
    - get around this by adding deferred attribute to script - won't hald document Parsing
    - more recently, can put in async attribute to signal that JS should be downloaded and executed in different thread (promise that you won't call document.write)
  - CSS is blocknig as well, DOM construction will also be blocked
    - just like HTML, css must be converted into something it can work with (CSSOM). also context-free. looks like a tree, 'cascade'.
    - JS can read and modify the DOM, can also read and modify the CSSOM
  - CSSOM is made, JS continues to be parsed and executed until we reach the end of the HTML document
  - CSSOM and DOM tree combined to the render tree and begins the paint process
  - browser holds off on rendering anything until DOM and CSSOM trees are constructed
  - good idea to put stylesheets at the top of the page
  - putting stylesheets at the bottom will prevent progressive rendering
  - spec says CSS should go in the headers
  - rendering tree corresponds to DOM tree, but not one-to-one
    - no non-visual dom elements (display: none, <script> tags, etc)
  - rendering tree contains info about what nodes exist, but not what they look like
  - layout process, root render, starts with HTML element of the document, continues with each renderer that requires it. recursive process
  - in order to not do a full layout for
  - dirty bit system. the layout that is changed marks itself as "dirty" or needing layout. dirty or children are dirty. global or incremental (done incrementally based on a timer)
  - painting process
    - rendering tree is parsed again
    - global or incremental (only dirty regions are repainted)
  - HTML document fully downloaded & parsed - HTML marked as interactive, documentReady event is fired
  - scripts marked as deferred are executed
  - scripts downloaded & parsed, documentLoaded event is fired

## HTTP/2

A lot of performance checks wont be necessary with HTP2
