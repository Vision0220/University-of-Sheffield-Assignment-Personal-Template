# University-of-Sheffield-Assignment-Personal-Template

## Introduction

This template is modified from the program: https://github.com/ahills60/Thesis-Template

I have simplified the files and added the word counting function to make it easier to use in smaller assignments than the dissertation. 

The word counting function will count the words in the `mainbody.tex`, in which all modifications, the assignment works, should be put, to make sure the range of counting is correct. If you don't know how to enable this(which will be mentioned later), you can also just simply comment this sentence and avoid weird problems. 

This has been tested on macOS 12.0.1 with VS Code(works well on my mac). macOS and Linux are supposed to be functioning well, while you may need to change the path on Windows platform due to the difference between `/` and `\`.

## How to enable the word counting function

Firstly, you may need to change `settings.json` in VS Code

```json
    "latex-workshop.latex.tools": [
        {
            "name": "xelatex",
            "command": "xelatex",
            "args": [
                "-synctex=1",
                "-interaction=nonstopmode",
                "-file-line-error",
                "-pdf",
                "--enable-write18",
                "%DOCFILE%"
            ]
        },
        {
            "name": "pdflatex",
            "command": "pdflatex",
            "args": [
                "-synctex=1",
                "-interaction=nonstopmode",
                "-file-line-error",
                "%DOCFILE%"
            ]
        },
        {
            "name": "bibtex",
            "command": "bibtex",
            "args": [
                "%DOCFILE%"
            ]
        }
    ],
    "latex-workshop.latex.recipes": [
        {
            "name": "xelatex",
            "tools": [
                "xelatex"
            ],
        },
        {
            "name": "pdflatex",
            "tools": [
                "pdflatex"
            ]
        },
        {
            "name": "xe->bib->xe->xe",
            "tools": [
                "xelatex",
                "bibtex",
                "xelatex",
                "xelatex"
            ]
        },
        {
            "name": "pdf->bib->pdf->pdf",
            "tools": [
                "pdflatex",
                "bibtex",
                "pdflatex",
                "pdflatex"
            ]
        }
    ],
```

The key point is to add `--enable-write18`to the `xelatax` to enable the manipulation of the temporary file in `/tmp/wordcount.tex`, which will be immediately used when composing. 

To understand this, you may refer to this website: https://tex.stackexchange.com/questions/20444/what-are-immediate-write18-and-how-does-one-use-them

And my solution is inspired by this page: https://tex.stackexchange.com/questions/534/is-there-any-way-to-do-a-correct-word-count-of-a-latex-document. Thanks, Fran. 

## Other concerns

In my department, we are required to use APA 7, which means I choose to use `apalike` in `\bibliographystyle`.You may change it to adapt it to your requirement.

## Conclusion

This template should function well, enjoy it:)

