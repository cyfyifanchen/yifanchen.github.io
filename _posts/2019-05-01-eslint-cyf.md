---
title: "Putting Prettier Commit-lint Staged-lint into Eslint"
layout: post
date: 2019-05-01
tag:
- dev
blog: true
star: false
---
<span class="fl">C</span>t to the chase, nobody wants to do code review unless your KPI is code reviewing, which is quite impossible in reality. Code Review thus becomes a buzzword of completion. Without fitted criteria, Code Review usually means, I get my parts done, it’s your turn to review it, so I can chill out and watch YouTube. If there happen to be any problems, the routine goes again. You ended up interrupting others or waiting others to approve for your next action. In programming, we call it `blocking-tread`, which is not smart. Therefore, having a proper tool to automate it is ideal in the situation.

I wrote a <a href="https://www.npmjs.com/package/eslint-config-cyf">module</a> to do such a thing.

## Installing

## Local / Per Project Install

1. If you don't already have a `package.json` file, create one with `npm init`.

2. Then we need to install everything needed by the config:

```
npx install-peerdeps --dev eslint-config-cyf
```

3. You can see in your package.json there are now a big list of devDependencies.

4. Create a `.eslintrc` file in the root of your project's directory (it should live where package.json does). Your `.eslintrc` file should look like this:

```json
{
  "extends": ["cyf"]
}
```

Tip: You can alternatively put this object in your `package.json` under the property `"eslintConfig":`. This makes one less file in your project.

5. You can add two scripts to your package.json to lint and/or fix:

```json
"scripts": {
  "lint": "eslint .",
  "lint:fix": "eslint . --fix"
},
```

6. Now you can manually lint your code by running `npm run lint` and fix all fixable issues with `npm run lint:fix`. You probably want your editor to do this though.

## Global Install

1. First install everything needed:

```
npx install-peerdeps --global eslint-config-cyf
```

(**note:** npx is not a spelling mistake of **npm**. `npx` comes with when `node` and `npm` are installed and makes script running easier)

2. Then you need to make a global `.eslintrc` file:

ESLint will look for one in your home directory

- `~/.eslintrc` for mac
- `C:\Users\username\.eslintrc` for windows

In your `.eslintrc` file, it should look like this:

```json
{
  "extends": ["cyf"]
}
```

3. To use from the CLI, you can now run `eslint .` or configure your editor as we show next.

## Settings

If you'd like to overwrite eslint or prettier settings, you can add the rules in your `.eslintrc` file. The [ESLint rules](https://eslint.org/docs/rules/) go directly under `"rules"` while [prettier options](https://prettier.io/docs/en/options.html) go under `"prettier/prettier"`. Note that prettier rules overwrite anything in my config (trailing comma, and single quote), so you'll need to include those as well.

```js
{
  "extends": [
    "cyf"
  ],
  "rules": {
    "no-console": 2,
    "prettier/prettier": [
      "error",
      {
        "trailingComma": "es5",
        "singleQuote": true,
        "printWidth": 120,
        "tabWidth": 8,
      }
    ]
  }
}
```