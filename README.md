# Musical Signal Analysis Using Fourier Transform

A signal processing project that analyzes and compares the frequency content of two musical instruments,a  violin and clarinet, playing the same note (A4, 440 Hz). The project uses the Discrete Fourier Transform (DFT) to decompose audio signals into their frequency components and quantify why two instruments sound different despite playing the same pitch.

---

## Overview

When a musical instrument plays a note, it doesn't produce just one frequency. It produces a fundamental frequency (the pitch you hear) plus a series of harmonics — additional frequencies at integer multiples of the fundamental — each at different loudness levels. This distribution of harmonic loudness is called **timbre**, and it's the reason a violin and clarinet sound distinct even on the same note.

This project makes that difference visible and measurable using Fourier analysis.

---

## How It Works

1. **Load audio** — Two recordings of A4 (440 Hz) are loaded, one violin and one clarinet
2. **Run the DFT** — The raw audio waveform is decomposed into its frequency ingredients using the Fast Fourier Transform (FFT)
3. **Normalize** — Magnitudes are normalized relative to the fundamental so volume differences between recordings don't affect the comparison
4. **Extract harmonics** — The strength of the first 8 harmonics (440, 880, 1320... Hz) is measured for each instrument
5. **Compute spectral features** — Spectral centroid and spectral spread are calculated across the full frequency spectrum
6. **Compare** — Results are visualized and tabulated to show the timbral differences between the two instruments

---

## Results

| Feature | Violin | Clarinet |
|---|---|---|
| Spectral Centroid | 1863 Hz | 1672 Hz |
| Spectral Spread | 2371 | 1826 |
| Avg Harmonic Strength | 0.190 | 0.275 |
| High Harmonic Strength (5-8) | 0.044 | 0.049 |

The violin has a higher spectral centroid and spread, indicating its energy is distributed across a wider and higher frequency range — contributing to its brighter, richer sound. The clarinet has a more concentrated frequency distribution and stronger average harmonic strength, consistent with its characteristic warm, focused tone.

---

## Key Concepts

- **Fundamental frequency** — The base vibration rate of the instrument, perceived as pitch
- **Harmonics** — Extra frequencies at integer multiples of the fundamental, produced automatically by the physics of the instrument
- **Timbre** — The tonal character of a sound, determined entirely by the relative loudness of harmonics
- **DFT / FFT** — Mathematical tool that decomposes a sound signal into its frequency components
- **Spectral Centroid** — The weighted average frequency, indicating where most of the energy sits
- **Spectral Spread** — How scattered the energy is around the centroid

---

## Libraries Used

- `librosa` — Audio loading and processing
- `numpy` — FFT computation and numerical operations
- `matplotlib` — Visualization
- `pandas` — Data tables and comparison

---

## Limitations

- Analysis uses a single sustained note per instrument, which doesn't capture the full variability of real musical performance
- The FFT assumes the signal is stationary over time, which isn't always true for real music
- Factors like dynamics, vibrato, articulation, and recording conditions can affect results

---

## Possible Extensions

- Time-frequency analysis using Short-Time Fourier Transform (STFT) to capture how harmonics evolve over time
- Comparing multiple notes across different pitches
- Using machine learning to classify instruments based on spectral features
