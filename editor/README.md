# Blyx Swallow

Validate an exported payload's declared spans and checksum, then locate a byte.

This extension includes the Blyx Swallow 0.1.0 source, a runnable example and completions for its public functions. It uses the Blyx Language extension for syntax highlighting and execution.

## Run in the editor

1. Open an empty file named `swallow-demo.blyx`.
2. Type `blyx-swallow-demo` and select **Swallow — runnable example**. You can also use **Snippets: Fill File with Snippet**.
3. Choose **Blyx: Run File** from the command palette. Change an argument near the end of `fn main()` to try another input.

Expected output

```text
1
12976260
1
0
```

## Use Swallow in a project

Extract the starter into a new folder. It contains `main.blyx`, the licensed framework source in `vendor/swallow`, and a VS Code task. With the Blyx 0.2.1 compiler and host toolchain installed, run `blyxc native-run main.blyx` from that folder. Type `blyx-swallow-` in a Blyx file to see the framework completions. [Download the starter ZIP](https://github.com/Rahulchaube1/blyxxxx/releases/download/framework-editors-v0.1.0/blyx-swallow-starter-0.1.0.zip)

[API and input requirements](https://www.blyx-lang.space/packages/swallow) · [Framework source](https://github.com/Rahulchaube1/blyx-swallow/tree/74d9702c0e820be16279fece9b3738fd7b6b4988) · [Report an issue](https://github.com/Rahulchaube1/blyx-swallow/issues)

[GitHub Sponsors](https://github.com/sponsors/Rahulchaube1) · [Buy Me a Coffee](https://buymeacoffee.com/rahulchaube)
