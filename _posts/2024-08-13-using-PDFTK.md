---
layout: post
title:  "Merge two PDF files containing even and odd pages of a document"
date:   2024-08-13 08:00:00 +0100
categories: linux it PDF osx 
---

## Installing PDFTK on OSx
```bash
brew install pdftk-java
```

## Collating Pages (normal order)

```bash
pdftk A=odd.pdf B=even.pdf shuffle A B output collated.pdf
```


## Collating Pages (reversing the order of the even pages)

```bash
pdftk A=odd.pdf B=even.pdf shuffle A Bend-1 output collated_pages.pdf
```

## Links 
- [Merge two PDF files containing even and odd pages of a book](https://superuser.com/questions/516612/merge-two-pdf-files-containing-even-and-odd-pages-of-a-book)