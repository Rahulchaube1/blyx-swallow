## Verify a record table before interpreting a byte offset

Returns [checksum matches, actual Adler-32, record index, in-record offset]. The sum of payload lengths must equal the byte count. Use a verified cryptographic signature when authenticity is required. Invalid arguments and nonfinite results return an empty vector.

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

[Work through the example in the browser](https://www.blyx-lang.space/play?example=package-swallow)
