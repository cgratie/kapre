# kapre
Keras audio PREprocessing

Written by Keunwoo Choi

# Install
```bash
$ git clone https://github.com/keunwoochoi/kapre.git
cd kapre
$ pip install .
```

# Usage

## STFT
```python
from keras.models import Sequential
from kapre.TimeFrequency import Spectrogram

# stereo channel, maybe 1-sec audio signal
input_shape = (2, 44100) 
sr = 44100
model = Sequential()
# A "power-spectrogram in decibel scale" layer
model.add(Spectrogram(n_dft=512, n_hop=256, input_shape=src_shape, 
                      return_decibel=True, power=2.0, trainable=False,
                      name='trainable_stft'))
# Then add your model
# model.add(some convolution layers...)
```

## Mel-spectrogram
```python
from keras.models import Sequential
from kapre.TimeFrequency import Melspectrogram

# 6 channels (!), maybe 1-sec audio signal
input_shape = (6, 44100) 
sr = 44100
model = Sequential()
# A "amplitude mel-spectrogram in decibel scale" layer
model.add(Melspectrogram(n_dft=512, n_hop=256, input_shape=src_shape, 
                         return_decibel=True, power=1.0, trainable=False,
                         name='trainable_stft'))
# Then add your model
# model.add(some convolution layers...)
```

