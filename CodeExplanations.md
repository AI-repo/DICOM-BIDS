
"SeriesDescription": "FLAIR_TRA",
"ProtocolName": "32_FLAIR_1mm_ipat2",
ImageType": ["DERIVED", "SECONDARY", "MPR", "CSA MPR", "CSAPARALLEL", "M", "ND", "NORM", "FM", "FIL"],	
"RawImage": false,

"SeriesDescription": "32_FLAIR_1mm_ipat2_ORIG",
"ProtocolName": "32_FLAIR_1mm_ipat2",
"ImageType": ["ORIGINAL", "PRIMARY", "M", "ND", "NORM"],

"SeriesDescription": "AAHScout_MPR_sag",
"ProtocolName": "AAHScout",
"ImageType": ["DERIVED", "PRIMARY", "MPR", "ND", "NORM"],
"RawImage": false,


analyze the DICOM header information (extracted into the provided JSON files) from the Patient/ directory to understand the different MRI modalities present, identify normalized scans (especially T1w and FLAIR), and determine how to categorize these scans according to the BIDS standard.
1. Scan the `Patient/` directory for all `.json` files.
2. Read each JSON file and extract key metadata fields like `SeriesNumber`, `SeriesDescription`, `ProtocolName`, `ImageType`, `ScanningSequence`, `SequenceVariant`, etc.
3. Compile this information into a pandas DataFrame for easy viewing and analysis.
4. Display the DataFrame, showing a summary of all scans found.
5. Include markdown cells explaining the analysis and incorporating the final `dcm2bids_config.json` content we developed.


---------------
can you tell me the series numbers whose "ImageType" contains "DERIVED" information or the "RawImage" is "false"?
Can you use SpinEchoFieldMap files to correct the MRI images?
i would like to push all the files in the /src folder into the github repository. I do not want to push the data.

I need the complete code of converting DICOMs (.IMA) to NIfTI(.nii) and extracting header infromation into JSON(.json) sidecar files. Then to BIDS either using dcm2niix or other methods in .ipynb file.


Here's the plan:

1. __Analyze JSON Headers:__ I will read the content of the provided JSON files to extract key information like `SeriesDescription`, `ProtocolName`, `ImageType`, "RawImage", and other relevant fields to understand each scan type. We check the Series of each modality, if the "ImageType" contains ["DERIVED", "SECONDARY"] then we only convert that series. otherwise we check if ["DERIVED", "PRIMARY"] is avaiable. If not we convert the ["ORIGINAL"] series. Therefore, we intend to convert only the last "DERIVED" series of each modality and not all of them. Reflect these into the the json configuation file.
2. we can proceed to create a configuration file (e.g., `dcm2bids_config.json`) based on this mapping. This file will guide the `dcm2bids` tool for the actual conversion.
3. __Summarize Findings:__ I'll present a summary of the different scan types found and their characteristics based on the header information.
4. __Propose BIDS Mapping:__ Based on the analysis, I will suggest a mapping of these scans to the appropriate BIDS data types (anat, func, dwi, fmap, perf) and propose a naming convention.

I will now execute the dcm2bids command. This command assumes dcm2bids is installed and accessible in your environment. It will use the Patient/ directory as input, participant ID P013, session ID 01, the configuration file dcm2bids_config.json, and create the BIDS structure in a new directory named bids_output.

command:
```shell
dcm2bids -d Patient/ -p P013 -s 01 -c dcm2bids_config.json -o bids_output --clobber --force_dcm2bids
```

I need to create a jupyter notebook file where it shows all the analyzes of DICOM files, categories, number of series and other necesssary information. any graphs or tree structure that analyzes the headers and give information for later conversion to BIDS. The creation of config.json file. All related information that goes in a python or jupter notebook file.



Consider the Analysis.ipynb file:
1. I need the complete code of converting DICOMs (.IMA) to NIfTI(.nii) and extracting header infromation into JSON(.json) sidecar files. Then to BIDS either using dcm2niix or other methods at the begining of the .ipynb file.

2.when checking the json files, i would like to also list the series numbers whose "ImageType" contains "DERIVED" information or the "RawImage" is "false". 
We check the Series of each modality, if the "ImageType" contains ["DERIVED", "SECONDARY"] then we only convert that series. otherwise we check if ["DERIVED", "PRIMARY"] is avaiable. If not we convert the ["ORIGINAL"] series. Therefore, we intend to convert only the last "DERIVED" series of each modality and not all of them. Reflect these into the the json configuation file.
3.use SpinEchoFieldMap files to correct the MRI images









