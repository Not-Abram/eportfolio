---
title: "Post: Finding the size of a cache."
excerpt_separator: "<!--more-->"
categories:
  - Blog
tags:
  - Cacheing
---
In my Computer Organization and Architecture class this fall, 
we learned a lot about the components of computers. 
One of our focuses was on caching.

Here's how to find the total amount of bits in a direct-mapped cache.

- Given that the cache contains $16$KiB of data, has a block size of $4$ words, and is using a $32$-bit address, find the total SRAM required in bits. 
    - We first need to find know the cache size in the form of $2^n$ blocks
        - $16$ KiB $* 1024$ bytes/KiB $* 8$ bits/byte $= 131072$ bits
        - $4$ blocks $* 32$ bits/block $= 128$ bits/block
        - $131072/128 = 1024$ blocks
        - $\log(1024, 2) = 10 = n$
    - Them, we need to find know the block size in $2^m$ words
        - $\log(4, 2) = 2 = m$
    - The tag size is address size minus $n$ minus $m$ minus $2$, or  $32 - n - m - 2$
        - making $32 - 10 - 2 - 2 = 18$ bits
    - the total bits of SRAM needed for a direct-mapped cache is:
        - the number of blocks * (block bit size + the tag + the valid bit)
        - equaling $1024*(128 + 18 + 1) = 150528$ bits of SRAM
        - the SRAM is $150528 / 131072 = 1.15$ times as large as the cache size, or $15%$ bigger.