# **Q-EDU-Forge** - A Mini Open-Source Project for Quantum Education & Simulation (Granite-Assisted)

---

# **Primary Tools & Pipelines: Blender Python, IBM Granite, and ParaView + Point Cloud**

> **Portmanteaus & Etymologies.** **BlendQ** (Blender + Qubits), **GranTutor** (Granite + Tutor), and **ParaCloud** (ParaView + Point Cloud). “Blend” traces to Old English *blandan*, “to mix,” and **Granite** evokes igneous strength and stability; **ParaView**—from *para*, “beside,” and “view”—emphasizes comparative, side‑by‑side analysis.

### A. Concept in One Minute

**First, we compute small quantum experiments on a laptop. Then, we **see** them: we render states and circuits in **Blender** for cinematic, informative animations; we **study many runs at once** as **point clouds** in **ParaView**; and we get **live code help** from **IBM Granite**, which writes, explains, and fixes scripts as we go. Blender makes things look real. ParaView makes large datasets stay fast. Granite makes learning stick with immediate feedback. ([docs.blender.org][1])

**Concretely, Blender’s embedded Python (**`bpy`**) gives full programmatic control over scenes, geometry, materials, and headless rendering; its native **Point Cloud** data‑block and Geometry Nodes let us encode measurement‑induced sample sets (e.g., Bloch samples, tomography results) with per‑point attributes and radii. ParaView’s VTK pipeline and **Glyph/Point‑Gaussian** representations let us interrogate large sweeps with linked filters and comparative views. **Granite** (Watsonx‑hosted or local) supplies promptable code generation, QA, and rubric‑guided feedback for notebooks **and** `bpy` scripts, with a code‑specialized Granite family available. ([docs.blender.org][2])

---

## **1A) Blender Python as a Primary Visualization & Simulation Companion**

**What it adds.** Procedural, reproducible visualizations of $\lvert\psi\rangle$ trajectories, channel deformations, variational flows, and lattice/field scenes, driven entirely by Python. Assets render offline, headless, or interactively—ideal for lectures and short clips that concretize abstract math.

* **Embedded API (`bpy`) & style.** Blender exposes `bpy` and `mathutils` for scripting objects, materials, animation, and rendering; best practices align with PEP 8 (clean, testable add‑ons). ([docs.blender.org][2])
* **Point Cloud objects & GN.** Native **Point Cloud** objects store position, radius, and attributes; Geometry Nodes (**Points**, **Instance on Points**) procedurally generate and instance geometry, from qubit samples to lattice defects. ([docs.blender.org][3])
* **As a Python module.** For CI or batch rendering, use “Blender as a Python module” and run in headless mode, keeping demos deterministic. ([docs.blender.org][4])

> **Teaching hook.** HS: render a Bloch sphere and animate a single qubit’s precession. Graduate: bind Kraus‑map outputs to point attributes, render channel images on the sphere, and overlay vector fields for dissipators.

---

## **1B) ParaView + Point Cloud as a Primary Analysis Tier**

**What it adds.** Efficient, scalable inspection of **many** samples—shots, parameter sweeps, Monte‑Carlo noise studies—as **point clouds** with scalar/vector attributes, powered by VTK.

* **Readers.** Use **PLY** or **PTS** readers for point clouds; use **VTP** (VTK PolyData) for attributes and topology. ([paraview.org][5])
* **Representations.** Switch between **Glyph** (arrows, spheres, cones) and **Point Gaussian** for performant splats; use **Comparative Views** for side‑by‑side parameter scans. ([docs.paraview.org][6])
* **Filters.** Build pipelines (threshold, slice, stream tracer, resample) for hypothesis‑driven exploration. ([docs.paraview.org][7])

> **Teaching hook.**: color points by measurement outcome. Graduate: map density‑matrix invariants or estimator variances onto per‑point attributes, then interrogate clusters and outliers interactively.

---

## **1C) IBM Granite as the Agentic Coding & Assessment Layer (Primary)**

**What it adds.** A model‑agnostic but Granite‑optimized tutor that (1) writes and explains code in Colab and Blender, (2) generates rubrics and quizzes, and (3) critiques PRs. Favor **Granite Code** for scripting tasks. Granite can run in Watsonx, locally (some variants), or via OSS channels, giving flexibility in classrooms and hackathons. ([IBM][8])

* **Model availability & governance.** Granite models are openly documented and positioned for enterprise governance in Watsonx, with code‑oriented models opened by IBM Research; coverage includes chat templates and document‑grounding patterns. ([IBM][9])
* **Evolving openness.** Reporting in 2024–2025 has tracked IBM’s continued open‑model stance and ecosystem partnerships relevant to education. ([Reuters][10])

> **Teaching hook.**: “explain my error” and “what does this node do?” Graduate: “write a `bpy` operator to import Bloch samples and animate camera paths; add pytest stubs and docstrings.”

---

## **Primary Tools & Fit**

| Tool (Primary)             | What we use it for                                                                  | Interfaces & Formats                                                                                   | Why it is primary                                                 | Limits & Mitigations                                                                                     |
| -------------------------- | ----------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------ | ----------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------- |
| **Blender Python (`bpy`)** | Cinematic, parameterized visuals; GN‑driven point clouds; headless renders for docs | `bpy`, Geometry Nodes, Point Cloud object; headless/`--background`; CSV/NPY/PLY import; Python add‑ons | Pedagogically powerful, reproducible, and friendly to code review | Ultra‑large clouds: prefer ParaView or PLY instancing; use GN instancing, LOD, or decimation when needed |
| **ParaView + Point Cloud** | Fast, exploratory analysis of many samples; comparative studies; publication plots  | VTK (**.vtp** PolyData), **.ply**, **.pts**; Glyph/Point‑Gaussian; filters & comparative views         | Scales interactively, stays faithful to data attributes           | For story‑driven scenes: export to Blender via VTK→PLY hand‑off                                          |
| **IBM Granite**            | Tutor for code explanation, generation, quizzes, and rubric‑based feedback          | Watsonx API; local where supported; code‑specialized Granite                                           | Transparent docs, code specialization, and governance             | If offline or credits unavailable: swap to local OSS LLM via the existing provider‑agnostic layer        |

*References:* Blender `bpy` & Point Cloud docs; ParaView readers/filters; Granite model docs. ([docs.blender.org][2])

---

## **New Work Package (Primary): WP‑E - Blender Python Studio**

**E1. Procedural Bloch & Channel Scenes.** Generate Bloch spheres, sample $\lvert\psi\rangle$ point sets, channel ellipsoids, and vector‑field overlays; expose **control knobs** (samples, noise, camera, DOF). ([docs.blender.org][1])
**E2. Point‑Cloud Ingestors.** Import **PLY/CSV** and bind per‑point attributes (color, radius, label); optionally promote to GN instancing for fast shading. (Blender 4.x PLY operator: `bpy.ops.wm.ply_import`.) ([blender.org][11])
**E3. Headless Render Orchestrator.** Batch camera paths, resolution presets, and asset caching for CI. ([docs.blender.org][4])
**E4. Granite‑in‑the‑Loop.** Helper that hands code stubs/errors to Granite, returns patches, docstrings, and unit tests; runs in notebooks and Blender’s scripting workspace. ([IBM][12])
**E5. Pedagogical Overlays.** Grease‑pencil callouts, axis labels, and rubric‑aligned captions.

**Deliverables (E):** `blendq/` add‑on; demo `.blend`s; headless CLI; tests.

---

## **C3) ParaView + Point Cloud Recipes (Primary)**

* **Readers:** `PLYReader` (Stanford PLY), `PTSReader` (ASCII point clouds), `vtkXMLPolyDataReader` (VTP). ([paraview.org][5])
* **Representations:** **3D Glyphs** for arrows/cones; **Point Gaussian** for large clouds. ([docs.paraview.org][6])
* **Comparative Views:** side‑by‑side sweeps for optimizer settings or channel parameters. ([cep.tacc.utexas.edu][13])
* **Filters:** threshold, clip, slice, resample—keep pipelines declarative and saved as `.pvsm`. ([docs.paraview.org][7])

**VTK Interop Note.** Prefer **`.vtp`** (PolyData) for points + attributes; it is the canonical VTK XML format for unstructured point/line/surface sets. ([docs.vtk.org][14])

---

## **Interoperability: Data Paths & Exchange**

```
NumPy / Qiskit outputs
├─> VTK writer →  .vtp  ──> ParaView (Glyph/ Point Gaussian; pvsm)
└─> CSV/PLY  ──> Blender (Point Cloud/ GN instancing; headless renders)
```

* **`.vtp` PolyData** captures points with arbitrary named arrays; **ParaView** reads it natively. ([vtk.org][15])
* **`.ply`/`.pts`** handle scanner‑style clouds; **Blender** (via `bpy.ops.wm.ply_import`) and **ParaView** both accept PLY; ParaView also reads PTS natively. ([blender.org][11])

---

## **MVR (Minimal Viable Release)**

| Item      | Description                                                                   | Acceptance Test                                                          |
| --------- | ----------------------------------------------------------------------------- | ------------------------------------------------------------------------ |
| **MVR‑5** | Blender add‑on renders Bloch samples and channel ellipsoids from CSV/PLY      | CLI headless render produces frames; unit tests check attribute bindings |
| **MVR‑6** | ParaView pipeline loads `.vtp` point clouds, applies Glyph and Point Gaussian | Saved `.pvsm` reproduces the view, camera, and legend on open            |

---

## **Pedagogy Anchors (HS → Graduate)**

* Show on a **Blender** Bloch sphere how a depolarizing channel shrinks the point cloud toward the origin, and let students scrub sliders for noise. ([docs.blender.org][3])
* Implement Kraus maps $E_k$ and export Monte‑Carlo samples as **VTK PolyData** for **ParaView**; analyze estimator bias across optimizer configurations using comparative views. (For channels & Kraus, see Watrous’ open text.) ([Cheriton School of Computer Science][16])

---

## **Mind‑Map**

```
Q-EDU-Forge
├─ Curriculum (A) - A1 Qubits - A2 Channels - A3 VQE - A4 Transport
├─ Tutor (B) - Granite Code help
├─ Visualization (C)
│  ├─ C1 VTK Export
│  ├─ C2 ParaView Recipes (Glyph/ Pt Gaussian / Comparative)
│  └─ C3 Point Cloud Interop (PLY/ PTS/ VTP)
├─ Blender Python (E)  ← NEW PRIMARY
│  ├─ E1 Bloch & Channel Scenes
│  ├─ E2 Point-Cloud Ingestors (CSV/PLY, attributes)
│  ├─ E3 Headless Renders
│  └─ E4 Granite-in-the-Loop code assist
└─ Governance & Releases - Apache-2.0/ CC-BY 4.0; tests; CI; Zenodo DOI
```

---

## **Appendix A — Blender Python: Minimal, Colab‑style Script (PEP 8; control knobs)**

> **Purpose.** Import a PLY point cloud or CSV of Bloch vectors, create a lightweight point‑cloud visualization in Blender 4.x, and render frames headlessly. (Uses the **new** 4.x import operator names; OBJ/PLY importers moved under `bpy.ops.wm.*`.) ([blender.org][11])

```python
"""
BlendQ minimal loader: PLY or CSV → point cloud → quick render.

Control knobs:
- INPUT_MODE: 'PLY' or 'CSV'
- INPUT_PATH: path to .ply or .csv
- POINT_SIZE: viewport/render visual size
- USE_GN_INSTANCING: True → instance spheres on vertices for visibility
- FRAME_START/END: render window for short clips
"""

import bpy
from pathlib import Path

# ----- knobs -----
INPUT_MODE = 'PLY'            # 'PLY' or 'CSV'
INPUT_PATH = '/abs/path/to/bloch_samples.ply'  # or .csv with x,y,z[,r,label]
POINT_SIZE = 0.01
USE_GN_INSTANCING = True
FRAME_START, FRAME_END = 1, 1
OUTPUT_PATH = '//render.png'  # change to '//frames/####.png' for sequences

# ----- scene prep -----
bpy.ops.wm.read_factory_settings(use_empty=True)
scene = bpy.context.scene
scene.frame_start, scene.frame_end = FRAME_START, FRAME_END

# camera/light
bpy.ops.object.camera_add(location=(2.5, -2.5, 2.0))
cam = bpy.context.object
cam.data.lens = 50
bpy.ops.object.light_add(type='SUN', location=(5.0, -5.0, 8.0))

# ----- data ingest -----
def load_ply(filepath: str):
    # Blender 4.x (C++ importer):
    #   bpy.ops.wm.ply_import(filepath='...')
    # Legacy (<=3.x) was bpy.ops.import_mesh.ply(...) but is deprecated.
    res = bpy.ops.wm.ply_import(filepath=filepath)
    assert 'FINISHED' in res

def load_csv_as_vertices(filepath: str):
    import csv, mathutils
    # Make empty mesh, push CSV rows as vertices
    mesh = bpy.data.meshes.new("csv_points")
    obj = bpy.data.objects.new("csv_points", mesh)
    bpy.context.collection.objects.link(obj)

    verts = []
    with open(filepath, 'r', newline='') as f:
        reader = csv.reader(f)
        for row in reader:
            if not row or row[0].startswith('#'):
                continue
            x, y, z = map(float, row[:3])
            verts.append((x, y, z))

    mesh.from_pydata(verts, [], [])  # verts-only mesh for instancing/points
    mesh.update()

if INPUT_MODE.upper() == 'PLY':
    load_ply(INPUT_PATH)  # imports as a mesh or point set depending on file
else:
    load_csv_as_vertices(INPUT_PATH)

# ----- optional: geometry-nodes instancing for visibility -----
if USE_GN_INSTANCING:
    obj = bpy.context.selected_objects[0] if bpy.context.selected_objects else bpy.context.view_layer.objects.active
    bpy.context.view_layer.objects.active = obj
    # add GN modifier
    mod = obj.modifiers.new("inst_on_points", 'NODES')
    # build a simple node group: points/verts → instance small icospheres
    # (we rely on Blender’s default "Geometry" input and "Group Output")
    ng = bpy.data.node_groups.new("inst_on_points_group", 'GeometryNodeTree')
    mod.node_group = ng
    nodes = ng.nodes
    links = ng.links

    # nodes
    n_input = nodes.new("NodeGroupInput")
    n_output = nodes.new("NodeGroupOutput")
    n_geo_to_points = nodes.new("GeometryNodeMeshToPoints")
    n_ico = nodes.new("GeometryNodeMeshIcoSphere")
    n_instance = nodes.new("GeometryNodeInstanceOnPoints")
    n_set_shade = nodes.new("GeometryNodeSetShadeSmooth")

    # parameters
    n_geo_to_points.inputs['Radius'].default_value = POINT_SIZE
    n_ico.inputs['Radius'].default_value = POINT_SIZE
    n_ico.inputs['Subdivisions'].default_value = 1

    # layout
    n_input.location = (-600, 0); n_geo_to_points.location = (-400, 0)
    n_ico.location = (-400, -240); n_instance.location = (-200, 0)
    n_set_shade.location = (-40, 0); n_output.location = (140, 0)

    # links
    links.new(n_input.outputs['Geometry'], n_geo_to_points.inputs['Mesh'])
    links.new(n_geo_to_points.outputs['Points'], n_instance.inputs['Points'])
    links.new(n_ico.outputs['Mesh'], n_instance.inputs['Instance'])
    links.new(n_instance.outputs['Instances'], n_set_shade.inputs['Geometry'])
    links.new(n_set_shade.outputs['Geometry'], n_output.inputs['Geometry'])

# ----- camera aim & render -----
cam.constraints.new('TRACK_TO')
cam.constraints['Track To'].target = bpy.context.view_layer.objects[0]
cam.constraints['Track To'].track_axis = 'TRACK_NEGATIVE_Z'
cam.constraints['Track To'].up_axis = 'UP_Y'

scene.render.engine = 'BLENDER_EEVEE'
scene.render.filepath = OUTPUT_PATH
bpy.ops.render.render(write_still=True)
```

**Why these API choices?**

* **`bpy` & scripting workspace** are the documented path for operators, panels, and headless automation. ([docs.blender.org][1])
* **Point clouds & GN instancing** are the performant route to render many samples; Blender’s point cloud object stores positions/radii/attributes, and GN can instance lightweight geometry on those points. ([docs.blender.org][3])
* **`bpy.ops.wm.ply_import`** is the *current* 4.x PLY importer; the older `import_mesh.ply` name was removed in 4.0. ([blender.org][11])

> **If something is not true yet.** If Blender’s point cloud editing or import pipeline does not meet a specific need (for instance, extremely large clouds), then **export `.vtp`** and move analysis to **ParaView** (Glyph or Point Gaussian). Conversely, if ParaView lacks a cinematic element needed for a narrated lesson, then export a decimated or attribute‑curated **PLY** back to Blender for rendering. ([docs.paraview.org][6])

---

## **Appendix B — Quantum Background (Open Access anchors)**

* **Channels & Kraus maps.** See Watrous’ free monograph *The Theory of Quantum Information* (chapters on channels & CPTP maps). ([Cheriton School of Computer Science][16])
* **VQE as an educational lab.** Original VQE formulation and follow‑ups (Peruzzo et al.; and comparative analyses) provide a scaffold for A3’s mini‑lab. ([arXiv][17])

---

## **Acronym Glossary (Expanded)**

* **bpy** — Blender Python module (embedded interpreter and API). ([docs.blender.org][2])
* **GN** — Geometry Nodes (procedural geometry system in Blender). ([docs.blender.org][18])
* **PLY** — Polygon File Format (Stanford PLY). ([paraview.org][5])
* **PTS** — ASCII point cloud format used by some scanners (ParaView reader). ([paraview.org][19])
* **VTP** — VTK XML PolyData (points/lines/polygons + attributes). ([docs.vtk.org][14])
* **VTK** — Visualization Toolkit (data model used by ParaView). ([docs.vtk.org][14])
* **Granite (IBM)** — Open, enterprise‑governed foundation models; **Granite Code** is the code‑specialized family. ([IBM][8])

---

### **Placement Note**

* Put **Sections 1A–1C** immediately after your existing **1) Technical Rationale** to elevate these tools as primary.
* Insert **WP‑E** inside **3) Scope…** alongside WP‑A–D.
* Add **C3**, **Interoperability**, **MVR‑5/6**, and the **Glossary** to their matching sections.

---

**Citations & Docs used in this addendum:** Blender Python API (bpy, Point Cloud, Geometry Nodes); ParaView user guide (Glyph, Point Gaussian, filters, readers, comparative views) and VTK XML formats; IBM Granite model & code family docs and model availability; VQE and quantum channel open references. ([docs.blender.org][1])

---

> **Compatibility footnote.** In Blender 4.x, import operators moved under `bpy.ops.wm.*` (e.g., `wm.ply_import` / `wm.obj_import`). Update older scripts that reference `import_mesh.*` or `import_scene.*`. ([blender.org][11])

If you want, I can also generate a **clean, merged markdown file** with these sections spliced into your original document exactly where they belong.

[1]: https://docs.blender.org/api/current/info_quickstart.html "Quickstart - Blender Python API"
[2]: https://docs.blender.org/api/current/info_overview.html "API Overview - Blender Python API"
[3]: https://docs.blender.org/manual/en/latest/modeling/point_cloud/index.html "Point Cloud - Blender 4.5 LTS Manual"
[4]: https://docs.blender.org/api/current/info_advanced_blender_as_bpy.html "Blender as a Python Module"
[5]: https://www.paraview.org/paraview-docs/v5.12.0/python/paraview.simple.PLYReader.html "paraview.simple.PLYReader"
[6]: https://docs.paraview.org/en/latest/UsersGuide/displayingData.html "5. Displaying data — ParaView Documentation 6.0.0 ..."
[7]: https://docs.paraview.org/en/latest/UsersGuide/filteringData.html "6. Filtering Data"
[8]: https://www.ibm.com/granite "Granite"
[9]: https://www.ibm.com/granite/docs/models/granite "Granite 4.0"
[10]: https://www.reuters.com/technology/ibm-makes-more-ai-models-open-source-lands-saudi-arabia-deal-2024-05-21/ "IBM makes more AI models open source and lands Saudi Arabia deal"
[11]: https://developer.blender.org/docs/release_notes/4.0/python_api/ "Blender 4.0: Python API"
[12]: https://www.ibm.com/granite/docs/models/code "Granite Code"
[13]: https://cep.tacc.utexas.edu/user-guide/UsersGuide/displayingData.html "4. Displaying data — ParaView Documentation 5.9.1 ..."
[14]: https://docs.vtk.org/en/latest/vtk_file_formats/vtkxml_file_format.html "XML File Formats"
[15]: https://vtk.org/doc/nightly/html/classvtkXMLPolyDataReader.html "vtkXMLPolyDataReader Class Reference"
[16]: https://cs.uwaterloo.ca/~watrous/TQI/TQI.pdf "The Theory of Quantum Information"
[17]: https://arxiv.org/abs/1304.3061 "A variational eigenvalue solver on a quantum processor"
[18]: https://docs.blender.org/manual/en/latest/modeling/geometry_nodes/index.html "Geometry Nodes - Blender 4.5 LTS Manual"
[19]: https://www.paraview.org/paraview-docs/v5.12.0/python/paraview.simple.PTSReader.html "paraview.simple.PTSReader"
