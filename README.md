QueryBySingingHumming
=====================

This repository contains a state-of-the-art system for query-by-singing-humming programmed in C++ (based on references [1] and [2]). It is based on a combined note-based and frame-based approach. A collection of MIDI files and several .WAV queries (extracted from [3]) are also provided for testing. The folders of this repository contain the following files:

Folder .\src
------------

Visual C++ 2010 Express solution of this system for QBSH. This solution is provided in .\src\QBSH_win32_vc2010, and it consists of three main projects, which have been organized in three different projects:

* SDHBuildModel


usage: SDHBuildModel.exe mid_list.txt model_dir

This program takes the list mid_list.txt of candidate songs in MIDI format (it must be Type 0 format) and generates two files: QBH.Model and QBHModel.Info , which are later used during the matching process. Note: model_dir folder must be created before calling SDHBuildModel.exe.

* SDHumming

usage: SDHumming.exe QBH.Model QBHModel.Info query.wav results.txt

This program retrieves the top-20 most similar songs in QBHModel files (built with SDHBuildModel) from the query stored in query.wav. This wav file must have a sample rate of 8000Hz. This program references SDFuzzySearch.dll, so it must be referenced in the C++ project. In our case, we have referenced SDFuzzySearch.dll as follows:

SDHumming Properties > C/C++ > Additional Include Directories: ..\SDFuzzySearch (both in Debug and Release configuration). This step is needed to find SDFuzzySearch.h

SDHumming Properties > Linker > General > Additional Library Directories: ..\Release or ..\Debug (for Release or Debug configuration). This is the directory of sdfuzzysearch.lib file.

SDHumming Properties > Linker > Input > Additional Dependencies: sdfuzzysearch.lib

* SDFuzzySearch

SDFuzzySearch produces SDFuzzySearch.dll, which is needed for SDHumming.exe program. It implements the searching algorithm used in this query-by-singing-humming system. This project must be compiled prior to SDHumming.



Folder .\bin
------------

Binaries compiled for win32 of SDHBuildModel.exe, SDHumming.exe and SDFuzzySearch.dll




Folder .\Jang48plus2000noiseESSEN
---------------------------------

A ZIP file containing a collection of 48 midi files (taken from Jang's dataset [3]) PLUS 2000 extra songs taken from ESSEN collection [4].




Folder .\WAVqueries
-------------------

Five .WAV queries, correponding to the MIDI file with same name (e.g. 00013.wav --> 00013.mid). These .WAV queries are taken from Jang's dataset [3].



Contact
-------

Emilio Molina (email: emilio.mol.mar@gmail.com)

Lei Wang (email: leiwang.mir@gmail.com)

References
----------

[1] Lei Wang, Shen Huang, Sheng Hu, Jiaen Liang, Bo Xu, An Effective and Efficient Method for Query by Humming System Based on Multi-Similarity Measurement Fusion, ICALIP, 2008
 
[2] Lei Wang, Shen Huang, Sheng Hu, Jiaen Liang, Bo Xu, Improving Searching Speed and Accuracy of Query by Humming System Based on Three Methods: Feature Fusion, Candidates Set Reduction and Multiple Similarity Measurement Rescoring, INTERSPEECH, 2008

[3] http://mirlab.org/dataSet/public/MIR-QBSH-corpus.rar

[4] http://www.esac-data.org/
