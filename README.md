# Bootstrap_less

Bootstrap is a sleek, intuitive, and powerful front-end framework for faster and easier web development, created by [Mark Otto](https://twitter.com/mdo) and [Jacob Thornton](https://twitter.com/fat), and maintained by the [core team](https://github.com/orgs/twbs/people) with the massive support and involvement of the community.

To get started with bootstrap, check out <http://getbootstrap.com>!

This project contains all the bootstrap less source files. This project will be useful to create new themes using less.

# Usage

Create a new project with next structrue:

```
[project_root]
  |- pubspec.yaml
  |- web
    |- index.html
    |- theme.less
    |- ... other files and folders ...
  |- lib
    |- ... lib files and folders ...
```

In the `pubspect.yaml` file add the `bootstrap_less` dependency and `less_dart` dependency, then you will need to add `less_dart` transformer (this is in charge of converting less files into css).

```yaml
...
depencencies:
  ...
  bootstrap_less: ^0.0.1
  less_dart: ^0.3.3
  ...
transformers:
  ...
  less_dart:
    entry_point:
      - web/theme.less
      # any other less entry points should be added here
     include_path: packages/bootstrap_less/less
  ...
```

Then in the `theme.less` add the styles and variables you need to change.

```less
@import 'variables.less';
@import 'mixins.less';

@black: black;
@white: white;

.navbar {
  min-height: 40px;
}

.navbar-default {
  background: transparent;
  border: 0;
  margin-bottom: 0;
}

.navbar-nav > li {
  background: @black;

  a{
    padding: 10px;
  }
}
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
  <!-- you can also add theme.css ->>
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
