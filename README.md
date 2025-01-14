[![Version](https://img.shields.io/gem/v/autotest-fsevent.svg?style=flat)](https://rubygems.org/gems/autotest-fsevent)
[![Donorbox](https://img.shields.io/badge/donate-on_donorbox-yellow.svg)](https://donorbox.org/bitcetera)

# autotest-fsevent

Autotest relies on filesystem polling to detect modifications in source code files. In other words: The filesytem is constantly being traversed which causes quite some load on both the CPU and the harddrive. This is not healthy for your Mac and if you are working on a portable computer, it will drain your battery.

Apple has introduced FSEvent with Mac OS X 10.5 which is a very efficient way to have the operating system monitor file alterations. This gem teaches autotest to use FSEvent and therefore be nice to your Mac.

* [Homepage](https://github.com/svoop/autotest-fsevent)
* Author: [Sven Schwyn - Bitcetera](http://www.bitcetera.com)

## Install

This gem is [cryptographically signed](https://guides.rubygems.org/security/#using-gems) in order to assure it hasn't been tampered with. Unless already done, please add the author's public key as a trusted certificate now:

```
gem cert --add <(curl -Ls https://raw.github.com/svoop/autotest-fsevent/main/certs/svoop.pem)
```

In order to compile the fsevent binary at install time, Xcode (macOS development suite) must be installed. You can download it for free from:

https://developer.apple.com

You can use any ZenTest-compatible test suite with this gem such as:

* [minitest-autotest](https://rubygems.org/gems/minitest-autotest)
* [Zentest](https://rubygems.org/gems/ZenTest)
* [autotest-standalone](https://rubygems.org/gems/autotest-standalone)

Add this to your `Gemfile` or `gems.rb`:

```ruby
gem autotest-fsevent, group: :development
```

And securely install the bundle:

```
bundle install --trust-policy MediumSecurity
```

Then add the following line *after all other requires* in your `~/.autotest` file:

```
require 'autotest/fsevent'
```

## Troubleshooting

### Autotest Binary Not Present

Make sure you have either the ZenTest gem or the autotest-standalone gem installed. This dependency has been dropped as of autotest-fsevent-0.2.3 in order to allow any compatible test suite.

### Compilation of fsevent_sleep Failed

Make sure you have Xcode (Mac OS X Development Suite) installed. You can download it for free from:

https://developer.apple.com

If you don't want to install Xcode, [download the prebuilt fsevent_sleep binary](https://github.com/svoop/autotest-fsevent/tree/main/prebuilt), make the downloaded binary executable and install the gem as follows:

```
FSEVENT_SLEEP="/absolute/path/to/fsevent_sleep" gem install autotest-fsevent
```

## Development

To install the development dependencies:

```
bundle install
```

Please submit issues on:

https://github.com/svoop/autotest-fsevent/issues

To contribute code, fork the project on Github, add your code and submit a pull request:

https://help.github.com/articles/fork-a-repo

## License

The gem is available as open source under the terms of the [MIT License](http://opensource.org/licenses/MIT).
