---
layout: cv
title: Resume
permalink: resume/
jsarr:
- js/scripts.js
---

<h1 id="cv-title"><a href="{{ site.url }}">David Kartchner</a></h1>

<p id="cv-subtitle"><i>Researcher + Entrepreneur (<span class="cv-ai">ML</span> + <span class="cv-vis">Biomedicine</span>)</i></p>

<!-- <div id="cv-toc">
<ul class="cv-description">
	<li>Education</li>
	<li>Industry Experience</li>
	<li>Academic Research</li>
	<li>Honors and Awards</li>
	<li>Publications</li>
	<li>Talks</li>
	<li>Press</li>
	<li>Teaching</li>
	<li>Mentoring</li>
	<li>Grants and Funding</li>
	<li>Service</li>
	<li>References</li>
</ul>
</div> -->

<div>
I research how to enable <b><span class="cv-ai">natural language processing</span></b> (NLP) on new and dynamic problems by developing generative means of structuring data via  <b><span class="cv-ai">large language models (LLMs)</span></b> and <b><span class="cv-ai">knowledge graphs</span></b>.  I use these technologies to structure <b><span class="cv-vis">clinical data</span></b>  and <b><span class="cv-vis">biomedical research</span></b> , enabling clinicians to customizably curate structured data from any unstructured text.

<!-- I apply these technologies to  <b><span class="cv-vis">healthcare</span></b> and <b><span class="cv-vis">biomedicine</span></b> to enable clinical researchers to better understand disease etiology by . -->
</div>

<div class="cv-spacer"></div>

<div>
I have collaborated with researchers, developers, and clinicians while working at Enveda Biosciences, Facebook, GSK, Recursion Pharmaceuticals, and Intermountain Healthcare.
</div>

<!-- <div class="cv-spacer"></div>

<div>
My research is supported by a NASA Space Technology Research Fellowship.
</div> -->

<div class="cv-spacer"></div>

<div class="cv-image-links-wrapper">
	<div class="cv-image-links">
		{% for link in site.data.social-links %}
			{% if link.cv-group == 1 %}
				{% include social-link.html link=link %}
			{% endif %}
		{% endfor %}
	</div>
	<div class="cv-image-links">
		{% for link in site.data.social-links %}
			{% if link.cv-group == 2 %}
				{% include social-link.html link=link %}
			{% endif %}
		{% endfor %}
	</div>
</div>

***

## Education

{::nomarkdown}
{% for degree in site.data.education %}
{% include cv/degree.html degree=degree %}
{% endfor %}
{:/}

## Industry Experience

{% for experience in site.data.experiences %}
{% if experience.type == 'industry' %}
{% if experience.resume %}
{% include cv/experience.html experience=experience %}
{% endif %}
{% endif %}
{% endfor %}

## Academic Research Experience

{% for experience in site.data.experiences %}
{% if experience.type == 'academic' %}
{% if experience.resume %}
{% include cv/experience.html experience=experience %}
{% endif %}
{% endif %}
{% endfor %}

## Honors and Awards

{% for award in site.data.awards %}
{% include cv/award.html award=award %}
{% endfor %}

## Selected Publications

{% assign selectedBoolForBibtex = true %}

{% assign selected = site.categories.papers | where: 'selected', true %}
{% for pub in selected %}
{% include cv/publication.html pub=pub %}
{% endfor %}
<!-- 
### All Publications

{% assign selectedBoolForBibtex = false %}

### Journal

{% assign journal = site.categories.papers | where: 'type', "journal" %}
{% for pub in journal %}
{% include cv/publication.html pub=pub selectedBoolForBibtex=selectedBoolForBibtex %}
{% endfor %}

### Conference

{% assign conference = site.categories.papers | where: 'type', "conference" %}
{% for pub in conference %}
{% include cv/publication.html pub=pub selectedBoolForBibtex=selectedBoolForBibtex %}
{% endfor %}

### Workshop

{% assign workshop = site.categories.papers | where: 'type', "workshop" %}
{% for pub in workshop %}
{% include cv/publication.html pub=pub selectedBoolForBibtex=selectedBoolForBibtex %}
{% endfor %}

### Poster

{% assign poster = site.categories.papers | where: 'type', "poster" %}
{% for pub in poster %}
{% include cv/publication.html pub=pub selectedBoolForBibtex=selectedBoolForBibtex %}
{% endfor %}

<!-- ### Demo

{% assign demo = site.categories.papers | where: 'type', "demo" %}
{% for pub in demo %}
{% include cv/publication.html pub=pub selectedBoolForBibtex=selectedBoolForBibtex %}
{% endfor %} -->

### Miscellaneous

{% assign preprint = site.categories.papers | where: 'type', "misc" %}
{% for pub in preprint %}
{% include cv/publication.html pub=pub selectedBoolForBibtex=selectedBoolForBibtex %}
{% endfor %}




<!-- 
## Talks

{% assign talktitles = site.data.talks | group_by:"title" %}
{% for title in talktitles %}
{% include cv/talk.html talk=title %}
{% endfor %}

## Press

{% for press in site.data.press %}
{% include cv/press.html press=press %}
{% endfor %}

## Teaching

{% for teach in site.data.teaching %}
{% include cv/teaching.html teach=teach %}
{% endfor %}

## Mentoring

{::nomarkdown}
{% for mentee in site.data.mentoring %}
{% include cv/mentee.html mentee=mentee %}
{% endfor %}
{:/} -->


## Volunteer & Leadership Experience

<!-- <div class="cv-service-title"><b>Community Outreach</b></div> -->
{% for volunteer in site.data.volunteer %}
{% if volunteer.resume == true %}
{% include cv/volunteer.html volunteer=volunteer %}
{% endif %}
{% endfor %}    

<!-- <div class="cv-service-title"><b>Organizer</b></div>
{% for venue in site.data.organizer %}
{% include cv/venue.html venue=venue %}
{% endfor %}

<div class="cv-service-title"><b>Program Commitee</b></div>
{% for venue in site.data.pc %}
{% include cv/venue.html venue=venue %}
{% endfor %} -->

<!-- <div class="cv-service-title"><b>Reviewer</b></div>
{% for venue in site.data.reviewer %}
{% include cv/venue.html venue=venue %}
{% endfor %}  -->

<!-- <div class="cv-service-title"><b>Institutional</b></div>
{% for institution in site.data.institutional %}
{% include cv/institutional.html institution=institution %}
{% endfor %}

<div class="cv-service-title"><b>Member</b></div>
{% for member in site.data.memberships %}
{% include cv/member.html member=member %}
{% endfor %} -->


## Technical Skills

{% for skill in site.data.skills %}
{% include cv/skill.html skill=skill %}
{% endfor %}

<!-- ## Design

{% for design in site.data.designs %}
{% include cv/design.html design=design %}
{% endfor %} -->

## References

{% for reference in site.data.references %}
{% include cv/reference.html reference=reference %}
{% endfor %}

<!-- 
## Contact

David Kartchner 
`david.kartchner@gatech.edu`  
CODA Tech Square  
Georgia Tech  
756 W Peachtree St NW  
Atlanta, GA 30308
<span style="background: linear-gradient(0deg, #34495e, #3498db); -webkit-background-clip: text; -webkit-text-fill-color: transparent; display: block">
—  
USA  
Earth  
Solar System  
Milky Way  
Local Group  
Universe  
</span> -->


[cv]: /cv.pdf "My CV."

[pathology-dynamics]: https://sites.gatech.edu/cassie-mitchell-lab/ "Pathology Dynamics Lab"
[gt]: http://gatech.edu "Georgia Tech"
[cse]: http://cse.gatech.edu "GT Computational Science and Engineering"
[coc]: http://www.cc.gatech.edu "GT College of Computing"

[david]: http://davidkartchner.com "David Kartchner"

[github]: https:/www.github.com/davidkartchner "github.com/davidkartchner"

