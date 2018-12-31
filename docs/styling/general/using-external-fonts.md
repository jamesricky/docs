# Using external fonts
In Koala Framework 5.0 and later.

If you want to create your own font-reposetory see [creating a custom font repository](create-font-repository.md).

## Using webfontloader
#### 1. Add webfontloader to `composer.json`:

```json
"extra": {
    "require-npm": {
        "webfontloader": "^1.6.28"
    }
}
```

#### 2. Load your font in `themes/Theme/Web.js`:

```js
var WebFont = require('webfontloader');
WebFont.load({
    monotype: {
        projectId: 'my-awesome-font-project'
   }
});
```

#### 3. Make sure Web.js has been added to your assets in the `getRootSettings()` function of `themes/Theme/Component.php`:

```php
$ret['assets']['files'][] = 'web/themes/Theme/Web.js';
```

## Using a font repository
#### 1. Add the font repository to your `composer.json`

Require with npm (recommended):
```json
"extra": {
    "require-npm": {
        "myawesomefonts": "git+ssh://git@example.com:user/myawesomefonts.git#1.0.0"
    }
}
```

Or require with bower:
```json
"extra": {
    "require-bower": {
        "myawesomefonts": "git@example.com:user/myawesomefonts.git#1.0.0"
    }
}
```

#### 2. Add the fonts to your assets in the `getRootSettings()` function of `themes/Theme/Component.php`:
```php
$ret['assets']['files'][] = 'myawesomefonts/fonts.css';
```

<br>
<br>
Then run `composer update`, build the project and have fun with your fonts.
