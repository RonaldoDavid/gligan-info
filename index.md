---
layout: default
---

<style>
	.links {
  margin: 50px 10px 50px 0;
}

.links span {
  display: block;
  /* font-weight: bold; */
  font-size: 23px;
  text-transform: uppercase;
  font-style: italic;
  margin: 25px 5px;
}

.links a {
  font-weight: bolder;
  padding-right: 20px;
  position: relative;
  transition: .3s;
}

.links a:hover {
  opacity: 1;
  padding-right: 35px;
}

.links a::after {
  content: " →";
  position: absolute;
  right: 0;
  top: 50%;
  transform: translate(0, -50%);
}

@media screen and (max-width: 600px) {
  .links a {
    margin: 5px 0;
    display: block;
  }
}
</style>

<section>

<h1>Ronaldo David Gomes Gligan</h1>

<p>Hey! I'm <b>Ronaldo David Gomes Gligan</b> and I work as a
<b>Programmer</b> from the age of 8, I like too much the web but I
also know C (Arduino), PHP &amp; Python.</p>

<div class="links">
	<span class="link">
	  Check out my <a href="./blog">Blog</a>
	</span>
	<span class="link">
	  Look at my <a href="./social">Social Networks</a>
	</span>
	<span class="link">
	  Read more <a href="./about">About me</a>
	</span>
	<span class="link">
	  See my <a href="./gallery">Gallery</a>
	</span>
</div>

<p>Apart from programming I like to <b>write</b>. I have written
several books and guides and I have some more projects, here I leave
you some of my work:</p>




<h2>Articles</h2>

{% for post in site.posts %}
	{% unless post.next %}
		<h3 class="code">{{ post.date | date: '%Y' }}</h3>
	{% else %}
		{% capture year %}{{ post.date | date: '%Y' }}{% endcapture %}
		{% capture nyear %}{{ post.next.date | date: '%Y' }}{% endcapture %}
		{% if year != nyear %}
			<h3 class="code">{{ post.date | date: '%Y' }}</h3>
		{% endif %}
	{% endunless %}

	<ul>
		<li>
			<div class="post-date code">
				<span>{{ post.date | date: "%b %d" }}</span>
			</div>
			<div class="title">
				<a href="{{ post.url | prepend: site.baseurl | prepend: site.url }}">{{ post.title }}</a>
			</div>
		</li>
	</ul>

{% endfor %}

</section>