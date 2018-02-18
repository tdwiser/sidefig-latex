LaTeX package `sidefig`
=======================

Wrapping text around a figure (or, more generally, any box-shaped region) is a tricky subject in LaTeX.
Plain TeX has a powerful command, `\parshape`, which directs TeX to flow a paragraph within a defined region, with the geometry defined line-by-line.

Various packages (e.g. `wrapfig`) exist to facilitate this process for LaTeX users.
However, `\parshape` (and another powerful command, `\everypar`, which allows wrapping across multiple paragraphs) are overwritten by LaTeX `list` environments, including `itemize` and `enumerate`.
This causes typical approaches to fail when used near `list`s.

`sidefig` is a package which attempts to allow wrapping text around rectangular regions even in the presence of `list`s.

Here are some features of `sidefig`, which you can see demonstrated in `sidefig.tex`/`sidefig.pdf`:

* Text wrapping continues to work even if you start a list.
For example, lines will break a little bit earlier to make room for figures at right.

* Sublists are also supported:

	- If you add a `\sidefig` in a list, the package tries hard to make things look right even across multiple levels.
	
* Captions are also possible using an optional parameter to \verb|\sidefig|.

* Usage: `\sidefig[`*(optional caption)*`]{L` *or* `R}{`*(content)*`}` right before any paragraph or `\item`.

Additional Features
-------------------

The style of the caption can be controlled by redefining `\sidecapstyle`.
The default is 

	\def\sidecapstyle{\centering\small\it}

The caption can also be passed as an option to `\sidecapstyle` if you like.

The spacing between the content and the caption can be controlled with `\setlength{\sidecapskip}{`*(length)*`}`, default `2pt`.

If you don't want to be next to the `\sidefig` any more, use `\MoveBelowBox`.
This command is called automatically if you add a `\sidefig` that would otherwise overlap a previous one.

Acknowledgements
----------------

This code is heavily based off of the Plain TeX package `insbox` by Micha\l{} Gulczy\'nski, available at https://ctan.org/pkg/insbox.

Not all features of `insbox` are available due to poor interactions with `list`s.
Many things have been wrapped-around or otherwise rearranged to accommodate `list`s, but the core functionality is due to `insbox`.
