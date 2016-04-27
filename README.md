[![Build Status](https://img.shields.io/travis/mjt01/less-vars-to-js/master.svg?style=flat-square)](https://travis-ci.org/mjt01/less-vars-to-js)
[![Coverage Status](https://img.shields.io/coveralls/mjt01/less-vars-to-js.svg?style=flat-square)](https://coveralls.io/github/mjt01/less-vars-to-js?branch=master)
[![npm](https://img.shields.io/npm/v/less-vars-to-js.svg?style=flat-square)](https://www.npmjs.com/package/less-vars-to-js)
# less-vars-to-js
Read [LESS](http://lesscss.org/) variables from the contents of a file and return them as a javascript object.
```js
$ npm install --save less-vars-to-js
```

### Why?
I wrote this to use in our living style guide where we document our colour palette, typography, grid, components etc. This allows variables to be visualised in the style guide without having to read through the code (useful for non-technical team members).

### Usage
```js
import lessToJs from 'less-vars-to-js';
import fs from 'fs';

// Read the less file in as string
const paletteLess = fs.readFileSync('palette.less', 'utf8');

// Pass in file contents
const palette = lessToJs(paletteLess);

// Use the variables (example React component)
export default class Palette extends Component {
  render() {
    return (
      <div>
      {
        Object.keys(palette)
          .forEach(colour => (
            <div style={{ backgroundColor: palette[colour] }}>
              <p>{ colour }<p>
              <p>{ palette[colour] }</p>
            </div>
          ))
      }
      </div>
    );
  }
}
```

### License

[MIT](http://mjt01.mit-license.org)
