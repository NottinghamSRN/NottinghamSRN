---
title: Projects from Collaboratives
layout: page
---

These are projects from research collaboratives, working nationwide. These will often involve many students working at many hospital sites, with all the research gathered into a paper. The requirements can vary significantly, please see specific project details for more information.

<section>
	{% assign specialisms = site.projects | where_exp: "item", "item.path contains 'collaborative'" | group_by: "specialism" %}
	{% for specialism in specialisms %}
		<h2 id="{{specialism.name|default:"Other"|slugify}}">{{specialism.name|default:"Other"}}</h2>
		<div class="row">
			{% for item in specialism.items %}
				<div class="column">
					<div class="card">
						<div class="card-divider">
							<div class="row">
								<div class="column">
						    		<h3>{{item.title}}</h3>
								</div>
								<div class="column shrink">
									<a class="button" href="mailto:{{item.email}}">Contact Organiser</a>
								</div>
							</div>
						</div>
						{% if item.header_img %}
							<img src="{{item.header_img}}" />
						{% endif %}
						<div class="card-section">
							<dl>
								{% include components/project-info.html info=item %}
								<dt>Description</dt>
								<dd>
									{{item.content | markdownify }}
								</dd>
							</dl>
						</div>
					</div>
				</div>
			{% endfor %}
		</div>
	{% endfor %}
</section>
