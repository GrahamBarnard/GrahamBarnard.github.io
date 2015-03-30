---
layout: default
title: CV
permalink: /cv/
comments: false
---

<div class="profile">
	{% if site.logourl != "" %}<img src="{{ site.logourl }}" class="profileimage" alt="user">{% endif %}
	<h4>{{ site.title }}</h4>
	<p>{{ site.description }}</p>
	<hr>
</div>

<section class="posts wrapper">
	<article class="cv">
		<h1><i class="fa fa-cloud"></i>Summary</h1>
		<div class="excerpt">
			Professional developer working with all aspect of Salesforce.
		</div>
	</article>
	<article class="cv">
		<h1><i class="fa fa-briefcase"></i>Work Experience</h1>
		<h4>Senior Salesforce Developer at Traction on Demand</h4>
		<span>{{ "2014-08-01 12:00:00" | date: "%B %Y" }} - Now | Vancouver BC, Canada</span><br>
		<div class="excerpt">
			<ul>
				<li>Development on various Enterprise Salesforce Project including Apex classes, Visualforce pages, Batch jobs and Unit Tests</li>
				<li>Performing Code Reviews and Code Quality Audits</li>
				<li>Creating Automation Systems</li>
			</ul>
		</div>

		<h4>Salesforce Developer at Lightspeed Retail</h4>
		<span>{{ "2013-03-01 12:00:00" | date: "%B %Y" }} - {{ "2014-08-01 12:00:00" | date: "%B %Y" }} | Montreal, QC Canada</span><br>
		<div class="excerpt">
			<ul>
				<li>Redesigned a customer web portal</li>
				<li>Created REST Web Services to interact between different APIs including Salesforce, Zendesk, Braintree, User Voice and internal systems</li>
				<li>Created Salesforce API integration with external systems, Apex development, Visualforce pages</li>
			</ul>
		</div>	

		<h4>Intermediate Web and Mobile Developer at Walsh Integrated</h4>
		<span>{{ "2011-12-01 12:00:00" | date: "%B %Y" }} - {{ "2013-01-01 12:00:00" | date: "%B %Y" }} | Montreal, QC Canada</span><br>
		<div class="excerpt">
			<ul>
				<li>Redesigned and maintained a PHP CodeIgniter system</li>
				<li>Created REST Web Services for new mobile applications</li>
				<li>Maintained 2 Android mobile projects</li>
				<li>Maintained a Windows Mobile 6 application built in C#</li>
			</ul>
		</div>

		<h4>Freelance Web Developer</h4>
		<span>{{ "2011-02-01 12:00:00" | date: "%B %Y" }} - {{ "2011-11-01 12:00:00" | date: "%B %Y" }} | Montreal, QC Canada</span><br>
		<div class="excerpt">
			<ul>
				<li>Developed websites in a wide variety of control management system: Wordpress, Joomla, Magento, ExpressionEngine, etc</li>
				<li>Front End Development using HTML5, CSS3 and Javascript/jQuery</li>
			</ul>
		</div>

		<h4>Automation Scripter at Presagis</h4>
		<span>{{ "2007-01-01 12:00:00" | date: "%B %Y" }} - {{ "2007-09-01 12:00:00" | date: "%B %Y" }} | Montreal, QC Canada</span><br>
		<div class="excerpt">
			<ul>
				<li>Created automation scripts using the SilkTest language</li>
				<li>Created test documentation</li>
				<li>Software Tester for multiple products</li>
			</ul>
		</div>
	</article>

	<article class="cv">
		<h1><i class="fa fa-certificate"></i>Education & Certification</h1>
		<h4>Salesforce.com Certified Force.com Developer</h4>
		<span>February 2014</span><br>

		<h4>Bachelor of Computer Science Specializing In Web Services</h4>
		<span>September 2008 to December 2010 | University of Concordia</span><br>

		<h4>DCS, Computer Science</h4>
		<span>September 2005 to May 2008 | CEGEP John Abbott College</span><br>

	</article>
	
	<article class="cv">
		<h1><i class="fa fa-cogs"></i>Skills</h1>
		<div class="skill">
			<div class="name">Apex (100%)</div>
			<div class="progress">
				<div class="bar" style="width: 100%"></div>
			</div>
		</div>

		<div class="skill">
			<div class="name">Visualforce Pages (90%)</div>
			<div class="progress">
				<div class="bar" style="width: 90%"></div>
			</div>
		</div>

		<div class="skill">
			<div class="name">Javascript (80%)</div>
			<div class="progress">
				<div class="bar" style="width: 80%"></div>
			</div>
		</div>

		<div class="progress">
			<div class="bar" style="width: 90%;"></div>
		</div>

		<div class="skill">
			<div class="name">Python (50%)</div>
			<div class="progress">
				<div class="bar" style="width: 50%"></div>
			</div>
		</div>

		<div class="skill">
			<div class="name">PHP (90%)</div>
			<div class="progress">
				<div class="bar" style="width: 90%"></div>
			</div>
		</div>

		<div class="skill">
			<div class="name">Git (90%)</div>
			<div class="progress">
				<div class="bar" style="width: 80%"></div>
			</div>
		</div>

		<div class="skill">
			<div class="name">CSS (75%)</div>
			<div class="progress">
				<div class="bar" style="width: 75%"></div>
			</div>
		</div>

		<div class="skill">
			<div class="name">Java (50%)</div>
			<div class="progress">
				<div class="bar" style="width: 75%"></div>
			</div>
		</div>

		<div class="skill">
			<div class="name">CSS (75%)</div>
			<div class="progress">
				<div class="bar" style="width: 75%"></div>
			</div>
		</div>

	</article>
</section>