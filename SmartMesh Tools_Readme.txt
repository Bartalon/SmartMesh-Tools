//////////////////////////////////////
/////       SmartMesh Tools       ////
/////         Version 1.0         ////
//////////////////////////////////////
   //                          //
//////////////////////////////////////
////  Authored and Maintained by  ////
////                              ////
////  Dennis "Bartalon" Porter    ////
////                              ////
////  Dennis.Porter.3D@gmail.com  ////
////    www.DennisPorter3D.com    ////
//////////////////////////////////////


Installation Instructions:
1) Fully exit Maya.
2) Paste dpSmartMeshTools.mel into C:\Users\Owner\Documents\maya\2013-x64\scripts
    or equivalent scripts folder destination. Be sure to put it into the Scripts folder 
    located inside the 2013 folder (not the one inside the "maya" folder) or it won't install 
    properly.
3) Open Maya.
4) In Maya's MEL command line (or in the Script Editor), type in the following, then press enter:

source dpSmartMeshTools.mel; dpSmartMeshTools;


For updates check http://www.creativecrash.com/maya/script/smartmesh-tools or www.DennisPorter3D.com/mel.htm


/////////////////////////////////
//  User-Adjustable Variables  //
/////////////////////////////////

There is a section labeled the same inside the .mel file.  Follow the instructions in that section of the .mel file
for enabling or disabling certain features of the SmartMesh Tools.


/////////////
//  About  //
/////////////

This script replaces Maya's default operations of Combine, Separate, Extract, and Duplicate Face.  This tool is similar 
to detachSeparate.mel 1.1 by JeffD ( http://www.creativecrash.com/maya/script/detachseparate-mel ) but with additional features.

///  General Features:

	1)  Clean construction history - No more leftover groups when combining, separating, extracting, or duplicating faces
	2)  Specific naming conventions - No more mysterious "polySurface" objects
	3)	Quick hotkey implementation


///  Smart Combine:
	Combined objects will:

	1)  be renamed SmartCombine_#
	2) 	automatically center their pivots instead of defaulting to Origin
	3) 	try to land inside its starting group (if any), or whichever group contained the most objects involved with the operation
	4)  not cause instanced objects to disappear
	5)  never share the same short name, even if nested inside groups
	6)  take on the name of the group, if an entire group is being combined (so a group named Gun with 25 objects will result in 
		one mesh automatically named Gun)


///  Smart Separate:
	Separated objects will:

	1)  retain original object's name with _Sep appended as a suffix (for instance, TestMesh would separate into TestMesh_Sep_1 
		and TestMesh_Sep_2) so you can still identify the origins of separated objects in the Outliner/Hypergraph
	2)  retain the original object's pivot point instead of defaulting to Origin
	3)  stay inside their groups
	4)  not cause instanced objects to disappear


///  Smart Extract:
	Extracted objects will:

	1)  retain original object's name with _Ext appended as a suffix
	2)  retain original object's pivot point instead of defaulting to Origin
	3)  not generate a polyChipOff node on its originating mesh, but instead a deleteComponent node
	4)	will have a clear construction history and will not be linked with its originating mesh (deleting history on the extracted 
		element will not delete history on the original mesh)
	5)  stay as one object even if selecting multiple non-contiguous elements (regular Extract would result in each element as a 
		separate object)


///  Smart Duplicate Face:
	Duplicated faces will:

	1)  retain original object's name with _Dup appended as a suffix
	2)  retain original object's pivot point instead of defaulting to Origin
	3)  not affect construction history whatsoever on the original mesh!  This means you can duplicate faces on rigged meshes or 
		other objects with complex history you want to retain.
	4)  not affect instanced objects
	5)  stay inside their groups


///  Additional Features:

	1)  Automated hotkey binding
	2)  Automated shelf button creation



///////////////////////
//  Version History  //
///////////////////////

27 January 2015 -- Version 1.1.0

	1)  Added variables for users to control whether or not the custom naming conventions will be used.  (See first few commented lines inside .mel file)
	2)  Fixed an issue where binding custom hotkeys did not work.
	3)  Fixed an issue where using Smart Separate on a grouped object with no elements to separate would inadvertently ungroup it.
	4)  Added additional information to the Help window.


21 December 2015
	1)  Initial Release.