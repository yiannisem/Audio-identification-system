# Audio-identification-system

Description
----------

This repository contains the implementation of an audio identification system, developed as part of the Music Informatics module for the MSc Sound and Music Computing programme at Queen Mary University of London.

The aim of the project is to identify matching tracks in a database given a noisy audio excerpt. This is done with a fingerprinting-based approach that uses constellation maps to represent tracks, and shifted inverted lists to cut down on the computational cost of searching for matches (the method is explained thoroughly in the accompanying written report).


Project Structure
----------------

MI coursework 2 code.ipynb: The main implementation in Jupyter Notebook form.

database_recordings/: Folder containing 200 clean audio files (30 seconds, 22050 Hz).

query_recordings/: Folder containing 213 noisy audio excerpts (10 seconds, 44100 Hz).

output.txt: Example output file with the top 3 matches for each query.

MI_Coursework_2_report.pdf: Full report describing the method, evaluation, and findings.


How to Run
----------

Ensure you are using Python 3 with standard libraries, including:

- numpy
- scipy
- librosa
- scikit-image

To generate the fingerprint database:

```
fingerprintBuilder('/path/to/database/', '/path/to/fingerprints/')
```

To perform identification:

```
audioIdentification('/path/to/queryset/', '/path/to/fingerprints/', '/path/to/output.txt')
```

Each line in output.txt will look like:

```
query001.wav    dbmatch01.wav    dbmatch02.wav    dbmatch03.wav
```


Evaluation
----------

Hyperparameter tuning revealed the following:

Top-1 Accuracy: up to 78.40%

Top-3 Accuracy: up to 82.16%

Pop tracks are consistently easier to identify than classical, likely due to sharper note-attacks.

Removing frequency bin hashing improves accuracy but increases runtime.

