# A Sign Language Deepfake Dataset

<div align="center">
    <img src="assets/Fig7.png">
    <p></p>
</div>

<div align="center">
    <a href="https://github.com/ControlNet/AV-Deepfake1M/issues">
        <img src="https://img.shields.io/github/issues/ControlNet/AV-Deepfake1M?style=flat-square">
    </a>
    <a href="https://github.com/SLDF/network/members">
        <img src="https://img.shields.io/github/forks/SLDF?style=flat-square">
    </a>
    <a href="https://github.com/SLDF/stargazers">
        <img src="https://img.shields.io/github/stars/SLDF?style=flat-square">
    </a>
    <a href="https://github.com/SLDF/blob/master/LICENSE">
        <img src="https://img.shields.io/badge/license-CC%20BY--NC%204.0-97ca00?style=flat-square">
    </a>
    <a href="https://arxiv.org/abs/2311.15308">
        <img src="https://img.shields.io/badge/arXiv-2311.15308-b31b1b.svg?style=flat-square">
    </a>
</div>

This is the official repository for the paper 
[Generation and Detection of Sign Language Deepfakes - A Linguistic and Visual Analysis](http://arxiv.org/abs/2311.15308).

## Abstract
A question in the realm of deepfakes is slowly emerging pertaining to whether we can go beyond
facial deepfakes and whether it would be beneficial to society. Therefore, this research presents a positive
application of deepfake technology in upper body generation, while performing sign-language
for the Deaf and Hard of Hearing (DHoH) community. The resulting videos are later vetted with
a sign language expert. This is particularly helpful, given the intricate nature of sign language, a
scarcity of sign language experts, and potential benefits for health and education. The objectives of
this work encompass constructing a reliable deepfake dataset, evaluating its technical and visual credibility
through computer vision and natural language processing models, and assessing the plausibility
of the generated content. With over 1200 videos, featuring both previously seen and unseen individuals
for the generation model, using the help of a sign language expert, we establish a deepfake dataset
in sign language that can further be utilized to detect fake videos that may target certain people of
determination. The expert annotations reveal that the generated fake videos are comparable to real
sign language videos.Linguistic analysis, employing textual similarity scores and interpreter evaluations,
reveals promising similarity between authentic and fraudulent sign language videos where in
the interpretation of a fake is atleast 90% the same as the real video. Visual analysis demonstrates
that visually convincing deepfake videos can be produced, even with entirely new subjects using our
approach. Leveraging a pose/style transfer model for video generation, our method pays meticulous
attention to detail, producing hands in a manner that allows interpretability, while closely matching
the driving video. We further apply machine learning algorithms to establish a baseline performance
on the dataset for deepfake detection.

## Dataset

### Download

### Baseline Benchmark

Specificity | Sensitivity | Accuracy
0.9091 0.8030 0.8384

| Method                     | AP@0.5 | AP@0.75 | AP@0.9 | AP@0.95 | AR@50 | AR@20 | AR@10 | AR@5  |
|----------------------------|--------|---------|--------|---------|-------|-------|-------|-------|
| PyAnnote                   | 00.03  | 00.00   | 00.00  | 00.00   | 00.67 | 00.67 | 00.67 | 00.67 |
| Meso4                      | 09.86  | 06.05   | 02.22  | 00.59   | 38.92 | 38.81 | 36.47 | 26.91 |
| MesoInception4             | 08.50  | 05.16   | 01.89  | 00.50   | 39.27 | 39.00 | 35.78 | 24.59 |
| EfficientViT               | 14.71  | 02.42   | 00.13  | 00.01   | 27.04 | 26.43 | 23.90 | 20.31 |
| TriDet + VideoMAEv2        | 21.67  | 05.83   | 00.54  | 00.06   | 20.27 | 20.12 | 19.50 | 18.18 |
| TriDet + InternVideo       | 29.66  | 09.02   | 00.79  | 00.09   | 24.08 | 23.96 | 23.50 | 22.55 |
| ActionFormer + VideoMAEv2  | 20.24  | 05.73   | 00.57  | 00.07   | 19.97 | 19.81 | 19.11 | 17.80 |
| ActionFormer + InternVideo | 36.08  | 12.01   | 01.23  | 00.16   | 27.11 | 27.00 | 26.60 | 25.80 |
| BA-TFD                     | 37.37  | 06.34   | 00.19  | 00.02   | 45.55 | 35.95 | 30.66 | 26.82 |
| BA-TFD+                    | 44.42  | 13.64   | 00.48  | 00.03   | 48.86 | 40.37 | 34.67 | 29.88 |
| UMMAFormer                 | 51.64  | 28.07   | 07.65  | 01.58   | 44.07 | 43.45 | 42.09 | 40.27 |


### Metadata Structure

The metadata is a json file for each subset (train, val), which is a list of dictionaries. The fields in the dictionary are as follows.
- file: the path to the video file.
- original: if the current video is fake, the path to the original video; otherwise, the original path in VoxCeleb2.
- split: the name of the current subset.
- modify_type: the type of modifications in different modalities, which can be ["real", "visual_modified", "audio_modified", "both_modified"]. We evaluate the deepfake detection performance based on this field.
- audio_model: the audio generation model used for generating this video.
- fake_segments: the timestamps of the fake segments. We evaluate the temporal localization performance based on this field.
- audio_fake_segments: the timestamps of the fake segments in audio modality.
- visual_fake_segments: the timestamps of the fake segments in visual modality.
- video_frames: the number of frames in the video.
- audio_frames: the number of frames in the audio.

## License

The dataset is under the [EULA](eula.pdf). You need to agree and sign the EULA to access the dataset.

The other parts of this project is under the CC BY-NC 4.0 license. See [LICENSE](LICENSE) for details.

## References

If you find this work useful in your research, please cite it.

```bibtex
@article{cai2023avdeepfake1m,
  title = {AV-Deepfake1M: A Large-Scale LLM-Driven Audio-Visual Deepfake Dataset},
  action = {Cai, Zhixi and Ghosh, Shreya and Adatia, Aman Pankaj and Hayat, Munawar and Dhall, Abhinav and Stefanov, Kalin},
  journal = {arXiv preprint arXiv:2311.15308},
  year = {2023},
}
```
