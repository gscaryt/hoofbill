# 🐴 Hoofbill 🦜

A swipe-'em-up for people who find horses and toucans genuinely fascinating.
Fifty profiles — twenty-five horses, twenty-five toucans — each with a real
photograph, an invented name, an age nobody verified, and a biography that is
frankly none of your business.

Swipe right on the ones you like. They go in your **Menagerie**. Swipe left on
the ones you don't. Nothing bad happens. It is a birthday present, not a moral test.

## Playing it

Open `index.html` in any modern browser. No build step, no dependencies, no
internet connection needed once the folder is on your machine.

| Do this | To |
| --- | --- |
| Drag the card right, or tap ♥ | Keep them |
| Drag the card left, or tap ✕ | Pass |
| Tap ↺ | Undo the last swipe |
| Tap the card, or ⓘ | Read the full profile |
| ← → ↑ U | The same four things, on a keyboard |

Three tabs along the bottom:

- **Deck** — the swiping.
- **Menagerie** — everyone you kept. Tap one to read them again or let them go.
- **Field Guide** — all fifty, always, whether you swiped on them or not.

The three chips at the top filter everything at once: **Everyone**, **Horses only**,
**Toucans only**. The little number next to each chip tells you how many you're
looking at on the current tab.

Your Menagerie is saved in the browser's local storage, so it survives closing
the tab. It lives only on that device, in that browser.

> **On iPhone/iPad:** iOS won't run JavaScript from a local file opened through
> Files, Mail or OneDrive — the app will look frozen. Host the folder somewhere
> (GitHub Pages works) and open the link in Safari, then **Add to Home Screen**.
> On a Mac or PC, opening `index.html` directly is fine.

## What's in here

```
index.html          the whole app — layout, styling, swipe logic
profiles.js         the cast: 50 profiles, easy to edit or extend
img/                50 photographs, pre-cropped to 4:5, ~6 MB total
image-credits.json  which Wikimedia Commons file each photo came from
```

## Adding more

Every profile is one object in `profiles.js`:

```js
{id:'h25', kind:'horse', img:'img/horse_25.jpg', name:'Doreen', age:11,
 species:'Nokota', origin:'North Dakota, USA',
 stat:['Height','14.2 hh'],
 bio:"Two sentences of nonsense.",
 tags:['Tag one','Tag two','Tag three'],
 prompt:['A prompt heading','The answer to it.']}
```

Drop a 4:5 image into `img/`, add the object, reload. `kind` must be
`'horse'` or `'toucan'` — that's what drives the filters and the colour accents.

## Where the pictures came from

All fifty are real animals, sourced from Wikimedia Commons and cropped to a
consistent 4:5. `image-credits.json` maps every file back to its Commons page.
A couple carry the photographer's own watermark, which has been left alone.

The names, ages, opinions, grudges and unresolved feelings about geese are
entirely invented.
