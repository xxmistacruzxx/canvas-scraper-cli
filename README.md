# Canvas Scraper CLI

A NodeJS command-line interface for scraping and downloading data (e.g. assignments and modules) from a Canvas course.

## Dependencies

Canvas-Scraper uses [Puppeteer](https://pptr.dev/), a headless browser, to navigate and scrape data from Canvas. This requires some form of [Chromium](https://www.chromium.org/chromium-projects/) to be available on the system. The easiest way to do this is by installing [Google Chrome](https://www.google.com/chrome/).

## Getting Started

You'll first need to get the cookies for your current Canvas session to allow the scraper to have credentials to your Canvas. This needs to be done in JSON format (an example can be found in cookies-example.json).

The easiest way to do this is by logging into Canvas in your browser and using an extension to export your current cookies (e.g. [CookieManager](https://chromewebstore.google.com/detail/cookiemanager-cookie-edit/hdhngoamekjhmnpenphenpaiindoinpo) for Chrome).

### Using Pre-Compiled Release

First, download the latest version from the [Releases](https://github.com/xxmistacruzxx/canvas-scraper/releases) page and extract the ZIP file. Inside the folder, you'll find three (3) different executables, with each being for a different operating system.

To use the executable, you can either open it using your file explorer (which will open a wizard to guide you through the different arguments and flags) or simply navigate to the directory in a shell and call the executable.

e.g Windows<br/>
`./canvas-scraper.exe [options] <url>`

### Using Source Code

You will need [NodeJS](https://nodejs.org/en) and [NPM](https://docs.npmjs.com/downloading-and-installing-node-js-and-npm).

Once installed, download the project dependencies using...

`npm i`

After, you can simply run the entry file directly...

`node index.js [options] <url>`

## Usage

```
Usage: canvas-scraper [options] <url>

Scrape data from a canvas course

Arguments:
  url                      Course Homepage URL (e.g. https://<school_domain>/courses/<course_id>)

Options:
  -o, --output <dir_name>  output directory name (default: "courses/course")
  -c, --cookies <path>     path to cookies file (default: "cookies.json")
  -a                       scrape assignments (default: false)
  -m                       scrape modules (default: false)
  -h, --help               display help for command
```

You must use the 'a' and/or 'm' flags, otherwise no data will be scraped.

## Download File Structure

- ASSIGNMENTS
  - [\<Assignment\> (<(Grade %) or (Points Earned/Total Points) or (N/A) or (✅ or ❌)>)]
    - .ASSIGNMENT
      - .ASSIGNMENT.pdf
      - {Embedded Files}
    - .COMMENTS.txt
    - .SUBMISSIONDETAILS.pdf
    - {Submission Files}
  - .ASSIGNMENTS.pdf
- MODULES
  - MODULE SECTION
    - MODULE NAME
      - .MODULE.pdf
      - {Embedded Files}
  - .MODULES.pdf
- .HOMEPAGE.pdf

## Video Tutorial

Watch the video below for a quick guide on how to download and use the CLI!

[![Video Tutorial Thumbnail](https://img.youtube.com/vi/LkUe-pfXVFE/0.jpg)](https://www.youtube.com/watch?v=LkUe-pfXVFE)
