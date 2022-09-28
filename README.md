# dokku-redash

dokku-redash is a plugin for [dokku][dokku] that allows you to easily deploy a [redash][redash] instance on your server.

## Installation

```sh
sudo dokku plugin:install https://github.com/LeStormy/dokku-redash.git
```

### Upgrading from previous versions

```sh
sudo dokku plugin:update redash
```

## Commands

```
$ dokku redash:help
    redash:create <app> <repo>         Create a Redash app from the given repo (or the official repo if none given)
```

## Dependencies

You must have installed the [postgres plugin][dokku-postgres] and the [redis plugin][dokku-redis].
Redash uses both and this plugin will not work otherwise.

## Usage

Create a Redash app simply with this command:

`$ dokku redash:create redash`

This will create a dokku app named redash, a postgres and a redis service named redash, and link them all together.

By default, this will build and deploy Redash from the [official repository][redash].
You can change this behavior by specifying the https URL of your Redash fork like so: 

`$ dokku redash:create redash "https://github.com/LeStormy/redash.git"`

## Final Configuration

This plugin does not set a domain for your Redash instance. Don't forget to set one!
It's as easy as this: 

`$ dokku domains:set redash redash.stormycat.xyz`

Think about SSL! I like to use the [letsencrypt plugin][dokku-letsencrypt] but you do you!

## Voilà !

You're all set :3

## License

This plugin is released under the MIT license.

[dokku]: https://github.com/dokku/dokku
[redash]: https://redash.io
[dokku-postgres]: https://github.com/dokku/dokku-postgres
[dokku-redis]: https://github.com/dokku/dokku-redis
[dokku-letsencrypt]: https://github.com/dokku/dokku-letsencrypt
