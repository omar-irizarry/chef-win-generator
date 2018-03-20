# chef-win-generator
This is a Custom Chef Generator for Windows.  This generator has been tested with a Windows 2016 virtual machine, windows host and ChefDk 2.5.3.

The custom generator is based on `chef generate generator` with the following differences:

1. .kitchen.yml is configured to work with a windows vm using winrm.
2. Integration testing and Unit testing default files have been tailored.
3. build_cookbook is disabled.  To enable build_cookbook un-comment last line of recipes/cookbook.rb
4. Attributes have been defined to customize .kitchen.yml and metadata.rb files:

## Attributes
```
default['win2016gen']['metadata']['copyright_holder'] = 'The Authors'
default['win2016gen']['metadata']['email'] = 'you@company.com'
# possible license values all_rights, apachev2, gplv2, gplv3, mit
default['win2016gen']['metadata']['license'] = 'apachev2'
default['win2016gen']['metadata']['git_org'] = 'https://github.com/yourcompany/'
default['win2016gen']['kitchen']['kitchen_gui'] = 'true'
default['win2016gen']['kitchen']['http_proxy'] = 'http://<username>@yourproxy:port'
default['win2016gen']['kitchen']['https_proxy'] = 'http://<username>@yourproxy:port'
default['win2016gen']['kitchen']['deprecations_errors'] = 'true'
default['win2016gen']['kitchen']['vagrant_username'] = 'vagrant'
default['win2016gen']['kitchen']['vagrant_password'] = 'vagrant'
default['win2016gen']['kitchen']['vm_name'] = 'windows2016min'
default['win2016gen']['kitchen']['custom_memory'] = '2000'
default['win2016gen']['kitchen']['private_ip'] = '192.168.1.1'
```
## Usage
`chef generate cookbook -g .\path\to\chef-win-generator cookbookname`

You can also add the following line to the config.rb/knife.rb `chefdk.generator_cookbook '.\path\to\chef-win-generator'` and call `chef generate cookbook cookbookname`.  The chef generate will default to use chef-win-generator.