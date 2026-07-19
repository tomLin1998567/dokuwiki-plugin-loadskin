# DokuWiki Plugin: LoadSkin — PHP 8 Compatible Fork

Fork of [selfthinker/dokuwiki-plugin-loadskin](https://github.com/selfthinker/dokuwiki-plugin-loadskin) (archived upstream, last updated 2017).

Allows admins to select different templates for specific pages or namespaces, and users to choose their preferred template for the whole wiki.

## ✅ PHP 8 Compatibility Fixes

The upstream plugin was written for PHP 5/7 and triggers deprecation warnings under PHP 8. This fork fixes all known issues:

| Fix | Line | Before | After |
|-----|------|--------|-------|
| Remove `require_once` | — | `require_once(DOKU_PLUGIN.'action.php')` | Removed (modern DokuWiki uses autoloading) |
| Undefined array key | `_getTplPerNamespace()` | `if($data[$id])` | `if(isset($data[$id]) && $data[$id])` |
| Undefined array key | `_getTplPerUser()` | `$_SERVER['REMOTE_USER']` | `$_SERVER['REMOTE_USER'] ?? ''` |
| Undefined array key | `_tplUserConfig()` | `return $data[$user]` | `return $data[$user] ?? false` |

No functionality changes — only PHP 8 compatibility.

## Installation

Copy the `loadskin/` folder into your DokuWiki `lib/plugins/` directory:

```bash
cd /path/to/dokuwiki
git clone https://github.com/tomLin1998567/dokuwiki-plugin-loadskin.git lib/plugins/loadskin
```

Or download the ZIP from the [releases page](https://github.com/tomLin1998567/dokuwiki-plugin-loadskin/releases).

Then enable the plugin via **Admin → Extensions**.

## Usage

- **Admin:** Configuration → LoadSkin — assign templates to pages or namespaces.
- **User:** A template switcher appears on pages where multiple templates are available.

## Credits

- Original authors: [Michael Klier](https://github.com/selfthinker) and [Anika Henke](https://github.com/selfthinker)
- PHP 8 compatibility fixes by [tomLin1998567](https://github.com/tomLin1998567)
