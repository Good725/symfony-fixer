# Symfony Upgrade Fixer [![Build Status](https://travis-ci.org/umpirsky/Symfony-Upgrade-Fixer.svg)](https://travis-ci.org/umpirsky/Symfony-Upgrade-Fixer)

Analyzes your Symfony project and tries to make it compatible with the new version of Symfony framework.

## Installation

### Manual

#### Local

Download the ``symfony-upgrade-fixer.phar`` file and store it somewhere on your computer.

#### Global

You can run these commands to easily access ``symfony-upgrade-fixer`` from anywhere on
your system:

```bash
$ sudo wget https://github.com/umpirsky/Symfony-Upgrade-Fixer/releases/download/v0.1.3/symfony-upgrade-fixer.phar -O /usr/local/bin/symfony-upgrade-fixer
$ sudo chmod a+x /usr/local/bin/symfony-upgrade-fixer
```
Then, just run ``symfony-upgrade-fixer``.

### Composer

#### Local

```bash
$ composer require umpirsky/symfony-upgrade-fixer
```

#### Global

```bash
$ composer global require umpirsky/symfony-upgrade-fixer
```

Make sure you have ``~/.composer/vendor/bin`` in your ``PATH`` and
you're good to go:

```bash
$ export PATH="$PATH:$HOME/.composer/vendor/bin"
```
Don't forget to add this line in your `.bashrc` file if you want to keep this change after reboot.

## Usage

The ``fix`` command tries to fix as much upgrade issues as possible on a given file or directory:

```bash
$ symfony-upgrade-fixer fix /path/to/dir
$ symfony-upgrade-fixer fix /path/to/file
```

The ``--dry-run`` option displays the files that need to be fixed but without actually modifying them:

```bash
$ symfony-upgrade-fixer fix /path/to/code --dry-run
```

## Fixers available

| Name  | Description |
| ----  | ----------- |
| form_configure_options | The method AbstractType::setDefaultOptions(OptionsResolverInterface $resolver) have been renamed to AbstractType::configureOptions(OptionsResolver $resolver). |
| form_events | The events PRE_BIND, BIND and POST_BIND were renamed to PRE_SUBMIT, SUBMIT and POST_SUBMIT. |
| form_getname_to_getblockprefix | The method FormTypeInterface::getName() was deprecated, you should now implement FormTypeInterface::getBlockPrefix() instead. |
| form_option_names | Options precision and virtual was renamed to scale and inherit_data. |
| form_parent_type | Returning type instances from FormTypeInterface::getParent() is deprecated, return the fully-qualified class name of the parent type class instead. |
| form_type_names | Instead of referencing types by name, you should reference them by their fully-qualified class name (FQCN) instead. |
| get_request | The getRequest method of the base controller class was removed, request object is injected in the action method instead. |
| inherit_data_aware_iterator | The class VirtualFormAwareIterator was renamed to InheritDataAwareIterator. |
| progress_bar | ProgressHelper has been removed in favor of ProgressBar. |
| property_access | Renamed PropertyAccess::getPropertyAccessor to PropertyAccess::createPropertyAccessor. |

## Real Life Examples

It is tested against few cool Symfony projects:

* [Sylius](https://github.com/Sylius/Sylius/pull/3571)
* [OroPlatform](https://github.com/orocrm/platform/pull/345)
* [Akeneo PIM](https://github.com/akeneo/pim-community-dev/pull/3571)

## Contribute

The tool is based on PHP Coding Standards Fixer and the [contributing process](https://github.com/FriendsOfPhp/php-cs-fixer/blob/master/CONTRIBUTING.md) is very similar. I see no sense in re-doing it so far.

If you want to contribute to README, please don't edit `README.md` directly - it is autogenerated. Edit `README.tpl` instead and run:
```bash
$ symfony-upgrade-fixer readme > README.md
```
