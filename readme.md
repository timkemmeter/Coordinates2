# Creating a custom theme for the Podigee webplayer

This repository contains the necessary documentation and materials to get you started with creating a custom webplayer theme. It includes the standard theme files for the Podigee webplayer, which can be used for developing your own theme in case you booked the separate "Custom webplayer package" from us.

## Pre-Requirements

- basic knowledge of HTML & CSS
- a web browser
- a code / text editor (vim, VS Code, ...)
- a working development environment utilizing Python 3

## Getting started

1. Clone the repository and change your working directory to the root folder of this repository.
2. Make a copy of the folder containing the `standard` theme files (e.g. `cp -R themes/standard themes/my-theme`).
3. Adjust the player configuration file `podcast.json`. To do so change the name of the theme in the block `options` in the mentioned json file and adjust the path for the keys `themeCss` and `themeHtml` to use `my-theme` instead of `standard`.

```json
"options": {
  "theme": "my-theme",
  ...
  "themeCss": "http://0.0.0.0:8080/themes/my-theme/index.css",
  "themeHtml": "http://0.0.0.0:8080/themes/my-theme/index.html"
}
```

4. Start a simple CORS-enabled Python 3 webserver from the root of the repository folder to serve a webpage with the embedded player that uses your own theme:

```bash
$ python3 httpserver.py
```

You can pass a specific port to the script. Please make sure to change all occurrences of 8080 in this repository (`index.html, podcast.json`) in this case.

5. Open a web browser with the URL `http://0.0.0.0:8080`.
6. Start being creative and adjust / extend the CSS file in the folder of `my-theme` with the styling information that fits your preferences / requirements. 😎

## Make use of your new theme

When you are done developing your own theme, you can simply upload the HTML and CSS file from `my-theme` to your own webspace. Put the URLs to these files in the `Web-Player` tab in the podcasts settings in your Podigee account. Make the advanced settings visible, switch the player theme to `External theme` and fill in the URLs to the CSS and HTML.

**Note:** please make sure to let your webserver add a CORS header when delivering the files. Either use a wildcard `*` or `https://player.podigee-cdn.net` to allow the CORS request only from our player CDN.
