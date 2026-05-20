##Overview
This dataset contains high-density diffuse optical tomography (HD-DOT) and functional MRI (fMRI) data from six healthy adult participants. DOT data were collected across three imaging sessions, and fMRI data were collected in a separate fourth session. Participants passively viewed silent natural movie clips, totaling 120 minutes of unique training content and 90 minutes of repeated test content (10 minutes per run). All movie stimuli were drawn from Nishimoto et al. (2011); the semantic labels were drawn from Huth et al. (2012). The test set contains a 1-minute deviation from the original Nishimoto et al. (2011)stimulus set (clip 8, seconds 421–480), for which semantic labels were generated separately following the annotation methods described in Huth et al. (2012). 

##Stimuli and task design
Training movies comprised 12 unique 10-minute runs (Trn001–Trn012). Event files (events.tsv) label these as TRAINMOVIE.

Test movies comprised nine unique 1-minute clips, each repeated 10 times across three sessions. Each session covered three consecutive clips: session 1 covered clips 1–3, session 2 clips 4–6, and session 3 clips 7–9, with 3–4 repetitions per run. In filenames, test movie runs are labeled ValSc{N} where S is the session number (1–3) and N is the clip index within that session (1–3); for example, Val2c1 refers to the first clip of session 2 (clip 4 of the full test set). Event files use the session-relative labels TESTMOVIECLIP1, TESTMOVIECLIP2, TESTMOVIECLIP3, which map to the same indexing. 

Localizer tasks used a block design and included two runs per session: an auditory word list task (HW) and a visual checkerboard task with left and right stimulation (AC).

##Data organization
Data are organized in BIDS format.
•	sub-*/: Raw HD-DOT and fMRI data; defaced T1w anatomical scans.
•	derivatives/Processed_fMRI/: Fully preprocessed fMRI data (.mat and .nii).
•	derivatives/freesurfer/: FreeSurfer segmentation masks (aseg). Masks were generated using both T1w and T2w images; T2w scans are not included in this release. 
•	derivatives/reconDOT/: Reconstructed HD-DOT images (HbO and HbR) in image space, one .mat file per run. Each file includes an info.paradigm field encoding task events as pulse indices: Pulse 1 = rest; HW Pulse 2 = word list onset; AC Pulse 2 = right and Pulse 3 = left checkerboard onset; Trn Pulse 2 = movie onset; Val Pulse 2–4 = clips 1–3 onset (session-relative, as described above). The info.movName field contains the run label (e.g., Val001c1, Trn001).
•	derivatives/Amats/: A-matrices used for DOT image reconstruction (.mat).
•	derivatives/Viz/: Field-of-view and cortical surface files per participant.
•	derivatives/DOT_MovieData_Full/: Concatenated HD-DOT responses. TrainFull: 7200×nVox; TestFull: 10×540×nVox.
•	derivatives/SemanticLabels/: Binary semantic annotation matrices. X_test: 540×1708; X_train: 7200×1708. Category labels are in utils/wordnet_categories.txt.
•	derivatives/Stimulus/: Movie stimuli at 15 Hz. TestMovies: 512×512×3×8100; TrainMovies: 512×512×3×108000.

##Notes
•	Model weights and analysis scripts accompanying the manuscript are available at [TBD].
•	See the manuscript for full acquisition and preprocessing details.