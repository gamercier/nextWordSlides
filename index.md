# NextWord! App
Gustavo Mercier  
`r format(Sys.time(), "%d %B, %Y")`  



## Motivation

* Mobile devices are small platforms where typing input is cumbersome.
* Voice input is one solution, but has drawbacks:
     + Require large computer resources
     + May fail to recognize the user's voice:
          - Due to accents
          - Temporary voice changes due to sickness, like colds
* Assisted typing is another solution.
* "NextWord!" is a prototype assisted typing program suitable for mobile devices.
     + It is fast and has as a small foot print.

## Algorithm

* Prediction engine:
     + Statistical 4-gram language model with modified stupid back off algorithm
          - Optimized for the small foot print of "NextWord!"
* The N-gram database:
     + Source corpus is web text.
          - A good simulation for mobile device input
     + Trimmed for small size
          - Retained vocabulary still recovers 95% of the corpus.
          - Reduces the contribution from rare N-grams.
          - Done while mantaining accuracy.

<!-- Slidy source hosted in [github cvCalculator_slides](https://github.com/gamercier/cvCalculator_slides/tree/gh-pages) -->

<!-- Shiny app source hosted in [github cvCalculator](https://github.com/gamercier/cvCalculator) -->

## The App

* The prototype is simple.
     + The user fills a text input box with an phrase in English.
     + Once the user pauses three guesses are provided.
     + For analysis the output includes supplementary information:
          - Stupid back off scores
          - The source n-gram that contains the guessed word as the last word.
* The input is filtered to match the one applied to the source corpus.
* Output is unchanged until better guesses are found.
     + The default guesses are the 3 most frequent unigrams.

## User experience

* The experience with the prototype is less than adequate, but can be improved.
* Tests show that at least one of the guesses will be correct 20-30% of the time.
* Performance is best for web text, but worse for non-web based text.
* The source corpora and its processing can still be refined to improve accuracy.

## Significance

* The strength of this App is its small size
     + Database 3.6Mb.
* It is also fast with real time results.
     + 1.3msec per guess.
* Extrinsic test sets provide a more realistic measure of performance
     + Avoid optimizing perplexity.
     + Suitable for non-strictly probabilitic model, like stupid backoff.