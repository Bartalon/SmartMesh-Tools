# SmartMesh-Tools
Combine, Separate, Extract, and Duplicate Face without losing instances or dealing with those pesky invisible transform nodes.

This script replaces Maya's default operations of Combine, Separate, Extract, and Duplicate Face.  This tool is similar to detachSeparate.mel 1.1 by JeffD ( https://www.creativecrash.com/maya/script/detachseparate-mel ) but with additional features and more up to date functionality for newer versions of Maya.

# Latest Features:
- Added customizeable variables to turn on or off tool's custom naming conventions (View commented code inside the .mel file)


## General Features:
- Clean construction history - No more leftover groups when combining, separating, extracting, or duplicating faces
- Specific naming conventions - No more mysterious "polySurface" objects
- Quick hotkey implementation

### Smart Combine
Combined objects will:
- be renamed SmartCombine_#
- automatically center their pivots instead of defaulting to Origin
- try to land inside its starting group (if any), or whichever group contained the most objects involved with the operation
- not cause instanced objects to disappear
- never share the same short name, even if nested inside groups
- take on the name of the group, if an entire group is being combined (so a group named Gun with 25 objects will result in one mesh automatically named Gun)

### Smart Separate
Separated objects will:
- retain original object's name with _Sep appended as a suffix (for instance, TestMesh would separate into TestMesh_Sep_1 and TestMesh_Sep_2) so you can still identify the origins of separated objects in the Outliner/Hypergraph
- retain the original object's pivot point instead of defaulting to Origin
- stay inside their groups
- not cause instanced objects to disappear

### Smart Extract
Extracted objects will:
- retain original object's name with _Ext appended as a suffix
- retain original object's pivot point instead of defaulting to Origin
- not generate a polyChipOff node on its originating mesh, but instead a deleteComponent node
- will have a clear construction history and will not be linked with its originating mesh (deleting history on the extracted element will not delete history on the original mesh)
- stay as one object even if selecting multiple non-contiguous elements (regular Extract would result in each element as a separate object)

### Smart Duplicate Face
Duplicated faces will:
- retain original object's name with _Dup appended as a suffix
- retain original object's pivot point instead of defaulting to Origin
- not affect construction history whatsoever on the original mesh!  This means you can duplicate faces on rigged meshes or other objects with complex history you want to retain.
- not affect instanced objects
- stay inside their groups


## Additional Features:
- Automated hotkey binding
- Automated shelf button creation
