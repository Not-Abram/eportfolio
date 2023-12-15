---
title: "Post: Finding the size of a cache."
excerpt_separator: "<!--more-->"
categories:
  - Blog
tags:
  - Cacheing
---
<script
  src="https://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML"
  type="text/javascript">
</script>

In my Computer Organization and Architecture class this fall, we learned a lot about the components of computers. 
One of the topics we covered was on caching. I spent a lot of time making sure I understood it, only for it to be completely absent from the final :(\
So, I am writing down the process my classmates and I worked out during our exam study session. 

Here's a demonstration on how to find the total amount of bits in a direct-mapped cache:

Given that the cache contains $$16$$KiB of data, has a block size of $$4$$ words, and is using a $$32$$-bit address, find the total SRAM required in bits. 
  - We first need to find know the cache size in the form of $$2^n$$ blocks.
      - $$16$$ KiB $$*$$ $$1024$$ bytes/KiB $$*$$ $$8$$ bits/byte $$= 131072$$ bits
      - $$4$$ words/block $$*$$ $$32$$ bits/word $$= 128$$ bits/block
      - $$131072/128 = 1024$$ blocks
      - $$\log_2(1024) = 10 = n$$.
  - Then, we need to find know the block size in $$2^m$$ words:
      - $$\log_2(4) = 2 = m$$.
  - The tag size is address size minus $$n$$ minus $$m$$ minus $$2$$, or  $$32 - n - m - 2$$
      - making $$32 - 10 - 2 - 2 = 18$$ bits.
  - the total bits of SRAM needed for a direct-mapped cache is:
      - the number of blocks $$*$$ (block bit size $$+$$ the tag $$+$$ the valid bit)
      - equaling $$1024*(128 + 18 + 1) = 150528$$ bits of SRAM
      - the SRAM is $$150528 / 131072 = 1.15$$ times as large as the cache size, or $$15\%$$ bigger.