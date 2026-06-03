GPT-5.4 generated:

Your site’s CI build is very simple. From publish.yaml, go.mod, module.yaml, and package.json, the local environment you need to match is:

1. Git
2. Hugo Extended 0.119.0
3. Go, because this site uses Hugo Modules
4. No npm or Node build step for the website itself

The Node 20 warning in the log is only about GitHub Actions internals, not your local Hugo build.

**Windows Setup**

Use PowerShell on Windows 11:

```powershell
winget install Git.Git
winget install GoLang.Go
winget install Hugo.Hugo.Extended
```

Then verify:

```powershell
git --version
go version
hugo version
```

What matters most is that `hugo version` reports `v0.119.0` and `+extended`. If `winget` installs a newer Hugo, uninstall it and install Hugo Extended 0.119.0 manually from the official Hugo releases page:
https://github.com/gohugoio/hugo/releases/tag/v0.119.0

After install, open a new PowerShell window in your repo folder and run:

```powershell
hugo mod get
hugo mod tidy
hugo server --disableFastRender --navigateToChanged
```

That gives you the local dev server for debugging. Open the URL Hugo prints, usually http://localhost:1313/.

**Closest Match To CI**

Your CI build effectively runs this:

```powershell
$env:HUGO_ENVIRONMENT="production"
$env:HUGO_CACHEDIR="$env:TEMP\hugo_cache_runner"
hugo --minify --baseURL "https://oscaryau525.github.io/"
```

That is the best local command to reproduce the GitHub Pages build result. The cache dir is optional, but setting it makes your local setup closer to the workflow.

**Recommended Workflow**

For day-to-day editing:

```powershell
hugo server --disableFastRender --navigateToChanged
```

For a production-equivalent check before pushing:

```powershell
$env:HUGO_ENVIRONMENT="production"
hugo --minify --baseURL "https://oscaryau525.github.io/"
```

If module downloads fail, the usual fixes are:

```powershell
go env
hugo mod clean
hugo mod get
```

If you want exact OS parity with the Ubuntu runner, use WSL2 with Ubuntu 24.04 and install the same Hugo version there. For normal building and debugging, native Windows 11 is sufficient.

If you want, I can next give you one of these:
1. a copy-paste PowerShell setup script for your machine
2. a VS Code launch/tasks setup for one-click local preview
3. a troubleshooting checklist for common Hugo Module issues on Windows