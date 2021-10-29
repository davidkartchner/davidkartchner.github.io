---
layout: home
title: Home
---

<div id ="intro-wrapper" class="l-middle">
	<div id="intro-title-wrapper" class="intro-left">
		<h1 id="intro-title">Hi, I'm David Kartchner</h1>
		<div id="intro-subtitle">
			I'm a PhD Student at Georgia Tech 
		</div>
	</div>
	<div class="intro-left">
	<div class="intro-left">
		I research how to enable <b><span class="cv-ai">natural language processing</span></b> on new and dynamic problems by developing ai-driven models for scalable data labeling powered by active learning and weak supervision. I apply these technologies to  <b><span class="cv-vis">healthcare</span></b> and <b><span class="cv-vis">biomedicine</span></b> to enable clinical researchers to better understand disease etiology and improve care delivery.  
	</div>
	<div style="height: 1rem"></div>
	<div class="intro-left">
		I currently work with <a href="https://bme.gatech.edu/bme/faculty/Cassie-S.-Mitchell">Cassie Mitchell</a> in the <a href="https://sites.gatech.edu/cassie-mitchell-lab">Laboratory for Pathology Dynamics</a>. I previsouly completed a MS in Mathematics from Brigham Young University advised by <a href="https://math.byu.edu/~jeffh/">Jeff Humpherys</a>.
	</div>
	<div style="height: 1rem"></div>
    <div>
        I have collaborated with scientists, developers, clinicians, and epidemiologists while working at Facebook, GlaxoSmithKline, Recursion Pharmaceuticals, and Intermountain Healthcare.
    </div>
	<!-- <div>
		I have collaborated with designers, developers, and scientists while working at <img class="intro-logo" style="width: 19px; padding-bottom: 5px;" src="/images/apple.svg"> Apple, <img class="intro-logo" style="width: 18px; padding-bottom: 3px;" src="/images/microsoft.svg"> Microsoft Research, <img class="intro-logo" style="width: 24px" src="/images/nasa.svg"> NASA Jet Propulsion Lab, and <img class="intro-logo" style="width: 24px;" src="/images/pnnl.svg"> Pacific Northwest National Lab.
	</div> -->
	<!-- <div style="height: 1rem"></div>
	<div>
		My research is supported by a <a href="https://www.nasa.gov/strg/nstrf">NASA Space Technology Research Fellowship</a>.
	</div> -->
</div>

<div class="intro-right">
	<img id="intro-image" class="intro-right" src="/images/portrait.png">
	<div style="height: 0.5rem"></div>
	<div id="intro-image-links" class="intro-right">
		{% for link in site.data.social-links %}
			{% if link.on-homepage == true %}
				{% include social-link.html link=link %}
			{% endif %}
		{% endfor %}
	</div>
	<div style="height: 0.5rem"></div>
	<div id="intro-cv-wrapper" class="intro-right">
		{% for link in site.data.social-links %}
			{% if link.id == "cv-web" %}
				{% include social-link.html link=link %}
			{% endif %}
		{% endfor %}
	</div>
	</div>
</div>

<hr class="l-middle home-hr">

<h2 class="feature-title l-middle">
	Featured <a href="/cv#publications">Research Publications</a>
</h2>
<div class="cover-wrapper l-screen">
	{% assign sortedPublications = site.categories.papers | sort: 'feature-order' %}
	{% for feature in sortedPublications %}
		{% if feature.featured == true %}
			{% include feature.html feature=feature %}
		{% endif %}
	{% endfor %}
</div>

<h2 class="feature-title l-middle">
	<a href="{{ site.url }}/everything-else" style="color: #303030">Everything Else</a>
</h2>
<div id="everything-else" class="l-middle">
	<a href="{{ site.url }}/projects"><div>Projects</div></a>
	<a href="{{ site.url }}/blog"><div>Blog</div></a>
	<a href="{{ site.url }}/archive"><div>Archive</div></a>
</div>
<!-- <p class="l-middle intro-text" markdown="1">
	Including a list of [projects][projects], the [blog][blog], [monthly music playlists][monthly-music], [stuff I use][stuff-i-use], and the [archive][archive].
</p> -->



[gt]: http://www.gatech.edu "Georgia Tech"
[cse]: http://cse.gatech.edu "Georgia Tech Computational Science and Engineering"
[coc]: http://www.cc.gatech.edu "Georgia Tech College of Computing"

[cv]: {{ site.url }}/cv