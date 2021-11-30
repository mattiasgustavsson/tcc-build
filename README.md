# tcc-build
Binaries for building with Tiny C Compiler from github workflow

Use this in your `.github/workflows/main.yml` file to build with tcc
```
name: build
on: [push, pull_request]

jobs:
  build-windows-tcc:
    runs-on: windows-2019
    steps:
      - uses: actions/checkout@v1
      - uses: robinraju/release-downloader@v1.2
        with:
          repository: "mattiasgustavsson/tcc-build"
          tag: "tcc64"
          fileName: "tcc-0.9.27-win64-bin.zip"
      - name: extract tcc
        run: 7z x tcc-0.9.27-win64-bin.zip
      - name: build
        run: |
          tcc/tcc source/main.c
```
