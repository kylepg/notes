<title>misc - markdown</title>

<h2>Syntax guide</h2>

<p>Here’s an overview of Markdown syntax that you can use anywhere on GitHub.com or in your own text files.</p>

<h3>Headers</h3>

<div class="language-markdown highlighter-rouge"><div class="highlight"><pre class="highlight"><code><span class="gh"># This is an &lt;h1&gt; tag</span>
<span class="gu">## This is an &lt;h2&gt; tag</span>
<span class="gu">###### This is an &lt;h6&gt; tag</span>
</code></pre></div></div>

<h3>Emphasis</h3>

<div class="language-markdown highlighter-rouge"><div class="highlight"><pre class="highlight"><code><span class="ge">*This text will be italic*</span>
<span class="ge">_This will also be italic_</span>

<span class="gs">**This text will be bold**</span>
<span class="gs">**This will also be bold**</span>

<span class="ge">_You **can** combine them_</span>
</code></pre></div></div>

<h3>Lists</h3>

<h4>Unordered</h4>

<div class="language-markdown highlighter-rouge"><div class="highlight"><pre class="highlight"><code><span class="p">*</span> Item 1
<span class="p">*</span> Item 2
<span class="p">  *</span> Item 2a
<span class="p">  *</span> Item 2b
</code></pre></div></div>

<h4>Ordered</h4>

<div class="language-markdown highlighter-rouge"><div class="highlight"><pre class="highlight"><code><span class="p">1.</span> Item 1
<span class="p">1.</span> Item 2
<span class="p">1.</span> Item 3
<span class="p">   1.</span> Item 3a
<span class="p">   1.</span> Item 3b
</code></pre></div></div>

<h3>Images</h3>

<div class="language-markdown highlighter-rouge"><div class="highlight"><pre class="highlight"><code><span class="p">![</span><span class="nv">GitHub Logo</span><span class="p">](</span><span class="sx">/images/logo.png</span><span class="p">)</span>
Format: !<span class="p">[</span><span class="nv">Alt Text</span><span class="p">](</span><span class="sx">url</span><span class="p">)</span>
</code></pre></div></div>

<h3>Links</h3>

<div class="language-markdown highlighter-rouge"><div class="highlight"><pre class="highlight"><code>http://github.com - automatic!
<span class="p">[</span><span class="nv">GitHub</span><span class="p">](</span><span class="sx">http://github.com</span><span class="p">)</span>
</code></pre></div></div>

<h3>Blockquotes</h3>

<div class="language-markdown highlighter-rouge"><div class="highlight"><pre class="highlight"><code>As Kanye West said:
<span class="gt">
&gt; We're living the future so</span>
<span class="gt">&gt; the present is our past.</span>
</code></pre></div></div>

<h3>Inline code</h3>

<div class="highlighter-rouge"><div class="highlight"><pre class="highlight"><code>I think you should use an
`&lt;addr&gt;` element here instead.
</code></pre></div></div>

<p><a id="GitHub-flavored-markdown" title="GFM" class="toc-item"></a></p>

<h2>GitHub Flavored Markdown</h2>

<p>GitHub.com uses its own version of the Markdown syntax that provides an additional set of useful features, many of which make it easier to work with content on GitHub.com.</p>

<p>Note that some features of GitHub Flavored Markdown are only available in the descriptions and comments of Issues and Pull Requests. These include @mentions as well as references to SHA-1 hashes, Issues, and Pull Requests. Task Lists are also available in Gist comments and in Gist Markdown files.</p>

<h3>Syntax highlighting</h3>

<p>Here’s an example of how you can use syntax highlighting with <a href="https://help.github.com/articles/basic-writing-and-formatting-syntax/">GitHub Flavored Markdown</a>:</p>

<div class="highlighter-rouge"><div class="highlight"><pre class="highlight"><code>```javascript
function fancyAlert(arg) {
  if(arg) {
    $.facebox({div:'#foo'})
  }
}
```
</code></pre></div></div>

<p>You can also simply indent your code by four spaces:</p>

<div class="highlighter-rouge"><div class="highlight"><pre class="highlight"><code>    function fancyAlert(arg) {
      if(arg) {
        $.facebox({div:'#foo'})
      }
    }
</code></pre></div></div>

<p>Here’s an example of Python code without syntax highlighting:</p>

<div class="highlighter-rouge"><div class="highlight"><pre class="highlight"><code>def foo():
    if not bar:
        return True
</code></pre></div></div>

<h3>Task Lists</h3>

<div class="highlighter-rouge"><div class="highlight"><pre class="highlight"><code>- [x] @mentions, #refs, [links](), **formatting**, and &lt;del&gt;tags&lt;/del&gt; supported
- [x] list syntax required (any unordered or ordered list supported)
- [x] this is a complete item
- [ ] this is an incomplete item
</code></pre></div></div>

<p>If you include a task list in the first comment of an Issue, you will get a handy progress indicator in your issue list. It also works in Pull Requests!</p>

<h3>Tables</h3>

<p>You can create tables by assembling a list of words and dividing them with hyphens <code class="highlighter-rouge">-</code> (for the first row), and then separating each column with a pipe <code class="highlighter-rouge">|</code>:</p>

<div class="highlighter-rouge"><div class="highlight"><pre class="highlight"><code>First Header | Second Header
------------ | -------------
Content from cell 1 | Content from cell 2
Content in the first column | Content in the second column
</code></pre></div></div>

<p>Would become:</p>

<table>
  <thead>
    <tr>
      <th>First Header</th>
      <th>Second Header</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Content from cell 1</td>
      <td>Content from cell 2</td>
    </tr>
    <tr>
      <td>Content in the first column</td>
      <td>Content in the second column</td>
    </tr>
  </tbody>
</table>

<h3>SHA references</h3>

<p>Any reference to a commit’s <a href="http://en.wikipedia.org/wiki/SHA-1">SHA-1 hash</a> will be automatically converted into a link to that commit on GitHub.</p>

<div class="highlighter-rouge"><div class="highlight"><pre class="highlight"><code>16c999e8c71134401a78d4d46435517b2271d6ac
mojombo@16c999e8c71134401a78d4d46435517b2271d6ac
mojombo/github-flavored-markdown@16c999e8c71134401a78d4d46435517b2271d6ac
</code></pre></div></div>

<h3>Issue references within a repository</h3>

<p>Any number that refers to an Issue or Pull Request will be automatically converted into a link.</p>

<div class="highlighter-rouge"><div class="highlight"><pre class="highlight"><code>#1
mojombo#1
mojombo/github-flavored-markdown#1
</code></pre></div></div>

<h3>Username @mentions</h3>

<p>Typing an <code class="highlighter-rouge">@</code> symbol, followed by a username, will notify that person to come and view the comment. This is called an “@mention”, because you’re <em>mentioning</em> the individual. You can also @mention teams within an organization.</p>

<h3>Automatic linking for URLs</h3>

<p>Any URL (like <code class="highlighter-rouge">http://www.github.com/</code>) will be automatically converted into a clickable link.</p>

<h3>Strikethrough</h3>

<p>Any word wrapped with two tildes (like <code class="highlighter-rouge">~~this~~</code>) will appear crossed out.</p>

<h3>Emoji</h3>

<p>GitHub supports <a href="https://help.github.com/articles/basic-writing-and-formatting-syntax/#using-emoji">emoji</a>! <img class="emoji" title=":sparkles:" alt=":sparkles:" src="https://assets-cdn.github.com/images/icons/emoji/unicode/2728.png" height="20" width="20"> <img class="emoji" title=":camel:" alt=":camel:" src="https://assets-cdn.github.com/images/icons/emoji/unicode/1f42b.png" height="20" width="20"> <img class="emoji" title=":boom:" alt=":boom:" src="https://assets-cdn.github.com/images/icons/emoji/unicode/1f4a5.png" height="20" width="20"></p>

<p>To see a list of every image we support, check out the <a href="http://www.emoji-cheat-sheet.com/">Emoji Cheat Sheet</a>.</p>
