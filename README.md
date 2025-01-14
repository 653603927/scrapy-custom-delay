# Scrapy-Custom-Delay

[![PyPI](https://img.shields.io/pypi/v/scrapy-custom-delay)](https://pypi.org/project/scrapy-custom-delay/)
[![PyPI - Python Version](https://img.shields.io/pypi/pyversions/scrapy-custom-delay)](https://pypi.org/project/scrapy-custom-delay/)

`Scrapy-Custom-Delay` is a package that lets you set different delay for different website, using the [Scrapy](https://github.com/scrapy/scrapy) framework.

## Install
```
$ pip install scrapy-custom-delay
```

## Usage

### Step 1: Use the following config values in your scrapy settings:

1. Enable the AutoThrottle extension.

	```python
	AUTOTHROTTLE_ENABLED = True
	```

2. Enable the Custom Delay Throttle by adding it to `EXTENSIONS`.

	```python
	EXTENSIONS = {
	    'scrapy.extensions.throttle.AutoThrottle': None,
	    'scrapy_domain_delay.extensions.CustomDelayThrottle': 300,
	}
	```

3. Add `{'regex': 'download delay (in seconds)'}` to the `DOMAIN_DELAYS`.

	something like:

	```python
	# set up custom delays per domain
    # if two or more regexes satisfy, the first one will be used
	DOMAIN_DELAYS = {
	    r'^images.google.com*$': 1.0,
	    r'*github*': 0.5,
	}
	```
