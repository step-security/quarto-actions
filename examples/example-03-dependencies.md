# Quarto Actions: Dependencies

If you want to execute computational content in GitHub Actions workflows, you are going to have to install the necessary software dependencies in your action.

## Installing R

Add the following entry to your GitHub Actions workflow:

```yaml
- uses: step-security/r-lib-actions/setup-r@v2
  with:
    r-version: '4.2.0' # The R version to download (if necessary) and use.
```

If you're using `quarto-publish-example.yml`, add those right after the `# add software dependencies here` comment.

### Using **renv** to manage R packages

If you are managing your R package dependencies with `renv`, the following action will install the dependencies:

```yaml
- uses: step-security/r-lib-actions/setup-renv@v2
  with:
    cache-version: 1
```

See [the `setup-renv` documentation](https://github.com/step-security/r-lib-actions/tree/v2/setup-renv) for how to use `cache-version`.
See [the `renv` documentation](https://rstudio.github.io/renv) for how to use **renv** with a project.

### Installing R packages manually

You can also use `step-security/r-lib-actions/setup-r-dependencies@v2` to install required R packages for your content. See more about 
this actions at [the `setup-r-dependencies` documentation](https://github.com/step-security/r-lib-actions/tree/v2/setup-r-dependencies). 
It can handle dependencies with a `DESCRIPTION` in your project, or you can also list manually what is needed. e.g

```yaml
- uses: step-security/r-lib-actions/setup-r-dependencies@v2
  with:
    packages:
      any::knitr
      any::rmarkdown
      any::downlit
      any::xml2
```

## Installing Jupyter

Add the following entry to your GitHub Actions workflow:

```yaml
- uses: actions/setup-python@v4
  with:
    python-version: '3.x' # Version range or exact version of a Python version to use, using SemVer's version range syntax
- run: pip install jupyter
```

### Using `requirements.txt`

```yaml
- uses: actions/setup-python@v4
  with:
    python-version: '3.x' # Version range or exact version of a Python version to use, using SemVer's version range syntax
    cache: 'pip'
- run: pip install jupyter # (if jupyter is not part of your requirements.txt)
- run: pip install -r requirements.txt
```

## Installing Julia

```yaml
- uses: julia-actions/setup-julia@v1
- run: julia --project -e 'using Pkg; Pkg.instantiate()'
```
