# **Q-EDU-Forge** - A Mini Open-Source Project for Quantum Education & Simulation (Granite-Assisted, Blender-Enabled)

> **Portmanteau & Etymology.** **Q-EDU-Forge** merges “Q” (quantum), “EDU” (education), and “Forge” (workshop for shaping tools; from Latin *fabrica*), denoting, practically and purposefully, a place to shape, test, and publish quantum learning tools. We will, consistently and transparently, teach terminology with short etymologies; when historical, person-named labels exist, we will prefer descriptive terms first, while, helpfully, cross-referencing the historical name.

---

## 0) Concept in One Minute

With simple steps and with visual tools, learners will run small quantum experiments on their laptops, while a helpful artificial intelligence tutor writes, explains, and corrects code as they go. The project supplies ready-to-run Google Colab notebooks, clear videos, and interactive visualizations. Because it is open-source, teachers and learners everywhere, freely and collaboratively, can improve it. Visual scenes will flow into ParaView and Blender, so that quantum states, fields, and lattices are, vividly and reproducibly, seen in three dimensions. :contentReference[oaicite:1]{index=1}

---

## 0.5) Audience & Philosophy (General-Public, Vocabulary-Forward)

- **Audience.** Motivated general public, spanning high school to senior undergraduate levels; not a school-bound curriculum, rather a community-built learning path.
- **Vocabulary-first promise.** We will introduce necessary vocabulary, patiently and iteratively, with short etymologies; we will prioritize **practical, descriptive** terms before historical eponyms (e.g., “state-sphere (historically ‘Bloch sphere’)”, “operator-sum representation (historically ‘Kraus operators’)”), so that meaning leads names.
- **Assessment posture.** Rubrics shall be guidance, not gatekeeping; quizzes are **optional**, **non-punitive**, and **replayable** with answer reveal at the end.

---

## 1) Technical Rationale

Analytically and systematically, we combine:  
1) **Reusable, Colab-ready notebooks** for circuits, channels, device-adjacent models (Hamiltonians, noise, simple transport).  
2) **Agentic tutor** using IBM Granite (preferred) with a clean, provider-agnostic interface; **Ollama** is supported for local fallback.  
3) **Visualization pipelines** exporting to VTK for ParaView **and** directly scripting Blender via Blender Python for imports, point clouds, geometry nodes, and glTF/PLY pathways.  
4) **Rigorous templates** (PEP 8, PEP 257, Google style) with “control knobs” for parameters, reproducibly.  
5) **Fabrication-adjacent CAD flow**: **GDSTK helpers** for GDSII, bridges to **Qiskit Metal** in Colab, and **possible OpenEMS** hooks for field simulation, with conversion utilities to VTK/point clouds for visualization. :contentReference[oaicite:2]{index=2}

---

## 2) Problem Statement & Objectives

**Problem.** Beginners and practitioners, globally and consistently, face fragmented resources, brittle environments, and minimal feedback when learning quantum computing and device-adjacent modeling. :contentReference[oaicite:3]{index=3}

**Objectives.**
- Provide, rapidly and transparently, a **cohesive starter curriculum** with runnable notebooks and parameterized experiments.  
- Offer, iteratively and adaptively, a **Granite-assisted tutor** (with Ollama fallback) that explains, critiques, and tests code.  
- Deliver, visually and interactively, **ParaView- and Blender-ready outputs** for states, channels, fields, and lattices.  
- Publish, openly and permissively, **curriculum + code + data** under Apache-2.0 / CC-BY 4.0. :contentReference[oaicite:4]{index=4}

---

## 3) Scope, Work Packages, and Deliverables

### WP-A — **Core Edusim Notebooks** (Colab-first)
- **A1. Qubits & Gates**: state prep, “state-sphere (historically ‘Bloch’),” measurement; HS visuals first, then math.  
  *Knobs*: number of shots, noise levels, gate angles.
- **A2. Circuits & Channels**: operator-sum representation (historically “Kraus”), depolarizing / amplitude-damping channels, tomography.  
  *Knobs*: channel parameters, tomography depth.
- **A3. Variational Mini-Lab**: two-qubit VQE on toy Hamiltonians; optimizer sweeps.  
  *Knobs*: ansatz depth, learning rate, random seed.
- **A4. Transport & Lattices (intro)**: tight-binding toy models, band sketches, VTK/point-cloud exports for 3‑D viewing.  
  *Knobs*: lattice size, hopping terms, boundary conditions.  
**Deliverables (A):** Four Colab notebooks with unit tests, datasets, and VTK/PLY exporters. :contentReference[oaicite:5]{index=5}

### WP-B — **Granite-/Ollama-Assisted Tutor**
- **B1. Prompt templates** for “explain this error,” “write unit tests,” “generate scaffolds,” “Socratic hints.”  
- **B2. Auto-rubrics**: formative checks; **optional, non-punitive quizzes** with answer reveal.  
- **B3. Lesson generator** from concept maps.  
**Deliverables (B):** Tutor module, example configs, usage docs; Granite preferred when credits are available; Ollama fallback when local.

### WP-C — **Visualization & Export**
- **C1. VTK export** from NumPy arrays and density matrices (isosurfaces / glyphs).  
- **C2. ParaView recipes** for pipelines and colorbars; reproducible figures.  
**Deliverables (C):** `viz/` utilities and ParaView state files. :contentReference[oaicite:6]{index=6}

### **WP-E — Blender Python + Point Clouds (New)**
- **E1. Point cloud import & shading**: write PLY/glTF from A1–A4; Blender Python script auto-imports, normalizes scales, and applies **node-based** shading mapping probability amplitudes to emission/roughness.  
- **E2. Geometry Nodes for lattices**: procedural lattice/graph instancing from CSV/NPZ; color by degree, phase, or energy.  
- **E3. Camera & render automation**: scripted turntables with consistent exposure and transparent backgrounds for docs.  
*Deliverables (E):* `blender/` scripts (`bpy`), example `.blend` with node groups, and headless CLI recipes.

### **WP-F — GDSTK + Qiskit Metal + Possible OpenEMS (New)**
- **F1. GDSTK helpers**: PEP 8/PEP 257-compliant utilities for cells, layers, units, and parameterized patterns (e.g., pads, CPWs).  
- **F2. Qiskit Metal in Colab**: minimal demo to sketch a layout block, then export DXF/GDS and round-trip via GDSTK.  
- **F3. OpenEMS hooks (optional)**: oct2py-based stubs to generate a field-solver script, run remotely or in container, and convert results to VTK/point-cloud.  
*Deliverables (F):* `cad/` (GDSTK), `eda/` (Metal stubs), `ems/` (OpenEMS launcher), and conversion examples.

---

## 4) Minimal Viable Release (MVR)

| Item | Description | Acceptance Test |
|---|---|---|
| MVR-1 | Notebook A1 runs on Colab GPU/CPU with no manual fixes | Unit tests pass; renders state-sphere & histograms |
| MVR-2 | Tutor answers “why did my circuit fail?” and cites offending code | Returns a fix + explanation + runnable diff |
| MVR-3 | ParaView pipeline renders exported VTK from A2/A3 | Opens `.vtp`/`.vti`; shows legend & camera presets |
| **MVR-4** | One **optional**, non-punitive quiz per notebook | Autograder yields score with hints; answer reveal enabled |
| **MVR-5** | Blender script imports a point cloud and renders a turntable | Headless render completes; images saved deterministically | :contentReference[oaicite:7]{index=7}

---

## 5) Architecture

```

[User (Colab)]
├─> Notebooks (A1–A4) ──> Compute (Qiskit simulators; NumPy/SciPy)
├─> Tutor (B1–B3) ──────> Granite / Ollama ──> Hints/Scaffolds
├─> Viz (C1–C2) ───────> VTK writers ──> ParaView scenes
└─> Blender (E1–E3) ──> PLY/glTF import ──> Geometry Nodes & Renders
└─> CAD/EDA (F1–F3) ──> GDSTK ⇄ Qiskit Metal ⇄ (optional) OpenEMS

```
*(Provider-agnostic tutor; offline “no‑LLM” paths preserved; headless Blender supported.)* :contentReference[oaicite:8]{index=8}

---

## 6) Open Licensing & Governance

- **Code**: Apache-2.0; **Educational content**: CC-BY 4.0; **Data**: CC0 where possible.  
- **Governance**: CONTRIBUTING.md, CODE_OF_CONDUCT.md, issue templates, and a lightweight RFC folder.  
- **Releases**: Semantic versioning, tagged artifacts, and DOI via Zenodo. :contentReference[oaicite:9]{index=9}

---

## 7) Timeline (12 Weeks or so)

| Week | Milestone |
|---|---|
| 1–2 | Repo bootstrapped; A1 notebook complete; style/lint gates (PEP 8/257; **pylint** baseline) |
| 3–4 | A2 channels + VTK exporter; ParaView sample scenes |
| 5–6 | **WP-E Blender**: point clouds → Blender import; scripted turntable |
| 7–8 | **WP-F GDSTK + Metal**: helpers + minimal layout; quizzes for A1–A2 |
| 9–10 | **OpenEMS hooks (optional)** + A3 VQE mini-lab polish |
| 11 | Instructor guide; packaging; non-punitive quiz engine full pass |
| 12 | Public release; showcase renders; application submissions & demos | :contentReference[oaicite:10]{index=10}

---

## 8) Budget & Funding Map (Mini-Grant Scale)

*(Unchanged in structure; Blender/EDA additions fit within the same mini-grant by scoping demos.)* :contentReference[oaicite:11]{index=11}

---

## 9) Eligibility & Program Alignment

*(As drafted; Granite/Hackathon alignment remains apt; Blender and CAD flows improve outreach potential.)* :contentReference[oaicite:12]{index=12}

---

## 10) Risk & Mitigation

| Risk | Impact | Mitigation |
|---|---|---|
| API/model drift (Granite or alternative) | Tutor prompts degrade | Pin versions; ship offline “no-LLM” paths; abstract provider layer |
| Environment brittleness | Onboarding friction | Colab-first; `requirements.txt`; smoke tests; reproducible seeds |
| Blender headless differences | Render failures | Provide containerized CLI; test on Linux CI; prebuilt `bpy` mapping |
| EDA/solver complexity | Setup overhead | Keep OpenEMS optional; ship stubs; provide docker recipes |
| Scope creep | Delays | MVR gate; six-module cap; backlog triage weekly | :contentReference[oaicite:13]{index=13}

---

## 11) Evaluation & Impact Metrics

- **Adoption**: GitHub stars, forks, unique Colab runs, VTK/ParaView/Blender asset downloads.  
- **Learning**: Quiz improvement deltas; completion rates; anonymous feedback forms.  
- **Visualization**: Number of reproducible renders (ParaView/Blender) generated by users.  
- **Sustainability**: External PRs; issues closed; new maintainers onboarded. :contentReference[oaicite:14]{index=14}

---

## 12) Community Plan

- **Docs & Tutorials**: Screen-captures, captions, and written guides for each notebook and Blender pipeline.  
- **Workshops**: Two online sessions (recorded), one educator roundtable.  
- **Ecosystem Bridges**: Integration examples for Qiskit; clear “good first issue” tasks.  
- **Showcases**: Submit to Granite-aligned hackathons; present outcomes publicly. :contentReference[oaicite:15]{index=15}

---

## 13) Naming Conventions & Identity Shifts (Counterfactuals)

If hosted-model access were unavailable, we would, practically and transparently, switch to a local instruction-tuned model via **Ollama** and rename the tutor extension to **“Open‑Tutor.”** The *tutor module* identity would change (provider-agnostic), while the *project identity* would remain consistent. :contentReference[oaicite:16]{index=16}

---

## 14) Mind-Map (Visible Branches)

```

Q-EDU-Forge
├─ Curriculum (A)
│  ├─ A1 Qubits & Gates
│  ├─ A2 Channels & Tomography
│  ├─ A3 Variational Mini-Lab
│  └─ A4 Transport Intro
├─ Tutor (B)
│  ├─ Error Explain & Scaffolds
│  ├─ Quizzes (optional, non-punitive)
│  └─ Lesson Generator
├─ Visualization (C)
│  ├─ VTK Export → ParaView
│  └─ PLY/glTF → Blender Python (E)
├─ CAD/EDA (F)
│  ├─ GDSTK Helpers
│  ├─ Qiskit Metal (Colab)
│  └─ OpenEMS (optional)
├─ Governance & Releases
│  ├─ Apache-2.0 / CC-BY 4.0
│  └─ CI, Tests, Zenodo DOI
└─ Tooling
├─ pylint, pre-commit, PEP 8/257
└─ Granite / Ollama (provider-agnostic)

```
:contentReference[oaicite:17]{index=17}

---

## 15) Proposed Repository Structure

```

q-edu-forge/
├─ notebooks/         (A1–A4)
├─ tutor/             (B1–B3; Granite & Ollama adapters)
├─ viz/               (VTK writers; ParaView .pvsm states)
├─ blender/           (E: bpy scripts; node groups; CLI recipes)
├─ cad/               (F: GDSTK helpers; GDS/DXF samples)
├─ eda/               (F: Qiskit Metal stubs; export bridges)
├─ ems/               (F: OpenEMS launcher stubs; converters)
├─ pedagogy/          (rubrics; instructor guides; quiz JSON)
├─ tests/             (pytest; smoke tests; lint checks)
├─ tools/             (pylint configs; pre-commit hooks)
├─ docs/              (mkdocs; screenshots; renders)
└─ LICENSE, CONTRIBUTING, CODE_OF_CONDUCT

````
:contentReference[oaicite:18]{index=18}

---

## 16) Submission Checklist (Unitary Foundation & Similar)

- [x] Public GitHub repo (Apache-2.0 / CC-BY 4.0).  
- [x] Two-minute video pitch: goal, audience, demo clip, roadmap (include Blender turntable).  
- [x] Short form with clear impact statement and openness commitments.  
- [x] Parallel enrollment in Granite-aligned hackathon for visibility, credits, and prize eligibility. :contentReference[oaicite:19]{index=19}

---

## 17) Acronym Glossary (Extended)

- **AI** — Artificial Intelligence.  
- **API** — Application Programming Interface.  
- **CC-BY 4.0** — Creative Commons Attribution 4.0 International License.  
- **CI** — Continuous Integration.  
- **DOI** — Digital Object Identifier.  
- **GDSTK** — GDSII Stream Toolkit (Python library for IC layout).  
- **GDSII** — Graphic Design System II layout format.  
- **GLTF** — Graphics Language Transmission Format.  
- **GPU** — Graphics Processing Unit.  
- **LLM** — Large Language Model.  
- **MVR** — Minimal Viable Release.  
- **Ollama** — Local model runner/orchestrator for LLMs.  
- **OpenEMS** — Open Electromagnetic Field Solver (FDTD-style).  
- **PEP** — Python Enhancement Proposal.  
- **PLY** — Polygon File Format (point clouds/meshes).  
- **QPU** — Quantum Processing Unit.  
- **SDK** — Software Development Kit.  
- **VTK** — Visualization Toolkit.  
- **VQE** — Variational Quantum Eigenvalue method (variational solver for eigenproblems). :contentReference[oaicite:20]{index=20}

---

## 18) Blender Python — From First Picture to Procedural Scenes (New)

**HS-level explanation (plain, stepwise).** We will, firstly and visually, turn numbers into pictures. A quantum state’s measurement probabilities become points and colors. We export those points to a simple `.ply` file. Blender then reads that file, places every point in 3-D, and assigns colors and sizes according to the probabilities. Next, with a short script, Blender spins a camera around the points and saves images as a smooth turntable.

**Graduate-level explanation (practical, precise).** Let $\lvert\psi\rangle \in \mathbb{C}^{2^n}$ and let $p_i = \lvert \psi_i \rvert^2$ be computational-basis probabilities. We map basis indices $i$ to $\mathbb{Z}_2^n$ bitstrings and embed them into $\mathbb{R}^3$ by a Gray-code or Hamming-weight-aware embedding for spatial regularity. Phase $\arg(\psi_i)$ maps to hue or normal map perturbations; amplitude $\lvert \psi_i \rvert$ maps to point radius or emission strength. Blender Python (`bpy`) constructs a node tree (Geometry Nodes + Shader Nodes) that instantiates sphere glyphs, binds attributes (amplitude, phase) from custom vertex colors or from a generated attribute layer, and renders headlessly with consistent camera intrinsics.

**Blender pipeline details.**
1. **Data export**: `notebooks/A1` writes `state_points.ply` with XYZ + RGB(A) + optional custom attributes (amplitude, phase).  
2. **Import & nodes**: `blender/import_pointcloud.py` loads PLY/glTF, builds a Geometry Nodes graph that sizes instances by amplitude and colors by phase.  
3. **Render automation**: `blender/render_turntable.py` creates a circular camera path, keyframes exposure, and outputs PNGs with transparent background for docs and slides.  
4. **Reproducibility**: headless runs via `blender -b scene.blend -P render_turntable.py -- --frames 180 --radius 4.0 --seed 42`.

**Mini example (export point cloud in Colab).**
```python
# Colab cell: export a quantum state as a point cloud (PLY), PEP 8 / PEP 257 compliant.
from __future__ import annotations
from dataclasses import dataclass
import numpy as np

@dataclass
class CloudKnobs:
    """Control knobs for point-cloud export."""
    n_qubits: int = 3
    seed: int = 7
    radius: float = 0.03  # visual scale hint, used later in Blender
    use_gray: bool = True

def gray_code_embed(bitstrings: np.ndarray) -> np.ndarray:
    """Embed bitstrings into R^3 by Gray-coded Morton-like layout."""
    n = bitstrings.shape[1]
    coords = np.zeros((bitstrings.shape[0], 3), dtype=float)
    # Simple 3-axis packing: split bits into x,y,z interleaves
    coords[:, 0] = bitstrings[:, ::3].dot(2 ** np.arange((n + 2) // 3))
    coords[:, 1] = bitstrings[:, 1::3].dot(2 ** np.arange((n + 1) // 3))
    coords[:, 2] = bitstrings[:, 2::3].dot(2 ** np.arange(n // 3))
    # Normalize to [-1, 1]
    coords = 2.0 * (coords - coords.min(0)) / (coords.ptp(0) + 1e-9) - 1.0
    return coords

def write_ply(path: str, xyz: np.ndarray, rgba: np.ndarray) -> None:
    """Write a minimal PLY point cloud."""
    header = (
        "ply\nformat ascii 1.0\n"
        f"element vertex {len(xyz)}\n"
        "property float x\nproperty float y\nproperty float z\n"
        "property uchar red\nproperty uchar green\nproperty uchar blue\nproperty uchar alpha\n"
        "end_header\n"
    )
    with open(path, "w", encoding="utf-8") as f:
        f.write(header)
        for (x, y, z), (r, g, b, a) in zip(xyz, rgba):
            f.write(f"{x:.6f} {y:.6f} {z:.6f} {int(r)} {int(g)} {int(b)} {int(a)}\n")

def demo_export(knobs: CloudKnobs = CloudKnobs()) -> None:
    """Generate a random state, map amplitudes/phases to RGBA, and export PLY."""
    rng = np.random.default_rng(knobs.seed)
    dim = 2 ** knobs.n_qubits
    psi = rng.normal(size=dim) + 1j * rng.normal(size=dim)
    psi = psi / np.linalg.norm(psi)
    probs = np.abs(psi) ** 2
    phases = (np.angle(psi) + np.pi) / (2 * np.pi)  # [0,1]
    # Bits
    bits = (np.arange(dim)[:, None] >> np.arange(knobs.n_qubits)) & 1
    xyz = gray_code_embed(bits[:, ::-1])
    # Map amplitude & phase to color
    hue = phases
    sat = np.ones_like(hue)
    val = np.sqrt(probs / probs.max())
    # HSV to RGB (simple)
    k = np.stack([ (hue * 6) % 6, ], axis=1)
    r = val
    g = val * (1 - 0.5 * sat)
    b = val * (1 - sat)
    rgba = np.stack([255 * r, 255 * g, 255 * b, 255 * np.ones_like(r)], axis=1)
    write_ply("state_points.ply", xyz, rgba.astype(np.uint8))

demo_export()
print("Wrote state_points.ply")
````

**Blender headless import & render (run locally or in CI).**

```python
# blender/import_pointcloud.py  (run with: blender -b -P blender/import_pointcloud.py -- --in state_points.ply)
import bpy, sys, argparse

def parse_args():
    parser = argparse.ArgumentParser()
    parser.add_argument("--in", dest="infile", type=str, required=True)
    parser.add_argument("--radius", type=float, default=0.03)
    parser.add_argument("--frames", type=int, default=180)
    return parser.parse_args(sys.argv[sys.argv.index("--") + 1:])

def main():
    args = parse_args()
    bpy.ops.wm.read_factory_settings(use_empty=True)
    bpy.ops.import_mesh.ply(filepath=args.infile)
    obj = bpy.context.selected_objects[0]
    # Shade smooth and add simple emission material
    mat = bpy.data.materials.new("AmpPhaseMaterial")
    mat.use_nodes = True
    obj.data.materials.append(mat)
    # Camera & turntable
    bpy.ops.object.camera_add(location=(0, -3, 1.5))
    cam = bpy.context.object
    bpy.context.scene.camera = cam
    bpy.ops.object.empty_add(type='PLAIN_AXES', location=(0,0,0))
    empty = bpy.context.object
    cam.parent = empty
    for f in (1, args.frames+1):
        empty.rotation_euler[2] = 0 if f == 1 else 6.28318
        empty.keyframe_insert(data_path="rotation_euler", frame=f, index=2)
    bpy.context.scene.render.filepath = "//renders/frame_"
    bpy.ops.render.render(animation=True)
if __name__ == "__main__":
    main()
```

---

## 19) Rubric & Quiz Policy (Optional, Non-Punitive)

* **Optional participation.** Quizzes are opt-in; they are for self-checks and exploration.
* **No point deductions.** Scores never decrease upon retries; best score is kept; answer reveal available after completion.
* **Vocabulary-first prompts.** Terms include short etymologies; when an eponym exists, both the descriptive term and the historical label are shown.
* **Exportable results.** Quiz attempts and feedback can be exported (JSON/CSV) for personal records.

---

## Appendix A — GDSTK Helpers + Qiskit Metal + Possible OpenEMS (Colab Examples)

> **Note.** These cells are structured for Colab with “control knobs,” PEP 8/PEP 257 style, and **pylint** friendliness. The OpenEMS step is optional and stubbed for portability.

**A.1 Install & Lint**

```python
# Colab cell: environment setup
!pip -q install gdstk qiskit-metal pylint oct2py  # openEMS itself is external; this installs Octave bridge
!python -m pylint --version
```

**A.2 GDSTK helper (parameterized, PEP 8/257)**

```python
from __future__ import annotations
from dataclasses import dataclass
import gdstk

@dataclass
class PadKnobs:
    """Control knobs for a demo GDS cell."""
    width: float = 100.0
    height: float = 100.0
    metal: int = 1

def build_demo_cell(knobs: PadKnobs = PadKnobs()) -> gdstk.Library:
    """Create a simple rectangular pad as a GDS library."""
    lib = gdstk.Library(unit=1e-6, precision=1e-9)
    cell = lib.new_cell("PAD_DEMO")
    rect = gdstk.rectangle((0, 0), (knobs.width, knobs.height), layer=knobs.metal)
    cell.add(rect)
    return lib

lib = build_demo_cell()
lib.write_gds("demo_pad.gds")
print("Wrote demo_pad.gds")
```

**A.3 Qiskit Metal round-trip (minimal sketch)**

```python
# Minimal import; full Qiskit Metal designs may require additional setup and an X11-less backend in Colab.
from qiskit_metal import designs
from qiskit_metal import draw
from qiskit_metal.toolbox_metal import MetalGUI

design = designs.DesignPlanar()
# (Sketch) Add a CPW or pad shape; then export as GDS/DXF
# design._chips.main; design.add_component(...)  # kept minimal here for portability
print("Qiskit Metal design initialized (sketch).")
```

**A.4 (Optional) OpenEMS hook via Octave bridge**

```python
from oct2py import octave

def check_openems() -> bool:
    """Check if openEMS is on the Octave path."""
    try:
        octave.eval("ver;")  # basic check
        # Users addpath('/path/to/openEMS'); in their environment or container
        return True
    except Exception as exc:
        print("Octave not available or openEMS not configured:", exc)
        return False

if check_openems():
    # Users can craft an Octave script to run FDTD and write HDF5/VTK for viz
    print("OpenEMS path configured. See ems/ templates for scripts.")
else:
    print("Skipping OpenEMS demo (optional).")
```

**A.5 ParaView & Blender bridge**

```python
# After simulation/export, convert arrays → VTK/PLY; we showed PLY earlier.
# For ParaView: write .vtp/.vti in viz/; for Blender: glTF/PLY path is recommended.
print("Use viz/ writers for VTK; use the Blender importer for PLY/glTF.")
```

---

## Appendix B — Tutor: Granite + Ollama + pylint

* **Provider-agnostic interface.** `tutor/` exposes `explain_error(code, trace)`, `suggest_tests(code)`, and `quiz_check(json)`; backends: Granite (hosted) and Ollama (local).
* **Style gates.** `pre-commit` runs `pylint`, `isort`, and docstring checks; failing style does not block learning notebooks but flags suggestions.
* **Privacy-first.** Local mode keeps code and attempts on-device.

---

## Appendix C — Vocabulary & Etymology Pattern

* **Descriptive-first labels** with short etymologies:

  * *state-sphere* (historically “Bloch sphere”): sphere of pure states for a single two-level system; “sphere” (Greek *sphaira*).
  * *operator-sum representation* (historically “Kraus operators”): channel action via $\sum_k E_k \rho E_k^\dagger$; “operator” (Latin *operari*, to work).
* **Consistency.** Historical names remain searchable in side notes; instructional text uses descriptive labels first.
