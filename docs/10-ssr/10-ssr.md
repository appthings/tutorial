## Lab 10: Server-side Rendering (SSR) of Web Components

1. We saw in tutorial 9 that Web Components can be great for productivity by promoting reuse, and thanks to encapsulation they can improve maintainability as well. So far you saw components that are rendered client-side, beginning with JavaScript loading. Unfortunately, this dynamic loading still presents challenges for most search engines (only Google uses a virtual Chrome engine that executes JavaScript when crawling). Content rendered by Web Components can not be seen by all search engines. We also see that especially browsers that still require polyfills take a little longer to render Web Components, and we wish to reduce this 'time to glass' to an absolute minimum.

2. Fortunately, in many situations both issues can be overcome with _Server-Side Rendering_ (SSR). The idea of SSR is to make the server render the component and deliver the render result as part of the page HTML that is delivered to the browser. The user sees the content more quickly because the browser does not need to retrieve additional content for display. If the component needs additional browser interactivity (e.g. custom JavaScript on-click), we still load the component JavaScript into the browser to provide that functionality, and upgrade the (server-side generated) HTML with these features in the browser. We would call this kind of component a _hybrid_, as some features are delivered on the server, and some are delivered in the browser. The result of this technique is a greater perceived performance for the user as well as full visibility of the content by search engines. Depending on the frequency of content changes, the complete page may still be cached by a CDN. If not, it may take a little longer to prepare the main page response, but in many cases the server will have higher bandwidth and more resources to process the loading tasks than the user's device.

3. Download and unzip topseed-ssr-master.zip from <a href='https://github.com/topseed/topseed-ssr' target='_blank'>https://github.com/topseed/topseed-ssr</a> to your location of choice on your developer machine and open the project in VS Code. Open Terminal Shell ``(Ctrl+Shift+`)``, type `'cd ssr-topseed-io [Enter]'`, do the `'npm install [Enter]'` and then `'node index [Enter]'`. You should see console output 'Web server listening at http://localhost:9081'. In the browser, navigate to <a href='http://localhost:9081' target='_blank'>http://localhost:9081</a>, and visit Dashboard, List, Circle, Prelist and List menu items. If you use Prepros on this project, ensure that auto-compile for Pug is turned off.

4. Revisit the Dashboard page. It contains two server-side rendered components: 'Myssrcomp' and 'List'. Especially in Firefox and Edge it should be noticeable that these components display more quickly than the others. On the 'List' page, the component is rendered server-side as well. If you inspect the raw HTML in the browser (e.g. with 'Rightclick-View Page Source') you can find the component content 'Hi this is myssrcomp1' in the markup.

5. SSR components can use Shadow DOM for CSS encapsulation but they don't have to. We use a process called 'rehydration' in the browser to apply Shadow DOM.  On the server, we wrap the content to be subjected to Shadow DOM in a `<shadow-root>` tag. Inspect `/public/page/dashboard/index.pug` and find the call to  `TW.rehydrate('my-ssrcomp')`, which converts the tag to an actual Shadow DOM with its scoped CSS. (Efforts are underway with the WC3 to make this standard browser behavior, eventually eliminating the need for this JavaScript). In this example the content is rendered before the Shadow DOM is in place, leading to potential style conflicts, but we could avoid that with CSS of `shadow-root * {opacity:0}` or similar.

6. Inspect `/server/route/dashboard/index.js`. The route (installed in `/topssed-ssr-io/index.js`) renders the HTML of the named components 'Myssrcomp' and 'List' and embeds it in the otherwise static page HTML retrieved from `/public/page/dashboard/index.pug`. In our utility library at `/server/util/SR.js`, we use _skatejs/ssr_ for the actual server-side rendering of each component HTML, and _Cheerio_, a server-side version of JQuery to embed it in the page. In `/server/route/dashboard/index.js`, we also specify that the 'List' component has to obtain custom data before rendering by setting the `initFn` for this component (It is our good practice to keep business logic outside of components, i.e. framework-agnostic and thus more future-safe).

7. Inspect the 'List' component HTML Template at `/public/_webComp/List.pug` and see where we use the `<shadow-root>` tag to mark the Shadow DOM. The component JavaScript is separated out at `/public/_webComp/List.js` so it can be loaded separately from the client side for the upgraded 'hybrid' features (this is done in `/public/page/dashboard/index.pug` with a  call to  `TW.loadComp('/_webComp/List.js')`).

8. Inspect the 'List' component Custom Element JavaScript at  `/public/_webComp/List.js`. See how we use a test for 'module' in `connectedCallback` to trigger server-side only functionality. In this example, the component's `list` function is used on the server, and the `nav` function is used on the client. To provide compatibility with IE11, we would down-compile these ES6 components to ES5. With a little bit of work (such as a tag attribute `ssr='true'`), this component could be made fully _Universal_, i.e. usable as a hybrid as well as a pure client-side component. 

9. In practice, for our own components we decide on a case-by-case basis whether the component really needs a Shadow DOM, and whether it should be rendered server-side or client-side. Perceived performance and the need for SEO would be the main decision criteria.

10. Like tutorial 9, if this tutorial felt a little heavy, we would be happy to help get you started with in-house seminars, workshops and 'training the trainer'.  That applies to other labs as well.  Just email us at hi [at] appthings.io or contact us through <a href='https://m.appthings.io' target='_blank'>https://m.appthings.io</a>.