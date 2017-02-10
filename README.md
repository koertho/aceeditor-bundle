# Ace Editor Bundle #

Bundle provides a [ace editor](http://ace.ajax.org) integration into Symfony3 Form component.

# Installation #

Add bundle into your ``composer.json`` file.

```
{
    "repositories": [
        {
            "type": "vcs",
            "url": "https://github.com/koertho/aceeditor-bundle"
        }
    ],
    "require": {
        "norzechowicz/aceeditor-bundle": "dev-master",
    }
}
```

Register bundle in AppKernel.php

```php
// app/AppKernel.php

public function registerBundles()
{
    return array(
        new Norzechowicz\AceEditorBundle\NorzechowiczAceEditorBundle(),
        // ...
    );
}
```

Update project dependencies

```
$ php composer.phar update
```

# Usage #

```php
/* @var $builder \Symfony\Component\Form\FormBuilderInterface */

$builder->add('description', AceEditorType::class, array(
    'wrapper_attr' => array(), // aceeditor wrapper html attributes.
    'width' => 200,
    'height' => 200,
    'font_size' => 12,
    'mode' => 'ace/mode/html', // every single default mode must have ace/mode/* prefix
    'theme' => 'ace/theme/monokai', // every single default theme must have ace/theme/* prefix
    'options' => [
      'enableBasicAutocompletion' => false,
		'enableSnippets' => false,
		'enableLiveAutocompletion' => false
    ]
    'tab_size' => null,
    'read_only' => null,
    'use_soft_tabs' => null,
    'use_wrap_mode' => null,
    'show_print_margin' => null,
    'show_invisibles' => null,
    'highlight_active_line' => null
));
```

Above code will create textarea element that will be replaced with ace editor instance.
Textarea value is updated on every single change in ace editor.

# Configuration #

> This section is optional, you dont need to configure anything and your ace_editor form type will still work perfectly fine

There are also few options that alows you to manipulate including ace editor javascript sdk. 

```
# app/config/config.yml

norzechowicz_ace_editor:
    base_path: "bundles/norzechowiczaceeditor/ace"
    autoinclude: true
    debug: false # sources not minified with uglify.js
    noconflict: true # uses ace.require instead of require
```

You can also include ace editor directly from github, all you need to do is setting ``base_path`` option 

```
norzechowicz_ace_editor:
    base_path: "http://rawgithub.com/ajaxorg/ace-builds/master"
```

[![Bitdeli Badge](https://d2weczhvl823v0.cloudfront.net/norzechowicz/aceeditor-bundle/trend.png)](https://bitdeli.com/free "Bitdeli Badge")

