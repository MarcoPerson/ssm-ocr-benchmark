# SSM-OCR Benchmark

**A Benchmark of State-Space Models vs. Transformers and BiLSTM-based Models for Historical Newspaper OCR**

[![arXiv](https://img.shields.io/badge/arXiv-2604.00725-b31b1b.svg)](https://arxiv.org/abs/2604.00725)
[![Conference](https://img.shields.io/badge/ICDAR-2026-2E5C8A.svg)](https://arxiv.org/abs/2604.00725)

> Accepted at **ICDAR 2026** (International Conference on Document Analysis and Recognition).
>
> Preprint: https://arxiv.org/abs/2604.00725

This repository will host the code, trained model weights, dataset splits, and evaluation protocols for our benchmark of State-Space Models (Mamba) against Transformer- and BiLSTM-based recognizers for historical newspaper OCR.

---

## Status

**The code and trained model weights are not yet available. They will be released here upon publication.**

We are preparing everything for a clean, reproducible release. Watch or star this repository to be notified when the resources go live. Planned contents:

- [ ] Mamba-based OCR architectures (CTC, autoregressive, non-autoregressive variants)
- [ ] Baseline configurations (VAN, DAN, DANIEL)
- [ ] Trained model checkpoints
- [ ] Standardized train / validation / test splits
- [ ] Gold-standard (>99% verified) test annotations
- [ ] Evaluation scripts (CER / WER, latency, throughput, memory)

---

## Overview

End-to-end OCR for historical newspapers is difficult: degraded print, mixed typography (Antiqua and Fraktur), complex multi-column layouts, and multilingual text. Transformer-based recognizers dominate current research, but their O(n²) attention makes paragraph-level transcription and large-scale deployment costly in latency and memory.

We investigate linear-time **State-Space Models (SSMs)**, specifically Mamba, as a scalable alternative for OCR sequence modeling. We present, to our knowledge, the first OCR architecture built on SSMs, combining a CNN visual encoder with bidirectional and autoregressive Mamba sequence modeling, and run a large-scale benchmark comparing SSMs with Transformer- and BiLSTM-based recognizers under identical training conditions.

## Key contributions

- **First SSM-based OCR.** A CNN encoder with bidirectional and autoregressive Mamba, in three decoding variants (CTC, AR, NAR).
- **Controlled benchmark.** 6 neural models across 3 decoding paradigms and 3 model families, plus 4 production OCR engines (PERO-OCR, Tesseract, TrOCR, Gemini), all under identical training.
- **Dual granularity.** Evaluated at both line and paragraph level.
- **Reproducible release.** Code, checkpoints, splits, and gold-standard (>99%) test annotations.

## Key results

On historical newspapers from the Bibliothèque nationale du Luxembourg (BnL), all neural models reach competitive accuracy (around 2% CER at line level), making computational efficiency the main differentiator.

- Mamba-AR matches DAN at line level (1.83% CER) while running 2.9x faster.
- At the paragraph level, Mamba-AR stays within 0.83% CER of DAN (6.07% vs 5.24%) while running 2.05x faster.
- Memory scaling is near-linear for Mamba (1.26x) versus quadratic for DAN (2.30x) at 1,000-character sequences.

## Dataset

The benchmark uses public-domain pre-1878 newspapers from the Bibliothèque nationale du Luxembourg, in German, French, and Luxembourgish, at both line and paragraph granularity. Links to the data and our standardized splits will be added here on release.

Source collection: https://data.bnl.lu/data/historical-newspapers/

## Citation

If you find this work useful, please cite:

```bibtex
@inproceedings{ssmocr2026,
  title     = {A Benchmark of State-Space Models vs. Transformers and BiLSTM-based Models for Historical Newspaper OCR},
  author    = {Agbeti-Messan, Merveilles and Chatelain, Clement and Tranouez, Pierre and Nicolas, Stephane and Paquet, Thierry},
  booktitle = {International Conference on Document Analysis and Recognition (ICDAR)},
  year      = {2026},
  eprint    = {2604.00725},
  archivePrefix = {arXiv},
  primaryClass  = {cs.CV}
}
```

## Contact

For questions about the work, please open an issue or contact the authors at LITIS UR4108, University of Rouen Normandy.

## License

The license will be specified at release.
