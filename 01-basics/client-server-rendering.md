# Client Side vs Server Side Rendering

## Client Side Rendering

In Client Side Rendering, browser is responsible for rendering the web page. The server sends a basic HTML File & a Js bundle (after site has been deployed on a server). Browser runs the Js bundle which generates & displays UI. After Initial load, all updates & navigation happen in browser using Js. without reloading entire page.

- It reduces Server load, as server mainly handles API/ data requests & not page rendering.
- It leads to Interactive, dynamic user Experience, smoother navigation & real time updates.
- It also means slower initial load times, because browser needs to download & execute Js before showing content & SEO Challenges as search engines may find indexing content difficult on client-side.

## Server Side Rendering

In Server Side Rendering, the server generates the complete HTML for each page and sends it to the browser. The browser displays the page immediately, and then JavaScript can take over for further interactivity.

For each new page request, server renders React Component into HTML which is then sended over to client. Browser displays this HTML & React hydrates it to make it interactive.

- This means faster Initial load times, as browser recieves ready-to-go HTML.
- It means SEO optimisation as search engines can index pre-rendered content.
- Better experience on slow networks as browser does less work here. 
- It also means, Slower Navigation as each new page needs a round trip to server, more server resources & more complex development & deployment.

> **Hydration** is only used with SSR. In this, when HTML from server is loaded by browser on client side, React matches it with its V-DOM, attaches event handlers & listeners to existing HTML elements & takes over DOM management from here onwards. It brings interactivity & performance in SSR apps as full UI re-render is not needed & SEO optimisation also takes place.
