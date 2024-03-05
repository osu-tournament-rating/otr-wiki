# Code Styling

The `otr-api` project enforces specific styling rules. We utilize some convenient tools to do this for us, however!

## CSharpier

We utilize the [CSharpier](https://github.com/belav/csharpier/blob/main/README.md) tool for all of our formatting. The repository already includes some basic configurations. We also utilize the [dotnet runtime's](https://github.com/dotnet/runtime) [.editorconfig](https://github.com/dotnet/runtime/blob/main/.editorconfig) file for minor styling adjustments.

To use CSharpier, follow the informative [CSharpier README](https://github.com/belav/csharpier/blob/main/README.md). This will be enforced by CI, so always run the formatting command before making a pull request.

`cd` to the root of the repository.

```bash
cd otr-api
```

Run the formatter.

```bash
dotnet csharpier .
```