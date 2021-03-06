# Change Log

## [2.2.5](https://github.com/antergos/web-greeter/tree/2.2.5) ~ 04-24-2017

**Fixed:**

  * Support for webkitgtk 2.16+

[Full Changelog](https://github.com/antergos/web-greeter/compare/2.2.4...2.2.5)


## [2.2.4](https://github.com/antergos/web-greeter/tree/2.2.4) ~ 04-04-2017

**Added:**

  * Support for webkitgtk 2.16+

[Full Changelog](https://github.com/antergos/web-greeter/compare/2.2.3...2.2.4)


## [2.2.3](https://github.com/antergos/web-greeter/tree/2.2.3) ~ 02-18-2017

**Changed:**

  * Revert workaround implemented in v2.2.2 for webkit2gtk 2.14.4+. It remains in place for
    versions in the 2.14.0 series older than 2.14.4.

[Full Changelog](https://github.com/antergos/web-greeter/compare/2.2.2...2.2.3)


## [2.2.2](https://github.com/antergos/lightdm-webkit2-greeter/tree/2.2.2) ~ 01-18-2017

**Fixed:**

  * Implement workaround to prevent the web process from crashing in webkit2gtk 2.14.3

[Full Changelog](https://github.com/antergos/lightdm-webkit2-greeter/compare/2.2.1...2.2.2)


## [2.2.1](https://github.com/antergos/lightdm-webkit2-greeter/tree/2.2.1) ~ 12-26-2016

**Fixed:**

  * Increased the timeout for the "theme loaded" check to ensure themes are given 
    enough time to load (when running on less powerful systems). (GH #98)
  * Fixed issue where users' custom .face image failed to load. (GH #98)

[Full Changelog](https://github.com/antergos/lightdm-webkit2-greeter/compare/2.2...2.2.1)


## [2.2](https://github.com/antergos/lightdm-webkit2-greeter/tree/2.2) ~ 12-18-2016

**Added:**

  * The JavaScript API for themes is now [fully documented](https://goo.gl/0iPzA4).
  * New Theme Error Recovery System that will alert the user when errors are
    detected during JavaScript execution and give them the option to to load a fallback theme.
  * New config option: secure_mode (enabled by default). When enabled, only local http
    requests are allowed in themes. All non-local requests will be blocked.
  * It is now possible to override the language and format used by the greeter when displaying
    the current time. See the greeter config file for details.
  * A new utility method for getting the current localized time is available to themes.
  * Simple theme now has a fade out exit animation.

**Changed:**

  * Switched build systems from Autotools to Meson.
  * Updated API usage for LightDM 1.19.2+.
  * Updated bundled JS & CSS vendor libs to their latest versions.
  * Updated translations with latest changes contributed by the Antergos Community on Transifex.
  * Default theme:
    - Buttons and user list-box items received some minor style enhancements.
    - Theme is now compatible with the latest jQuery.
  * Simple theme:
    - Removed deprecated HTML4 tags.
    - Improved styles for the input field.

**Fixed:**

  * The ugly default X cursor will no longer be shown after the greeter exits.
  * Default theme:
    - The error messages container will now appear correctly (size and position).
    - It is now once again possible to skip straight to password entry by pressing either
      the spacebar or the enter key.

**Removed:**

  * Removed the Theme Heartbeat system.

[Full Changelog](https://github.com/antergos/lightdm-webkit2-greeter/compare/2.1.6...2.2)


## [2.1.6](https://github.com/antergos/lightdm-webkit2-greeter/tree/2.1.6) ~ 10-17-2016

**Added:**

  * The greeter is now compatible with LightDM 1.19.2+

[Full Changelog](https://github.com/antergos/lightdm-webkit2-greeter/compare/2.1.5...2.1.6)


## [2.1.5](https://github.com/antergos/lightdm-webkit2-greeter/tree/2.1.5) ~ 10-14-2016

**Fixed:**

  * Remove old code related to GDKWindow filters as it is no longer necessary and
    was actually causing issues with webkitgtk 2.14+.

[Full Changelog](https://github.com/antergos/lightdm-webkit2-greeter/compare/2.1.4...2.1.5)


## [2.1.4](https://github.com/antergos/lightdm-webkit2-greeter/tree/2.1.4) ~ 04-27-2016

**Added:**

  * New Theme Heartbeat System to allow the greeter to detect and respond to theme failures.

**Changed:**

  * Updated translations.

[Full Changelog](https://github.com/antergos/lightdm-webkit2-greeter/compare/2.1.3...2.1.4)


## [2.1.3](https://github.com/antergos/lightdm-webkit2-greeter/tree/2.1.3) ~ 04-16-2016

**Added:**

  * New Theme Heartbeat System to allow the greeter to detect and respond to theme failures.

**Changed:**

  * Implemented work-around in default theme for a webkit2gtk bug related to localStorage.
  * Moved vendor css, js, & font files into new top level `_vendor` directory for
    easy access from any theme that needs them.

**Fixed:**

  * Default theme:
    - Fix time format when no value is cached.
    - Fix empty session dropdown when no session is cached.

[Full Changelog](https://github.com/antergos/lightdm-webkit2-greeter/compare/2.1.2...2.1.3)


## 2.1.2

* Allow access to right-click context menu when debug mode is enabled in lightdm-webkit2-greeter.conf.
* Add additional debug messages to the default theme to help identify points of failure.
* Fix issue with screen blanking functionality when greeter is used as a lockscreen.

## 2.1.1

* Fix default theme initialization failure if config file values are missing.

## 2.1.0

* It is now possible to configure branding including logos and backgrounds
  in lightdm-webkit2-greeter.conf.
* The GTK+ fade-out on-exit animation was removed in favor of allowing themes
  to handle the animation with webkit (via javascript) as the latter provides
  a much nicer effect. See the default antergos theme for an implementation example.
* Themes Javascript API Improvements:
  - Themes can now easily query values from lightdm-webkit2-greeter.conf
    using the new global "config" object:
    * config.get_str()
    * config.get_num()
    * config.get_bool()
  - A new global object "greeterutil" was added to provide utility functions
    to themes. Newly added utility functions:
    * greeterutil.dirlist() - List the contents of a directory.
    * greeterutil.text2html() - Escape HTML entities in a string.
  - Themes should now query the config file for the distro logo to use. See
    the default antergos theme for an implementation example.
* Default theme:
  - Theme is no longer compiled to ES2015 as Webkit2Gtk now supports ES6.
  - The logo can now be configured in lightdm-webkit2-greeter.conf.
  - The background images directory can also be configured in lightdm-webkit2-greeter.conf.
* Several small bug fixes, enhancements, and code cleanup commits also made it into this release.

## 2.0.0

* Version scheme updated for both the webkit1 and webkit2 greeters as follows:
  - MAJOR.MINOR.UNIQUE_FIXES
    * MAJOR: Denotes a major release. Shared by legacy webkit1 and webkit2 greeters.
    * MINOR: Denotes small changes/fixes. Also shared by webkit 1 and webkit2 greeters.
    * UNIQUE_FIXES: Denotes fixes unique to either the legacy webkit1 or webkit2 greeters.
* Legacy Webkit1 greeter development is officially in maintenance-only mode (bug fixes only).
* Webkit2 greeter supersedes the Webkit1 greeter and is the focus of all new development.
* Completed API including the guest and auto-login functions.
* API is now completely in-line with LightDM API.
* Several functional code improvements.
* Added Exception handling.
* Added man page.
* Default theme:
  - Added translations.
  - Added confirmation dialogue for system actions.
  - Theme's script was completely rewritten in ES6.
  - Use babel to compile ES6->ES5 until webkit catches up.

## 0.2.3

* Add support for getting the lock_hint from lightdm.
* Default webkit theme is now antergos.
* Code formatting cleanup

## 0.2.1

* Handle tasks that a WM would normally handle.
* Code clean-up

## 0.2.0

* Add missing lightdm.set_language function
* Fix compile warnings

## 0.1.3

* Port from webkitgtk -> webkit2gtk
* Use GTK+ 3.0

## 0.1.2

* Fix files not being added to tarball
* Don't use AC_CONFIG_MACRO_DIR in configure.ac

## 0.1.1

* Update to work with newer LightDM

## 0.1.0

* Split out into separate module from lightdm
