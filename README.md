# Bootstrap_less

Bootstrap is a sleek, intuitive, and powerful front-end framework for faster and easier web development, created by [Mark Otto](https://twitter.com/mdo) and [Jacob Thornton](https://twitter.com/fat), and maintained by the [core team](https://github.com/orgs/twbs/people) with the massive support and involvement of the community.

To get started with bootstrap, check out <http://getbootstrap.com>!

This project contains all the bootstrap less source files. This project will be useful to create new themes using less.

# Usage

Create a new project with next structure:

```
[project_root]
  ├─ pubspec.yaml
  ├─ web
  │  ├─ index.html
  │  ├─ theme.less
  │  ├─ variables.less
  │  └─ ... other files and folders ...
  └─ lib
     └─ ... lib files and folders ...
```

In the `pubspect.yaml` file add the `bootstrap_less` dependency and `less_dart` dependency, then you will need to add `less_dart` transformer (this is in charge of converting less files into css).

```yaml
...
depencencies:
  ...
  bootstrap_less: any
  less_dart: any
  ...
transformers:
  ...
  - less_dart:
    entry_point:
      - web/theme.less
      # any other less entry points should be added here
    include_path: web
  ...
```

Then in `variables.less` add the variables you want to modify

```less
// Cerulean 3.3.6
// Variables
// --------------------------------------------------


//== Colors
//
//## Gray and brand colors for use across Bootstrap.

@gray-base:              #000;
@gray-darker:            lighten(@gray-base, 13.5%); // #222
@gray-dark:              lighten(@gray-base, 20%);   // #333
@gray:                   lighten(@gray-base, 33.5%); // #555
@gray-light:             lighten(@gray-base, 60%);   // #999
@gray-lighter:           lighten(@gray-base, 93.5%); // #eee

@brand-primary:         #2FA4E7;
@brand-success:         #73A839;
@brand-info:            #033C73;
@brand-warning:         #DD5600;
@brand-danger:          #C71C22;

...
```

Then in the `theme.less` add the styles you need to change.

```less
@import "packages/bootstrap_less/less/bootstrap";
@import "variables"; // variables should be imported after bootstrap to override variables values

// Cerulean 3.3.5
// Bootswatch
// -----------------------------------------------------

n2s-icon :extend(.glyphicon) {}

.btn-shadow(@color) {
  #gradient > .vertical-three-colors(lighten(@color, 8%), @color, 60%, darken(@color, 4%));
  filter: none;
  border-bottom: 1px solid darken(@color, 10%);
}

// Navbar =====================================================================

.navbar {
  .btn-shadow(@navbar-default-bg);
  filter: none;
  .box-shadow(0 1px 10px rgba(0, 0, 0, 0.1));

  &-default {

    .badge {
      background-color: #fff;
      color: @navbar-default-bg;
    }
  }

  &-inverse {
    #gradient > .vertical-three-colors(lighten(@navbar-inverse-bg, 8%), lighten(@navbar-inverse-bg, 4%), 60%, darken(@navbar-inverse-bg, 2%));
    filter: none;
    border-bottom: 1px solid darken(@navbar-inverse-bg, 10%);

    .badge {
      background-color: #fff;
      color: @navbar-inverse-bg;
    }
  }

  .navbar-nav > li > a,
  &-brand {
    text-shadow: 0 1px 0 rgba(0, 0, 0, 0.1);
  }
}

...
```

Finally in the `index.html` you will add the link to `theme.css` as it follows:

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <title>Bootstrap Example</title>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <!-- you could add bootstrap.css file -->
  <link rel="stylesheet" href="packages/bootstrap_less/less/bootstrap.css">
  <!-- you can also add theme.css -->
  <link rel="stylesheet" href="theme.css">
</head>
<body>
  <!-- ... content here ... -->
</body>
</html>
```

## Bugs and feature requests

Have a bug or a feature request? [Please open a new issue](https://github.com/twbs/bootstrap/issues/new).

## Copyright and license

Code and documentation copyright 2011-2015 Twitter, Inc. Code released under [the MIT license](https://github.com/twbs/bootstrap/blob/master/LICENSE). Docs released under [Creative Commons](https://github.com/twbs/bootstrap/blob/master/docs/LICENSE).
