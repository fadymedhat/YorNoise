
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

| Total samples | Clip Duration | Classes  | Folds | Rail samples | Traffic samples | 
|:---:|:---:|:---:|:---:|:---:|:---:|
|1527 | 4 secs |2 | 10 | 620 | 907 |
 
## Metda-data .csv
  The YorNoise dataset can be used on its own or as additional two classes to the 
  [UrbanSound8K](https://urbansounddataset.weebly.com/urbansound8k.html) dataset.
   The UrbanSound8K is a dataset of 10 environmental sounds pressigned into 10-folds with a total of 8732 sound file of 4 seconds each.
   YorNoise follows the exact clip arrangements of the UrbanSound8k to be compatible with it for combined experiments of both datasets.
    The YorNoise_UrbanSound8K.csv follows the original metadata file of the UrbanSound8k dataset with the additional inclusion of 
     The YorNoise fold splits and relevant columns. Below are the relevant columns for the rest of the columns please refer to the 
        [UrbanSound8K](https://urbansounddataset.weebly.com/urbansound8k.html).
     

* __dataset_seq :__ the file id across both datasets combined [0, 10258]
* __per_class_seq :__ the id of the file across other files in the same category (zero-indexed)
* __fold :__ fold id of a file [1, 10] (10 folds for cross-validation)
* __classID :__ the class id for the combined datasets [0, 11]. Classes of id from 0 to 9 belong to UrbanSound8k and ids 10 and 11 are of YorNoise. 
    * 0 = air_conditioner
    * 1 = car_horn
    * 2 = children_playing
    * 3 = dog_bark
    * 4 = drilling
    * 5 = engine_idling
    * 6 = gun_shot
    * 7 = jackhammer
    * 8 = siren
    * 9 = street_music
    * 10 = rail
    * 11 = traffic
    


## Citing YorNoise
If you are using YorNoise dataset in your research, please cite:

> Fady Medhat, David  Chesmore and John Robinson, **Masked Conditional Neural Networks for Environmental Sound 
> Classification**, *Artificial Intelligence XXXIV*. SGAI, 2017.
>
> <a href="https://arxiv.org/ftp/arxiv/papers/1805/1805.10004.pdf"><img src="https://img.shields.io/badge/download-.pdf-blue.svg" alt="download paper" title="download paper" align="right" /></a>
> [DOI: https://doi.org/10.1007/978-3-319-71078-5_2]

## License
 <a rel="license" href="http://creativecommons.org/licenses/by-nc/3.0/"><img alt="Creative Commons License" style="border-width:0" src="https://i.creativecommons.org/l/by-nc/3.0/88x31.png" /></a><br />This work is licensed under a <a rel="license" href="http://creativecommons.org/licenses/by-nc/3.0/">Creative Commons Attribution-NonCommercial 3.0 Unported License</a>.

## References

[1] J. Salamon, C. Jacoby, and J. P. Bello, "A Dataset and Taxonomy for Urban Sound Research," in Proceedings of the 22nd ACM International Conference on Multimedia, Orlando, USA, 2014, pp. 1041-1044.