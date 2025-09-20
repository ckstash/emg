<a id="emg"></a>

# emg

<a id="emg.generator"></a>

# emg.generator

<a id="emg.generator.EulerianMelodyGenerator"></a>

## EulerianMelodyGenerator Objects

```python
class EulerianMelodyGenerator()
```

Generates melodies using Eulerian paths in De Bruijn graphs.

<a id="emg.generator.EulerianMelodyGenerator.__init__"></a>

#### \_\_init\_\_

```python
def __init__(soundfont_path,
             scale="C-Major-Pentatonic",
             bpm=200,
             kmer_length=4,
             num_kmers=8,
             num_repeats=8,
             random_seed=2)
```

Initialize the melody generator.

**Arguments**:

- `soundfont_path` _str_ - Path to the .sf2 SoundFont file.
- `scale` _str_ - Musical scale in the format "Key-ScaleName", where key is in the set {"C", "C#", "D", "D#", "E", "F", "F#", "G", "G#", "A", "A#", "B"}, and ScaleName is in the set {"Major", "Natural-Minor", "Major-Pentatonic", "Minor-Pentatonic", "Mixolydian", "Dorian"}.
- `bpm` _int_ - Beats per minute.
- `kmer_length` _int_ - Length of each k-mer.
- `num_kmers` _int_ - Number of k-mers to generate.
- `num_repeats` _int_ - Number of times to repeat the final note sequence.
- `random_seed` _int_ - Seed for reproducibility.

<a id="emg.generator.EulerianMelodyGenerator.generate_eulerian_kmers"></a>

#### generate\_eulerian\_kmers

```python
def generate_eulerian_kmers(k, count, scale_notes, seed=42)
```

Generate k-mers over the given scale that form a connected De Bruijn graph.

<a id="emg.generator.EulerianMelodyGenerator.build_debruijn_graph"></a>

#### build\_debruijn\_graph

```python
def build_debruijn_graph(kmers)
```

Build De Bruijn-style graph.

<a id="emg.generator.EulerianMelodyGenerator.generate_and_save_graph"></a>

#### generate\_and\_save\_graph

```python
def generate_and_save_graph(graph_dict, output_file=None, seed=100, k=1)
```

Visualize a De Bruijn graph and save it as a PNG.

**Arguments**:

- `graph_dict` _dict_ - Adjacency list of the graph.
- `output_file` _str, optional_ - Path to save the PNG file. Defaults to None (current dir).
- `seed` _int_ - Layout seed.
- `k` _float_ - Node spacing parameter.

<a id="emg.generator.EulerianMelodyGenerator.find_eulerian_path"></a>

#### find\_eulerian\_path

```python
def find_eulerian_path(adj, in_deg, out_deg)
```

Find an Eulerian path in the De Bruijn-style graph.

<a id="emg.generator.EulerianMelodyGenerator.flatten_path"></a>

#### flatten\_path

```python
def flatten_path(path_nodes)
```

Flatten a list of note tuples into a single list.

<a id="emg.generator.EulerianMelodyGenerator.compose_and_export"></a>

#### compose\_and\_export

```python
def compose_and_export(final_notes,
                       mp3_file=None,
                       midi_file=None,
                       wav_file=None)
```

Compose a melody from notes and export as MP3.

**Arguments**:

- `final_notes` _list_ - List of note names (without octaves).
- `mp3_file` _str, optional_ - Path to save the MP3 file. Defaults to None (current dir).
- `midi_file` _str, optional_ - Path to save the intermediate MIDI file. Defaults to None.
- `wav_file` _str, optional_ - Path to save the intermediate WAV file. Defaults to None.

<a id="emg.generator.EulerianMelodyGenerator.run_generation_pipeline"></a>

#### run\_generation\_pipeline

```python
def run_generation_pipeline(graph_png_path, mp3_output_path)
```

Run the full melody generation pipeline:
1. Generate k-mers
2. Build De Bruijn graph
3. Save graph visualization
4. Find Eulerian path
5. Flatten to note sequence
6. Repeat sequence and export as MP3

**Arguments**:

- `graph_png_path` _str_ - Path to save the graph PNG.
- `mp3_output_path` _str_ - Path to save the MP3 file.

