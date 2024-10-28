+++
title = 'What is really music?'
date = 2024-10-17T13:56:48-03:00
draft = true
+++

**Note**: the following is pure logical deduction. I didn't read any articles about the relation of math and music.

**Note**: the following was written keeping a guitar fretboard in mind. But the theory is the same for every instrument.

## Playing with different parts of the fretboard keeping the same fingers position

The initial four notes of _Do I Wanna Know_ are: `F2 G2 A#2 G2`

**If we, keeping the same rhythm, use other random notes, it won't probably sound like _Do I Wanna Know_ obviously.**

However, **keeping the same fingers position on the fretboard, and the same rhythm, we can move to whatever part of the fretboard,
it'll sound like _Do I Wanna Know_ even though it may sound strange in some cases, it's still recognizable.**

**Important (exception)**: when transposing including the first strings `B` and `E`, you have to move up one semitone for the
finger position of `A#2`. e.g.: `D#4 F4 G#4 F4` instead of `D#4 F4 G4 F4`.

But when transposing including _only_ `B` and `E` strings, you do not need to move up one semitone.

> Why the exception? Probably because the way the guitar strings are tuned by default.
> The notes on a fret follows the circle of fifht but it deviates by a semitone on the first two strings.

> Try it for yourself. Try to play, keeping the same rhythm, with `D3 E3 G3 E3`
> You see? Yes, yes, yes!

## Assumption: Mathematical Signature

Sound is just frequency.

And music is just a sequence of different frequencies with arbitrary intervals between them
that sounds cool to our brain for some neurological reason.

And of course, music can be made by different sequences in parallel with different frequencies and rhythms.

> Why just _specific_ sequences and groups of frequencies sound cool to our brain?
> This is a very interesting philosophical and biological question.

Ok but back to _Do I Wanna Know_. Just transposing the hands position throughout the fretboard, the song is still
recognizable. Why?

My guess is that each sequence of frequencies (aka music) bring with itself _a mathematical signature_ which
is defined by the frequencies, intervals and how they're blend together.

So `F2 G2 A#2 G2` played in a certain rhythm has this unique mathematical relation between the frequencies that is abstracted
by our brains.

Therefore, when we transpose our hand to another part of the fretboard keeping the same fingers position and playing
with the same rhythm, the _mathematical signature is still the same!_ The only difference is the frequencies being used.

> Example:
>
> It's like a linear function defined by: `f(x) = 3x + 4`
> For different `x`s, the output will be different. But still, the relation between all outputs
> are dictated by this base `3<x> + 4`.
>
> Note: I'm not saying the mathematical relations of music are linear functions.

So let's investigate this mathematical underlying concepts of music!!!

## Music variables

First, let's play with which variables music rely on and what is like the state of a singular moment for a given music.

> _Important_: I just realized that defining the entire state of Music in a structure is no easy work.
>
> There can be multiple notes being played at the same time with different rhythms! My point of having a mathematical signature still applies
> for a more complex piece of music but...
>
> For the sake of our goal here which is to find if there really is such a thing as a mathematical signature of a given piece of music,
> we'll **ONLY consider musics (or pieces of it) where only one note is played at time**

`Music []SongState` here we define that music is an _ordered list_ `SongState`.

> it's underlying data structure would be either a list or a linked list.
> (this is not a CS blog post so I'll abstract this kind of things the maximum that I can)

```
type SongState {
    Frequency (Number)
    DurationUntilNext (Number in seconds)
}
```

> I just realized most of the times PressDuration will be the same as DurationUntilNext. But let's keep it here for now.

That is it! Let's get as an example the four first notes of _Do I Wanna Know_:

```
type Music []SongState

let DoIWannaKnow = []SongState{
    SongState{F, 0.2, 0.2},
    SongState{G, 0.5, 0.5},
    SongState{A#, 0.5, 0.5}
    SongState{G, 2, 2}
}
```

## Arguments: Mathematical Signature

Let's get back to the initial assumption:

Music, being a sequence of song states with different rhythms (and possibly different rhythms and melodies in parallel),
does have a mathematical signature based on its states and how they are ordered.

For this assumption, we consider:
TODO:

Since we're considering the same rhythm and the same fingers position on the fretboard, the only variable that matters now
is the frequencies because all the rest is constant for our assumption of transposing fingers position throughout the fretboard.

Let's analyze the frequencies then:

### Do I Wanna Know: frequencies comparison

Here, using the same example of _Do I Wanna Know_, let's compare the original notes sequence with the transposition example:

Original: `F2 G2 A#2 G2`

Tranposed 1: `D3 E3 G3 E3`

Tranposed 2: `D#4 F4 G#4 F4`

Let's compare each note frequency with each other:

I don't know but I have this gut feeling that I should subtract these numbers:

#### Subtraction: Original vs Transposed 1

- `F2 - D3 = 87.31 - 146.83 = -59.52 Hz`
- `G2 - E3 = 98.00 - 164.81 = -66.81 Hz`
- `A#2 - G3 = 116.54 - 196.00 = -79.46 Hz`
- `G2 - E3 = 98.00 - 164.81 = -66.81 Hz`

#### Subtraction: Original vs Transposed 2

- `F2 - D#4 = 87.31 - 311.13 = -223.82 Hz`
- `G2 - F4 = 98.00 - 349.23 = -251.23 Hz`
- `A#2 - G#4 = 116.54 - 415.30 = -298.76 Hz`
- `G2 - F4 = 98.00 - 349.23 = -251.23 Hz`

Ok it seems there is nothing here at all, let's actually divide the numbers then:

#### Division: Original vs Transposed 1

- `F2 / D3 = 87.31 / 146.83 = 0.5944`
- `G2 / E3 = 98.00 / 164.81 = 0.5945`
- `A#2 / G3 = 116.54 / 196.00 = 0.5946`
- `G2 / E3 = 98.00 / 164.81 = 0.5945`

#### Division: Original vs Transposed 2

- `F2 / D#4 = 87.31 / 311.13 = 0.2806`
- `G2 / F4 = 98.00 / 349.23 = 0.2806`
- `A#2 / G#4 = 116.54 / 415.30 = 0.2806`
- `G2 / F4 = 98.00 / 349.23 = 0.2806`
