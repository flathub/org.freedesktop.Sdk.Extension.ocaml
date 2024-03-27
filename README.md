# SDK Extension for OCaml stable

This extension contains various components of the [OCaml](https://ocaml.org/) stable toolchain.

Includes the [Dune build system](https://dune.build/) and the OCaml Package Manager [opam](https://opam.ocaml.org/).
## Create Flatpak OCaml applications

Several examples on how to Flatpak OCaml applications leveraging this SDK can be found [here](https://github.com/josecastillolema/flatpak-ocaml-examples).

## Debugging

In order to use this extension in a Flatpak SDK environment you may add all provided tools in your PATH by executing first:
```
$ source /usr/lib/sdk/ocaml/enable.sh
```

## Configure the Opam Environment

**NOTE: Opam environment (the `.opam` folder) is sandboxed per editor.** 

For example, vscodium might have different opam environment than emacs,
even when they use the same ocaml sdk extension.
[opam local swtich](https://opam.ocaml.org/blog/opam-local-switches/) can partially circumvent this issue.

Typically, global opam switches can be found in `~/.var/app/<editor flatpak id>/.opam`

## Add Persistent `.opam` Path

Add `.opam` as a persistent path for your editor of choice in [flatseal](https://flathub.org/apps/com.github.tchx84.Flatseal)

Using [vscodium](https://flathub.org/apps/com.vscodium.codium) as an example:

<img src="./img/opam-persistent-path-vscodium.png" width="400" alt="The persistent path setting in flatseal, showing a edited field with value `.opam` and a grey out uneditable field with value `.vscode-oss`"/>

## Initializing Opam Environment

In order to interactivelly install [OCaml Package Manager (opam)](https://opam.ocaml.org/) packages in a Flatpak environmment you will need to initialize a new environment:
```
$ opam init --disable-sandboxing
```

## Development
To use the SDK with your favourite editor:
```
$ sudo flatpak override --env=FLATPAK_ENABLE_SDK_EXT=ocaml com.visualstudio.code
$ sudo flatpak override --env=FLATPAK_ENABLE_SDK_EXT=ocaml org.gnu.emacs
$ sudo flatpak override --env=FLATPAK_ENABLE_SDK_EXT=ocaml io.neovim.nvim
```

or just use `FLATPAK_ENABLE_SDK_EXT=*` to load every SDK available in your system:
```
$ sudo flatpak override --env=FLATPAK_ENABLE_SDK_EXT=* com.visualstudio.code
```

When running your editor you should see something like this, i.e.:
```
$ flatpak run com.visualstudio.code
flatpak-vscode: Enabling SDK extension "ocaml"
```
