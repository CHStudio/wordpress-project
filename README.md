[WordPress](https://wordpress.org/) project creation helper [![Latest Stable Version](https://img.shields.io/packagist/v/chstudio/wordpress-project.svg)](https://packagist.org/packages/chstudio/wordpress-project)
===========================================================

This repository is an empty wordpress project that can be used to start a new website. It also contains some tools to
help project industrialisation (deployment, testing, content manipulation...).

## Create a new project

To start a new project using this barebone one, you just need to run :

```bash
composer create-project chstudio/wordpress-project [path] [version]
```

* `[path]` is the path to the installation directory, if not defined, a `wordpress-project` folder will be created in your
current path.
* `[version]` is the version of the project to use when installing, if not defined, the more recent stable is used, else
you can use : `dev-master`, `v0.0.0`, ...

You can also use a simple `git clone` :

```bash
git clone https://github.com/CHStudio/wordpress-project.git
```

## Configuration

To configure database credentials and all the others settings, you can rely to command parameters or create a specific
`wp-cli.local.yml` file at project root.

You must check the [WP-CLI configuration handbook](https://make.wordpress.org/cli/handbook/config/) for more details.

Example of local configuration :

```yml
path: public/wp-cms
color: true

core install:
  title: "WordPress Project !"
  url: http://wordpress-project.dev
  admin_user: stephane
  admin_email: s.hulard@chstudio.fr

core config:
  dbuser: root
  dbpass: mypass
  dbname: my_database
  extra-php: |
    define( 'WP_DEBUG', true );
    define( 'WP_POST_REVISIONS', 50 );
```

Beware, never add your `wp-cli.local.yml` file to Git, it may contains sensitive information.

## Installation

This project rely on [WP-CLI](https://make.wordpress.org/cli/) to perform common tasks.

To install your local environment you must run the following commands :

```bash
bin/wp core download
bin/wp core config
bin/wp core install
mv public/wp-cms/wp-config.php public
```

If your local configuration is not defined, you must pass all the required parameters. You can get more details by
running `--help` flag on each command (will display parameters and command description).

If you haven't defined it, the `core install` will prompt the generated administrator password, you'll be asked to change it
after your first admin panel login.

The last one moves the generated configuration file to your project public root. It's mandatory to use the
`public/wp-content` folder as code container.

When the execution has succeded, you can access your local installation.

## Philosophy

You can review some details about this project philosophy here (french) : http://www.24joursdeweb.fr/2014/comment-bien-versionner-son-site-wordpress-avec-git-et-github/

A presentation was made at the first WordCamp in Lyon (france). You can review the [video](http://wordpress.tv/2015/06/13/stephane-hulard-wordpress-git-et-lintegration-continue/) or the [slides](http://www.slideshare.net/s_hulard/wordpress-gitintegrationcontinuehulardwordcamplyon2015).

## Contributing

We welcome everyone to contribute to this project. Below are some of the things that you can do to contribute.

- Read [our contributing guide](CONTRIBUTING.md).
- [Fork us](https://github.com/chstudio/wordpress-project/fork) and [request a pull](https://github.com/chstudio/wordpress-project/pulls) to the [develop](https://github.com/chstudio/wordpress-project/tree/develop) branch.
- Submit [bug reports or feature requests](https://github.com/chstudio/wordpress-project/issues) to GitHub.

## LICENSE

Apache License 2.0 
