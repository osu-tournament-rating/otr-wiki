# Code Styling

The `otr-api` project enforces specific styling rules, enforced easily via `dotnet format`.

## Formatting

To format your code to our standards, simply execute the following from the root folder.

```
dotnet format --severity info
```

The codebase also utilizes [Husky](https://alirezanet.github.io/Husky.Net/guide/#features), a tool to locally run scripts before commits are made. The current setup will automatically run the above command on your staged changes before any commit is made. If for any reason Husky should need to be disabled, set an environment variable `HUSKY=0` or include the flag `--no-verify` on any `git commit` command.