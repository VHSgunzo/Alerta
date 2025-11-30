# `alerta`: show GUI dialogs from the command line

`alerta` is a small command-line tool that will display a simple graphical X11 dialog to the user.

It is similar to [Zenity] and [KDialog], but **statically linked** and with
**zero C/C++ dependencies**.

In addition to being a command-line tool, `alerta` can also be used as a Rust library,
for showing simple dialogs from Rust applications that don't want to pull in an entire GUI
framework.

[Zenity]: https://gitlab.gnome.org/GNOME/zenity
[KDialog]: https://github.com/KDE/kdialog

## Goals

- Produce a <500 KB statically linked executable.
- No hard dependencies on `xcb`, `xlib`, or other C libraries.
- Try not to look *completely* out of place in common desktop environments.

## To get started:
* **Download the latest revision**
```
git clone https://github.com/VHSgunzo/Alerta.git && cd rust-nightly-template
```
* **Compile a binary**
```
rustup install nightly
rustup target add x86_64-unknown-linux-musl
rustup component add rust-src --toolchain nightly
cargo build --release
```
* Or take an already precompiled binary file from the [releases](https://github.com/VHSgunzo/Alerta/releases)

## Showcase

```shell
$ alerta "Hello World!"
```

![Dialog (light theme) with an "Information" icon and the text "Hello World!"](screenshots/hello-world.png)

```shell
$ alerta --icon=error --title="Oh no!" --theme=dark --buttons=retrycancel $'Whoops!\n\nAn error has occurred!'
```

![Error dialog (dark theme) with Retry and Cancel buttons](screenshots/error.png)

```shell
$ alerta --icon=question --title="Fries?" --theme=dark --buttons=yesno "Would you like some fries with that?"
```

![Question dialog (dark theme) with Yes and No button](screenshots/question.png)
