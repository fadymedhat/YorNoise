[![license](https://img.shields.io/github/license/mashape/apistatus.svg?maxAge=2592000)](https://github.com/fadymedhat/YorNoise-for-MCLNN/blob/master/LICENSE)

# YorNoise Environmental Sounds Dataset


YorNoise is a dataset focusing on vehicle sounds (road and rail traffic) that we collected in the city of York.
Recordings were taken in different locations near traffic movements, where vehicles were either speeding or shifting 
from stationary to the speed limit near bus stops. Various types of road vehicles are recorded irrespective of the size. 
Rail traffic was collected near the rail tracks outside the train station to avoid overlapping sound from passengers 
and the station loudspeaker announcements. The rail sounds were captured for trains of different sizes and types, e.g. cargo, passengers, etc., over tracks of 
varying distances from the microphone. The time taken by the longest train to pass across a microphone is approximately 40 seconds and the shortest 20 seconds. 

## Audio Capturing
All recordings were captured by a professional recorder (TASCAM DR-40) fitted on a tripod at the height of 1 m above the ground. 
The below table lists the captured files properties.

   | Format | Sampling Rate | Channel | Word Depth| 
|:---:|:---:|:---:|:---:|
 | .wav | 44100 Hz |mono | 16 bits | 

## Dataset Editing

We listened to all the captured clips, which were 5 minutes each to validate the clips we were going to include in the 
 dataset. Sounds of 4 seconds in duration were found to be sufficient for the human to distinguish environmental sounds as studied 
 in [1]. Accordingly, all validated files were split into 4-second clips. We listened to all the 4 second files and 
 dropped the ones that are less than 4 seconds or silent. The filtered files were further redistributed into 10-folds. 
 The folds distribution considered that all 4-second clips belonging to the same original 5 minutes file reside in the same fold 
 to avoid contaminating the folds with sounds from the same origin and consequently biasing the testing accuracy. 
 
 A summary of the dataset is listed below:

| Total samples | Clip Duration | Folds | Rail samples | Traffic samples | 
|:---:|:---:|:---:|:---:|:---:|
|1527 | 4 secs | 2 | 10 | 620 | 907 |
 
  The details of the dataset are listed 
 in Table ‎7.28. The parameters used for the model, and the training complexity statistics are captured in Table ‎7.29.
 
 
 The sound recordings were captured by a professional recorder (TASCAM DR-40) fitted on a tripod at the height of 1 m.
 The dataset was recorded at a sampling rate of 44 kHz with a mono channel, and a word depth of 16 bits. 
 







 

The [YorNoise](https://github.com/fadymedhat/YorNoise) environmental sound dataset.

| Clip Duration  | Format | Count | Categories|
|:---:|:---:|:---:|:---:|
| 4 secs | .wav | 1527 | 2 |

Dataset Summary:
 * Clips are 4-seconds in length with 44100 Hz sampling rates.
 * The dataset is released into predefined 10-fold splits for cross-validation.
 * It is combined through the experiments with the [UrbanSound8k](https://urbansounddataset.weebly.com/urbansound8k.html) dataset to form a 12-classes dataset.  

 
 This folder contains:
  * Scripts required to prepare the UrbanSound8k dataset for the MCLNN processing.
  * Pretrained weights and indices for the 10-fold cross-validation in addition to the standardization parameters 
  to replicate the results in:
 
    _Fady Medhat, David Chesmore and John Robinson, "Recognition of Acoustic Events Using Masked Conditional Neural Networks," 2017 16th IEEE International Conference on Machine Learning and Applications (ICMLA)_
 
 ## Prepossessing
 
The preprocessing involved in preparing the YorNoise dataset is resampling to 22050 Hz.

#### Preparation scripts prerequisites

The [preparation scripts](https://github.com/fadymedhat/YorNoise-for-MCLNN/tree/master/YorNoise_preparation_scripts) require the following packages to be installed beforehand:
   * [ffmpeg](https://www.ffmpeg.org/) version N-81489-ga37e6dd
   * numpy 1.11.2+mkl
   * librosa 0.4.0
   * h5py 2.6.0yornoise_storage_ordering.txt
 
#### Steps
1. Download the [UrbanSound8k](https://urbansounddataset.weebly.com/urbansound8k.html) and execute its preprocessing scripts in the [preparation scripts](https://github.com/fadymedhat/UrbanSound8K-for-MCLNN/tree/master/UrbanSound8K_preparation_scripts) following the order of their labels.
1. Download the [YorNoise](https://github.com/fadymedhat/YorNoise) dataset and execute the scripts in the [preparation scripts](https://github.com/fadymedhat/YorNoise-for-MCLNN/tree/master/YorNoise_preparation_scripts) following the order of their labels.
2. Make sure the files are ordered following the [YorNoise_storage_ordering](https://github.com/fadymedhat/YorNoise-for-MCLNN/blob/master/yornoise_storage_ordering.txt) file.
3. Configure the spectrogram transformation within the [Dataset Transformer](https://github.com/fadymedhat/MCLNN/tree/master/dataset_transformer) and generate the MCLNN-Ready hdf5 for the dataset using the [YorNoiseUrbansound8k_MCLNN.csv](https://github.com/fadymedhat/YorNoise-for-MCLNN/blob/master/YorNoise_preparation_scripts/YorNoiseUrbanSound8KwithAdditionalColumnsForMCLNN.csv)  file





4. Generate the indices for the folds using the [Index Generator](https://github.com/fadymedhat/MCLNN/tree/master/index_generator) script.




[1] J. Salamon, C. Jacoby, and J. P. Bello, "A Dataset and Taxonomy for Urban Sound Research," in Proceedings of the 22nd ACM International Conference on Multimedia, Orlando, USA, 2014, pp. 1041-1044.