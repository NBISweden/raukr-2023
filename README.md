# Raukr 2023 • Course materials

**NBIS Summer School • Advanced R for Bioinformatics**

## Local render

- To preview/render, you must use [Quarto\>=1.2.269](https://quarto.org/docs/download/)
- If using RStudio, use [v2022.07.1 or newer](https://posit.co/download/rstudio-desktop/)
  - You need to install the R packages necessary for your topic/file

:bangbang: Do not use visual editor! It messes up the code formatting.

## Adding/Modifying topics

- Fork the repository and clone locally
- Keep the topic name simple, preferably one word
- To add a **topic**, create
  - **slides/topic/index.qmd**
  - **labs/topic/index.qmd**
  - The YAML metadata should minimally look like this:

    ```         
    ---
    title: "Topic"
    author: "Author"
    description: "This topic covers this and that."
    format: html
    ---
    ```

- `format` must be `html` for reports and `revealjs` for presentations
- For assets relating to the document (figures, files etc), create
  - **slides/topic/assets/**
  - **labs/topic/assets/**
- To preview, run in terminal
  - `quarto preview slides/topic/index.qmd`
  - `quarto preview labs/topic/index.qmd`
  - Saving the file updates the preview
- To render, run in terminal
  - `quarto render slides/topic/index.qmd`
  - `quarto render labs/topic/index.qmd`
  - Rendered files are written to **/docs**
  - To view in browser, open
    - **docs/slides/topic/index.html**
    - **docs/labs/topic/index.html**
- Finally commit changes (both source files and rendered files)

```
git stage .
git commit -m "Added topic"
```

- Push changes to your fork and send a pull request

## Tips & Conventions

- For compute heavy steps, save intermediate and read them in
- Be mindful of the size of files
  - Store large data files elsewhere (dropbox, google drive etc) and link them
  - Scale down and [compress images](https://compressjpeg.com/)
- Use simple topic labels and do not make them needlessly complex
- The qmd files must be in the correct location when rendering/previewing else metadata from config is not used
- Declare R packages at the beginning of every qmd document
- Qmd files must have a format defined, either **format: html** or **format: revealjs**
- Make a note of the default **execute** settings in `_quarto.yml`
- Use level 2 heading as the highest level
- All bullet points are defined by `-`
- Define options in code chunks using `#|`
- Adjusting dimension of images `![Caption](path/to/image.jpg){width="50%"}`
- Divs are defined using `:::`
- Classes are defined using `{.class}`
- Example of a class on a div
- Remember to spell-check your document
  - Language used is en-us

```         
::: {.class}
Content
:::
```

- Example of a class on a span `[Content]{.class}`
- Columns are defined as such

```
:::: {.columns}
::: {.column width="50%"}
Contents
:::
::: {.column width="50%"}
Contents
:::
::::
```

### RevealJS

- Slides are defined by `##` rather than `---`
- Manual increment is defined by `. . .` rather than `--`
- Horizontal rule is defined by `---` rather than `***`
- For presenter notes are defined by `:::{.notes}` rather than `???`
- For small notes in the bottom of the slide, you can use

```
::: {.aside}
Contents
:::
```
