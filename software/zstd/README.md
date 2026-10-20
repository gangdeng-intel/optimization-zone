# Zstandard (zstd) Compression with Intel® QAT

## Overview

Zstandard (zstd) is a widely used lossless compression format known for fast
compression and decompression with strong compression ratios. Its flexibility
makes it suitable for many types of data and applications.

At a high level, zstd compression has two stages. First, a dictionary coder
such as LZ77 finds repeated data and represents it as sequences containing
matches, offsets, and literals. Then, zstd encodes those sequences using
Finite State Entropy (FSE) or Huffman coding.

## Intel® QuickAssist Technology

Intel® QuickAssist Technology (Intel® QAT) is an integrated workload
acceleration feature on Intel® Xeon® Scalable processors. It is designed to
improve performance and efficiency for compute-intensive workloads, including
AI, analytics, application and content delivery, and high-speed networking.

## Intel® QAT ZSTD Plugin

The Intel® QuickAssist Technology ZSTD Plugin (QAT ZSTD Plugin) accelerates
Zstandard compression using Intel® QAT hardware. Starting with zstd v1.5.4,
the block-level sequence producer API allows custom sequence producers to be
registered. The QAT sequence producer offloads generation of block-level
sequences (literals and matches) to QAT, targeting compression levels L1–L12.
Zstd then post-processes the sequences to produce valid compressed blocks,
preserving compatibility and compression results.

## Performance

Intel® QAT delivers up to **3.2× higher throughput** than zstd compression
level 5 and up to **2.5× higher throughput** than zstd compression level 4.

The following compression ratios are reported for the Silesia Corpus:

| Configuration | Compression ratio |
| --- | ---: |
| QAT-ZSTD level 9 | 2.76 |
| zstd level 4 | 2.74 |
| zstd level 5 | 2.77 |

The compression ratio is calculated as the input size divided by the
compressed output size. A higher ratio means the compressed output is smaller
relative to the input.

For more details about the QAT ZSTD Plugin, see the
[Intel® QAT ZSTD Plugin project on GitHub](https://github.com/intel/QAT-ZSTD-Plugin).
