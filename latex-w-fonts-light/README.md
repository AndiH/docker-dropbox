# LaTeX with Fonts [LIGHT]

This is the lighter companion to `latex-w-fonts`, using 2 GB less space.

Size reduction is achieved by not installing the full *TeX Live* distribution (`texlive-full`) but only the base version (`texlive-base`) with individual additions. (See notes on *lightness*!)

As in `latex-w-fonts`, free fonts from to places are installed:

* Fonts from the [Google Fonts repository](https://github.com/google/fonts)
* Fonts from [Adobe's Github repositories](https://github.com/adobe-fonts), hosting all *Source* fonts (Source Code Pro, Source Serif Pro, Source Sans Pro). Those are actually part of Google's font repository, but apparently a few are missing.

## Compiling LaTeX with Container

Your usual local LaTeX call needs to be prefixed to target the docker image. To handle user permissions correctly, I use

```bash
docker run --rm -i --user="$(id -u):$(id -g)" --net=none -v $PWD:/data andih/latex-w-fonts-light:latest latexmk -xelatex -shell-escape FILE.TEX
```

(The command is from [blang/latex-docker](https://github.com/blang/latex-docker), who wrapped into a [handy shell script, `dockercmd.sh`](https://github.com/blang/latex-docker/blob/master/dockercmd.sh).)

## Notes on Lightness

The reduction in size wrt to `latex-w-fonts` comes with a price: Some packages might not be installed. For example are basically all language packges missing.

If you find something missing, the reasonable solution is to use `latx-w-fonts-light` as a base (`FROM`) and expand it for your own needs. Let me know if you do this; I'm very much curious what you find is missing.
