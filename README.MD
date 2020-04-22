# Instructions

## How to build
- Export IBM Carbon Icons from the [Figma file](https://www.figma.com/file/YxzqZzimoylCVlqCKAdOsy/IBM-Carbon-Icons?node-id=0%3A1)
- Search SVG files in Finder and move them all to a single folder named "icon-svg-files" within your project file
- Rename them all to lowercase using `for f in *; do mv "$f" "$f.tmp"; mv "$f.tmp" "\`echo $f | tr "[:upper:]" "[:lower:]"\`"; done`
- Create an empty folder called "icon-font"
- Run [icon-font-generator](https://www.npmjs.com/package/icon-font-generator): `icon-font-generator icon-svg-files/*.svg -o icon-font -n ibm-icons -p ibm-icon -t span --normalize true --height 128 --html false -j false --types 'woff2'`
    - For web use WOFF, for mobile app (i.e. ionic) use WOFF2
- In ibm-icons.css, add the following properties:
```css
span[class^="ibm-icon-"]:before, span[class*=" ibm-icon-"]:before {
    display: flex;
    justify-content: center;
    align-items: center;
    font-size: 24px;
}
```

## How to use
- Move the icon-font folder to your project
- Import it into your main SCSS file
- use the icons as follows, replacing whatever is after ibm-icon- with the icon name (use the [css file](https://github.com/alpiel91/carbon-iconfont/blob/master/icon-font-mobile/ibm-icons.css) for reference):
```html
<span class="ibm-icon-info"></span>
```
