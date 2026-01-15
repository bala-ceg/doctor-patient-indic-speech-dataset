## Doctor–Patient Indic Speech Dataset

Multilingual doctor–patient conversational speech dataset intended for research in automatic speech recognition (ASR), speaker diarization, translation, and spoken-language understanding for Indic languages.

## Supported languages
- Tamil
- Hindi
- Telugu
- Malayalam
- Kannada
- Marathi
- Gujarati
- Bengali
- Punjabi

## Summary
- Natural, two-speaker (Doctor + Patient) clinic dialogues.
- Audio: per-conversation MP3 files.
- Transcripts: plain-text transcripts (UTF-8), in the native language and a corresponding English transcript for each conversation.
- License: CC BY 4.0 (Creative Commons Attribution 4.0 International).

## Repository structure
- audio/<language>/convo_001.mp3
  - Example: `audio/hindi/convo_001.mp3`
- transcripts/<language>/convo_001.txt
  - Native-language transcript for the conversation.
  - Example: `transcripts/kannada/convo_001.txt`
- transcripts/english/convo_001.txt
  - English transcripts (parallel where available).
- README.md
  - This file.
- (Other files/folders may be present — please inspect repository root for additions.)

## File formats and encoding
- Audio: MP3 (mono or stereo — check individual files). Sample rates may vary; convert as needed for downstream toolchains.
- Transcripts: UTF-8 plain text. Each `convo_*.txt` contains the full conversational transcript. There is no strict timestamp markup (timestamps are not provided in the current dataset).

## Typical dataset layout example
- audio/hindi/convo_001.mp3
- transcripts/hindi/convo_001.txt
- transcripts/english/convo_001.txt

## Intended use cases
- Train/test ASR systems for Indic languages.
- Cross-lingual experiments using English parallel transcripts.
- Speaker diarization and turn-taking analysis (two speakers: doctor and patient).
- Natural language understanding in health-care conversational contexts.
- Data augmentation and transfer learning for low-resource languages.

## How to use (examples)
1. Clone the repository:
   git clone https://github.com/bala-ceg/doctor-patient-indic-speech-dataset.git

2. Inspect available languages and files:
   ls audio
   ls transcripts

3. Convert audio (example using ffmpeg) to WAV 16kHz mono for ASR training:
   ffmpeg -i audio/hindi/convo_001.mp3 -ar 16000 -ac 1 audio/hindi/convo_001_16k.wav

4. Preprocessing transcripts:
   - Confirm UTF-8 encoding.
   - Normalize punctuation and whitespace as required by your tokenizer/ASR pipeline.
   - If using forced-alignment or training, you may need to create per-utterance segmentations and speaker labels.

## Notes and caveats
- Speaker labels: Conversations are two-speaker dialogues (Doctor vs Patient). The provided transcripts may not include explicit per-line speaker markers; you may need to add speaker-turn annotations if required by your workflow.
- Timestamps: There are no fine-grained timestamps included. If you need turn-level alignments, perform forced alignment with an ASR/alignment tool.
- Data quality: Transcripts appear to be natural conversational text in each language. Inspect examples in `transcripts/<language>/` to confirm orthography and punctuation conventions for your use case.
- Privacy & ethics: These are simulated/natural dialogues intended for research. Ensure your intended use complies with the dataset license and ethical guidelines for clinical data research.

## License
- This dataset is licensed under the Creative Commons Attribution 4.0 International (CC BY 4.0) license.
- Link: https://creativecommons.org/licenses/by/4.0/

## How to cite
If you use this dataset in academic work, please cite the repository and its authors. Example (modify as needed):

    Balaji Seetharaman. Doctor–Patient Indic Speech Dataset. https://github.com/bala-ceg/doctor-patient-indic-speech-dataset. CC BY 4.0.

(If there is a paper or DOI associated with the dataset, please include full bibliographic details here.)

## Contributing
- Contributions are welcome: add more dialogues, fix transcripts, add timestamps, or include speaker-turn annotations.
- Suggested workflow:
  - Fork the repo
  - Add or update data and include a short description file for additions
  - Open a pull request describing changes
- Please follow license terms when adding external material.

## Contact & acknowledgements
- Repository owner: bala-ceg (GitHub)
- For questions or data-use permissions beyond CC BY 4.0, open an issue in this repository or contact the maintainer via their GitHub profile.

## Acknowledgements
- Thanks to contributors and annotators who prepared the multilingual medical dialogues.
- This dataset aims to help research in multilingual ASR and health-care conversational AI for Indic languages.

## Versioning & provenance
- Check commit history for provenance of data files.
- If you require a specific snapshot (commit SHA), use the repository tag or commit when cloning:
  git clone --branch <branch-or-tag> --single-branch <repo-url>

## Further work I can do
- Add per-utterance/turn-level speaker labels and example TSV manifest for common ASR toolkits.
- Create sample preprocessing and data-loading scripts for frameworks such as Kaldi, ESPnet, or Hugging Face.
- Create a CITATION.cff if you want a machine-readable citation.
