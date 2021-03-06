# Pyppeteer Ghost Cursor
Python port of <a href="https://github.com/Xetera/ghost-cursor">Xetera/ghost-cursor</a>, for use with pyppeteer.

> Generate realistic, human-like mouse movement data between coordinates or navigate between elements with puppeteer
like the definitely-not-robot you are.

<b>NOTE:</b> Currently only for use with the <a href="https://github.com/pyppeteer/pyppeteer/tree/pup2.1.1">`pup2.1.1`</a> branch of pyppeteer. Support for the `dev` branch will likely be added in the future.

## Usage

Generating movement data between 2 coordinates.

```python
from pyppeteer_ghost_cursor import path

start = {
    "x": 220,
    "y": 402,
}

end = {
    "x": 902,
    "y": 1032,
}

route = path(start, end)

 # [
 #   { "x": 100, "y": 100 },
 #   { "x": 108.75573501957051, "y": 102.83608396351725 },
 #   { "x": 117.54686481838543, "y": 106.20019239793275 },
 #   { "x": 126.3749821408895, "y": 110.08364505509256 },
 #   { "x": 135.24167973152743, "y": 114.47776168684264 }
 #   ... and so on
 # ]
```

Usage with pyppeteer:

```python
from pyppeteer_ghost_cursor import createCursor
import pyppeteer

async def main(url):
  selector = "#sign-up button"
  browser = await pyppeteer.launch(headless=False)
  page = await browser.newPage()
  cursor = createCursor(page)
  await page.goto(url)
  await page.waitForSelector(selector)
  await cursor.click(selector)

```

## More info
The original repo gives <a href="https://github.com/Xetera/ghost-cursor#puppeteer-specific-behavior"> a description of some of the cool features</a>, along with <a href="https://github.com/Xetera/ghost-cursor#how-does-it-work">a good explanation of how it works.</a>

