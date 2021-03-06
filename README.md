# Backlight

Backlight is a pointless script inspired by the Ubuntu Unity Launcher. It will take an image/icon,
and find it's mean background color as well as it's glow color. It will return an object with
values in both RGB and HEX format for use.

## Fetch

The recommended way to install Backlight is [through composer](http://packagist.org).

Just create a composer.json file for your project:

```JSON
{
    "minimum-stability" : "dev",
    "require": {
        "tyler-king/backlight": "dev-master"
    }
}
```

And run these two commands to install it:

    $ curl -s http://getcomposer.org/installer | php
    $ php composer.phar install

Now you can add the autoloader, and you will have access to the library:

```php
<?php
require 'vendor/autoload.php';
```

## Usage

The usage is pretty stright forward, very chainable (see the source). This is a 
basic example below.

```php
<?php

use TylerKing\Backlight\Backlight;

$backlight = new Backlight('chrome-icon.png');
print_r($backlight->getBackground()); // Returns the RGB and HEX of the background to use.
print_r($backlight->getMean()); // Returns the RGB and HEX of the outter glow to use.
```

By running `print_r` or `var_dump` you will receieve an output containing the mean 
background-color and the glow color for the icon or image.

```
stdClass Object
(
    [background] => stdClass Object
        (
            [rgb] => Array
                (
                    [0] => 192
                    [1] => 123
                    [2] => 18
                )

            [hex] => #c07b12
        )

    [glow] => stdClass Object
        (
            [rgb] => Array
                (
                    [0] => 229
                    [1] => 146
                    [2] => 22
                )

            [hex] => #e59216
        )

)
```

You can also *pointlessly* convert the image to pure HTML/CSS.

```php
<?php

use TylerKing\Backlight\Backlight;

$backlight = new Backlight('chrome-icon.png');
file_put_contents('image.html', $backlight->toHTML());
```

By opening image.html in your browser you will now see the image in HTML/CSS format.

## Notes

* This library uses Imagick library.
* Required PHP 5.4
* Supported image types currently is with PNG and JPG.
