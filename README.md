# WP Localizer
Simple & Useful WP Localizer Library For Plugins / Themes

[![Latest Stable Version][latest-stable-version-img]][latest-stable-version-link]
[![Latest Unstable Version][latest-Unstable-version-img]][latest-Unstable-version-link]
[![Total Downloads][total-downloads-img]][total-downloads-link]
[![WP][wpcs-img]][wpcs-link]
[![License][license-img]][license-link]
[![composer.lock available][composerlock-img]][composerlock-link]

## Installation
The preferred way to install this extension is through [Composer][composer].

To install **WP_Localizer library**, simply:

    $ composer require varunsridharan/wp-localizer

The previous command will only install the necessary files, if you prefer to **download the entire source code** you can use:

    $ composer require varunsridharan/wp-localizer --prefer-source

You can also **clone the complete repository** with Git:

    $ git clone https://github.com/varunsridharan/wp-localizer.git

Or **install it manually**:

[Download Localizer.php][downloadphp]:

    $ wget https://raw.githubusercontent.com/varunsridharan/wp-localizer/master/src/Localizer.php


## Options
| Option Name | Value | Description |
| --- | --- | --- |
| `id` |  String | Unique ID it should be a **slug** |
| `scripts` | Array |  An Array of script handles to check before localizing the data  |
| `frontend` | true / false |  Load in frontend ? ( By default it loads only in wp-admin )
| `functions` | true / false |  Create useful JS Functions for getting values that are localized

### Javascript Functions
if **functions** arg is set to true then 2 javascript functions are generated
* `{id}_option` -- Function to get arguments passed from php Eg : (`myplugin_option('object2'')`);
* `{id}_txt` -- Function to get translated string passed from php Eg : (`myplugin_txt('some_title','Default Title'));

## Usage

```php
<?php
/**
 * Create A New Instance
 */
$instance = \Varunsridharan\WordPress\Localizer::instance( array(
    'id'        => 'myplugin',
    'scripts'   => array( 'my-plugin-script' ),
    'frontend'  => true,
    'functions' => true,
) );

/**
 * Get Existing Instance
 */
$instance_existing = \Varunsridharan\WordPress\Localizer::instance( 'myplugin' );

$instance->add( 'alert_info', array(
    'show' => false # It can be Array / String / Bool / Int
) );

$instance->add( 'object2', 'Some Value'/* It can be Array / String / Bool / Int */ );

/**
 * Merges With Existing object1 value.
 */
$instance->add( 'alet_info', array(
	'title' => 'Some Value',
), true );

// Translation.
$instance->text('alert_title',__('Your Alert Title'));

```
### Javascript Usage
```javascript
var $arg = myplugin_option( 'alert_info' );
if(true === $arg.show){
	alert($arg.title);
}
alert(myplugin_txt('alert_title','Default Title Here'));
```

**Note** `myplugin_option` AND `myplugin_txt` javascript functions are created dynamically 

---

## Contribute
If you would like to help, please take a look at the list of
[issues][issues] or the [To Do](#-todo) checklist.

## License
This project is licensed under **General Public License v3.0 license**. See the [LICENSE](LICENSE) file for more info.

## Copyright
2017 - 2018 Varun Sridharan, [varunsridharan.in][website]

If you find it useful, let me know :wink:

You can contact me on [Twitter][twitter] or through my [email][email].

## Backed By
| [![DigitalOcean][do-image]][do-ref] | [![JetBrains][jb-image]][jb-ref] |  [![Tidio Chat][tidio-image]][tidio-ref] |
| --- | --- | --- |

[twitter]: https://twitter.com/varunsridharan2
[email]: mailto:varunsridharan23@gmail.com
[website]: https://varunsridharan.in
[issues]: issues/
[composer]: http://getcomposer.org/download/
[downloadphp]:https://raw.githubusercontent.com/varunsridharan/wp-localizer/master/src/Localizer.php

[do-image]: https://vsp.ams3.cdn.digitaloceanspaces.com/cdn/DO_Logo_Horizontal_Blue-small.png
[jb-image]: https://vsp.ams3.cdn.digitaloceanspaces.com/cdn/phpstorm-small.png?v3
[tidio-image]: https://vsp.ams3.cdn.digitaloceanspaces.com/cdn/tidiochat-small.png
[do-ref]: https://s.svarun.in/Ef
[jb-ref]: https://www.jetbrains.com
[tidio-ref]: https://tidiochat.com

[latest-stable-version-img]: https://poser.pugx.org/varunsridharan/wp-localizer/version
[latest-Unstable-version-img]: https://poser.pugx.org/varunsridharan/wp-localizer/v/unstable
[total-downloads-img]: https://poser.pugx.org/varunsridharan/wp-localizer/downloads
[Latest-Unstable-version-img]: https://poser.pugx.org/varunsridharan/wp-localizer/v/unstable
[wpcs-img]: https://img.shields.io/badge/WordPress-Standar-1abc9c.svg
[license-img]: https://poser.pugx.org/varunsridharan/wp-localizer/license
[composerlock-img]: https://poser.pugx.org/varunsridharan/wp-localizer/composerlock

[latest-stable-version-link]: https://packagist.org/packages/varunsridharan/wp-localizer
[latest-Unstable-version-link]: https://packagist.org/packages/varunsridharan/wp-localizer
[total-downloads-link]: https://packagist.org/packages/varunsridharan/wp-localizer
[Latest-Unstable-Version-link]: https://packagist.org/packages/varunsridharan/wp-localizer
[wpcs-link]: https://github.com/WordPress-Coding-Standards/WordPress-Coding-Standards/
[license-link]: https://packagist.org/packages/varunsridharan/wp-localizer
[composerlock-link]: https://packagist.org/packages/varunsridharan/wp-localizer
