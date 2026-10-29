# How to add a product

This page shows how to add a product to the Made to Order page. You do it on GitHub's website. You do not need to install anything.

Every product has one entry in `data/products.yaml` and one photo in `assets/products/`.

## Before you start

- The product must be a Good 'til cancelled listing on eBay.
- Save the main photo from the eBay listing. Use a JPEG file.
- Name the photo in lower case, with hyphens, for example `odin-speedloader-adapter.jpg`.
- The photo should be at most 1600 pixels wide.

## Steps

1. Open github.com/makinbug/makinbug.github.io. Open the folder `assets`, then `products`.
2. Click **Add file**, then **Upload files**. Drop the photo in.
3. At the bottom, pick **Create a new branch for this commit**. Give it a name like `add-odin-adapter`. Click **Propose changes**. Do not open the pull request yet.
4. Use the branch menu at the top left to switch to your new branch.
5. Open `data/products.yaml`. Click the pencil icon to edit.
6. Copy one whole entry (from its `- name` line to its last line). Paste it where you want it. Change each line (see the next section).
7. Click **Commit changes**. Pick **Commit directly to the add-odin-adapter branch**.
8. Go to the **Pull requests** tab. Click **New pull request**. Pick your branch. Click **Create pull request**.
9. Wait for the `build` check to turn green. If it turns red, open it and read the message. It says what is wrong, for example a wrong category or a missing photo.
10. Click **Merge pull request**. Wait a few minutes. The product shows on makinbug.github.io.
11. Click the new buy button. Check that it opens the right eBay listing.

## The lines of an entry

```
- name: "ODIN speedloader adapter"
  category: "Airsoft Stuff"
  ebay: "https://www.ebay.co.uk/itm/123456789012"
  image: "odin-speedloader-adapter.jpg"
  alt: "Black 3D printed adapter fitted to an ODIN speedloader"
  text: "One or two plain lines about the product."
  weight: 10
  featured: true
```

| Line | What to put |
| --- | --- |
| `name` | The eBay title. |
| `category` | One of: `Miscellaneous Bits`, `Airsoft Stuff`, `Cycling Things`. Spell it exactly. |
| `ebay` | `https://www.ebay.co.uk/itm/` and the item number. Cut off everything after the number, such as `?hash=...`. |
| `image` | The photo's file name, exactly as uploaded. |
| `alt` | A short description of the photo, for people who can't see it. |
| `text` | Optional. One or two plain lines. Leave the whole line out if you have nothing to say. |
| `weight` | The order inside the group. Lower numbers come first. Use steps of 10, so you can add one between later. |
| `featured` | Put `featured: true` only on the 3 products for the home page. Leave the line out for all others. If you add a fourth, remove one of the others first. |

## Rules for the file

- The spaces at the start of each line matter. The `- name` line starts at the left edge. Every other line starts with two spaces. Copy an existing entry and the spaces come with it.
- Keep the quote marks (`"`) around text. Do not put a quote mark inside the text. An apostrophe is fine.
- Leave a blank line between entries.
- Do not put prices on the site. eBay prices change.

## Take a product off the site

Delete its entry from `data/products.yaml`, using the same branch and pull request steps. You can delete its photo from `assets/products/` too.

If a listing only sells out, you do not need to do anything. With eBay's out-of-stock option on, the listing is hidden but its link keeps working.

## The Cycling Things group

A group with no products does not show. Add one product with `category: "Cycling Things"` and the group appears.
