# Using Quarto Actions: Examples

* [Basics](./example-01-basics.md)
* [Freeze](./example-02-freeze.md)
* [Dependencies](./example-03-dependencies.md)
* [Render with no publish](./example-04-render-no-publish.md)
* [Rendering and publishing a non-top-level project](./example-05-non-top-level.md)
* [Publishing a single format, publishing without rendering](./example-06-no-render.md)
* [Publishing a single format](./example-07-publish-single-format.md)
* [Publishing to other services](./example-08-publish-to-others-services.md)

## FAQ

* My project uses git lfs storage; how should I adapt the action?

  If your project uses git lfs storage, you must opt-in to git lfs during the `checkout` step.

  ```yaml
        - name: Check out repository
          uses: actions/checkout@v4
          with:
            lfs: true # needed when using lfs for image storage
  ```

  See the [checkout action documentation](https://github.com/actions/checkout) for details.
