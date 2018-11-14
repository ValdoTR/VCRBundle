VCRBundle
=========

Integrates [php-vcr](https://github.com/moufmouf/php-vcr) into Symfony and its
web profiler.

<img src="https://cloud.githubusercontent.com/assets/66958/5232274/b841676e-774b-11e4-8f4e-1f3e8cb7739e.png" width="280" height="175" alt="PHP-VCR Symfony web profiler panel"/>
<img src="https://cloud.githubusercontent.com/assets/66958/5232275/b84288d8-774b-11e4-803c-7b72f75e59b0.png" width="280" height="175" alt="PHP-VCR Symfony web profiler panel - request details"/>
<img src="https://cloud.githubusercontent.com/assets/66958/5232276/b84411b2-774b-11e4-93a9-475a0eeede65.png" width="280" height="175" alt="PHP-VCR Symfony web profiler panel - response details"/>

## Installation

1. Add forked repository in *composer.json*:

```php
    "repositories": [
        {
            "type": "vcs",
            "url": "https://github.com/ValdoTR/VCRBundle.git"
        }
    ],
``` 

2. Require and install `php-vcr/vcr-bundle`:

```bash
composer require --dev php-vcr/vcr-bundle "dev-master"
```

3. Declare the bundle in your `app/AppKernel.php` file:

```php
public function registerBundles()
{
    if (in_array($this->getEnvironment(), array('dev', 'test'))) {
        $bundles[] = new VCR\VCRBundle\VCRVCRBundle();
    }
}
```

## Configuration reference

Configure the bundle in your *config_dev.yml* (for example):

```yaml
vcrvcr:
    enabled: true
    library_hooks:
        stream_wrapper: true
        curl: true
        soap: true
    request_matchers:
        method: true
        url: true
        query_string: true
        host: true
        headers: false
        body: false
        post_fields: true
        soap_operation: true
    cassette:
        type: yaml
        path: <where_you_want_to_save_your_cassette>
        name: vcr.yml
```
> Note: The cassette file must be versionned 


## Credits

  * [Kévin Gomez](http://github.com/K-Phoen/)
  * [Ludovic Fleury](https://github.com/ludofleury) - to whom I borrowed the
    design of the web profiler part from his [GuzzleBundle](https://github.com/ludofleury/GuzzleBundle/).

## License

This bundle is released under the MIT license.
