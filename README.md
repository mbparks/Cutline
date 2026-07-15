# CUTLINE

**CUTLINE v2.0.0** is a self-contained browser-based vector drawing and laser-project preparation tool. It is designed for creating, checking, arranging, and exporting 2D geometry for laser cutters without requiring a desktop CAD or illustration package.

The complete application is contained in a single HTML file. It can be opened locally, placed on a static website, or stored with a project for portable offline use.

## Purpose

CUTLINE focuses on the work between an initial drawing and a production-ready laser file. It combines basic SVG drawing, dimensional control, path editing, manufacturing layers, preflight checks, material sheets, simple nesting, kerf compensation, holding bridges, parametric part generators, and SVG/DXF export.

CUTLINE is intended for:

- Makers and fabrication laboratories
- Artists and designers preparing laser-cut work
- Engineering and prototyping teams
- Educators and students
- Small production jobs and one-off fixtures
- Field use where installing software is not practical

## Key Features

### Vector drawing

- Select, move, resize, rotate, mirror, duplicate, and delete objects
- Line, rectangle, rounded rectangle, ellipse, slot, polygon, and arc tools
- Polyline pen, Bézier pen, and freehand drawing
- Transparent drawing background
- Default black stroke width of 1 px
- Optional fills and configurable line caps
- Multiple editable layers

### Anchor and path editing

- Add, delete, and move anchor points
- Edit Bézier control handles
- Insert anchors on existing segments
- Open and close paths
- Join nearby endpoints
- Split paths at selected anchors
- Reverse path direction
- Simplify and clean paths
- Flatten Bézier curves into production polylines

### Precision controls

- Units in pixels, millimeters, centimeters, and inches
- Numeric X, Y, width, height, line length, and angle fields
- Lock width, height, length, angle, or aspect ratio
- Grid snapping
- Endpoint, midpoint, center, intersection, and alignment snapping
- Configurable snap tolerance and angular increment
- Keyboard nudging in the active document unit
- Persistent and associative measurements

### Geometry operations

- Vector union
- Subtract
- Intersect
- Exclude
- Positive and negative offsets
- Inside and outside kerf compensation
- Round, square, and miter offset joins
- Configurable offset tolerance and miter limit

### Manufacturing layers

Each layer can be assigned an operation type:

- Cut
- Score
- Engrave
- Construction
- Ignore

Layers also support:

- Visibility and locking
- Custom colors
- Export inclusion control
- DXF layer mapping
- Laser power
- Speed
- Pass count
- Frequency
- Air-assist setting
- Process notes

Machine settings are documentation values. CUTLINE does not directly control a laser cutter.

### Material sheets

- Multiple sheets in one project
- Sheet-specific geometry
- Shared manufacturing layers and job settings
- Add, duplicate, rename, switch, and delete sheets
- Common metric and imperial sheet presets
- Custom sheet dimensions
- Material margin and part spacing
- Configurable machine origin
- Grain-direction setting
- Nominal material-utilization display

### Arrays and layout

- Linear arrays
- Rectangular grid arrays
- Circular arrays
- Optional rotation of circular copies
- Align left, center, right, top, middle, and bottom
- Horizontal and vertical distribution
- Center selection on the artboard
- Basic automatic shelf nesting
- Optional 90-degree part rotation
- Grain-aware rotation restrictions

### Tabs and bridges

- Add evenly spaced holding bridges to closed outlines
- Configure bridge count and width
- Preserve the original unbroken outline internally
- Restore the complete outline after bridge creation
- Recognize intentional bridges during preflight

### Parametric generators

- Six-panel finger-joint box layout
- Rectangular hole grids
- Living-hinge panels

Generated geometry remains editable after creation.

### Import and export

#### SVG import

CUTLINE imports common SVG geometry, including:

- Paths
- Lines
- Rectangles and rounded rectangles
- Circles and ellipses
- Polygons and polylines
- Cubic and quadratic curves
- SVG arcs
- Groups
- Common transforms
- Basic inherited stroke and fill styles

#### DXF import

The ASCII DXF importer supports common 2D entities:

- `LINE`
- `LWPOLYLINE`
- `CIRCLE`
- `ARC`
- `ELLIPSE`

DXF layers are mapped into CUTLINE layers when possible.

#### SVG export

- Transparent background
- Physical document dimensions
- Layer and operation metadata
- Optional fill removal
- Artboard, drawing-bounds, or selection-only export
- Hidden and construction-layer controls
- Embedded CUTLINE job, material, sheet, and process metadata

#### DXF export

- ASCII DXF
- Physical unit information
- Configurable origin behavior
- Layer names and approximate layer colors
- Native `LINE`, `LWPOLYLINE`, `CIRCLE`, and `ELLIPSE` entities where applicable
- Tolerance-controlled polyline conversion for more complex geometry

DXF is a centerline geometry format in CUTLINE. SVG fills and stroke widths are not represented as machined widths.

## Laser Preflight

The preflight system checks the active sheet for common production problems:

- Open cut paths
- Unjoined nearby endpoints
- Duplicate or overlapping geometry
- Self-intersecting paths
- Extremely short segments
- Very small features
- Geometry outside the material sheet
- Filled geometry on cut layers
- Export-enabled construction geometry
- Empty layers

Each reported issue can be selected and located on the canvas. Safe automatic fixes can remove duplicate consecutive anchors, close endpoints that are already within tolerance, and remove duplicate line objects.

Preflight is an aid, not a substitute for reviewing the final file in the software used to operate the laser cutter.

## Quick Start

1. Download `cutline_v2.0.0.html`.
2. Open the file in a current desktop browser.
3. Set the job, material, units, and active material sheet.
4. Create or import geometry.
5. Assign objects to Cut, Score, Engrave, Construction, or Ignore layers.
6. Enter dimensions and apply constraints as needed.
7. Apply offsets or kerf compensation only after confirming the machine and material kerf.
8. Arrange repeated parts with arrays or basic nesting.
9. Add holding bridges where needed.
10. Run Preflight.
11. Export an SVG or DXF production file.
12. Review the exported file in the laser-control software before running the job.

## Recommended Workflow

### 1. Define the job

Enter the job name, project or revision reference, quantity, material, thickness, and notes.

### 2. Configure the material sheet

Choose a preset or enter custom dimensions. Set margins, part spacing, machine origin, and grain direction.

### 3. Organize manufacturing layers

Create separate layers for cut, score, engrave, and construction geometry. Enter machine settings as process documentation.

### 4. Draw or import geometry

Use CUTLINE's drawing tools or import an existing SVG or ASCII DXF file.

### 5. Apply precision controls

Use numeric dimensions, locks, smart snapping, rulers, alignment, and distribution to establish the required geometry.

### 6. Prepare geometry for fabrication

Use path cleanup, booleans, offsets, kerf compensation, arrays, bridges, and nesting as appropriate.

### 7. Run preflight

Resolve blocking errors and review warnings. Intentional open score or engrave paths may be acceptable, but open cut outlines should be reviewed carefully.

### 8. Export and verify

Export SVG or DXF, then open the result in the laser-control application. Confirm scale, units, layer mapping, origin, duplicate lines, and operation order.

## Keyboard Shortcuts

| Shortcut | Action |
|---|---|
| `V` | Select tool |
| `A` | Anchor-point tool |
| `M` | Measurement tool |
| `P` | Polyline pen |
| `B` | Bézier pen |
| `F` | Freehand tool |
| `L` | Line tool |
| `R` | Rectangle tool |
| `U` | Rounded rectangle tool |
| `E` | Ellipse tool |
| `S` | Slot tool |
| `G` | Polygon tool |
| `C` | Arc tool |
| `Delete` or `Backspace` | Delete selection |
| `Ctrl/Cmd + D` | Duplicate selection |
| `Ctrl/Cmd + Z` | Undo |
| `Ctrl/Cmd + Shift + Z` | Redo |
| `Ctrl/Cmd + Y` | Redo |
| `Ctrl/Cmd + E` | Open SVG export dialog |
| Arrow keys | Nudge selection by 1 active unit |
| `Shift` + Arrow keys | Nudge selection by 10 active units |
| `Space` + drag | Pan the workspace |
| Mouse wheel | Zoom |
| `Escape` | Cancel the current action and return to Select |
| `Enter` | Finish an active pen or Bézier path |

Some tools also use `Shift` as a temporary proportional or angular constraint while drawing or resizing.

## Project Files and Recovery

CUTLINE can save an editable project as a `.cutline` JSON file. This preserves geometry, sheets, layers, job information, material information, process settings, and workspace configuration.

The application also maintains:

- A current autosave in browser storage
- Up to 20 recovery checkpoints
- Manual recovery checkpoints
- Restore, download, and delete controls for saved checkpoints

Browser storage belongs to the browser profile and device being used. Clearing site data, using private-browsing mode, or changing browsers can remove locally stored autosaves and recovery checkpoints. Save important projects as `.cutline` files outside the browser.

## Deployment

CUTLINE does not require a server-side application, database, build process, package manager, or external JavaScript library.

To publish it on a website:

1. Rename `cutline_v2.0.0.html` if desired.
2. Upload it to any static web host.
3. Link directly to the HTML file.

Example directory:

```text
/cutline/
  index.html
  README.md
```

The application can also run directly from the local filesystem. Some browser features, particularly clipboard access, may require HTTPS or `localhost` depending on browser security settings.

## Privacy and Offline Use

CUTLINE performs drawing, import, export, autosave, and recovery operations in the browser. The application does not require an account or a network connection after the HTML file has been loaded.

Project data remains in the browser unless the user explicitly downloads, uploads, copies, or shares a file.

## Browser Requirements

Use a current desktop browser with support for:

- SVG
- JavaScript modules and modern JavaScript syntax
- File input and Blob downloads
- Local storage
- Pointer events

A desktop or laptop with a mouse or trackpad is recommended. Touch-only operation has not been optimized as the primary workflow.

## Current Limitations

- Nesting uses a basic rectangular shelf-placement method. It is not an industrial polygon nesting engine.
- Nesting evaluates object bounds and does not place parts inside internal holes.
- Finger-joint output must be verified with a small material and kerf test before production.
- Boolean and offset results are polygonal production paths. Complex curves may gain additional anchors.
- Offsets currently require closed geometry.
- DXF import is limited to supported ASCII 2D entities.
- Binary DXF, blocks, text, dimensions, hatches, splines, and many advanced CAD entities are not imported.
- SVG filters, masks, text, images, clipping systems, and advanced CSS styling are not intended as production import features.
- Laser power and speed values are documentation only and are not transmitted to a machine.
- Estimated vector-processing time is informational and may not match actual machine time.
- CUTLINE does not generate machine-specific G-code or directly operate a laser cutter.

## Safety

Laser cutters can cause fire, smoke, hazardous fumes, eye injury, and equipment damage. Always:

- Follow the laser manufacturer's operating procedures
- Confirm that the material is safe to laser process
- Use appropriate ventilation and filtration
- Verify focus, origin, power, speed, and pass count
- Supervise the machine during operation
- Test unfamiliar materials and kerf settings on scrap material
- Review the exported file before starting the job

Do not rely on CUTLINE to determine whether a material or machine setting is safe.

## Version

Current release: **CUTLINE v2.0.0**

CUTLINE is delivered as a single-file Field Instrument.
