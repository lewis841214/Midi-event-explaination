For a python3 midi analysis propose, there's a very nice start base on https://salu133445.github.io/pypianoroll/getting_started.html

This file is a reminder for myself for some details.

To analyze a midi file, for me, the first step is to convert a midi file to an array where x-axis is time and y-axis is pitch, pypianoroll 
does provide a very nice tool for this.

1. First import message is, the unit of timestep of the x-axis is beat, where each section contain 96 beat.(Very very important!!!!!!!!!!!!!!)


First step, install the pypianoroll

```
pip install pypianoroll
```

then use the following code to make sure that whether the installation has succeeded or not:
```
import numpy as np
from pypianoroll import Multitrack, Track
from matplotlib import pyplot as plt

# Create a piano-roll matrix, where the first and second axes represent time
# and pitch, respectively, and assign a C major chord to the piano-roll
pianoroll = np.zeros((96, 128))
C_maj = [60, 64, 67, 72, 76, 79, 84]
pianoroll[0:95, C_maj] = 100

# Create a `pypianoroll.Track` instance
track = Track(pianoroll=pianoroll, program=0, is_drum=False,
              name='my awesome piano')

# Plot the piano-roll
fig, ax = track.plot()
plt.show()
```

ok, to import a midi file:
```
another_multitrack = Multitrack('sample.mid')
```

as easy to use huh



and then,to get the piano roll array(cause my imported midi file is a multitrack file so we can only get the merged array):
```
mat=another_multitrack.get_merged_pianoroll()
print(mat)
```
To get a single track piano_roll array

