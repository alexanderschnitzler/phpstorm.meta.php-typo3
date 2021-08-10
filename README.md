# .phpstorm.meta.php for TYPO3

This repository contains a `.phpstorm.meta.php` file which can be used to ease the work with TYPO3 projects in phpstorm. TYPO3 comes with a couple of factory methods which cannot clearly define a return type. In the past, a `dynamicReturnTypeMeta.json` file has often been used to tackle said issue. This however depends on a certain plugin to be installed. A `.phpstorm.meta.php` file can be used out of the box with all current phpstorm version.

## Example

```php
$class = \TYPO3\CMS\Core\Utility\GeneralUtility::makeInstance(\Foo::class);
```

In TYPO3, this method is usually used as a replacement for `new` but obviously, said method cannot state a return type.
To let phpstorm know what return type to expect, a simple override rule has to be define in `.phpstorm.meta.php`.

```php
// .phpstorm.meta.php
namespace PHPSTORM_META {
    override(\TYPO3\CMS\Core\Utility\GeneralUtility::makeInstance(0), type(0));
}
```

Now, phpstorm know the type of variable `$class`.
