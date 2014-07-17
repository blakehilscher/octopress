---
layout: post
title: "Grape API Formatter for Sending Inline Data"
date: 2013-03-10T22:14:48-04:00
comments: true
categories: [grape, rails, ruby, snippets]
excerpt: test
---

<p>I needed to add a .png formatter to the <a href="http://quandl.com/help/api">quandl</a> Grape API.</p>

<p>The png is generated using phantomjs, so it needed to be sent down inline.</p>

<figure class='code'><figcaption><span></span></figcaption><div class="highlight"><table><tr><td class="gutter"><pre class="line-numbers"><span class='line-number'>1</span>
<span class='line-number'>2</span>
<span class='line-number'>3</span>
<span class='line-number'>4</span>
<span class='line-number'>5</span>
<span class='line-number'>6</span>
<span class='line-number'>7</span>
</pre></td><td class='code'><pre><code class='ruby'><span class='line'><span class="n">content_type</span> <span class="ss">:png</span><span class="p">,</span> <span class="s2">&quot;image/png&quot;</span>
</span><span class='line'>
</span><span class='line'><span class="n">formatter</span> <span class="ss">:png</span><span class="p">,</span> <span class="nb">lambda</span> <span class="p">{</span> <span class="o">|</span><span class="n">response</span><span class="p">,</span> <span class="n">env</span><span class="o">|</span>
</span><span class='line'>    <span class="n">path</span> <span class="o">=</span> <span class="n">response</span><span class="o">.</span><span class="n">try</span><span class="p">(</span><span class="ss">:object</span><span class="p">)</span><span class="o">.</span><span class="n">try</span><span class="p">(</span><span class="ss">:to_png</span><span class="p">)</span>
</span><span class='line'>    <span class="n">rack</span> <span class="o">=</span> <span class="ss">Rack</span><span class="p">:</span><span class="ss">:Response</span><span class="o">.</span><span class="n">new</span><span class="p">(</span><span class="no">File</span><span class="o">.</span><span class="n">read</span><span class="p">(</span><span class="n">path</span><span class="p">)</span> <span class="p">,</span> <span class="mi">200</span><span class="p">,</span> <span class="p">{</span> <span class="s2">&quot;Content-type&quot;</span> <span class="o">=&gt;</span> <span class="s2">&quot;image/png&quot;</span> <span class="p">})</span><span class="o">.</span><span class="n">finish</span>
</span><span class='line'>    <span class="n">rack</span><span class="o">[</span><span class="mi">2</span><span class="o">].</span><span class="n">body</span><span class="o">[</span><span class="mi">0</span><span class="o">]</span>
</span><span class='line'><span class="p">}</span>
</span></code></pre></td></tr></table></div></figure>
