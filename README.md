# Octopus Maps Project

**Update: 10th May 2025**

This project is a practice website for ENGL 5050, running on [11ty](https://www.11ty.dev/), [tailwindcss](https://tailwindcss.com/), and [daisyui](https://daisyui.com/). The research about octopus maps is credited to the whole team: Xingyu Lan, Daocheng Lin, Yifan Wang, Yutong Yang. I also want to thank Dr. York, who gives me invaluable instructions and helps me about the troubleshooting.

## Notes for Developer

**Important note**: please do not store unprocessed images with `.jpg`, `.png`, etc. extensions in the repository (or any binary file larger than 1MB in size). Over time, this will take up a lot of space on our computers. Instead, make sure all images have been converted into `.webp` format using an [online converter](https://cloudconvert.com/webp-converter) before storing them in the repository. 

### To use
1. Download or clone the repository (or fetch from the origin)
2. In the terminal: `npm install` to download the dependencies
3. Then: `npm run dev` to build and start the dev server 
4. Visit [http://localhost:8080](http://localhost:8080) to view the site
5. To stop the server (in order to change configurations or recompile tailwind, for example) just press `control + C` (on a mac), then `npm run dev` again to rebuild.

### Notes
This is a fairly standard implementation with only a few customizations. Below are the most notable files and their basic functions.

#### in `/package.json`
+ dependencies are declared
+ npm scripts are defined
+ project details are specified
+ used to generate `package-lock.json` during build step

#### in `src/styles/index.css`
+ installs tailwind and plugins
+ Implements fonts from google fonts
+ sets daisyUI themes for light and dark mode (currently set to autumn)

#### in `/eleventy.config.mjs`
+ Files are read from `/src` and built to `/dist`
+ Templating is done with nunjucks `.njk` by default
+ Content pages are in markdown `.md` (with native HTML processing)
+ The `src/assets` directory is passed through to `dist`

#### in `/tailwind.config.js`
+ Theme is extended to use fonts with `.font-playfair` and `.font-poppins` classes
+ nothing else happens here yet

#### in `/src/_includes`
+ Base template is `default.njk`
+ Nav and footer components 

#### in `/src/assets`
+ for now this is so images are passed into the `dist` directory
+ later it can be used for any file assets

## Logs

### 11th May, 2025

#### Update
+ Successfully deploy the page on GitHub. I did two things:
    1. **Add gh-pages plugin:** Use the plugin, gh-pages to create an individual branch `gh-pages` that only put the files of `dist` folder in the main branch in it. Then, I set the "gh-pages" as the branch that host the website. In this workflow, there are only the *output files* in the `dist` folder, so I will need to output all the changes in the *input files* everytime. To do this, I built `npm run deploy` function on the `package.json`. In this process, I got a clear idea on how 11ty contributes to the workflow of coding and reduces the cognitive load for human being: it's developed because of human's limited working memory.
    2. **Fix the path of css and images:** I change the path of `index.css` in `default.njk` from `/styles/index.css` to `./style/index.css`. Then it works. I'm not quite sure how the path works, it seems that the former path indicate the root folder and the latter path indicate the current folder.
        + I change the background images of the swiper from `bg-[url(/assets/img/images.webp)]` to `style="background-image: url(./assets/img/images.webp);"` The strange thing here is that I tried `bg-[url(./assets/img/images.webp)]` but it doesn't work. Really confused in this part. 

#### To-DO
+ Build a responsive frontpage for the mobile phone.

### 10th May, 2025

#### Update
+ Build a responsive front page for tablet and computer.
+ Adjust the color palette and typography.

#### To-do
+ Finish the "feature exampls" section.
+ Adjust some issues about responsive design.
+ Create a responsive front page for mobile phone.