# 🐴 Hoofbill 🦜🐄

A swipe-'em-up for people who find horses, toucans and cows genuinely fascinating.
**152 profiles** — 51 horses, 50 toucans, 50 cows and one unicorn — each with a real
photograph, an invented name, an age nobody verified, and a biography that is
frankly none of your business.

Swipe right on the ones you like. They go in your **Menagerie**. Swipe left on
the ones you don't. Nothing bad happens. It is a birthday present, not a moral test.

**Available in English and Brazilian Portuguese** — tap the flag in the top right.
Everything translates except the names, which are the same in both languages
because Bartolomé is Bartolomé. Every profile has a sex (shown as ♂/♀), so the
Portuguese adjectives agree properly rather than defaulting to masculine — a cow is
a *vaca* and a bull is a *touro*, and the biographies are written to match.

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
| 🇬🇧 / 🇧🇷 | Switch language |

Three tabs along the bottom:

- **Deck** — the swiping.
- **Menagerie** — everyone you kept. Tap one to read them again or let them go.
- **Field Guide** — all 152, always, whether you swiped on them or not.

The four chips at the top filter everything at once: **Everyone**, **Horses only**,
**Toucans only**, **Cows only**. The number on each chip is how many you're looking
at on the current tab. The unicorn files itself under Horses, which is his position
and he is sticking to it.

Your Menagerie and your language choice are saved in the browser's local storage,
so they survive closing the tab. They live only on that device, in that browser.

> **On iPhone/iPad:** iOS won't run JavaScript from a local file opened through
> Files, Mail or OneDrive — the app will look frozen. Host the folder somewhere
> (GitHub Pages works) and open the link in Safari, then **Add to Home Screen**.
> On a Mac or PC, opening `index.html` directly is fine.

## What's in here

```
index.html          the whole app — layout, styling, swipe logic, i18n
profiles.js         the cast, in English: 152 profiles, easy to edit or extend
pt.js               the Brazilian Portuguese strings, keyed by profile id
img/                152 photographs, pre-cropped to 4:5, ~20 MB total
image-credits.json  which Wikimedia Commons file each photo came from
```

## Adding more

Every profile is one object in `profiles.js`:

```js
{id:'h51', sex:'f', kind:'horse', img:'img/horse_51.jpg', name:'Doreen', age:11,
 species:'Hanoverian', origin:'Lower Saxony',
 stat:['Height','16.1 hh'],
 bio:"Two sentences of nonsense.",
 tags:['Tag one','Tag two','Tag three'],
 prompt:['A prompt heading','The answer to it.']}
```

Drop a 4:5 image into `img/` (760×950 is what the existing ones use), add the object,
reload. `kind` must be `'horse'`, `'toucan'` or `'cow'` — that drives the filters and
the colour accents. Add `mythical:true` for anything that isn't strictly real; it gets
the purple treatment.

A fourth kind means four edits, all in one place each: add it to `KINDS` and
`KIND_EMOJI` near the top of the script, add a `.chip` button to the filter row, add
the `cows`/`cow`/`empty…` strings to both dictionaries, and add the four colour rules
(`.chip.on.X`, `.kindmark.X`, `.card.X .tg`, `.gcell.X .dot`). Everything else —
counts, queues, the field guide, the empty states — reads the kind rather than
naming it.

`sex` is `'m'` or `'f'`. It shows as ♂/♀ on the card, and it matters: Portuguese
inflects adjectives, so Dolly is *acabada* while Douglas would be *acabado*. If you
add a profile, set the sex first and write the Portuguese to agree with it. It also
picks the noun on the detail sheet — Mare/Stallion, Cow/Bull, Female/Male.

For the Portuguese version, add a matching entry to `pt.js` under the same id with
`species`, `origin`, `bio`, `tags` and `prompt`. Heights in hands are converted to
centimetres automatically and cow weights are already metric, so don't translate the
`stat` field. A profile with no
Portuguese entry simply falls back to English rather than breaking.

## Where the pictures came from

All of them are real animals sourced from Wikimedia Commons and cropped to a
consistent 4:5. `image-credits.json` lists, for every file, the Commons page, the
photographer and the licence.

Commons only hosts freely licensed material, so every photo here is CC BY, CC BY-SA,
CC0 or public domain — reuse is fine as long as the credit travels with it, which is
what that file is for. A few images carry the photographer's own watermark, which has
been left alone. The app itself credits Wikimedia Commons on each profile.

Everything that isn't a photograph — the code, the names, the biographies — is mine
to give away, so treat it as yours.

The one exception is Steve, whose horn was drawn and composited on. He maintains
it is not glued on. The credits file says otherwise.

The names, ages, opinions, grudges and unresolved feelings about geese are
entirely invented.
