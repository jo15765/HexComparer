# HexComparer

Compare two binary files side-by-side at the byte level.

HexComparer is a small Windows desktop utility for diffing hex dumps of two files. Use it for save-game analysis, firmware blobs, or any time you need to see where two binaries diverge, not just whether they match.

![.NET Framework](https://img.shields.io/badge/.NET%20Framework-4.5.2-512BD4)
![Platform](https://img.shields.io/badge/platform-Windows-0078D4)

---

## Features

- Load two files and compare them as hex and ASCII (typical hex-editor layout)
- Highlight offset, changed bytes, and length mismatches
- Handles large binaries (sample saves in this repo are about 350 KB)
- Simple WinForms UI

---

## Requirements

- **OS:** Windows
- **Runtime:** .NET Framework 4.5.2 or later
- **Optional:** Visual Studio 2019 or newer with the .NET desktop development workload

---

## Getting started

### Clone

```bash
git clone https://github.com/jo15765/HexComparer.git
cd HexComparer
```

### Build with Visual Studio

1. Open `Hex Compare v2.sln`
2. Choose **Debug** or **Release** (platform **x86**)
3. Build → Build Solution
4. Run from `bin\Debug\` or `bin\Release\`

### Build with MSBuild

From **Developer Command Prompt for VS**:

```cmd
msbuild "Hex Compare v2.sln" /p:Configuration=Release /p:Platform=x86
```

---

## Usage

1. Launch **Hex Compare**
2. Select **File A** and **File B**
3. Run **Compare**
4. Review results:
   - If files match, you should see no differences (or a single summary)
   - If they differ, inspect offsets and byte values for each mismatch

**Tip:** For very large files, use a **Release** build for better performance.

---

## Sample data in this repo

Binary fixtures for manual testing (for example, two save slots vs a base `game01`):

| File | Notes |
|------|--------|
| `game01` | Baseline save / reference binary |
| `Slot1_game01` | Slot 1 variant |
| `Slot4_game01` | Slot 4 variant |
| `slotoptions1.save` | Small options/metadata blob (slot 1) |
| `slotoptions4.save` | Small options/metadata blob (slot 4) |
| `slot1guid.throwaway` | GUID-related sidecar (slot 1) |
| `slot4guid.throwaway` | GUID-related sidecar (slot 4) |

**Example:** Compare `game01` with `Slot1_game01` to see which bytes change between slots.

---

## Project layout

```text
HexComparer/
├── Hex Compare v2.sln
├── Hex Compare v2.csproj
├── Form1.cs                 (main UI, when present in your branch)
├── game01
├── Slot1_game01
├── Slot4_game01
└── …
```

The `.csproj` references WinForms sources such as `Form1.cs`. If those files are missing from a clone, restore them from your local copy or an earlier commit.

---

## Roadmap

- Export diff report (CSV or HTML)
- Jump to next / previous difference
- Drag-and-drop file paths
- Optional .NET 8 CLI port

---

## Contributing

1. Fork the repository
2. Create a branch: `git checkout -b feature/my-change`
3. Commit and push your changes
4. Open a Pull Request against `main`

---

## License

Add a `LICENSE` file (for example MIT) when you choose a license. Until then, default copyright applies.

---

## Links

- Repository: https://github.com/jo15765/HexComparer
