# LaTeX with Fonts

Provides a full LaTeX installation, augmented by some free/Open Source fonts. The image is quite large (TeX is…); you might be interested in the slightly smaller `latex-w-fonts-light` version.

Currently, free fonts from two places are installed:

* Fonts from the [Google Fonts repository](https://github.com/google/fonts)
* Fonts from [Adobe's Github repositories](https://github.com/adobe-fonts), hosting all *Source* fonts (Source Code Pro, Source Serif Pro, Source Sans Pro). Those are actually part of Google's font repository, but apparently a few are missing.

## Compiling LaTeX with Container

Your usual local LaTeX call needs to be prefixed to target the docker image. To handle user permissions correctly, I use

```bash
docker run --rm -i --user="$(id -u):$(id -g)" --net=none -v $PWD:/data andih/latex-w-fonts:latest latexmk -xelatex -shell-escape FILE.TEX
```

(The command is from [blang/latex-docker](https://github.com/blang/latex-docker), who wrapped it into a [handy shell script, `dockercmd.sh`](https://github.com/blang/latex-docker/blob/master/dockercmd.sh).)
