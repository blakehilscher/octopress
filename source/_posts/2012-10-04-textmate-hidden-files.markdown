---
layout: post
title: "Show Hidden Files and Folders in Textmate"
date: 2012-10-04T22:14:48-04:00
comments: true
categories: 
---
<figure class='code'><figcaption><span></span></figcaption><div class="highlight"><table><tr><td class="gutter"><pre class="line-numbers"><span class='line-number'>1</span>
<span class='line-number'>2</span>
<span class='line-number'>3</span>
<span class='line-number'>4</span>
<span class='line-number'>5</span>
<span class='line-number'>6</span>
<span class='line-number'>7</span>
<span class='line-number'>8</span>
<span class='line-number'>9</span>
<span class='line-number'>10</span>
<span class='line-number'>11</span>
<span class='line-number'>12</span>
<span class='line-number'>13</span>
<span class='line-number'>14</span>
</pre></td><td class='code'><pre><code class='ruby'><span class='line'><span class="c1"># Want to show hidden files and folders in your TextMate project drawer? Simple, just modify the file and folder patterns in TextMate&#39;s preferences.</span>
</span><span class='line'>
</span><span class='line'><span class="c1"># Instructions:</span>
</span><span class='line'><span class="c1"># Go to TextMate &gt; Preferences...</span>
</span><span class='line'><span class="c1"># Click Advanced</span>
</span><span class='line'><span class="c1"># Select Folder References</span>
</span><span class='line'>
</span><span class='line'><span class="c1"># Replace the following:</span>
</span><span class='line'>
</span><span class='line'><span class="c1"># File Pattern</span>
</span><span class='line'><span class="o">!</span><span class="p">(</span><span class="sr">/\.(?!\W*)[^/</span><span class="o">]*|</span><span class="p">\</span><span class="o">.</span><span class="p">(</span><span class="n">gitkeep</span><span class="o">|</span><span class="no">DS_Store</span><span class="o">|</span><span class="n">tmproj</span><span class="o">|</span><span class="n">o</span><span class="o">|</span><span class="n">pyc</span><span class="p">)</span><span class="o">|/</span><span class="no">Icon</span><span class="p">\</span><span class="n">r</span><span class="o">|/</span><span class="n">svn</span><span class="o">-</span><span class="n">commit</span><span class="p">(\</span><span class="o">.</span><span class="n">[</span><span class="mi">2</span><span class="o">-</span><span class="mi">9</span><span class="o">]</span><span class="p">)</span><span class="sc">?\</span><span class="o">.</span><span class="n">tmp</span><span class="p">)</span><span class="err">$</span>
</span><span class='line'>
</span><span class='line'><span class="c1"># Folder Pattern</span>
</span><span class='line'><span class="o">!.</span><span class="n">*</span><span class="o">/</span><span class="p">(</span><span class="o">.</span><span class="n">git</span><span class="o">|</span><span class="no">CVS</span><span class="o">|</span><span class="n">_darcs</span><span class="o">|</span><span class="n">_MTN</span><span class="o">|</span><span class="p">\{</span><span class="n">arch</span><span class="p">\}</span><span class="o">|</span><span class="n">blib</span><span class="o">|.</span><span class="n">*</span><span class="o">~</span><span class="p">\</span><span class="o">.</span><span class="n">nib</span><span class="o">|.</span><span class="n">*</span><span class="p">\</span><span class="o">.</span><span class="p">(</span><span class="n">framework</span><span class="o">|</span><span class="n">app</span><span class="o">|</span><span class="n">pbproj</span><span class="o">|</span><span class="n">pbxproj</span><span class="o">|</span><span class="n">xcode</span><span class="p">(</span><span class="n">proj</span><span class="p">)?</span><span class="o">|</span><span class="n">bundle</span><span class="p">))</span><span class="err">$</span>
</span></code></pre></td></tr></table></div></figure>
