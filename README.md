# Leo's Art Gallery

A walk-through 3D gallery that runs as a plain website. There is no database: everything guests see comes from the files in this repository.

- `index.html` is the gallery. You never need to edit it.
- `gallery.json` is the list you edit: gallery name, your email, the pledge totals, and one entry per piece of art.
- Your pictures go in the `art` folder.
- `LICENSE` and `COPYRIGHT.md` say the code is MIT-licensed and the artwork is all rights reserved.

## First-time setup (about 10 minutes)

1. Create a free account at github.com.
2. Create a **new repository**. Name it something like `childhood-art-gallery` and keep it **Public** (free hosting requires a public repository).
3. In the repository, choose **Add file > Upload files** and upload `index.html`, `gallery.json` and this `README.md`. Press **Commit changes**.
4. Open **Settings > Pages**. Under "Build and deployment", set **Source** to "Deploy from a branch", pick the **main** branch and the **/ (root)** folder, then save.
5. Wait a few minutes. Your gallery is at `https://YOUR-USERNAME.github.io/childhood-art-gallery/`. That is the link you send to guests.

Until you add art, the hall shows four sample drawings.

## Set your details

Open `gallery.json` on GitHub, press the pencil icon, edit, and press **Commit changes**.

| Line | What it does |
|---|---|
| `title`, `artist`, `welcome` | The gallery name, the artist line on every placard, and the welcome text. |
| `bio` | The artist's bio, one paragraph per quoted line. It shows as wall text near the entrance and in **The artist** tab. Leave it as `[]` to hide both. |
| `email` | Where pledges are sent. While it still says `example.com`, guests can only copy their pledge. Consider an address made just for the gallery, because it is visible to anyone who opens the site. |
| `cause` | What pledges support, in a few words. |
| `howToDonate` | How guests keep their pledge (for example, how to pay you or where to sign up to volunteer). Shown in the pledge steps. |
| `suggestedDonation` | A number, with no dollar sign. Use `0` to hide it. |
| `pretendGuests` | How many cartoon visitors wander the hall, from `0` to `8`. |

## Let guests send messages without opening their email (recommended)

By default, the pledge and guest book buttons open the guest's own email app. To have the gallery send messages straight to your inbox instead, add a free Web3Forms key:

1. Go to web3forms.com and enter the email address that should receive the messages.
2. An access key arrives in that inbox. Copy it.
3. Edit `gallery.json` and paste it between the quotes: `"formKey": "paste-your-key-here"`.

After that, guests fill in the form in the gallery and press **Send**. Each pledge and guest book message reaches you as an email from Web3Forms. Pledges for a piece ask for the guest's email address so you can reply with the picture.

The free plan covers 250 messages a month. The key is meant to be public, so it is fine in this file. Messages pass through Web3Forms on their way to you. If a send ever fails, the guest is offered the email-app and copy options instead.

## Add a piece of art

1. Save a web-size copy of the scan: about 1600 pixels on the long side, JPG, under 500 KB. Keep the full-resolution original to yourself. This repository is public, so anything you upload here can be downloaded by anyone.
2. Give the file a simple name such as `beach-dinosaur.jpg`.
3. Open the `art` folder on GitHub, then choose **Add file > Upload files**. Uploading from inside the folder puts the picture there.
4. Edit `gallery.json` and add an entry inside the `"art": [ ]` brackets:

```json
"art": [
  {
    "file": "art/beach-dinosaur.jpg",
    "title": "Dinosaur at the beach",
    "medium": "Crayon on construction paper",
    "year": "2026",
    "note": "He is swimming because it is hot.",
    "pledges": 0
  },
  {
    "file": "art/rainbow.jpg",
    "title": "Rainbow, mostly"
  }
]
```

Only `file` is required, and it must start with `art/`. Entries are separated by commas, and the last one has no comma after it. Pieces hang in the order they appear in the list, alternating left and right walls.

## Remove a piece

Delete its entry from `gallery.json`, then delete the picture file (open the file on GitHub, press the three-dot menu, **Delete file**).

## Update the pledge numbers

When a pledge email arrives, edit `gallery.json`:

```json
"totals": {
  "pledges": 12,
  "donated": 140,
  "volunteerHours": 9.5
}
```

- `pledges` is the number of pledges received.
- `donated` is the dollar total, with no dollar sign.
- `volunteerHours` is the hours total.
- To show a count on one piece's placard, raise that piece's `"pledges"` number.

These numbers change only when you edit them. Guests see the update a few minutes after you commit.

## Guest book

Guests sign from the **Guest book** tab or by leaving the box ticked when they pledge. Either way you get an email, and its last line is a ready-made entry like this:

```json
{"name":"Grandma Jo","date":"2026-11-15","message":"Keep drawing! I love your colors."}
```

To add it, edit `gallery.json` and paste that line inside the `"guestbook": [ ]` brackets, with a comma between entries:

```json
"guestbook": [
  {"name":"Grandma Jo","date":"2026-11-15","message":"Keep drawing! I love your colors."},
  {"name":"Uncle Sam","date":"2026-11-16","message":"The sun with legs is my favorite."}
]
```

Add new entries at the end. The book shows the newest first, and the latest four appear on the wall at the far end of the hall. The site cannot record visitors by itself, so the book lists only people who chose to sign.

## Which picture to send

Every pledge email names the piece twice: its title, and a "Picture file" line with the exact file name from `gallery.json` (for example `art/beach-dinosaur.jpg`). Keep your full-resolution originals under the same names and you can find the right one at a glance.

## How pledging works for guests

A guest picks a piece, enters a dollar amount, volunteer hours, or both, and presses a button that opens their own email app with the pledge already written and addressed to you. You reply with the full-resolution picture. The site stores nothing about guests.

## If something looks wrong

- **Samples are showing and a yellow note mentions a typo:** `gallery.json` has a missing comma, quote or bracket. Compare it with the examples above.
- **A frame says "Picture not found":** the `file` name in `gallery.json` does not match the uploaded file exactly, including capital letters and the ending (`.jpg` is not `.JPG`).
- **A change is not showing:** wait a few minutes and reload.
