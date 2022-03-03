# Code examples only

Trying to reduce the amount of text.

## High order array methods

- `filter`: this is an example from my Guitar Chord Namer app. The steps for the app up to this point are:
  1. Get the fret #'s entered by the user (6 input fields)
  1. Convert the fret #'s into chromatic notes (letter names) and store in a variable named `chordTones`
  1. In case of duplicate notes, get only unique notes and store in a variable named `uniqueNotes`. So given `chordTones` which could be 3 to 6 notes:

```js 
// 3. In case of duplicate notes, get only unique notes
  let uniqueNotes = [];

  uniqueNotes = chordTones.filter(tone => !uniqueNotes.includes(tone) && tone !== undefined ? uniqueNotes.push(tone) : null);
```
Code explanation: A later step involvs creating a 12-note array for each note, which I them use to compare each note to every other note to determine the interval distance. That is how the chord name match is found. Duplicate notes are not needed and would only make the logic more complicaated so they need to be removed:

1. If the note has already exists in `uniqueNotes` (aleady been pushed) then using the not includes condition will skip that note. 
1. But the user does not have to enter a fret number for every string. When they do not, then that string will have no value -> `undefined`. So we need to account for those as well. 
1. So filter out notes that are already in the `uniqueNotes` array or are undefined, then push them onto the array.
1. I am hoping that `null` is the correct choise for the ternary else condition. 
