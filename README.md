# The Downpour HTML engine

Hello, welcome to the Downpour HTML engine! This is a small "game engine" which takes a data.js file and converts it into a working HTML page with multiple "pages" that can be naviagted between, each containing a set of images, text and other objects that can have various styles applied to them. This data.js file is expected to be made with [the Downpour app](https://downpour.games).

- The easiest way to use this is to use the Downpour app, make a game, sign up for an account, and then press the upload button. This will host your game on [downpour.games](https://downpour.games), and will not require you to think about code or web hosting at all.
- The second easiest way to use this is to use the Downpour app, make a game and then press the export button. This will give you a zip file containing the game, all assets used, and a version of the Downpour engine. You can then host this anywhere that will accept a folder of files that can be served statically (Github, Neocities and itch.io all come to mind, as does basically any web server)
- The more complicated ways involve modifying either the data.js file or the index.html file by hand. That's presumably why you're here.

## A few notes on the code
There is a constant `LOCAL`, which controls some of the logic depending on whether the game is hosted on downpour.games or not. 

If you want to have nice social sharing images, it's suggested you add edit the following section, and insert it in index.html where it says `<!-- social sharing section -->`:

```html
    <meta property="og:title" content="Game title" />
    <meta property="og:url" content="https://example.com/downpourgame" />
    <meta property="og:image" content="https://example.com/downpourgame/media/cover.jpg" />
    <meta property="og:image:width" content="300" />
    <meta property="og:image:height" content="300" />
    <meta property="og:site_name" content="Downpour" />
    <meta property="og:type" content="website" />

    <meta name="twitter:card" content="summary_large_image">
    <meta name="twitter:title" content="Game title">
    <meta name="twitter:description" content="A Downpour game by Author">
    <meta name="twitter:image" content="https://example.com/downpourgame/media/cover.jpg">
```

`data.js` is a JS file rather than a JSON file because this allows games to be run directly from a file browser without tripping over any of the restrictions web browsers place on things hosted at a `file://` path

This code is inconsistently marked with JSDoc sections - this is because I like type assistance when writing code, but do not want to set up a Typescript build step for working on this code.

It is desirable that this engine is one self contained HTML file. At some point it might make sense to break it apart into separate files, but not yet.