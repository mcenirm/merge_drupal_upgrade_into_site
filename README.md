Terrible tools for merging a Drupal version upgrade into a git-managed web site.

# Make a Drupal Upgrade Patch

`make_drupal_upgrade_patch` will download the Drupal core
distribution files for two releases and create a patch file
representing the differences. It will omit certain files
(e.g., `CHANGELOG.txt`) that typically should be removed
from an active Drupal site.

An example use case is to apply core security fixes without
overwriting site-specific customizations.
[Never Hack Core](https://www.drupal.org/best-practices/do-not-hack-core)!

Currently supports only Drupal 6.x and 7.x.

## Example

```Shell
make_drupal_upgrade_patch 6.36 6.38
```

The resulting patch file is named `upgrade_drupal-6.36-6.38.patch`.

To apply the patch:

```Shell
cd $DRUPAL_ROOT
patch -p1 < ...path/to/upgrade_drupal-6.36-6.38.patch
... Resolve conflicts ...
drush updb
```
