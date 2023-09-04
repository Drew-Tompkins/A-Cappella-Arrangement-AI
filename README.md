# A-Cappella-Arrangement-AI
An LSTM-based seq2seq encoder-decoder model trained to convert audio data into A Cappella arrangements. The input is processed audio data in the form of piano roll data, and the output is a corresponding A Cappella arrangement in the form of a MIDI file.

## Table of Contents
- [Data](#data)
- [Model Architecture](#model-architecture)
- [Results](#results)
- [Contributing](#contributing)
- [License](#license)

## Data
- **Source**: This model was trained on input data in the form of the audio of pop songs and target data in the form of the midi files of each song's a cappella arrangement.
- **Preprocessing**: Audio files were preprocessed by first using an open-source audio to midi converter. Both the pop song and a cappella MIDI files were then converted to piano roll format and stored in a NumPy array.

## Model Architecture

### Hyperparameters
- **Number of Notes**: 128
- **Units in LSTM**: 64
- **Number of LSTM Layers**: 2
- **Chunk Length**: 1000

### Encoder
- **Input Shape**: (num_notes, chunk_length) or (128, 1000)
- **LSTM Layer**: 64 units, returns states
- **Outputs**: Encoder states (state_h, state_c)

### Decoder
- **Input Shape**: (num_notes, chunk_length) or (128, 1000)
- **LSTM Layer**: 64 units, returns sequences, and states
- **TimeDistributed Dense Layer**: Output shape matches target size, linear activation
- **Initial State**: Encoder states

### Compilation
- **Optimizer**: Adam
- **Loss Function**: Mean Squared Error (MSE)

To get a summary of the model architecture, you can run `model.summary()` in your code.


## Results
As this is version 1 of this project and a proof of concept, results were expectedly preliminary but promising.

## Contributing
Feel free to fork the project and submit a pull request with your changes!

## License
This project is licensed under the [MIT License](LICENSE).
