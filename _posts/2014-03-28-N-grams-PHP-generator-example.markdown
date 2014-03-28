---
layout: post
title:  "N-grams PHP generator example"
date:   2014-03-28 15:52:46
categories: php
---

N-grams are useful for many situations - but you might need to use them when you're developing a search solution.

Here's an example on how to generate an array with all the N-grams for an specific word.

{% highlight php %}
<?php

function ngrams($word, $min_gram_length = 2) {
        $ngrams = array();
        $word = trim($word);
        $len = strlen($word);
        $max_gram_length = $len - 1;
         
        //BEGIN N-GRAM SIZE LOOP $a
         
        for ($a = $min_gram_length; $a <= $max_gram_length; $a++) { //BEGIN N-GRAM SIZE LOOP $a
             
            for ($pos = 0; $pos < $len; $pos ++ {  //BEGIN POSITION WITHIN WORD $pos
                 
                if(($pos + $a -1) < $len) {  //IF THE SUBSTRING WILL NOT EXCEED THE END OF THE WORD
                 
                $ngrams[] = substr($word, $pos, $a);
 
                }  //END IF THE SUBSTRING WILL NOT EXCEED THE END OF THE WORD
             
            } //END POSITION WITHIN WORD $pos
         
        }  //END N-GRAM SIZE LOOP $a
         
        $ngrams = array_unique($ngrams);
         
return $ngrams;
}

?>
{% endhighlight %}

The example is a function `ngrams()` which has 2 arguments:
* The first, `$word`, (which is required) is the word for which you'll need the N-grams generated
* The second, `$min_gram_length`, (which is optional, default = 2) is self-explanatory - contains the minimum gram length.
