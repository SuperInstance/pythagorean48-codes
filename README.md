# pythagorean48-codes

**Shared codebook for SuperInstance fleet — 48 exact direction vectors.**

Used by:
- `fleet-coordinate` — trust topology encoding
- `aboracle` — research note encoding
- `holonomy-consensus` — consensus verification

## Why?

Pythagorean48 is the only exact encoding for 2D unit vectors using 16-bit integers:
- 48 directions = log₂(48) ≈ **5.585 bits per vector**
- Zero drift after unlimited hops (exact integer math, no f32 accumulation)
- Every direction is on the unit circle exactly: x² + y² = 1

## Usage

```rust
use pythagorean48_codes::TrustVector;

let v = TrustVector::from_f32(0.6, 0.8);
let (x, y) = v.to_f32(); // exact round-trip

let dirs = TrustVector::all_directions(); // 48 exact vectors
```

## Python

```python
from pythagorean48 import TrustVector

v = TrustVector.from_f32(0.6, 0.8)  # encode
x, y = v.to_f32()  # decode
```

## Install

```bash
cargo add pythagorean48-codes  # Rust
pip install pythagorean48-codes  # Python (coming soon)
```

## Math

All 48 vectors come from Pythagorean triples:
- 3-4-5 (8 directions)
- 5-12-13 (8 directions)
- 7-24-25 (8 directions)
- 8-15-17 (8 directions)
- 9-40-41 (8 directions)
- Cardinal axes (4 directions)
- Swapped variants (4 directions)

Each vector is (xn/xd, yn/yd) where xn² + yn² = xd² exactly.
