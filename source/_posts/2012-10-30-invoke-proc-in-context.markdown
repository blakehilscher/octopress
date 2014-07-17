---
layout: post
title: "Invoke a proc in the context of another object"
date: 2012-10-30T22:14:48-04:00
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
<span class='line-number'>15</span>
<span class='line-number'>16</span>
<span class='line-number'>17</span>
<span class='line-number'>18</span>
<span class='line-number'>19</span>
<span class='line-number'>20</span>
<span class='line-number'>21</span>
<span class='line-number'>22</span>
</pre></td><td class='code'><pre><code class='ruby'><span class='line'><span class="k">class</span> <span class="nc">ObjectContext</span>
</span><span class='line'>
</span><span class='line'>  <span class="k">def</span> <span class="nf">initialize</span>
</span><span class='line'>    <span class="vi">@number</span> <span class="o">=</span> <span class="mi">10</span>
</span><span class='line'>  <span class="k">end</span>
</span><span class='line'>
</span><span class='line'>  <span class="k">def</span> <span class="nf">evaluate</span><span class="p">(</span><span class="nb">proc</span><span class="p">)</span>
</span><span class='line'>    <span class="n">instance_exec</span> <span class="o">&amp;</span><span class="nb">proc</span>
</span><span class='line'>  <span class="k">end</span>
</span><span class='line'>
</span><span class='line'><span class="k">end</span>
</span><span class='line'>
</span><span class='line'><span class="c1"># our multiplication proc</span>
</span><span class='line'><span class="n">t</span> <span class="o">=</span> <span class="o">-&gt;</span> <span class="p">{</span> <span class="nb">puts</span><span class="p">(</span> <span class="vi">@number</span> <span class="o">*</span> <span class="vi">@number</span><span class="p">)</span> <span class="p">}</span>
</span><span class='line'>
</span><span class='line'><span class="c1"># evaluate in current context</span>
</span><span class='line'><span class="vi">@number</span> <span class="o">=</span> <span class="mi">5</span>
</span><span class='line'><span class="n">t</span><span class="o">.</span><span class="n">call</span> <span class="c1">#=&gt; 25 </span>
</span><span class='line'>
</span><span class='line'><span class="c1"># evaluate in context of an ObjectFactory instance </span>
</span><span class='line'><span class="n">o</span> <span class="o">=</span> <span class="no">ObjectContext</span><span class="o">.</span><span class="n">new</span>
</span><span class='line'><span class="n">o</span><span class="o">.</span><span class="n">evaluate</span><span class="p">(</span><span class="n">t</span><span class="p">)</span> <span class="c1">#=&gt; 100</span>
</span></code></pre></td></tr></table></div></figure>
