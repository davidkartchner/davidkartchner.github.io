---
layout: home
title: Home
---

<div id ="intro-wrapper" class="l-middle">
	<div id="intro-title-wrapper" class="intro-left">
		<h1 id="intro-title">Hi, I'm David Kartchner</h1>
		<div id="intro-subtitle">
			I'm an AI/ML researcher at <a href="https://truveta.com">Truveta</a>
		</div>
	</div>
	<div class="intro-left">
	<div class="intro-left">
		I build <b><span class="cv-ai">large language models (LLMs)</span></b> to extract, synthesize, and rigorously analyze biomedical data to power applications in <b><span class="cv-vis">biomedicine</span></b>, <b><span class="cv-vis">drug discovery</span></b> and <b><span class="cv-vis">healthcare</span></b>.  I am currently building Truveta's proprietary language model powered by the electronic health records of 120 million patients.  
		<!-- I research how to enable <b><span class="cv-ai">natural language processing</span></b> on new and dynamic problems by developing ai-driven models for scalable data labeling powered by active learning and weak supervision. I apply these technologies to  <b><span class="cv-vis">healthcare</span></b> and <b><span class="cv-vis">biomedicine</span></b> to enable clinical researchers to better understand disease etiology and improve care delivery.   -->
	</div>
	<div style="height: 1rem"></div>
	<div class="intro-left">
		Prior to Truveta, I was a PhD student in the <a href="https://sites.gatech.edu/cassie-mitchell-lab">Laboratory for Pathology Dynamics</a> advised by <a href="https://bme.gatech.edu/bme/faculty/Cassie-S.-Mitchell">Cassie Mitchell</a>. My dissertation research focused on <b><span class="cv-ai">semi-supervised learning</span></b> and <b><span class="cv-ai">large language models (LLMs)</span></b> for knowledge graph construction and information extraction with limited to no labeled data. I previsouly completed a MS in Mathematics from Brigham Young University advised by <a href="https://math.byu.edu/~jeffh/">Jeff Humpherys</a>.
	</div>
	<div style="height: 1rem"></div>
    <div>
        Prior to Truveta, I have worked in ML research across the TechBio and Healtcare at <a href="https://www.envedabio.com">Enveda Bioscienes</a>, <a href="https://www.meta.com/">Meta</a>, <a href="https://www.gsk.com">GlaxoSmithKline</a>, <a href="https://www.recursion.com">Recursion Pharmaceuticals</a>, and <a href="https://intermountainhealthcare.org">Intermountain Healthcare</a>.
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
	<img id="intro-image" class="intro-right" src="/images/portrait_2023.jpeg">
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
    <a href="{{ site.url }}/cv#publications"><div>Publications</div></a>
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