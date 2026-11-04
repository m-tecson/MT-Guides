# Selecting your structure and aligning to a cryo-EM map
Consult with Dr. Greene prior to selecting your structure, you may select a solved crystal structure in the PDB or may be required to do ab-initio model building. This guide will assume you already have your model built and selected.

In this case, we will be using wild type human glutamine synthetase turnover (PDB ID = 9OTO) as an example.

With ChimeraX open, open your structure from the PDB using the open command alongside the PDB ID OR if you have your model saved drag that into your ChimeraX session:

Using Command Line: ```Open PDB ID```
![alt text](assets/Refinements+Dep/Step1_CLI_Import.gif)
Command input: ```open 9oto```

Drag and drop file from Finder/File Manager:
![alt text](assets/Refinements+Dep/Step1_DragandDrop.gif)

Next, drag and drop your map from Finder/File Manager then using the Model Pane select your structure. Using the right mouse options, translate it closer to the map, rotate and move as necessary. Navigate to tools -> volume data -> Fit in Map to fit your structure into the map. 
![alt text](assets/Refinements+Dep/Step1.5_Alignment.gif)

You may also use CLI: Fitmap #1 inMap #2. This assumes #1 is your structure and #2 is your cryo-EM map.

**IF YOU HAVE A MUTANT, NOW IS THE TIME TO INTRODUCE THE MUTATION**
You can introduce a mutation to the WT structure by using the command ```swapaa :residue# AA 3 letter code``` i.e. R341C mutation in GS would be ```swapaa :341 cys```. This will introduce the Arg -> Cys mutation to all 10 subunits.

Lastly, save your now aligned structure for use in downstream steps. Be sure to uncheck "use untransformed coordinates"
![alt text](assets/Refinements+Dep/Step1.7_SaveAlignment.gif)

You can also open the newly saved file to ensure alignment.
![alt text](assets/Refinements+Dep/Step1.8_ConfirmAlignment.gif)

After confirming alignment, you may now delete asymmetric subunits as needed. Below are a rough guide corresponding to human glutamine synthetase.
C1 = Independent subunits, do not delete any monomers
C5 = Chains A & G are the asymmetric units (one subunit from each ring) ```del /B-E, F, H-J```
D5 = All subunits are identitcal, can delete all but chain A ```del /B-J```

Confirm with Dr. Greene before proceeding.

After structures are well-refined according to Molprobity, we will symmetry expand in ChimeraX.