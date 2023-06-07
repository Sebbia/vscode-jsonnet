# Jsonnet Support for Visual Studio Code

Jsonnet NG is a fork of original extenstion from [heptio](https://github.com/heptio/vscode-jsonnet) 
with some fixes and improvements. This fork created because the original 
project was abandoned and archived.

Extension features:

- simple syntax highlighting and code completion for [Jsonnet][jsonnet]
  files (specifically, files with the `.jsonnet` and `.libsonnet` 
  suffixes)
- Markdown-style preview pane that auto-updates every time you save
- manual formatting of Jsonnet documents

![Jsonnet preview][jsonnet-demo]

## Usage

Syntax highlighting works out of the box. Just open any `.jsonnet` or
`.libsonnet` file, and it will magically work.

To enable the Jsonnet preview pane, it is necessary to install the
Jsonnet command line tool (_e.g._, through `brew install jsonnet`). If
you don't add the `jsonnet` executable to the `PATH` then you will
need to customize `jsonnet.executablePath` in your `settings.json`, so
that the extension knows where to find it.

After this, you can use the keybinding for `jsonnet.previewToSide` (by
default this is `shift+ctrl+i`, or `shift+cmd+i` on macOS), and the
preview pane will open as in the picture above. Also you can bring a preview
by clicking **preview button** on the editor toolbar. 


For the formatting feature you have to configure `jsonnet.fmtExecutablePath`
in you `setting.json`. After this you can use **Format document** feature.

## Customization

This extension exposes the following settings, which can be customized
in `settings.json`:

* `jsonnet.executablePath`: Tells the extension where to find the
  `jsonnet` executable, if it's not on the `PATH`. (NOTE: This setting
  is always necessary on Windows.)
* `jsonnet.fmtExecutablePath`: Tells the extension where to find the
  `jsonnetfmt` executable, if it's not on the `PATH`. (NOTE: This setting
  is always necessary on Windows.)
* `jsonnet.fmtOptions`: Options that are passed when calling the
  `jsonnetfmt` executable. E.g. `--indent 2 --string-style d --comment-style s --no-pad-arrays --pad-objects --pretty-field-names`.
* `jsonnet.libPaths`: Additional paths to search for libraries when compiling Jsonnet code.
  It suppports variable substitution: `${workspaceFolder}`.
* `jsonnet.outputFormat`: Preview output format: yaml or json (default is yaml).
* `jsonnet.extStrs`: External strings to pass to `jsonnet` executable.
* `jsonnet.tlaStrs`: Top-level arguments to pass to `jsonnet` executable as strings.
* `jsonnet.tlaCodes`: Top-level arguments to pass to `jsonnet` executable as code.

This extension exposes the following commands, which can be bound to
keys:

* `jsonnet.previewToSide`: Compiles the Jsonnet file to JSON, places
  result in a "preview" window in the pane to the right of the active
  pane, or in the current pane if active window is pane 3 (since
  vscode only allows 3 panes). Default: bound to `shift+ctrl+i` (or
  `shift+cmd+i` on macOS).
* `jsonnet.previewToSide`: Compiles the Jsonnet file to JSON, places
  result in a "preview" window in the current active pane. Default: no
  keybinding.
* `jsonnet.extStrs`: An object of variable, value pairs. Allows you to
  customize the external variables passed to the `jsonnet` command
  line. It can be particularly useful to set this in a workspace
  configuration, so that you can set different variables on a
  per-project basis.
* `jsonnet.tlaStrs`: An object of variable, value pairs. Allows you to
  customize the top level arguments passed to the `jsonnet` command
  line as strings. It can be particularly useful to set this in a workspace
  configuration, so that you can set different variables on a
  per-project basis.
* `jsonnet.tlaCodes`: An object of variable, value pairs. Allows you to
  customize the top level arguments passed to the `jsonnet` command
  line as jsonnet code. It can be particularly useful to set this in a workspace
  configuration, so that you can set different variables on a
  per-project basis.
* `jsonnet.outputFormat`: A choice of two string literals: `["json",
  "yaml"]`. This tells the extension what format you'd like the output
  to be (_i.e._, allows you to either output JSON or YAML).

[jsonnet]: http://jsonnet.org/ "Jsonnet"
[jsonnet-demo]: https://raw.githubusercontent.com/heptio/vscode-jsonnet/master/images/kube-demo.gif
