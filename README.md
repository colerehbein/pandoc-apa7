# pandoc-apa7

This project is CURRENTLY A WORK IN PROGRESS. It is a LaTeX template for use with pandoc to convert Markdown into an APA 7-compliant LaTeX file. 

This enables a greatly simplified academic writing workflow. One can draft a Markdown manuscript in any Markdown editor (suggestions below), convert the Markdown to a LaTeX file using pandoc, and then generate a (hopefully!) perfect PDF file.

At this time, the project is focused on establishing the most basic working template with the goal of adding enhancements later. This means focusing on fine-tuning page, text, citation, and bibliogrpahic formatting before turning to things like tables, graphs, or images (yikes!). 

I am a Mac user so these instructions are geared towards macOS.

# Installation

Most of this software can also be installed in the command line using appropriate Homebrew commands.

## Required Software

### Markdown editor

Use whatever Markdown editor you like. I personally enjoy Zettlr <https://zettlr.com> because it manages citations well. However, exporting Zettlr manuscripts to Markdown involves altering a Zettlr asset to prevent the internal pandoc from rendering citations as properly formatted citations (eg. (Smith, 2022)) instead of as Markdown citations (eg. [@smith2022]). This is outside the scope of this README but please contact the author should such a workaround be desired.

### Pandoc

Pandoc is needed to use the pandoc templates. You can find it here: <https://pandoc.org/installing.html>.

### LaTeX

You'll need a LaTeX distribution to build the APA formatted pdf files (e.g., MikTex or MacTex). This can be found here: <https://ctan.org/starter>

#### Latex Packages

##### BibLaTeX

This is the most robust and well-supported citation package for APA7 and the only one fully supported by the LaTeX apa7 package at the time of this writing. You can install this through the Tex Live Utility gui provided 

### Zotero with BetterBibTex

I can't imagine how you're managing your references without Zotero. The BetterBibTex plugin generates unique citation keys that can be adjusted to your preference, and then can export the .bib file needed to properly render citations and the references section during the pandoc conversion.

<!---
This was original material from the first project. Not sure how it incorporates at this time.

## Filters

Pandoc doesn't yet support cross referencing figures and tables. You'll need a Python distribution to install two filters to be able to do this. The filters are `pandoc-fignos` and `pandoc-tablenos`. You can find links and installation instructions here <https://github.com/tomduck/pandoc-fignos>
!>

# Usage

Download the file APA7.tex and put it in your project directory or in a resources/template file that you'll be able to find later. 

In this project directory, you'll also want to put your .md file of your manuscript and your .bib file with your references. This file will also be home to all the exports from pandoc.

In the command line, change the working directory to the project directory. Use the command:
	$ pandoc 
	
This should produce a properly formatted LaTeX file that can then be rendered into a pdf using the following pandoc command:
	$ pandoc
	
Or you can load the LaTeX source into an editor of your choice, such as texstudio, for double-checking and compiling. 

## Pandoc YAML Metadata Block

These templates makes heavy use of the pandoc metadata block at the beginning of your document. I've also provided a snippet you can use to insert the metadata and fill in what is needed (Tools > Snippets). Most of the commands used in the `apa7` package are fields that can be used in the YAML header. See documentation for more details: <https://mirror.math.princeton.edu/pub/CTAN/macros/latex/contrib/apa7/apa7.pdf>. Fields used in this template are:

- `mode`
    - Set to `man`, `doc`, `stu`, or `jou`. This is the only *absolutely* necessary option to generate a file with no errors.
- `title`
    - Main title of the document. Consistent with the pandoc variable.
- `subtitle`
    - Running head title. Consistent with the pandoc variable.
- `author`
    - List of authors. Put multiple authors on one line to group by affiliation. Consistent with the pandoc variable.
- `institute`
    - List of affiliations. Won't work with docx. You have to add this manually.
- `twogroups`, `threegroups`, ... , `sixgroups`
    - Set one of these to true if grouping authors by different affiliations, as in the twogroup YAML example. If anyone of these options are not set, it will use the standard `\author{}` command.
- `authornote`
    - A note that will be placed at the bottom of the title page, or footnote if in `jou` mode.
- `bibliography`
    - Location of your bibtex references file, whatever pandoc-citeproc will read. Can add multiple fields for multiple files.
- `date`
    - Place anything typed here as you would in the `\note{}` apa6 latex command.
- `keywords`
    - List of keywords that will show under the abstract. See YAML metadata example.
- `abstract`
    - The abstract text of the manuscript.
- `floatsintext` (optional)
    - If this field is present and set to `true`, it will keep figures and tables with text or at the end of the document.
- `classoption` (optional)
    - A list of options that the `apa6` package will understand. See link to manual above. Don't use the LaTeX options `jou`, `man`, or `doc` here. Use the dedicated YAML field `mode` instead. If the field isn't used, it defaults to manuscript mode. Also the `longtable` option is already specified since it's necessary for pandoc to work with tables. Don't enter it twice. Some useful options may be `noextraspace`, `draftfirst`, etc...
- `joucommands` (optional)
    - If you are in journal mode and want to use the other journal commands, the commands are as follows (also see the link to the apa6 manual for more details).
    - `leftheader`
    - `journal`
    - `volume`
    - `ccoppy`
    - `copnum`
- `colorlinks` (optional)
    - Colorize links and citations.

You can try additional fields not mentioned here:

<https://pandoc.org/MANUAL.html#variables-set-by-pandoc>

# Possible Paths Forward/Desired Features

- modify template to allow for document classes not from apa7 package, like letter or book, while maintaining some aspects of APA format

# Acknowledgements

Thanks to the original developer of the template, iamamutt on github. The original was designed for APA6. An update for APA7 that is not specific to Sublime or VSStudio was called for.

Thanks to David Weiss for developing the APA7 LaTeX packages and keeping them up to date.

# License

GPU Public License 3.0

# Metadata

This README was last updated Oct. 8, 2022.
