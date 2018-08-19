# Installation

- Install latest version of PHP (>=7)
- Install latest version of git
- Install pandoc
- Windows user may need to add above in their PATH variable

```bash
  git clone https://github.com/shirshak55/Latest-Laravel-Docs-Generator laravel-docs-generator
```

# Generating offline documents

After you have completed the [installation](#installation) of required libraries & cloned the repo, you can build offline documentation for latest version of laravel by simply issueing following command from within the cloned directory.

```bash
$ /gen-doc.sh
```

With above command the documentation will be generated in **pdf** format with name **laravel.pdf** in the same directory. For most cases this will suffice your need of using this tool, but if not, then move on...

## Output formats

The default output format is **pdf** & the default file name is **laravel.pdf**, but as [pandoc](http://johnmacfarlane.net/pandoc/) is a versatile file format converter you can actually generate offline documents of any of format that [pandoc](http://johnmacfarlane.net/pandoc/) supports for output file. For example if you want to generate the offline document in **html** format, just pass a filename with **.html** extension as the first argument of the script as follows:

```bash
$ ./gen-doc.sh l4docs.html
```

To know more about the supported formats see explanation of **-t** && **-o** options in [documentation for pandoc](http://johnmacfarlane.net/pandoc/README.html#options) or man page for pandoc

Additionally you can pass any [options](http://johnmacfarlane.net/pandoc/README.html#options) that pandoc supports to control or fine tune the generated document as per your need. For example, the following command will generate an **html5** document instead of **html4** (which is default for html output)

```sh
  sh gen-doc.sh laravel.html -t html5
```

# Customization

To control the output of generated files, this tool uses [pandoc templates](http://johnmacfarlane.net/pandoc/README.html#templates) some default templates available from https://github.com/jgm/pandoc-templates as a git submodule. If you have the knowledge of customizing those templates, feel free to hack & twek the existing templates to meet your needs. Also for a comprehensive documentation of pandoc, please refer to the [github repo](https://github.com/jgm/pandoc) for pandoc.

# Contributing

If you find any bug, please file an issue in github issue tracker or fork & send pull request with fixes.

Thank You!
Shirshak Bajgain