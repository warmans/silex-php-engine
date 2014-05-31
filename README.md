# SilexPhpEngine

Simple service provider for the PhpEngine of the [Symfony Templating Component](https://github.com/symfony/Templating).

## Usage

Add to composer.json and install.

Update service configuration:

```php
//create application
$app = new Silex\Application();

//view config
$app['view.paths'] = array(
    '/path/to/view/dir/%name%.html.php'' //name is replace by the template name
);

//register view service
$app->register(new SilexPhpEngine\ViewServiceProvider());
```

Note if you're using the config provider you can just add the view.paths option to your config.

Now in a controller you can use the view service to render a template:

```php
$app->get('/', function() use ($app) {
    return $app['view']->render('index'); //will load /path/to/view/dir/index.html.php
});
```

To find out what options are available within a view refer to:

* [The Symfony Cookbook](http://symfony.com/doc/current/cookbook/templating/PHP.html)
* [The Symfony Docs](http://symfony.com/doc/current/components/templating/introduction.html)