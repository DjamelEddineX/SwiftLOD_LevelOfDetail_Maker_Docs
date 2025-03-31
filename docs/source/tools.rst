Tools
##########

Process Selected Objects (Toggle)
*******************************

* **What it does**:
 * **If enabled**: Generates LODs for all selected objects in the scene
 * **If disabled**: Processes only the active (last selected) object
* **When to use**:
 * ✔ When batch processing multiple assets
 * ✔ When focusing on a single important model
* **Default**: Enabled

LOD Count (Integer Input)
************************

* **What it does**:
 * Sets the number of LOD variations to generate (excluding original LOD0)
 * Example: Value of 3 creates LOD0 (original), LOD1, LOD2, and LOD3
* **Valid range**: 1-10
* **Recommended values**:
 * 3-4 for game assets
 * 1-2 for architectural visualization
* **Default**: 3

Simplification Power (Slider)
****************************

* **What it does**:
 * Controls overall intensity of mesh decimation
 * Lower values preserve more detail
 * Higher values maximize performance
* **Technical note**:
 * Directly affects the Decimate modifier's ratio parameter
* **Range**: 0.1-1.0
* **Default**: 0.5

LOD Ratio (Slider)
*****************

* **What it does**:
 * Determines reduction ratio between consecutive LOD levels
 * Each LOD will be this fraction of the previous LOD's density
* **Example**:
 * 0.7 means: LOD1 = 70% of LOD0, LOD2 = 70% of LOD1, etc.
* **Range**: 0.1-1.0
* **Default**: 0.7

Generate LODs (Button)
*********************

* **Action**:
 * Executes LOD generation with current parameters
* **Creates**:
 * New collection named ``[OriginalObjectName]_LODs``
 * Copies of original mesh with progressive decimation
* **Note**:
 * Original mesh remains completely unchanged

Export Directory (Path Selector)
*******************************

* **What it does**:
 * Sets output location for all exported FBX files
* **Requirements**:
 * Must be set before exporting
 * Supports absolute or relative paths
* **Best practice**:
 * Use project-relative paths when possible

Unity Export (Button)
********************

* **Output**:
 * Single FBX containing all LOD levels
* **Unity workflow**:
 * Automatically recognized by LOD Group component
 * Preserves parent-child hierarchy
* **Recommended for**:
 * Projects using Unity's built-in LOD system

Unreal Export (Button)
*********************

* **Output**:
 * Separate FBX files for each LOD level
* **Naming convention**:
 * ``[AssetName]_LOD0.fbx``, ``[AssetName]_LOD1.fbx``, etc.
* **Unreal integration**:
 * Automatically detects LOD sequence on import
* **Recommended for**:
 * UE4/UE5 projects

Export Raw LODs (Button)
***********************

* **Output**:
 * Individual FBX files with exact Blender names
* **Use cases**:
 * Custom game engines
 * Proprietary pipelines
 * Manual LOD setup
* **Naming**:
 * Preserves complete original object names

Delete LOD Collection(s) (Button)
********************************

* **Function**:
 * Removes all generated LOD objects and their collection
* **Safety features**:
 * Never affects original mesh
 * Undoable operation
* **Visibility**:
 * Only appears when LOD collections exist in scene

Show Presets (Toggle)
********************

* **What it does**:
 * Expands/collapses the preset management panel
* **Default state**: Collapsed

Save Preset (Button)
*******************

* **Action**:
 * Stores current settings as named preset
* **Saves**:
 * LOD Count
 * Simplification Power
 * LOD Ratio
 * Export path
 * Process Selected toggle state
* **Storage**:
 * Saved to ``swiftlod_presets.json``
 * Persistent between Blender sessions

Preset List (Interactive UI)
****************************

* **Components**:
 * **Preset name**: User-defined label
 * **Load button (↩️)**: Applies stored settings
 * **Delete button (❌)**: Removes preset permanently
* **Organization**:
 * Listed in creation order
 * Scrollable if many presets exist
* **Sharing**:
 * Preset file can be copied to other workstations
