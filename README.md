<img src="assets/logo.png" width="112" height="112" alt="A cobalt barn swallow turns in flight with twin tail streamers trailing.">

# Swallow

Validate an exported payload's declared spans and checksum, then locate a byte. This Blyx workflow framework is part of the validation and configuration collection.

A valid byte offset can point into the wrong serialized record if lengths have drifted. Verify the table and payload before interpreting the offset. [IETF RFC 1950, Adler-32](https://www.rfc-editor.org/rfc/rfc1950)

## Editor extension

Install **RahulChaube.blyx-swallow** to run the worked example and use the framework’s function completions in a Blyx file. Open an empty `.blyx` file, enter `blyx-swallow-demo`, then choose **Blyx: Run File**. [Editor downloads](https://www.blyx-lang.space/packages/swallow#editor) · [Download the extension](https://github.com/Rahulchaube1/blyxxxx/releases/download/framework-editors-v0.1.0/blyx-swallow-0.1.0.vsix) · [Starter with framework source](https://github.com/Rahulchaube1/blyxxxx/releases/download/framework-editors-v0.1.0/blyx-swallow-starter-0.1.0.zip)

## Install and run

Install [Blyx 0.2.1](https://www.blyx-lang.space/download) with a Rust toolchain and host linker for native builds.

```sh
git clone --depth 1 --branch v0.1.0 https://github.com/Rahulchaube1/blyx-swallow.git
cd blyx-swallow
blyxc native-run example.blyx
blyxc native-run tests.blyx
```

[Run the editable browser example](https://www.blyx-lang.space/play?example=package-swallow) · [Package page](https://www.blyx-lang.space/packages/swallow) · [Handbook](https://doc.blyx-lang.space/guide/swallow)

## Import the module

Run this in the directory containing your application's entry file.

```sh
git clone --depth 1 --branch v0.1.0 https://github.com/Rahulchaube1/blyx-swallow.git vendor/swallow
```

```blyx
use vendor::swallow::swallow;

fn main() {
    let lengths = [1, 1];
    let payload = [65, 66];
    let offset = 1.0;
    let checksum = 12976260.0;
    let result = swallow_inspect(lengths, payload, offset, checksum);
    if len(result) == 0 { println!("invalid"); return; }
    let mut i = 0;
    while i < len(result) {
        println!(at(result, i));
        i += 1;
    }
}
```

Expected output

```text
1
12976260
1
0
```

## API

`swallow_inspect(lengths, payload, offset, checksum)`

Returns [checksum matches, actual Adler-32, record index, in-record offset]. The sum of payload lengths must equal the byte count. Use a verified cryptographic signature when authenticity is required. Invalid arguments and nonfinite results return an empty vector. Integers carried in numeric vectors use the exact range from −(2^53−1) to 2^53−1.

| Argument | Domain |
| --- | --- |
| lengths | Vector of values, each a nonnegative exact integer |
| payload | Vector of values, each a whole byte in [0,255] |
| offset | A nonnegative exact integer |
| checksum | A nonnegative exact integer |

## Run the command-line project

Run the example with your own numbers. Vector arguments accept up to 16 comma-separated entries; use `[]` for an empty vector. The imported API accepts longer vectors. Invalid arguments return a nonzero exit status.

```sh
blyxc native-run project.blyx -- "1,1" "65,66" 1 12976260
```

## Libraries

- [RecordSpan](https://github.com/Rahulchaube1/blyx-recordspan/tree/v0.1.0) — Locate the nonempty length-prefixed record containing a byte offset.
- [AdlerBytes](https://github.com/Rahulchaube1/blyx-adlerbytes/tree/v0.1.0) — Compute the RFC 1950 Adler-32 checksum over a sequence of bytes.

This release includes identical copies of both library modules so a tagged clone can build offline.

## Verification and contributions

The regression suite in [tests.blyx](tests.blyx) checks the example, boundary cases and invalid inputs. Include a short reproducer and your compiler version in [an issue](https://github.com/Rahulchaube1/blyx-swallow/issues). The source is dual-licensed under [MIT](LICENSE-MIT) or [Apache-2.0](LICENSE-APACHE). The [artwork notice](assets/NOTICE.txt) records credits for earlier editions.

## Connect with Rahul Chaube

[Portfolio](https://www.rahulchaube1.com/) · [GitHub](https://github.com/Rahulchaube1) · [LinkedIn](https://www.linkedin.com/in/rahulchaube1) · [Hugging Face](https://huggingface.co/oncody) · [X](https://x.com/RahulChaube_) · [EverestQ](https://www.everestqai.com/) · [Contact](https://www.rahulchaube1.com/contact)

[Blyx website](https://www.blyx-lang.space/) · [BlyxTorch](https://www.blyx-lang.space/packages/blyxtorch) · [Handbook](https://doc.blyx-lang.space/) · [Community](https://www.blyx-lang.space/community)

Support Rahul’s open-source work through [GitHub Sponsors](https://github.com/sponsors/Rahulchaube1) or [Buy Me a Coffee](https://buymeacoffee.com/rahulchaube).
