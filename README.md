# TopSeed

TopSeed aims to be a showcase of best practices and approaches for designers and front end developers
who want to build stunning mobile-first web apps with some of the best technologies
available now. Some may call it a stack. Some may call it an architecture. 

TopSeed may provide some answers to those 
who look for great designs.

What technologies make our cut? Those that let us be the most
productive and creative. And that we know to be maintainable. And that we expect 
to be future-safe.

Architecture is like a kindergarden: we put the shoes here, the jackets over there,
and now we know where to find things. We propose approaches that make it easy
to design and develop cutting edge web apps.

We welcome scrutiny and feedback from anyone who tries to follow our approaches. 
We also welcome code contributions from seasoned designers and developers

## Some best practices demonstrated:
- Single Page Application (SPA)
- Designer friendly
- SPA with SEO
- SPA and AMP
- Server side data-binding and in-browser data binding
- Loosely coupled to architectures
- Web Components
- Mostly static (easy to maintain/develop and scale)


## Getting started with a 'hello world':

To run:
- install node.js with NPM from <http://nodejs.org>.
- A recent version is v7.6. You can check with $ node -v
- Download and unzip this project
- Open a command prompt in the project root and execute the following commands:  
$ cd webApp  
$ npm install (Note: this may take a moment to respond)  
$ node index    

Now open your favorite browser on localhost:8081 (or any other port proposed by the console). To see SPA, click menu one and then two, notice that it does not reaload the header.
If you add ?w=1 to the URL you get www page, else it is mobile/AMP (in 'two'). In production, we use subdomains www. or m.
to differentiate versions.

To edit, you can use any IDE, we like VS Code. Also we recommend that you use Sass for CSS with Pug (<http://youtu.be/wzAWI9h3q18>). Try Prepros.io on the project. When you edit /webApp/www/post/one/story1.md and save, it converts the markdown file into html. Refresh the browser and see the change you made. That is for webApp/www/post/one/ and for webApp/www/post/two/ It works as mobile (no client side .js) and SPA.

Explore https://zeit.co, our preferred way to deploy to the web. We also like Digital Ocean.

For more: http://github.com/topseed/topseed-demos

For forum: http://gitter.im/topseed-demos/Lobby

