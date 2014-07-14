# ByMySide

ByMySide is a sidebar for your website.

A website can have 2 sidebars (left + right)

Each sidebar can have 2 item blocks (top + bottom)

So you can have up to 4 item blocks on a page.

# Install

## Github

Download and extract the zip file by clicking on the "Download ZIP" button on your right.

## Bower

Either add `"bymyside": "~1.0"` or run `bower install bymyside --save`

# Usage

## HTML

Here is the structure of the sidebar:

```html
<div class="bymyside-container bymyside-container-[left|right]">
    <div class="bymyside-block bymyside-block-[top|bottom]">
        <a href="#" class="bymyside-item bymyside-item-scheme-[default|...] [bymyside-item-highlight]">
            <span class="bymyside-item-icon">H</span>
            <span class="bymyside-item-label">Hello World</span>
        </a>
    </div>
</div>
```

### Schemes

Scheme value (`bymyside-item-scheme-[name]`) can be any defined scheme.

#### Standard schemes

These schemes are always available:

`default`, `red`, `green`, `blue`, `yellow`

#### Brand schemes

Additional brand schemes are provided if you *don't* use the "-no-brands-" CSS:

`rss`, `twitter`, `google-plus`, `facebook`, `dribbble`, `dropbox`, `deviantart`, `bitbucket`, `instagram`, `tumblr`, `youtube`, `reddit`, `flickr`, `behance`, `linkedin`, `vine`, `stack-overflow`, `stumbleupon`, `skype`, `pinterest`

#### Custom schemes

You can add your own custom schemes either for the [CSS version](#css-custom-schemes) or the [SASS version](#sass-custom-schemes).

#### Highlight

By using `byside-item-highlight` on an item, the icon will be highlighted (same as the hover state) but not the label.

## CSS

You will find a `build` directory containing a `dev` and a `min` subdirectories, each containing multiple pre-compiled files:

- `bymyside[.min].css`: The full featured CSS for the 2 sidebars + the brands colors
- `bymyside-no-brands[.min].css`: The CSS for the 2 sidebars without the brands colors
- `bymyside-left-only[.min].css`: The CSS for the left sidebar + the brands colors
- `bymyside-left-only-no-brands[.min].css`: The CSS for the left sidebar without the brands colors
- `bymyside-right-only[.min].css`: The CSS for the right sidebar + the brands colors
- `bymyside-right-only-no-brands[.min].css`: The CSS for the right sidebar without the brands colors

This allow so have lightweight code if, for example, you just want to have a sidebar at right, and don't need the brand colors

### <a name="css-custom-schemes"></a>Custom Schemes

You can create custom color schemes for you items.
 
For example, to create a "foobar" color scheme, add this code to your CSS:

```css
.bymyside-item-scheme-foobar {
  background-color: #123456; /* Idle background color */
  color: #987654; /* Idle text color */
}

.bymyside-item-scheme-foobar:hover .bymyside-item-icon,
.bymyside-item-scheme-foobar:hover .bymyside-item-label,
.bymyside-item-scheme-foobar.bymyside-item-highlight .bymyside-item-icon {
    background-color: #ABCDEF; /* Highlight/Hover background color */
    color: #FEDCBA; /* Highlight/Hover text color */
}
```

Then use it by adding `bymyside-item-scheme-foobar` to your sidebar item.

## Sass

To use ByMySide in your project, just add `@import "path/to/smartbar.scss";` to your sass file.

You can use any other sass file (smartbar-no-brands.scss, ...) for predefined options, or you can configure your own options:

### Global options

```
Option                   | Default | Description
_______________________________________________________________________________
$bymyside-with-brands    | true    | Generate the CSS for brand colors schemes
$bymyside-custom-schemes | ()      | A map containing custom color schemes
```

### Left/Right sidebar specific options (prefix with either `$bymyside-left` or `$bymyside-right`)

```
Option              | Default                   | Description
____________________________________________________________________________________________________________________
*-enabled           | true                      | Generate the CSS for the left/right sidebar
*-width             | 60px                      | Width of the sidebar
*-item-height       | *-width                   | Height of a sidebar item
*-offset-top        | 20px                      | Space between the top of screen and the top of block-top
*-offset-bottom     | 20px                      | Space between the bottom of screen and the bottom of block-bottom
*-bg-color          | #333                      | Sidebar background color (and item default bg color)
*-text-color        | #ddd                      | Sidebar text color (and item default text color)
*-bg-color-hover    | lighten(*-bg-color, 7%)   | Item default background color on hover/highlight
*-text-color-hover  | lighten(*-text-color, 7%) | Item default text color on hover/highlight
*-font-size         | *-width / 2               | Sidebar font size
*-border-radius     | *-width / 6               | Sidebar border radius
```

### <a name="sass-custom-schemes"></a>Custom Schemes

Creating a custom scheme with sass is easier, define a `$bymyside-custom-schemes` map:

```sass
$bymyside-custom-schemes: (
    foobar: (text: #AAA, bg: #BBB, text-hover: #CCC, bg-hover: #DDD),
    barbaz: (bg-hover: #ABC),
    hello-world: (bg: #DEF, text-hover: #DEF)
);
```

Then you can use `bymyside-item-scheme-foobar`, `bymyside-item-scheme-barbaz` and `bymyside-item-scheme-hello-world`
