# Prediction-of-Finger-Flexion-4th-Brain-Computer-Interface-Data-Competition

The goal of this element of the competition is to predict the flexion of individual fingers from signals recorded from the surface of the brain (electrocorticography (ECoG)). This data set contains brain signals from three subjects, as well as the time courses of the flexion of each of five fingers. The task in this competition is to use the provided flexion information in order to predict finger flexion for a provided test set. The performance of the classifier will be evaluated by calculating the average correlation coefficient r between actual

I. SUBJECTS
The three subjects in the data set were epileptic pa- tients at Harborview Hospital in Seattle, Washington. Each patient had electrode grids placed subdurally on the surface of the brain for the purpose of extended clini- cal monitoring and localization of seizure foci. Each sub- ject gave informed consent to participate in this study, which was approved by the internal review board (IRB) of Harborview Hospital. All patient data have been anonymized according to IRB protocol in accordance with HIPAA regulations.

II. RECORDINGS
Signals from the electrode grid were amplified and dig- itized using Synamps2 amplifiers (Neuroscan, El Paso, TX). The general-purpose BCI system BCI2000 [1] pro- vided visual stimuli to the patient, acquired brain sig- nals from the Synamps2 system, and also recorded the flexion of individual fingers (on the hand contralateral to the implanted grid) using a data glove (Fifth Dimen- sion Technologies, Irvine, CA). BCI2000 stored the brain signals, the timing of stimulus presentation, and the flex- ion of each of the fingers in a data file. Data files were converted to Matlab format for this competition. Each patient had subdural electrode arrays (Ad-Tech, Racine, WI) implanted. Each array contained 48-64 platinum electrodes that were configured in 8x6 or 8x8 arrange- ments. The electrodes had a diameter of 4 mm (2.3mm exposed), 1 cm inter-electrode distance, and were em- bedded in silastic. Electrocorticographic (ECoG) signals (i.e., 62, 48, and 64 channels from subjects 1, 2, and 3, respectively) were acquired with respect to a scalp ref- erence and ground (Fig. 1), band pass filtered between 0.15 to 200 Hz, and sampled at 1000 Hz.

III. EXPERIMENTAL PROTOCOL
The subjects were cued to move a particular finger by displaying the corresponding word (e.g., ”thumb”) on a computer monitor placed at the bed-side (Fig. 2). Each cue lasted two seconds and was followed by a two-second rest period during which the screen was blank. During each cue, the subjects typically moved the requested fin- ger 3-5 times. This number varied across subjects and fingers. There were 30 movement stimulus cues for each finger (i.e., a total of 150 cue presentations and about 90-150 flexions of each finger); stimulus cues were inter- leaved randomly. This experiment lasted 10 minutes for each subject.
Subsequent offline analysis showed that ring (4th) finger movements were correlated with either middle (3rd) or little (5th) finger movements. Thus, while this ring (4th) finger position is included with the training data, it will not be used for evaluation purposes.

IV. DATA STRUCTURE
The data for each subject are contained in a separate MATLAB file that is named “subX comp.mat” where “X” denotes the subject number. Each file contains three variables:
• “train data” - this variable, in time × channels, gives the first 2/3 (6 min, 40s) of recorded ECoG signals (400,000 samples at 1kHz sampling rate per channel) from the specified experiment, for every channel.
• “train dg” - this variable, in time × finger is the first 2/3 (6 min, 40s) of recorded finger position (thumb - index - middle - ring - little; 400,000 sam- ples (super-sampled to 1 kHz) per finger) for the associated experiment.
• “test data” - this variable, in time × channels, gives the last 1/3 (3 min, 20s) of recorded ECoG signals (200,000 samples at 1kHz sampling rate per chan- nel) from the specified experiment, for every chan- nel. These data will be used to predict the final 1/3 (3 min, 20s) of recorded finger position (thumb - index - middle - ring - little) for the associated experiment.

V. EVALUATION CRITERIA
Each participating group will submit three files titled “sub1 eval”, “sub2 eval”, and “sub3 eval”, corresponding to subjects 1-3, respectively. Each of these will contain a single variable, “eval dg,” with dimensions 200,000 × 5:
• “eval dg” - this variable, in time × channels, shall give the last 1/3 (3 min, 20s) of predicted finger flexion for each of the five fingers (thumb - index - middle - ring - little) for the associated experiment (200,000 samples per finger).
The evaluation criteria will be as follows: for each sub- ject, the received variable “eval dg” will be compared with the actual finger positions in “test dg,” which we have retained. We will calculate the correlation coefficient r between the actual and the predicted finger flexions for each subject and finger. We will not calculate the correlation coefficient for the 4th (ring) finger, because the flexion of this finger was typically correlated with the flexion of the 3rd (middle) or 5th (little) finger. The variable for predicted position should still be of dimension 200,000 × 5 (i.e., the 4th column will not be used for evaluation). The final score will be calculated as the arithmetic mean of the 12 correlation coefficients (4 per subject, 3 subjects). The submission with the highest score wins the competition.


VI. SOME THINGS TO KEEP IN MIND...
• The lag between the dataglove position measure- ment recording and the amplifier measurement is 37ms (± 3ms, SEM). This is of the same order of granularity in the dataglove position (which was sampled at 25Hz - every 40ms).
• There is a characteristic delay between brain activ- ity and resulting finger movement. You may want to take this into account.
• Please cite [2] when you use this dataset in a pub- lication.



