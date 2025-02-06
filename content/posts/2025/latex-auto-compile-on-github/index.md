---
title: LaTeX auto-compile on GitHub
date: 2025-02-06
tags: [LaTeX]
abstract: |
  A very useful feature for heavy LaTeX users.
---

This post explains how to set up a GitHub repository
so that it automatically compiles LaTeX documents to PDF,
so that it can be viewed directly on GitHub,
across different devices.

Although other tools, such as [Overleaf](https://www.overleaf.com/),
have similar features, and even provide real-time compilation,
I still prefer GitHub for my everyday work,
because I can use my favourite text editor
[Neovim](https://neovim.io/),
which increases my productivity,
and because Git provides more powerful version control features.

Since setting up this workflow,
it has also helped me in several, partly unexpected, ways:

- In a collaborative project, when my collaborators make a change,
  I can see the updated PDF directly on my phone,
  without having to compile it myself.

- When I post my papers on the
  [arXiv](https://arxiv.org/),
  which is notorious for its unwillingness to move away from
  the technology of the 1990s
  (it [hates](https://info.arxiv.org/help/prep.html#title-required) Unicode!),
  it requires authors to use a specific old version of TeX Live
  to produce the `.bbl` bibliography file, then upload it.
  With this set-up,
  I can have GitHub do this for me without having to install this old version.

Of course, you still need to have a working LaTeX installation
on your local machine to compile the document while you are writing it.

{{<toc>}}

## Setting permissions

Before setting up the workflow,
you need to set up the repository
to allow GitHub Actions to create releases.
To do this, follow these steps:

1. Go to your repository on GitHub,
   and go to the **Settings** tab.

2. In the **Settings** tab,
   click **Actions** in the sidebar,
   then click **General**.

3. Go to the **Workflow permissions** section,
   and check **Read and write permissions**.

4. Click the **Save** button in the
   **Workflow permissions** section.
   Note that this is not the **Save** button at the bottom of the page!

Now, we are ready to set up the workflow.

## Adding the workflow file

Create a `.github` directory in the root of your repository
(note the leading dot),
and inside it, create a `workflows` directory.

In the newly created `.github/workflows` directory,
create a file `build.yaml` with the following content:

```yaml
name: Build PDF and release
on: push

jobs:
  build_latex:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - name: Compile LaTeX
        uses: xu-cheng/latex-action@v3
        with:
          root_file: main.tex
      - name: Get timestamp
        run: echo "TIMESTAMP=$(date +'%Y-%m-%d %T')" >> $GITHUB_ENV
      - name: Release
        uses: softprops/action-gh-release@v2
        with:
          name: Draft ${{ env.TIMESTAMP }}
          files: main.pdf
          draft: true
```

If your main LaTeX file is not named `main.tex`,
you should replace the `main.tex` and `main.pdf`
above with your file names.
If your main file is in a subdirectory,
please see the [documentation](https://github.com/xu-cheng/latex-action)
of `latex-action` for compiling it,
and replace `main.pdf` with the path to your PDF file.

This workflow will then be triggered whenever you push to the repository,
and it will do the following:

- It will compile the LaTeX document in the repository.

- It will create a draft release on GitHub named
  `Draft YYYY-MM-DD HH:MM:SS`,
  of course with the actual date and time.
  It will attach the compiled PDF to this release.

- If there is a previous draft release, it will overwrite it.

To view the PDF on GitHub,
click **Releases** on your repository page,
and the PDF will be in the **Assets** section of the latest draft release.

## Customizations

Here are some common customizations you might want to make:

- To keep all versions of the PDFs,
  instead of overwriting the previous draft release,
  remove the `draft: true` line from the **Release** step.

- To change the date format in the release name,
  change the `date +'%Y-%m-%d %T'` in the **Get timestamp** step.
  This uses the Linux
  [`date`](https://www.man7.org/linux/man-pages/man1/date.1.html)
  command to get the current date and time.
  See [this tutorial](https://linuxize.com/post/linux-date-command/),
  for example, for more options.

- To use a specific TeX Live version,
  add a `texlive_version` field to the **Compile LaTeX** step:

  ```yaml
  - name: Compile LaTeX
    uses: xu-cheng/latex-action@v3
    with:
      root_file: main.tex
      texlive_version: 2023
  ```

  As of this writing, arXiv uses TeX Live 2023,
  which is what we have set it to here.

- To also include the `.bbl` file required by the arXiv in the release,
  add it to the **Release** step:

  ```yaml
  - name: Release
    uses: softprops/action-gh-release@v2
    with:
      name: Draft ${{ env.TIMESTAMP }}
      files: |
        main.pdf
        main.bbl
      draft: true
  ```

For more customization options, see the documentation of the
[`latex-action`](https://github.com/xu-cheng/latex-action)
and
[`action-gh-release`](https://github.com/softprops/action-gh-release)
actions.
