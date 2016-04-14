HirenPDFCrowdBundle
=================

This bundle act as a thin wrapper over the PDFCrowd API to ease integration with Symfony.

## Installation

### Using composer

    {
        "repositories": [
            {
                "type": "package",
                "package": {
                    "name": "pdfcrowd/pdfcrowd-php",
                    "version": "2.6",
                    "dist": {
                        "url": "http://pdfcrowd.com/static/clients/php/pdfcrowd-2.6-php.zip",
                        "type": "zip"
                    },
                    "autoload": {
                        "files": ["pdfcrowd.php"]
                    }
                }
            }
        ],
        "require": {
            "hiren/pdfcrowd-bundle": "dev-master"
        }
    }

### Add the bundle to your application kernel

``` php
// File: app/AppKernel.php
public function registerBundles()
{
    return array(
        // ...
        new Hiren\PDFCrowdBundle\AmpPDFCrowdBundle(),
        // ...
    );
}
```

## Configuration

``` yaml
hiren_pdf_crowd:
    username: your-username
    apikey: the-api-key
```

## Usage

### Controller

``` php
$pdfCrowd = $this->get('hiren_pdf_crowd.api');
$url = $this->generateUrl('route_name', array(), true);

$pdfData = $pdfCrowd->convertURI($url);
$fileName = $this->container->getParameter('kernel.root_dir') . '/../web/pdfs/example.pdf';

file_put_contents($fileName, $pdfData); // Make sure this directory is writable
```
