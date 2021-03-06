# ChangesJs

A DSL for exploring jazz chord changes.

## Information

**ChangesJs** is a DSL built for describing jazz chord changes.  It is meant to assist jazz musicians building music apps or education tools.  Upon building out a chord, the user can explore the various ways the chord can be described, the underlying scale of the chord, the chord tones of the chord and the sound of the chord.

A key feature of **ChangesJs** is the proper selection of enharmonics.  For example, take the split nine in a *C7(#9)* chord (a *Db* and a *D#*): **ChangesJs** will correctly display the split nine as a *D** rather than a *C#* or *Eb*.  In another example, take the true seven in a *C-diminished* chord (the seven is a *B*, and the true definition is a double flat seven): **ChangesJs** will automatically choose *Bbb* as the enharmonic for the seven in a *C-diminished* chord.  However, **ChangesJs** also provides a "legible" option which will resolve tones to their most "legible" form (*Bbb* to *A* in the previous example).

The syntax is pretty self-explanatory since it is meant to be read and written the way a musician would read and write a chord.

### Build

The "build" of **ChangesJs** is at ["lib/changes.js"](lib/changes.js) ([raw](https://cdn.rawgit.com/twitchax/changesjs/master/lib/changes.js)).

Live demo [here](http://twitchax.github.io/bower_components/changesjs/test/index.html).

Screencast demo [here](https://www.youtube.com/watch?v=C1UCETOFThw).

### Compatibility

Chrome 51+.

### Testing

Chrome 51+.

### Examples
A basic example follows:
```javascript
var chord = C['C'].seven().sharpNine();
console.log(`${chord.toString()}`);
```
yields
```
C7(♯9):
    Description: diminished whole tone, seventh mode of a melodic minor scale, melodic minor up a half step
    Chord Structure: 1, 3, 5, ♭7, ♯9
    Scale: C, D♭, D♯, E, F♯, G♯, B♭
    Chord: C, E, G, B♭, D♯
    Legible Scale: C, D♭, E♭, E, F♯, G♯, B♭
    Legible Chord: C, E, G, B♭, E♭
```

In addition to the fluent API, there is a rudimentary chord symbol parser.  For example:
```javascript
var chord = C['A7(b9)'];
console.log(`${chord.toString()}`);
```
yields
```
A7(♭9):
    Description: fully diminished (half step first), half/whole/half
    Chord Structure: 1, 3, 5, ♭7, ♭9
    Scale: A, B♭, C, C♯, D♯, E, F♯, G
    Chord: A, C♯, E, G, B♭
    Legible Scale: A, B♭, C, D♭, E♭, E, F♯, G
    Legible Chord: A, D♭, E, G, B♭
```

**ChangesJs** also has a "Player" that can play chords or notes in order:
```javascript
var root = C['C'];
P
    .add(root.major())
    .add(root.majorSeven())
    .add(root.minor())
    .add(root.minor().majorSeven())
    .add(root.minor().seven())
    .add(root.seven())
    .add(root.seven().sharpEleven())
    .add(root.plus().majorSeven())
    .add(root.plus().seven())
    .add(root.halfDiminished())
    .add(root.diminished())
    .add(root.seven().flatNine())
    .add(root.seven().sharpNine())
    .play(2000);
```
At present, these are all of the "well-defined" chords.

## License

```
The MIT License (MIT)

Copyright (c) 2016 Aaron Roney

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
```
