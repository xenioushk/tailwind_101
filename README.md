# Tailwind Setup

URL:
https://tailwindcss.com/


## Steps for the Tailwindcss setup

1. Go to the project root directory. Run the following commands to install `tailwind.css` as dev dependency.

```bash
npm init
npm i -D tailwindcss
```

2. Next, we need run the following command to create the `tailwind.config.js` config file.

```bash
npx tailwindcss init
```

3. Open the `tailwind.config.js` file and update the code like the following screenshot. This code will watch any changes of the html files and create `style` automatically.

![tailwind_config_file](/previews/tailwind_config_file.jpg)

4. Next, create a `src` folder and inside that folder create `input.scss` file. Add the followling lines of code into that file.

```css
@tailwind base;
@tailwind components;
@tailwind utilities;
```

5. Now, open the `package.json` file and add the following lines of code into scripts section

```javascript
  "scripts": {
    "dev": "npx tailwindcss -i ./src/input.scss -o ./css/styles.css --watch",
    "build": "npx tailwindcss -i ./src/input.scss -o ./css/styles.css"
  },
```
**Example:**

![package_json_config_file for tailwind](/previews/package_json_config_file.jpg)

6. Next, run the following command to compile the css code and keep watch for any changes.

```bash
npm run dev
```
**Output:**

![complied_css_output for tailwind](/previews/complied_css_output.jpg)

7. Now, add that css path to your html file.

![sample html file](/previews/html_file.jpg)

**Output:**

![sample html file output for tailwind](/previews/html_file_output.jpg)

Now, you are ready to use the tailwindcss for your project. 


## Advance setup and custom colors

1. Create a token.json file at the root directory of the project. Now you can add screen sizes and colors into that file.

```json
{
  "screens": {
    "sm": "480px",
    "md": "768px",
    "lg": "976px",
    "xl": "1440px"
  },
  "colors": {
    "tplPrimary": "#ff0000",
    "tplSecondary": "#0000ff"
  }
}
```

2. Next, import that `token.json` file into `tailwind.config.js` file. Update the `tailwindo.config.js` file with the following code snippets.

```javascript
/** @type {import('tailwindcss').Config} */
const colors = require('./token.json').colors;
const screens = require('./token.json').screens;
module.exports = {
  content: ["./*.html"],
  theme: {
    extend: {
      screens: {
        ...screens
      },
      colors: {
        ...colors
      }
    },
  },
  plugins: [],
}
```

3. Keep running the `npm run dev` command and now you can use the custom colors to your html file. Here is the examples.

**Background color**

```html
<div class="bg-tplPrimary">Hello world</div>
```
**Text color**

```html
<p class="text-tplPrimary">Hello world</p>
```