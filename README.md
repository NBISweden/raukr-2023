# Raukr 2023 • Course materials

**NBIS Summer School • Advanced R for Bioinformatics**

## Local preview/render

- To preview/render, you must use [Quarto\>=1.2.269](https://quarto.org/docs/download/)
- If using RStudio, use [v2022.07.1 or newer](https://posit.co/download/rstudio-desktop/)
- [VSCode](https://arinbasu.medium.com/why-quarto-with-vscode-is-a-great-data-science-tool-f0a259d28702) is a good alternative to RStudio for quarto documents
- You need to install the R packages necessary for your topic/file

:bangbang: Be wary of using the visual editor! It may mess up the code formatting.

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
- For assets relating to the document (figures, files etc), create an **assets** folder
  - **slides/topic/assets/**
  - **labs/topic/assets/**

:bulb: The document can be live previewed to view changes. Preview is automatically updated on saving the document. The preview files are copied to a temporary location and rendered independently from the defined output path. Sometimes, the preview can look a bit wonky, in which case, cancel and rerun.

- To preview, run in terminal
  - `quarto preview slides/topic/index.qmd`
  - `quarto preview labs/topic/index.qmd`
  - Saving the file updates the preview

:bulb: The document is rendered to the specified output format in the output directory.

- To render, run in terminal
  - `quarto render slides/topic/index.qmd`
  - `quarto render labs/topic/index.qmd`
  - Rendered files are written to **/docs**
  - To view in browser, open
    - **docs/slides/topic/index.html**
    - **docs/labs/topic/index.html**
    
:bangbang: Do not run `quarto render` as it will remove everything from **docs/** and attempt to render all the files. This might overwrite someone else's materials and also break since you won't have their R packages installed. So, only render your files.

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
  - Scale down to about 600px-800px and [compress images](https://compressjpeg.com/)
  - No reason for a image to be more than a few hundred KB
- Use simple topic labels and do not make them needlessly complex
- The qmd files must be in the correct location when rendering/previewing else metadata from config is not used
- Declare R packages at the beginning of every qmd document
- Qmd files must have a format defined, either **format: html** or **format: revealjs**
- Make a note of the default **execute** settings in `_quarto.yml`. You can override this for your document specifically if needed:

  ```
  execute:
    eval: true
    echo: false
  ```
  
- Use level 2 heading as the highest level
- Bullet points are defined by `-`
- Define options in code chunks using `#|` like `#| echo: true`
- Adjusting dimension of images `![Caption](path/to/image.jpg){width="50%"}`
- Divs are defined using `:::`
- Classes are defined using `{.class}`
  - Example of a class on a div
  
  ```
  ::: {.callout-note}
  content
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

- Remember to spell-check your document
  - Language used is en-us

### RevealJS

These are slide specific info. Comparisons here are to xaringan used previously for RaukR.

- Slides are defined by `##` rather than `---`
- Manual increment is defined by `. . .` rather than `--`
- Horizontal rule is defined by `---` rather than `***`
- Presenter notes are defined by `:::{.notes} content :::` rather than `???`
- For small notes in the bottom of the slide, you can use

```
::: {.aside}
Contents
:::
```
