# Project Apollo

An educational audio identification project: identify a track from a short recording and locate the recording within the indexed track.

The first baseline will implement spectral peak pairing, an inverted fingerprint index, and offset voting. No complete fingerprinting library is used.

## Environment

Requires Python 3.12 and uv.

```sh
uv sync
uv run jupyter lab
```

`uv sync` creates `.venv` and installs the project and development dependencies from `uv.lock`. Select the Python kernel from this environment in your notebook editor.

If using a terminal without uv:

```sh
source .venv/bin/activate
```

## Repository layout

```text
configs/          Experiment configurations (added when needed)
data/raw/deam/    Original local DEAM files, excluded from Git
data/processed/   Derived files and indexes, excluded from Git
data/queries/     Query clips and ground truth, excluded from Git
notebooks/        Step-by-step exploration and experiments
src/apollo/       Reusable code developed incrementally
tests/            Algorithm and contract tests added with implementations
```

## First milestone

1. Inspect dataset files, durations, sample rates, and channels.
2. Listen to one recording and plot its waveform.
3. Understand STFT and build the first spectrogram.
4. Choose preprocessing parameters from these observations.
5. Implement peaks, fingerprints, indexing, and matching on 20–50 recordings.
6. Recover the identity and starting timestamp of a known crop.

The repository currently contains environment configuration and scaffolding. Algorithm implementations will be added during learning.

## Development checks

```sh
uv run ruff check .
uv run ruff format --check .
uv run pytest
```

Tests will be added alongside algorithms; an empty test directory currently means pytest reports no tests collected.

## Data

Download audio and metadata from [the official DEAM page](https://cvml.unige.ch/databases/DEAM/) and extract under `data/raw/deam/`. See `data/README.md` for the expected paths.

Localization timestamps refer to the beginning of the indexed audio file. Emotion annotations and precomputed openSMILE features are not required for this baseline.
