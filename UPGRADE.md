# Upgrade from 0.4 to 0.5

## TTY prefix

`bin.dev_server.tty_prefix` was added with
`['node', 'node_modules/webpack-dashboard/bin/webpack-dashboard.js', '--']`
default value.

This requires changes in `package.json` and `webpack.config.js`.

You can set it to `[]` to disable NASA-like dashboard when compiling assets.
 
## AssetManager

Second parameter for `AssetManager::getAssetUrl` has been made optional.
If not provided, it is figured by configuration so that binary files could be loaded with `webpack_asset` twig function.

## Non-Javascript Entry File Support

Now you can use `webpack_asset` on other files than `.js` - for example, for images.

This requires changes in `package.json` and `webpack.config.js`.

You can disable this by setting `entry_file.enabled` to `false` in `config.yml`.

You should always do this procedure after updating this bundle:
- run `maba:webpack:setup`, replace files and merge changes
- run `npm install` (this should be done with `composer install` (and) as a step in deployment)

## Explicit API for semantic versioning

Some interfaces, classes and class methods were marked with `@api`.
Any other classes or methods can be changed or removed without MAJOR release bump.

Also most of the services marked as private for the same reason - you should only use those that
are public.

## Deprecated setting custom twig function

`maba_webpack.twig.function_name` configuration option is deprecated and will be removed in 0.6
