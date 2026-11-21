<img src="assets/logo.png" width="112" height="112" alt="Blyx penguin checking indented lines against a stepped square.">

# IndentSteps

Audit fixed-step indentation measured on nonblank source lines. This Blyx library is part of the packaging and code quality collection.

A line can have acceptable length but invalid indentation. Preserve both counts and show the earliest actionable row. [PEP 8, indentation and line length](https://peps.python.org/pep-0008/)

## Install and run

Install [Blyx 0.2.1](https://www.blyx-lang.space/download) with a Rust toolchain and host linker for native builds.

```sh
git clone --depth 1 --branch v0.1.0 https://github.com/Rahulchaube1/blyx-indentsteps.git
cd blyx-indentsteps
blyxc native-run example.blyx
blyxc native-run tests.blyx
```

[Run the editable browser example](https://www.blyx-lang.space/play?example=package-indentsteps) · [Package page](https://www.blyx-lang.space/packages/indentsteps) · [Handbook](https://doc.blyx-lang.space/guide/towhee)

## Import the module

Run this in the directory containing your application's entry file.

```sh
git clone --depth 1 --branch v0.1.0 https://github.com/Rahulchaube1/blyx-indentsteps.git vendor/indentsteps
```

```blyx
use vendor::indentsteps::indentsteps;

fn main() {
    let indent = [0, 4, 12, 8, 0];
    let step = 4.0;
    let result = indentsteps_audit(indent, step);
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
2
12
```

## API

`indentsteps_audit(indent, step)`

Returns [off-grid or illegal jump count, first offending row, deepest column]. The first nonblank row starts at zero and one line can increase by at most one indent step. Invalid arguments and nonfinite results return an empty vector. Integers carried in numeric vectors use the exact range from −(2^53−1) to 2^53−1.

| Argument | Domain |
| --- | --- |
| indent | Vector of values, each a nonnegative exact integer |
| step | A positive exact integer |

## In use

[Towhee](https://github.com/Rahulchaube1/blyx-towhee) uses this module to combine indentation and line-width diagnostics for a measured source file.

## Verification and contributions

The regression suite in [tests.blyx](tests.blyx) checks the example, boundary cases and invalid inputs. Include a short reproducer and your compiler version in [an issue](https://github.com/Rahulchaube1/blyx-indentsteps/issues). The source is dual-licensed under [MIT](LICENSE-MIT) or [Apache-2.0](LICENSE-APACHE). Read the [artwork notice](assets/NOTICE.txt) for credits.

## Connect with Rahul Chaube

[Portfolio](https://www.rahulchaube1.com/) · [GitHub](https://github.com/Rahulchaube1) · [LinkedIn](https://www.linkedin.com/in/rahulchaube1) · [Hugging Face](https://huggingface.co/oncody) · [X](https://x.com/RahulChaube_) · [EverestQ](https://www.everestqai.com/) · [Contact](https://www.rahulchaube1.com/contact)

[Blyx website](https://www.blyx-lang.space/) · [BlyxTorch](https://www.blyx-lang.space/packages/blyxtorch) · [Handbook](https://doc.blyx-lang.space/) · [Community](https://www.blyx-lang.space/community)

Support Rahul’s open-source work through [GitHub Sponsors](https://github.com/sponsors/Rahulchaube1) or [Buy Me a Coffee](https://buymeacoffee.com/rahulchaube).
