Deep Speech model with Catalan
------------------------------


DeepSpeech version: 0.7.0-alpha.2

* [output_graph.pb](https://storage.googleapis.com/stashify-static/deepspeech_cat/output_graph.pb)

* [output_graph.tflite](https://storage.googleapis.com/stashify-static/deepspeech_cat/output_graph.tflite)

* [output_graph.pbmm](https://storage.cloud.google.com/stashify-static/deepspeech_cat/output_graph.pbmm)

* [kenlm.scorer](https://storage.googleapis.com/stashify-static/deepspeech_cat/kenlm.scorer)

* [best_dev-1298770.meta](https://storage.cloud.google.com/stashify-static/deepspeech_cat/best_dev-1298770.meta)

* [best_dev-1298770.data-00000-of-00001](https://storage.cloud.google.com/stashify-static/deepspeech_cat/best_dev-1298770.data-00000-of-00001)

* [alphabet.txt](https://storage.googleapis.com/stashify-static/deepspeech_cat/alphabet.txt)

Training with more Data:
========================

TF_FORCE_GPU_ALLOW_GROWTH=true python -u DeepSpeech.py --noearly_stop --alphabet_config_path alphabet.txt --load_train auto --train_files  train.csv --train_batch_size 8  --dev_files  dev.csv --dev_batch_size 8 --test_files test.csv --test_batch_size 8 --checkpoint_dir checkpoints/ --train_cudnn --n_hidden 2048 --epochs 40 --learning_rate 0.0001 --export_dir export/ --export_tflite --scorer_path kenlm.scorer --augmentation_pitch_and_tempo_scaling --augmentation_freq_and_time_masking --augmentation_spec_dropout_keeprate 0.8

Predict with audio
==================
(16000 Hz wav format)

deepspeech --model output_graph.pb --scorer kenlm.scorer --audio audio.wav 

Latest Training Loss
====================

* Loss: 61.576375
* Avg WER: 0.140000
