# Portability — load a brick without VectorForge

The library claim is **portable packages**, not “only works inside Pro.”

## What’s in a `*_portable.zip`

| Path | Role |
|------|------|
| `*.md` | Human-readable primary text |
| `chunks.jsonl` | One JSON object per chunk (`chunk_id`, `text`, `section_heading`, …) |
| `kb.json` | Manifest + chunk list order (aligns with embeddings rows) |
| `embeddings.npy` | Float matrix, one row per chunk (nomic-embed-text family, 768-d) |
| `embedding_provenance.json` | Model / dims / air-gap notes |
| `HANDOFF_README.md` | Operator notes from export |

## Minimal Python retrieval (generic stack)

```python
import json
from pathlib import Path
import numpy as np

brick = Path("ArduPilot_Plane")  # unzipped folder
chunks = [json.loads(l) for l in (brick / "chunks.jsonl").read_text().splitlines() if l.strip()]
# Prefer kb.json order if present
kb = json.loads((brick / "kb.json").read_text())
order = kb.get("chunks") or []
if order:
    by_id = {c["chunk_id"]: c for c in chunks}
    chunks = [by_id[c["chunk_id"]] for c in order if c.get("chunk_id") in by_id]

E = np.load(brick / "embeddings.npy").astype(np.float32)
E = E / (np.linalg.norm(E, axis=1, keepdims=True) + 1e-9)

# Embed query with the SAME model family (nomic-embed-text / compatible 768-d).
# Example: sentence-transformers or your local EmbeddingSystem.
# q = embed_query("What is FBWA mode?")  # shape (768,)
# q = q / (np.linalg.norm(q) + 1e-9)
# scores = E @ q
# top = scores.argsort()[::-1][:5]
# for i in top:
#     print(scores[i], chunks[i]["chunk_id"], chunks[i].get("section_heading"), chunks[i]["text"][:200])
```

No VectorForge install required for the matrix math — only for producing bricks or matching the exact embed path used at build.

## Plain Markdown

Open the primary `.md` or search `chunks.jsonl` with `rg` / any full-text index. You lose semantic ranking but keep full portability.

## Worked public evidence

See [RETRIEVAL_DEMO_ArduPilot_Plane.md](RETRIEVAL_DEMO_ArduPilot_Plane.md) for twenty real questions and citations against the published Plane brick.
