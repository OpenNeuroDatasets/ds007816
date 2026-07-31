<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
</head>
<body>

<p><strong>Overview</strong></p>
<p>This dataset contains high-density diffuse optical tomography (HD-DOT) and functional MRI (fMRI) data from six healthy adult participants. DOT data were collected across three imaging sessions, and fMRI data were collected in a separate fourth session. Participants passively viewed silent natural movie clips, totaling 120 minutes of unique training content and 90 minutes of repeated test content (10 minutes per run). All movie stimuli were drawn from Nishimoto et al. (2011); the semantic labels were drawn from Huth et al. (2012). The test set contains a 1-minute deviation from the original Nishimoto et al. (2011) stimulus set (clip 8, seconds 421–480), for which semantic labels were generated separately following the annotation methods described in Huth et al. (2012).</p>

<p>Data were acquired on a custom-built, whole-head Very High-Density Diffuse Optical Tomography (VHD-DOT) system Fogarty et al. (2025) at Washington University in St. Louis, USA. The continuous-wave system included 255 source positions (685 and 830 nm) and 252 avalanche photodiode detectors coupled to the head using optic fiber bundles. The imaging cap provided a first-nearest-neighbor separation of ∼9.75 mm, yielding 9,160 possible measurements with source-detector separations ≤40 mm across both wavelengths. </p> 

<p><strong>Stimuli and task design</strong></p>
<p>Training movies comprised 12 unique 10-minute runs (Trn001–Trn012). Event files (events.tsv) label these as TRAINMOVIE.</p>
<p>Test movies comprised nine unique 1-minute clips, each repeated 10 times across three sessions. Each session covered three consecutive clips: session 1 covered clips 1–3, session 2 clips 4–6, and session 3 clips 7–9, with 3–4 repetitions per run. In filenames, test movie runs are labeled Val<em>S</em>c<em>N</em> where <em>S</em> is the session number (1–3) and <em>N</em> is the clip index within that session (1–3); for example, Val2c1 refers to the first clip of session 2 (clip 4 of the full test set). Event files use the session-relative labels TESTMOVIECLIP1, TESTMOVIECLIP2, TESTMOVIECLIP3, which map to the same indexing.</p>
<p>Localizer tasks used a block design and included two runs per session: an auditory word list task (HW) and a visual checkerboard task with left and right stimulation (AC).</p>

<p><strong>Data organization</strong></p>
<p>Data are organized in BIDS format.</p>
<ul>
  <li><code>sub-*/</code>: Raw HD-DOT and fMRI data; defaced T1w anatomical scans.</li>
  <li><code>derivatives/Processed_fMRI/</code>: Fully preprocessed fMRI data (.mat and .nii).</li>
  <li><code>derivatives/freesurfer/</code>: FreeSurfer segmentation masks (aseg). Masks were generated using both T1w and T2w images; T2w scans are not included in this release.</li>
  <li><code>derivatives/reconDOT/</code>: Reconstructed HD-DOT images (HbO and HbR) in image space, one .mat file per run. Each file includes an <code>info.paradigm</code> field encoding task events as pulse indices: Pulse 1 = rest; HW Pulse 2 = word list onset; AC Pulse 2 = right and Pulse 3 = left checkerboard onset; Trn Pulse 2 = movie onset; Val Pulse 2–4 = clips 1–3 onset (session-relative, as described above). The <code>info.movName</code> field contains the run label (e.g., <code>Val001c1</code>, <code>Trn001</code>).</li>
  <li><code>derivatives/Amats/</code>: A-matrices used for DOT image reconstruction (.mat).</li>
  <li><code>derivatives/Viz/</code>: Field-of-view and cortical surface files per participant.</li>
  <li><code>derivatives/DOT_MovieData_Full/</code>: Concatenated HD-DOT responses. TrainFull: 7200×nVox; TestFull: 10×540×nVox.</li>
  <li><code>derivatives/SemanticLabels/</code>: Binary semantic annotation matrices. X_test: 540×1708; X_train: 7200×1708. Category labels are in <code>utils/wordnet_categories.txt</code>.</li>
  <li><code>derivatives/Stimulus/</code>: Movie stimuli at 15 Hz. TestMovies: 512×512×3×8100; TrainMovies: 512×512×3×108000.</li>
</ul>

<p><strong>Notes</strong></p>
<ul>
  <li>Model weights and analysis scripts accompanying this work are available at the associated G-Node GIN repository, <a href="https://gin.g-node.org/wfehner/visual-semantic-hddot">https://gin.g-node.org/wfehner/visual-semantic-hddot</a> (<a href="https://doi.org/10.12751/g-node.qf5ttf">DOI: 10.12751/g-node.qf5ttf</a>).</li>
  <li>See the associated preprint for full acquisition and preprocessing details.</li>
  <li><strong>Associated preprint.</strong> Fehner, W., Fogarty, M., Tang, J., Wilhelm, D., Bajracharya, A., Markow, Z. E., Hines, A., Trobaugh, J. W., Huth, A. G., &amp; Culver, J. P. (2025). Visual Semantic Encoding and Identification of Naturalistic Movies via High-Density Diffuse Optical Tomography. <a href="https://doi.org/10.64898/2025.12.03.692158">https://doi.org/10.64898/2025.12.03.692158</a></li>
</ul>

<p><strong>References</strong></p>
<p>Fogarty, M., Rafferty, S. M., Markow, Z. E., O’Sullivan, A. C., Svoboda, C. F., George, T., King, K., Wilhelm, D., Tripathy, K., Mugler, E. M., Naufel, S., Yin, A., Trobaugh, J. W., Eggebrecht, A. T., Richter, E. J., & Culver, J. P. (2025). Functional brain mapping using whole-head very high-density diffuse optical tomography. <em>Imaging Neuroscience</em>, 3. href="https://doi.org/10.1162/imag.a.54">https://doi.org/10.1162/imag.a.54</a>‌</p>
<p>Huth, A. G., Nishimoto, S., Vu, A. T., &amp; Gallant, J. L. (2012). A continuous semantic space describes the representation of thousands of object and action categories across the human brain. <em>Neuron</em>, 76(6), 1210–1224. <a href="https://doi.org/10.1016/j.neuron.2012.10.014">https://doi.org/10.1016/j.neuron.2012.10.014</a></p>
<p>Nishimoto, S., Vu, A. T., Naselaris, T., Benjamini, Y., Yu, B., &amp; Gallant, J. L. (2011). Reconstructing visual experiences from brain activity evoked by natural movies. <em>Curr Biol</em>, 21(19), 1641–1646. <a href="https://doi.org/10.1016/j.cub.2011.08.031">https://doi.org/10.1016/j.cub.2011.08.031</a></p>

</body>
</html>