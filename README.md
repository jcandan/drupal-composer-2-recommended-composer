# Drupal 8.8 Recommended Composer Enhancements

Because, let's face it, Drupal 8.8 core missed some key components that made `drupal-composer/drupal-project` awesome.

Here, we tackle the `.gitignore` file and `.env`.

## What to ignore

The Drupal 8.8+ composer-ready project templates nearly shipped with a `.gitignore` that would ignore composer-managed files (e.g. `vendor/`, `web/modules/contrib`). Although Composer documentation [recommends](https://getcomposer.org/doc/faqs/should-i-commit-the-dependencies-in-my-vendor-directory.md) that vendored files should not be committed, there are opposing schools of thought about whether vendored files should be a part of one's git repository. That `.gitignore` was deemed too opinionated for core. [This ticket](https://www.drupal.org/project/drupal/issues/3082958) may try to address this shortcoming.

Here we provide an oppinionated `.gitignore` that follows Composer recommended model of ignoring vendored files.

## Environment variables

We also missed out on the very useful `dotenv` file for environment specific variables. 

1. Copy the `autoload` property to `composer.json`.
2. Uncomment the `/web/sites/default/settings.php` in `.gitignore`
3. Follow the directions noted in `.env.example`
4. Place `load.environment.php` in your project root
5. Run the following:
   ```
   composer require vlucas/phpdotenv
   ```

## Drush Policies

Drush is great. Let's grab it, and add policies which protect production from any unwanted drush site-alias database or file overwrites.

1. Copy `PolicyCommands.php` to `drush/Commands/`
2. Run the following:
   ```
   composer require drush/drush
   ```
