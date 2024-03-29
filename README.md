# MA-remove-review-info
A browser extension to remove review information from certain pages on metal-archives.com.

## What does it do?
This script functions on the band and album pages, though differently for each. Taking the easiest first, on the album page, it looks for a description term with the value "Review:" and sets the corresponding description detail to "None yet", which is the default value when a release doesn't have any reviews.

On the band page, a function that looks at the tables in the document is called in a loop. If there is a change, it checks for a discography table and sets the text of certain element in each release to the empty string.

## What does it not do?
This script doesn't do anything on the Reviews tab since I assume the user wants to see that information if they navigate there.

## Possible improvements
Due to my poor knowledge of JS, there are certainly several improvements that can be made. Here are a few I've thought of, though the script works well enough for me as is.

- Find a way to stop (and start again) the band-page loop. The discography tables finish loading after the document has finished loading, and I'm not aware of a way to inspect these without a setInterval() loop. This causes a tradeoff in having the loop not run too often (though I've tried to have the function return as quickly as possible if there are no changes) vs removing the review information in a timely manner. (In my testing, however, even setting the loop timer down to 10 ms resulted in a noticeable blip on the screen if one is looking for it. The delay caused with 250 ms isn't much worse.)
- On the band page, simply color the anchor text black instead of changing/deleting it.
