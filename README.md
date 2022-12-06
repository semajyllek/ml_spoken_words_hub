---
annotations_creators:
- machine-generated
language_creators:
- other
language:
- ar
- as
- br
- ca
- cnh
- cs
- cv
- cy
- de
- dv
- el
- en
- eo
- es
- et
- eu
- fa
- fr
- fy
- ga
- gn
- ha
- ia
- id
- it
- ka
- ky
- lt
- lv
- mn
- mt
- nl
- or
- pl
- pt
- rm
- ro
- ru
- rw
- sah
- sk
- sl
- sv
- ta
- tr
- tt
- uk
- vi
- zh
license:
- cc-by-4.0
multilinguality:
- multilingual
size_categories:
- 10M<n<100M
source_datasets:
- extended|common_voice
task_categories:
- audio-classification
task_ids: []
pretty_name: Multilingual Spoken Words
language_bcp47:
- fy-NL
- ga-IE
- rm-sursilv
- rm-vallader
- sv-SE
- zh-CN
tags:
- other-keyword-spotting
---

# Dataset Card for Multilingual Spoken Words

## Table of Contents
- [Table of Contents](#table-of-contents)
- [Dataset Description](#dataset-description)
  - [Dataset Summary](#dataset-summary)
  - [Supported Tasks and Leaderboards](#supported-tasks-and-leaderboards)
  - [Languages](#languages)
- [Dataset Structure](#dataset-structure)
  - [Data Instances](#data-instances)
  - [Data Fields](#data-fields)
  - [Data Splits](#data-splits)
- [Dataset Creation](#dataset-creation)
  - [Curation Rationale](#curation-rationale)
  - [Source Data](#source-data)
  - [Annotations](#annotations)
  - [Personal and Sensitive Information](#personal-and-sensitive-information)
- [Considerations for Using the Data](#considerations-for-using-the-data)
  - [Social Impact of Dataset](#social-impact-of-dataset)
  - [Discussion of Biases](#discussion-of-biases)
  - [Other Known Limitations](#other-known-limitations)
- [Additional Information](#additional-information)
  - [Dataset Curators](#dataset-curators)
  - [Licensing Information](#licensing-information)
  - [Citation Information](#citation-information)
  - [Contributions](#contributions)

## Dataset Description

- **Homepage:** https://mlcommons.org/en/multilingual-spoken-words/
- **Repository:** https://github.com/harvard-edge/multilingual_kws
- **Paper:** https://datasets-benchmarks-proceedings.neurips.cc/paper/2021/file/fe131d7f5a6b38b23cc967316c13dae2-Paper-round2.pdf
- **Leaderboard:**
- **Point of Contact:**

### Dataset Summary

Multilingual Spoken Words Corpus is a large and growing audio dataset of spoken
words in 50 languages collectively spoken by over 5 billion people, for academic
research and commercial applications in keyword spotting and spoken term search,
licensed under CC-BY 4.0. The dataset contains more than 340,000 keywords,
totaling 23.4 million 1-second spoken examples (over 6,000 hours). The dataset
has many use cases, ranging from voice-enabled consumer devices to call center
automation. This dataset is generated by applying forced alignment on crowd-sourced sentence-level 
audio to produce per-word timing estimates for extraction.
All alignments are included in the dataset.

Data is provided in two formats: `wav` (16KHz) and `opus` (48KHz). Default configurations look like 
`"{lang}_{format}"`, so to load, for example, Tatar in wav format do:

```python
ds = load_dataset("MLCommons/ml_spoken_words", "tt_wav")
```

To download multiple languages in a single dataset pass list of languages to `languages` argument:
```python
ds = load_dataset("MLCommons/ml_spoken_words", languages=["ar", "tt", "br"])
```

To download a specific format pass it to the `format` argument (default format is `wav`):
```python
ds = load_dataset("MLCommons/ml_spoken_words", languages=["ar", "tt", "br"], format="opus")
```
Note that each time you provide different sets of languages, 
examples are generated from scratch even if you already provided one or several of them before 
because custom configurations are created each time (the data is **not** redownloaded though).

### Supported Tasks and Leaderboards

Keyword spotting, Spoken term search

### Languages

The dataset is multilingual. To specify several languages to download pass a list of them to the
`languages` argument:

```python
ds = load_dataset("MLCommons/ml_spoken_words", languages=["ar", "tt", "br"])
```

The dataset contains data for the following languages:

Low-resourced (<10 hours):
* Arabic (0.1G, 7.6h)
* Assamese (0.9M, 0.1h)
* Breton (69M, 5.6h)
* Chuvash (28M, 2.1h)
* Chinese (zh-CN) (42M, 3.1h)
* Dhivehi (0.7M, 0.04h)
* Frisian (0.1G, 9.6h)
* Georgian (20M, 1.4h)
* Guarani (0.7M, 1.3h)
* Greek (84M, 6.7h)
* Hakha Chin (26M, 0.1h)
* Hausa (90M, 1.0h)
* Interlingua (58M, 4.0h)
* Irish (38M, 3.2h)
* Latvian (51M, 4.2h)
* Lithuanian (21M, 0.46h)
* Maltese (88M, 7.3h)
* Oriya (0.7M, 0.1h)
* Romanian (59M, 4.5h)
* Sakha (42M, 3.3h)
* Slovenian (43M, 3.0h)
* Slovak (31M, 1.9h)
* Sursilvan (61M, 4.8h)
* Tamil (8.8M, 0.6h)
* Vallader (14M, 1.2h)
* Vietnamese (1.2M, 0.1h)

Medium-resourced (>10 & <100 hours):
* Czech (0.3G, 24h)
* Dutch (0.8G, 70h)
* Estonian (0.2G, 19h)
* Esperanto (1.3G, 77h)
* Indonesian (0.1G, 11h)
* Kyrgyz (0.1G, 12h)
* Mongolian (0.1G, 12h)
* Portuguese (0.7G, 58h)
* Swedish (0.1G, 12h)
* Tatar (4G, 30h)
* Turkish (1.3G, 29h)
* Ukrainian (0.2G, 18h)

Hig-resourced (>100 hours):
* Basque (1.7G, 118h)
* Catalan (8.7G, 615h)
* English (26G, 1957h)
* French (9.3G, 754h)
* German (14G, 1083h)
* Italian (2.2G, 155h)
* Kinyarwanda (6.1G, 422h)
* Persian (4.5G, 327h)
* Polish (1.8G, 130h)
* Russian (2.1G, 137h)
* Spanish (4.9G, 349h)
* Welsh (4.5G, 108h)

## Dataset Structure

### Data Instances

```python
{'file': 'абзар_common_voice_tt_17737010.opus',
 'is_valid': True,
 'language': 0,
 'speaker_id': '687025afd5ce033048472754c8d2cb1cf8a617e469866bbdb3746e2bb2194202094a715906f91feb1c546893a5d835347f4869e7def2e360ace6616fb4340e38',
 'gender': 0,
 'keyword': 'абзар',
 'audio': {'path': 'абзар_common_voice_tt_17737010.opus',
  'array': array([2.03458695e-34, 2.03458695e-34, 2.03458695e-34, ...,
         2.03458695e-34, 2.03458695e-34, 2.03458695e-34]),
  'sampling_rate': 48000}}
```

### Data Fields

* file: strinrelative audio path inside the archive
* is_valid: if a sample is valid
* language: language of an instance. Makes sense only when providing multiple languages to the 
dataset loader (for example, `load_dataset("ml_spoken_words", languages=["ar", "tt"])`)
* speaker_id: unique id of a speaker. Can be "NA" if an instance is invalid
* gender: speaker gender. Can be one of `["MALE", "FEMALE", "OTHER", "NAN"]`
* keyword: word spoken in a current sample
* audio: a dictionary containing the relative path to the audio file, 
the decoded audio array, and the sampling rate. 
Note that when accessing the audio column: `dataset[0]["audio"]` the audio file is automatically 
decoded and resampled to `dataset.features["audio"].sampling_rate`. Decoding and resampling of 
a large number of audio files might take a significant amount of time. 
Thus, it is important to first query the sample index before the "audio" column, 
i.e. `dataset[0]["audio"]` should always be preferred over `dataset["audio"][0]`

### Data Splits

The data for each language is splitted into train / validation / test parts.

## Dataset Creation

### Curation Rationale

[More Information Needed]

### Source Data

#### Initial Data Collection and Normalization

The data comes form Common Voice dataset.

#### Who are the source language producers?

[More Information Needed]

### Annotations

#### Annotation process

[More Information Needed]

#### Who are the annotators?

[More Information Needed]

### Personal and Sensitive Information

he dataset consists of people who have donated their voice online. 
You agree to not attempt to determine the identity of speakers.

## Considerations for Using the Data

### Social Impact of Dataset

[More Information Needed]

### Discussion of Biases

[More Information Needed]

### Other Known Limitations

[More Information Needed]

## Additional Information

### Dataset Curators

[More Information Needed]

### Licensing Information

The dataset is licensed under [CC-BY 4.0](https://creativecommons.org/licenses/by/4.0/) and can be used for academic
research and commercial applications in keyword spotting and spoken term search.

### Citation Information

```
@inproceedings{mazumder2021multilingual,
  title={Multilingual Spoken Words Corpus},
  author={Mazumder, Mark and Chitlangia, Sharad and Banbury, Colby and Kang, Yiping and Ciro, Juan Manuel and Achorn, Keith and Galvez, Daniel and Sabini, Mark and Mattson, Peter and Kanter, David and others},
  booktitle={Thirty-fifth Conference on Neural Information Processing Systems Datasets and Benchmarks Track (Round 2)},
  year={2021}
}
```

### Contributions

Thanks to [@polinaeterna](https://github.com/polinaeterna) for adding this dataset.
