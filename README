[![Paper DOI](https://img.shields.io/badge/Paper-10.1109/TNSRE.2021.3082551-blue)](https://doi.org/10.1109/TNSRE.2021.3082551)
[![PhysioNet](https://img.shields.io/badge/PhysioNet-hd--semg%2F1.0.0-green)](https://physionet.org/content/hd-semg/1.0.0/)
[![License](https://img.shields.io/badge/License-ODC--By--1.0-lightgrey)](https://opendatacommons.org/licenses/by/1-0/)

# HySER: High-Density Surface Electromyogram Recordings

BIDS-formatted version of the Hyser Surface EMG for Hand Gesture Recognition dataset (Jiang et al., 2021). 20 subjects performed 5 task types across 2 sessions using 256-channel high-density surface EMG (HD-sEMG) with simultaneous 5-finger force recordings.

## Subjects

20 right-handed participants (12M, 8F; age 21-34). Two sessions per subject separated by 3-25 days. Demographics in `participants.tsv`.

## Tasks

| Task | BIDS label | Description | Trials |
|------|-----------|-------------|--------|
| Pattern Recognition | `gesture01`-`gesture34` | 34 discrete hand gestures (Table I in paper) | 2 per gesture, each with 3 dynamic + 1 maintenance |
| Maximum Voluntary Contraction | `mvc` | MVC flexion/extension per finger | 2 per finger, 10s each |
| Single Finger (1-DOF) | `singlefinger` | Triangle force trajectory, individual fingers | 3 per finger, 25s each |
| Multi-Finger (N-DOF) | `multifinger` | Simultaneous multi-finger force tracking | 2 per combination, 25s each |
| Random | `random` | Free finger contractions at any force | 5 trials, 25s each |

## Equipment

- **EMG system:** Quattrocento (OT Bioelettronica, Torino, Italy), 2048 Hz, gain 150, 16-bit ADC
- **Electrodes:** Four 8x8 gelled elliptical arrays (5mm x 2.8mm), 10mm inter-electrode distance
- **Placement:** Two arrays on extensors (distal/proximal), two on flexors (distal/proximal) of right forearm
- **Reference:** Olecranon (elbow); Ground: head of ulna (right leg drive)
- **Hardware filters:** HP 10 Hz (2nd order), LP 500 Hz
- **Force sensors:** SAS + HSGA (Huatran, Shenzhen, China), 100 Hz, 5 fingers

## File Organization

- `*_emg.bdf` - 256-channel EMG data (BDF format)
- `*_physio.tsv.gz` - 5-finger force data (non-PR tasks only)
- `*_channels.tsv` - Channel metadata with electrode mapping (`signal_electrode` column)
- `*_electrodes.tsv` - Electrode positions in local grid coordinates (mm)
- `*_events.tsv` - Event markers (gesture trials or segment boundaries)

Non-PR tasks (MVC, singlefinger, multifinger, random) are merged from multiple original recordings into single files per session, with boundary events marking segment junctions.

## Coordinate Systems

Four local grid systems (`space-ed`, `space-ep`, `space-fd`, `space-fp`) in mm, anchored to a parent forearm system (`space-forearm`) in anatomical percent coordinates. See `space-*_coordsystem.json` files.

## Missing Data

6 gesture recordings absent in source dataset (not conversion failures):
sub-01/ses-2/gesture25, sub-03/ses-1/gesture04, sub-03/ses-2/gesture04, sub-05/ses-1/gesture34, sub-11/ses-1/gesture08, sub-19/ses-2/gesture11.

## Conversion

Converted using EMG-2-BIDS (EEGLAB + bids-matlab-tools). Data integrity verified: mean Pearson correlation >0.9999 between original WFDB and converted BDF across all 1514 recordings. See `dataset_description.json` for generator details.
