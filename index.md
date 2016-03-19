---
layout: default
title: "Count-Min Sketch Library"
lang: en
---

# Count-Min Sketch Library

## Introduction

Madoka is an implementation of a Count-Min sketch, a data structure for summarizing data streams. Madoka uses a conservative update mechanism to improve the accurary of sketches. In addition, Madoka uses an authorized update mechanism and an approximate counting algorithm for ultimate sketching. For more information, see the following web sites.

* Count-Min sketch
 * [Count-Min sketch - Wikipedia, the free encyclopedia](http://en.wikipedia.org/wiki/Count-Min_sketch)
 * [Count-Min Sketch](https://sites.google.com/site/countminsketch/)
* Approximate counting algorithm
 * [Approximate counting algorithm - Wikipedia, the free encyclopedia](http://en.wikipedia.org/wiki/Approximate_counting_algorithm)

Madoka was developed as a part of the Groonga project ([Groonga - An open-source fulltext search engine and column store](http://groonga.org/), special thanks to Brazil Inc.

## Installation

<div class="float">
<pre>
$ wget https://github.com/downloads/s-yata/madoka/madoka-0.0.2.tar.gz
$ tar zxf madoka-0.0.2.tar.gz
$ cd madoka-0.0.2/
$ ./configure
$ make
$ make check
$ sudo make install
$ sudo ldconfig
</pre>
</div>

Download [a package of Madoka](https://github.com/downloads/s-yata/madoka/madoka-0.0.2.tar.gz) and unpack it. Then, run <kbd>configure</kbd> and <kbd>make</kbd>. You may have to run <kbd>ldconfig</kbd> to use Madoka.

If you get source files from [GitHub](http://github.com/s-yata/madoka), <kbd>autoreconf -i</kbd> is needed to generate a <kbd>configure</kbd> script.

Madoka is tested on Ubuntu 11.10. If you have any problems in this process, please report an issue on [GitHub](http://github.com/s-yata/madoka/issues).

## Example

<div class="float">
<pre>
#include <iostream>
#include <madoka.h>

int main() {
  madoka::Sketch sketch;
  sketch.create();

  sketch.inc("Madoka", 6);
  sketch.inc("Homura", 6);
  sketch.inc("Homura", 6);

  std::cout << "Madoka: " << sketch.get("Madoka", 6) << std::endl;
  std::cout << "Homura: " << sketch.get("Homura", 6) << std::endl;
  std::cout << "Mami: " << sketch.get("Mami", 4) << std::endl;

  return 0;
}
</pre>
</div>

This is an example of using Madoka through its C++ interface. This example creates a sketch with default parameters and then increments values associated with <var>"Madoka"</var> and <var>"Homura"</var>. The example will print <var>"Madoka: 1"</var>, <var>"Homura: 2"</var> and <var>"Mami: 0"</var>.

## Interface

A Count-Min sketch supports not only counting items, as shown in the above example, but also inner products, which enable a sketch to serve as a feature vector. In addition, Madoka supports merging and shrinking sketches so as to make sketching more useful. See the following for more information about the APIs.

* English
 * "C API Documentation - to be written":doc/c-api.html
 * "C++ API Documentation":doc/cpp-api.html
* Japanese
 * "C API Documentation - to be written":doc/c-api.ja.html
 * "C++ API Documentation":doc/cpp-api.ja.html

## Implementation

* Japanese
 * Presentation slides ([PowerPoint](https://github.com/downloads/s-yata/madoka/TokyoNLP-09-madoka.pptx), [PDF](https://github.com/downloads/s-yata/madoka/TokyoNLP-09-madoka.pdf))

## License

Madoka is licensed under [the Simplified BSD License](http://www.opensource.org/licenses/bsd-license.php).

Copyright (c) 2012, Susumu Yata. All rights reserved.

Redistribution and use in source and binary forms, with or without modification, are permitted provided that the following conditions are met:

* Redistributions of source code must retain the above copyright notice, this list of conditions and the following disclaimer.
* Redistributions in binary form must reproduce the above copyright notice, this list of conditions and the following disclaimer in the documentation and/or other materials provided with the distribution.

THIS SOFTWARE IS PROVIDED BY THE COPYRIGHT HOLDERS AND CONTRIBUTORS "AS IS" AND ANY EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT NOT LIMITED TO, THE IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS FOR A PARTICULAR PURPOSE ARE DISCLAIMED. IN NO EVENT SHALL THE COPYRIGHT HOLDER OR CONTRIBUTORS BE LIABLE FOR ANY DIRECT, INDIRECT, INCIDENTAL, SPECIAL, EXEMPLARY, OR CONSEQUENTIAL DAMAGES (INCLUDING, BUT NOT LIMITED TO, PROCUREMENT OF SUBSTITUTE GOODS OR SERVICES; LOSS OF USE, DATA, OR PROFITS; OR BUSINESS INTERRUPTION) HOWEVER CAUSED AND ON ANY THEORY OF LIABILITY, WHETHER IN CONTRACT, STRICT LIABILITY, OR TORT (INCLUDING NEGLIGENCE OR OTHERWISE) ARISING IN ANY WAY OUT OF THE USE OF THIS SOFTWARE, EVEN IF ADVISED OF THE POSSIBILITY OF SUCH DAMAGE.
