# tsup Problem Matchers for VS Code

Provides [problem matchers](https://code.visualstudio.com/docs/editor/tasks#_processing-task-output-with-problem-matchers) for use with [tsup](https://tsup.egoist.sh/) projects.

## Features

Provides the following problem matchers:
- **\$tsup** &mdash; adds errors and warnings reported by [tsup](https://tsup.egoist.sh/)
- **\$tsup-watch** &mdash; adds errors and warnings reported by [tsup](https://tsup.egoist.sh/) while in watch mode
- **\$tsup-tsc** &mdash; adds TypeScript errors and warnings reported by [tsup](https://tsup.egoist.sh/) when `--dts` is enabled.
- **\$tsup-tsc-watch** &mdash; adds TypeScript errors and warnings reported by [tsup](https://tsup.egoist.sh/) when `--dts` is enabled while in watch mode.

## Usage

The following example shows how to add problem matchers to your project:

```json
{
	"version": "2.0.0",
	"tasks": [
		{
			"type": "npm",
			"label": "npm: watch",
			"detail": "tsup --watch",
			"script": "watch",
			"group": {
				"kind": "build",
				"isDefault": true
			},
			"problemMatcher": [
                "$tsup-watch",
                "$tsup-tsc-watch"
            ],
			"isBackground": true,
			"presentation": {
				"reveal": "never",
				"group": "watchers"
			},
		},
		{
			"type": "npm",
			"label": "npm: build",
			"detail": "tsup",
			"script": "build",
			"group": "build",
			"problemMatcher": [
				"$tsup",
				"$tsup-tsc"
			]
		}
	]
}
```
