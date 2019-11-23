# WordPress

If you want to use PurgeCSS with WordPress, you might need to whitelist classes generated by WordPress to avoid them being remove by PurgeCSS. `purgecss-with-wordpress` contains the classes needed to be whitelisted.

## Installation

You need to install [purgecss](https://github.com/FullHuman/purgecss) first.

Install `purgecss-with-wordpress`:
```sh
npm i --save-dev purgecss-with-wordpress
```

## Usage

```js{2,7,8}
import Purgecss from 'purgecss'
import purgecssWordpress from 'purgecss-with-wordpress'

const purgeCss = new Purgecss({
  content: ['**/*.html'],
  css: ['**/*.css'],
  whitelist: purgecssWordpress.whitelist,
  whitelistPatterns: purgecssWordpress.whitelistPatterns
})
const result = purgecss.purge()
```

If you have additional classes you want to include in either of the `whitelist` or `whitelistPatterns`, you can include them using the spread operator:

```js
{
  whitelist: [
    ...purgecssWordpress.whitelist,
    'red',
    'blue',
  ],
  whitelistPatterns: [
    ...purgecssWordpress.whitelistPatterns,
    /^red/,
    /blue$/,
  ]
}
```