---
layout: post
title:  "How do you parse HTML and XML in PHP"
date:   2014-03-27 15:52:46
categories: php
---

Most of us wonder need to parse HTML and XML in PHP every once in a while. This is how it's done.

Actually, PHP makes it really easy - it has the solution built-in.


Parse HTML in PHP
{% highlight php %}
<?php
$html = '<p><img src="http://www.example.com/example.png" alt="example" /></p>';
$dom = new DOMDocument;
$dom->loadHTML($html);
$imgs = $dom->getElementsByTagName('img');
?>
{% endhighlight %}

Parse XML in PHP:
{% highlight php %}
<?php
$xml = '<?xml version="1.0" encoding="utf-8"?>
<companies>
 <company>Google</company>
 <company>Yahoo</company>
 <company>Microsoft</company>
</companies>';

$dom = new DOMDocument;
$dom->loadXML($xml);
$companies = $dom->getElementsByTagName('company');
foreach ($companies as $company) {
    echo $company->nodeValue;
}
?>
{% endhighlight %}



