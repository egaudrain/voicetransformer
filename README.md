# voicetransformer

A wrapper over [pyworld](https://pypi.org/project/pyworld/) to make voice transformation easy.

The wrapper is based on the [vt_server_module_world](https://github.com/egaudrain/VTServer/blob/master/src/vt_server_module_world.py),
also offering a command line interface.

## Install

```
pip install -U https://github.com/egaudrain/voicetransformer/archive/refs/heads/main.zip
```

## Example

Use it as a module:

```python3
import voicetransformer as vt

m = {
    "f0": "-5 st",
    "vtl": "+ 1st"
}

vt.process_world("mysound.wav", m, output_filename="mynewsound.wav")
```

If a filename is given as input, and no folder is provided for cache, the result
of the analysis step of WORLD will be stored in a pickle file in the same folder.

To control the cache, use:

```python3
vt.process_world("mysound.wav", m, output_filename="mynewsound.wav", cachefolder="./cache")
```

If you don't want to cache anything and just want to process a sound from an array rather
than a file:

```python3
import voicetransformer as vt
import soundfile as sf

x, fs = sf.read("mysound.wav")

# Do some processing...
y = x * 2

m = {
    "f0": "-5 st",
    "vtl": "+ 1st"
}

z, fs = vt.process_world((y, fs), m)
```

## License

voicetransformer, a simple wrapper for pyworld
Copyright (C) 2024 Etienne Gaudrain

This program is free software: you can redistribute it and/or modify
it under the terms of the GNU General Public License as published by
the Free Software Foundation, either version 3 of the License, or
(at your option) any later version.

This program is distributed in the hope that it will be useful,
but WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
GNU General Public License for more details.

You should have received a copy of the GNU General Public License
along with this program.  If not, see <https://www.gnu.org/licenses/>.
