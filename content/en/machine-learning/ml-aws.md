---
title: Machine Learning at AWS
---

## AWS Service Overview

### General Purpose Machine Learning Services
- Amazon Elastic Inference - attach GPU acceleration to Amazon
  instances:
  <https://aws.amazon.com/machine-learning/elastic-inference/>
- Amazon SageMaker - general purpose machine learning:
  <https://aws.amazon.com/sagemaker/>
- AWS Deep Learning AMI (DLAMI) - Linux with Deep Learning
  Hardware (AMI = Amazon Machine Image)
    - <https://aws.amazon.com/machine-learning/amis/>
    - <https://docs.aws.amazon.com/dlami/latest/devguide/what-is-dlami.html>

### Text and Speech Services
- Amazon Polly - text to speech service (blackbox):
  <https://aws.amazon.com/polly/>
- Amazon Comprehend - natural language processing (NLP) service
  (blackbox): <https://aws.amazon.com/comprehend/>
- Amazon Lex - Chat like Alexa (speech recognition and natural
  language understanding): <https://aws.amazon.com/lex/>
- Amazon Textract - extract text and data from scanned documents
  (blackbox): <https://aws.amazon.com/textract/>
- Amazon Transcribe - speech to text (blackbox):
  <https://aws.amazon.com/transcribe/>
- Amazon Translate - neural machine translation service
  (blackbox): <https://aws.amazon.com/translate/>

### Image and Video Services
- Amazon Rekognition - image and video analysis (blackbox):
  <https://aws.amazon.com/rekognition/>

### Toy Services
- AWS DeepLens - deep learning video camera (toy):
  <https://aws.amazon.com/deeplens/>
- AWS DeepRacer - autonomous deep learning 1/18th scale car (toy):
  <https://aws.amazon.com/deepracer/>

### Other Services
- Amazon Forecast - time-series forecasting service (blackbox):
  <https://aws.amazon.com/forecast/>
- Amazon Personalize - personalization and recommendation
  (blackbox): <https://aws.amazon.com/personalize/>
- Amazon SageMaker Ground Truth - manual labeling tools:
  <https://aws.amazon.com/sagemaker/groundtruth/>
- Amazon SageMaker Neo - compile models for speed and low memory
  footprint: <https://aws.amazon.com/sagemaker/neo/>

## SageMaker Links
- [Amazon SageMaker 10-Minute
  Tutorial](https://aws.amazon.com/blogs/machine-learning/category/artificial-intelligence/sagemaker/?sc_icampaign=pac-sagemaker-blogpost&sc_ichannel=ha&sc_icontent=awssm-2276&sc_iplace=console-right&trk=ha_awssm-2276)
- [Amazon SageMaker Technical
  deep-dive](https://aws.amazon.com/getting-started/tutorials/build-train-deploy-machine-learning-model-sagemaker/?sc_icampaign=pac-sagemaker-console-tutorial&sc_ichannel=ha&sc_icontent=awssm-2276&sc_iplace=console-body&trk=ha_awssm-2276)
- [Learn fundamentals and deep dive into Amazon SageMaker
  algorithmsLearn
  more](https://www.youtube.com/playlist?list=PLhr1KZpdzukcOr_6j_zmSrvYnLUtgqsZz&sc_icampaign=YT_deep-dive&sc_icontent=awssm-2747&sc_iplace=console-sagemaker-learning)
- [SageMaker - Developer Guide - Get
  Started](https://docs.aws.amazon.com/sagemaker/latest/dg/gs.html)

## Python API
- [Boto 3 Documentation](https://boto3.readthedocs.io)

## Services
- P3 (V100 GPU): <https://aws.amazon.com/de/ec2/instance-types/p3/>
- P2 (K80 GPU): <https://aws.amazon.com/de/ec2/instance-types/p2/>
- G3 (M60 GPU): <https://aws.amazon.com/de/ec2/instance-types/g3/>

## Performance Experiment with EC2 and LightGBM
Given:
- LightGBM Classification
- x_train.shape (13788428, 30)
- x_val.shape (2433253, 30)
- y_train.shape (13788428,)
- y_val.shape (2433253,)
- num_classes: 401
- num_boost_round: 4

Results:
- c5.24xlarge, 4,656 $/h, 96 vCPUs, 2nd Gen Intel Xeon Platinum
  8275CL, 3.6 GHz, 192 GiB RAM, time: 512 s
- m5.8xlarge, 1,84 $/h, 32 vCPUs, Intel Xeon Platinum 8175, 3.1 GHz,
  128 GiB RAM, time: 574 s
- r5.4xlarge, 1,216 $/h, 16 vCPUs, Intel Xeon Platinum 8175, 3.1 GHz,
  128 GiB RAM, time: 763 s
- other server, 4 (8) CPUs, Xeon W-2123, 3.6 GHz, 128 GiB RAM, time:
  856 s

## Connect
- Convert Key:
  <https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/putty.html>