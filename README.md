# TSM - Terminal Emulator State Machine

TSM is a state machine for DEC VT100-VT520 compatible terminal emulators. It
tries to support all common standards while keeping compatibility to existing
emulators like xterm, gnome-terminal, konsole, ..

TSM itself does not provide any rendering nor window management. It is a simple
plain state machine without any external dependencies. It can be used to
implement terminal emulators, but also to implement other applications that need
to interpret terminal escape sequences.

This library is very similar to libvte of the gnome project. However, libvte is
highly bound to GTK+, which makes it unsuitable for non-graphics projects that
need to parse escape sequences. Instead, TSM tries to restrict its API to
terminal emulation only. Furthermore, TSM does not try to establish a new
terminal emulation standard, but instead keeps compatibility as close to xterm
as possible. This is why the TERM variable can be set to xterm-color256 with any
TSM based terminal emulator.

## Requirements

libtsm has no runtime requirements other than a ISO-C compatible C library.
For keyboard key-symbols, the headers of libxkbcommon are needed during
compile-time only. libtsm ships a copy of these headers if they are not
available at compile-time.

# Armbian Build

```bash
git clone https://github.com/NickAlilovic/libtsm.git
cd libtsm
git archive --prefix=libtsm-4.3.0/ -o ../libtsm_4.3.0.orig.tar.gz HEAD
dpkg-buildpackage -us -uc
```

## Dependencies
### Required
- [meson](https://mesonbuild.com) >= 3.5
### Optional
- `xkbcommon-keysyms.h` from xkbcommon (Optional. Will use private copy if not found.)
## Test suite
- [check](https://libcheck.github.io/check/) >= 0.9.10 (For the test suite)
## Gtktsm
- gtk3
- cairo
- pango
- xkbcommon

## Documentation
There is currently no API documentation available. You can have a look at the
example terminal-emulator gtkterm [gtktsm-terminal.c](src/gtktsm/gtktsm-terminal.c)

## License
This software is licensed under the terms of an MIT-like license. Please see
[COPYING] for further information.
