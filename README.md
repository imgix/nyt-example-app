# NYT Style Clone Part One [WIP]

## About
Here is an app that demos some of the capabilities of the `imgix` SDK, API, and service. This "app" is currently a work in progress. Eventually, this (or a template like this) will be employed in a larger example app.

## Project Structure
The overall project structure is flat. There is no dev-server, but you can open `index.html` in Firefox or Chrome and the browser will do the rest.

### Project Directory Tree
```
nyt
├── README.md
├── index.html
└── style.css
```

## Design
The layout has been styled to be a simplistic, single-page, version of the [The New York Times](https://www.nytimes.com/) website.

There are three images that are loaded dynamically from an `imgix` source. Other than that, there isn't anything else being fetched over the network.

**This app does not use any javascript**. All of the responsiveness here is all done with the `imgix` API, `srcsets`, and CSS.

## Images
The first image is loaded using the [device pixel ratio](https://docs.imgix.com/apis/url/pixel-density/dpr), or `dpr`, parameter to allow for dpr-based srcset selection. The goal is to serve an image with the correct pixel density for a given device's screen's pixel density (resolution).
```html
<img srcset="https://eric.imgix.net/albright.jpeg?w=450 1x,
    --snipp--
    https://eric.imgix.net/albright.jpeg?w=450&dpr=3 3x"
    src="https://eric.imgix.net/albright.jpeg?w=450"
```

The second image is loaded in a similar manner. The only difference is the second image is _larger_. It is _logically_ larger. This means that the image width request is 640px which is larger than the first image, 450px. [Read more](https://docs.imgix.com/tutorials/responsive-images-srcset-imgix)

The third image is also loaded via the `imgix` srcset API, except that it leverages the `srcset` `sizes` attribute to allow the browser to select an appropriate image _for the viewport_. The sizes attribute presents the browser with a media query to help it choose the correct image to load.

The second and last images are works-in-progress. Ideally, we should be able to due some cool art-direction stuff. Stay tuned.

### Dependencies
This project depends on:

- html
- css
- an `imgix` [source](https://www.imgix.com)