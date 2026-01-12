# Advanced File Output Macro with Archive

This SolidWorks VBA macro automates the export of the active drawing and its referenced model to multiple file formats, while intelligently archiving previous revisions to maintain version history.

## Features

- **Drawing Export**: Exports the current drawing to DXF (with company-wide preferences) and PDF formats.
- **Model Export**: Exports the referenced part or assembly to STEP format.
- **Smart Filenames**: Constructs filenames using custom properties (Part Number, Description, and optional Revision) from the model and drawing.
- **Filename Sanitization**: Automatically cleans filenames to ensure Windows compatibility by replacing invalid characters.
- **Automatic Archiving**: Before exporting, moves older revisions of exported files to an "Archive" subdirectory, preserving version history.
- **Overwrite Protection**: Checks for existing files and prompts the user before overwriting current revisions.
- **Error Handling**: Validates exports and reports success or failure with detailed messages.

## Archiving Behavior

- Creates an "Archive" folder in the same directory as the drawing if it doesn't exist.
- Archives files with older revision numbers (e.g., "Part, Desc, Rev A.dxf" if current is "Rev B").
- Also archives revision-less files that match the base name.
- Handles filename collisions in the archive by appending timestamps.

## Usage

1. **Prerequisites**:
   - SolidWorks must be installed and running.
   - Open a drawing document that references a part or assembly.
   - Ensure the drawing is saved to disk.
   - The referenced model must have "Part Number" and "Description" custom properties set. "Revision" is optional (from the drawing).

2. **Running the Macro**:
   - Load and run `Advanced File Output with Archive.swp` in SolidWorks.
   - The macro will automatically archive old revisions and then export files to the same folder as the drawing.

3. **Output Files**:
   - `<Part Number>, <Description>[, Rev <Revision>].dxf` (drawing)
   - `<Part Number>, <Description>[, Rev <Revision>].pdf` (drawing)
   - `<Part Number>, <Description>[, Rev <Revision>].step` (model)

## Installation

- Download `Advanced File Output with Archive.swp` from this repository.
- In SolidWorks, go to Tools > Macro > Run, and select the .swp file.
- For persistent access, you can assign it to a toolbar button or menu.

## Requirements

- SolidWorks 2013 or later (due to DXF format version).
- VBA support enabled in SolidWorks.

## Notes

- The macro temporarily modifies DXF export preferences but restores them afterward.
- If no referenced model is found or required properties are missing, the macro will display an error and exit.
- All exports must succeed for the macro to complete; otherwise, it stops at the first failure.
- Archived files are moved to prevent accidental loss, but can be manually restored if needed.

## Contributing

Feel free to fork and improve the macro. Pull requests are welcome.