gsettings.el
============

This Emacs package provides helpers for
[GSettings](https://developer.gnome.org/gio/stable/GSettings.html),
the configuration system used by the [Gnome](https://www.gnome.org/)
desktop.

It can be used to read (and set) desktop configuration settings in
Emacs, which can be useful in `init.el` to set Emacs settings based on
the desktop configuration.

For parsing of configuration values, this package uses the
[gvariant.el](https://github.com/wbolster/emacs-gvariant) library.

Installation
------------

Install `gsettings.el` from Melpa, e.g.

```
M-x package-install RET gsettings RET
```

Or, using `use-package`:

```elisp
(use-package gsettings)
```

Usage
-----

Example:

``` elisp
(use-package gsettings
  :config
  (when (gsettings-available?)
    (blink-cursor-mode (if (gsettings-get "org.gnome.desktop.interface" "cursor-blink") 1 -1))))
```

After loading the library with `(require 'gsettings)` (not needed when
using `use-package`), you can use the following functions:

- `gsettings-available? ()`
- `gsettings-get (schema key)`
- `gsettings-get-default (schema key default)`
- `gsettings-list-schemas ()`
- `gsettings-schema-exists? (schema)`
- `gsettings-list-keys (schema)`
- `gsettings-reset (schema key)`
- `gsettings-set-from-gvariant-string (schema key value)`
- `gsettings-gnome-running?`
- `gsettings-apply-gnome-settings`

Most functions require the `gsettings` tool to be installed. You can
use the `gsettings-available?` helper as a guard.

License
-------

(This is the OSI approved 3-Clause BSD License.)

Copyright 2019 wouter bolsterlee

Redistribution and use in source and binary forms, with or without
modification, are permitted provided that the following conditions are
met:

1. Redistributions of source code must retain the above copyright
   notice, this list of conditions and the following disclaimer.

2. Redistributions in binary form must reproduce the above copyright
   notice, this list of conditions and the following disclaimer in the
   documentation and/or other materials provided with the
   distribution.

3. Neither the name of the copyright holder nor the names of its
   contributors may be used to endorse or promote products derived
   from this software without specific prior written permission.

This software is provided by the copyright holders and contributors
"as is" and any express or implied warranties, including, but not
limited to, the implied warranties of merchantability and fitness for
a particular purpose are disclaimed. In no event shall the copyright
holder or contributors be liable for any direct, indirect, incidental,
special, exemplary, or consequential damages (including, but not
limited to, procurement of substitute goods or services; loss of use,
data, or profits; or business interruption) however caused and on any
theory of liability, whether in contract, strict liability, or tort
(including negligence or otherwise) arising in any way out of the use
of this software, even if advised of the possibility of such damage.
