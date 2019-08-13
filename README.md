# Mueller-Model

## Goal

Train an RNN on the non-redacted text in the Mueller Report then use that model to attempt to predict what was redacted.

## Notes

- Eager Execution mode was not ideal for this project. I chose it as this was my first full project in TF and Eager Execution seemed easier to grasp than the graph based approach.
    - During training, model sizes were picked essentially by picking the largest model that wouldn't result in a ResourceExhausted error. 

- The overall flow originally came from [this](https://github.com/tensorflow/docs/blob/master/site/en/r2/tutorials/text/text_generation.ipynb) TensorFlow tutorial if you'd like more information on text generation. 

- Below are links to some pretrained versions I put on Google Drive. Feel free to download them as a jumping off point. The network configurations are in the notebook. 
  - [400 sequence length](https://drive.google.com/open?id=159SND9AsZSF8wOt_GVVl_uLFIkynzizs)
  - [750 sequence length](https://drive.google.com/open?id=123wOXo1rBl420RfZ2fD1j3DYdohNIROG)

## To Do

- Rewrite V2 without Eager Execution to allow for more parallelization of training, longer and bigger training runs and less random memory errors.

- Play with preceding characters for predictions.
    - I think setting the preceding characters so:
        _(length of the redaction + preceding characters) = (sequence_length the model is trained on)_ would be good for normalizing the predictors and the test data but its difficult with a low ceiling on the sequence_length

- Descend lower...
    - Obvious but I could only achieve a loss of ~1 with my current model. This caused the generated text to less realistic than it could have been.
    - It may require the "non-Eager" rework in order to expand the model to descend lower.
