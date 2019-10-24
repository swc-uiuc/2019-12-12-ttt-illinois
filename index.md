---
layout: workshop      # DON'T CHANGE THIS.
carpentry: "swc"    # what kind of Carpentry (must be either "lc" or "dc" or "swc").  
                      # Be sure to update the Carpentry type in _config.yml as well.  
venue: "University of Illinois"
address: "131 School of Information Sciences, 501 East Daniel Street, Champaign, Illinois"
latlng: "40.1076536,-88.2336951"
country: "us"      # lowercase two-letter ISO country code such as "fr" (see https://en.wikipedia.org/wiki/ISO_3166-1)
language: "en"     # lowercase two-letter ISO language code such as "fr" (see https://en.wikipedia.org/wiki/ISO_639-1)
humandate: "Dec 12–13, 2019"    # human-readable dates for the workshop (e.g., "Feb 17-18, 2020")
humantime: "9:00 am–5:00 pm"    # human-readable times for the workshop (e.g., "9:00 am - 4:30 pm")
startdate: 2018-12-12      # machine-readable start date for the workshop in YYYY-MM-DD format like 2015-01-01
enddate: 2018-12-13        # machine-readable end date for the workshop in YYYY-MM-DD format like 2015-01-02
instructor: ["Neal Davis","Elizabeth Wickes"] # boxed, comma-separated list of instructors' names as strings, like ["Kay McNulty", "Betty Jennings", "Betty Snyder"]
helper: [""]     # boxed, comma-separated list of helpers' names, like ["Marlyn Wescoff", "Fran Bilas", "Ruth Lichterman"]
contact: ["training@cse.illinois.edu"]    # boxed, comma-separated list of contact email addresses for the host, lead instructor, or whoever else is handling questions, like ["marlyn.wescoff@example.org", "fran.bilas@example.org", "ruth.lichterman@example.org"]
collaborative_notes: https://pad.carpentries.org/2019-12-12-ttt-illinois            # optional: URL for the workshop collaborative notes, e.g. an Etherpad or Google Docs document
eventbrite: 75333447369          # optional: alphanumeric key for Eventbrite registration, e.g., "1234567890AB" (if Eventbrite is being used)
---

{% comment %} See instructions in the comments below for how to edit specific sections of this workshop template. {% endcomment %}

{% comment %}
HEADER

Edit the values in the block above to be appropriate for your workshop.
If the value is not 'true', 'false', 'null', or a number, please use
double quotation marks around the value, unless specified otherwise.
And run 'make workshop-check' *before* committing to make sure that changes are good.
{% endcomment %}


{% if page.carpentry != site.carpentry %}
<div class="alert alert-warning">
You specified <code>carpentry: {{page.carpentry}}</code> in <code>index.md</code> and
<code>carpentry: {{site.carpentry}}</code> in <code>_config.yml</code>. Make sure you edit both files. After editing <code>_config.yml</code>, you need to run <code>make serve</code> again to 
see the changes take effect locally.
</div>
{% endif %}

{% comment %}
EVENTBRITE

This block includes the Eventbrite registration widget if
'eventbrite' has been set in the header.  You can delete it if you
are not using Eventbrite, or leave it in, since it will not be
displayed if the 'eventbrite' field in the header is not set.
{% endcomment %}
{% if page.eventbrite %}
<iframe
  src="https://www.eventbrite.com/tickets-external?eid={{page.eventbrite}}&ref=etckt"
  frameborder="0"
  width="100%"
  height="280px"
  scrolling="auto">
</iframe>
{% endif %}


<h2 id="general">General Information</h2>

{% if page.latlng %}
<p id="where">
  <strong>Where:</strong>
  {{page.address}}.
  Get directions with
  <a href="//www.openstreetmap.org/?mlat={{page.latlng | replace:',','&mlon='}}&zoom=16">OpenStreetMap</a>
  or
  <a href="//maps.google.com/maps?q={{page.latlng}}">Google Maps</a>.
</p>
{% endif %}

{% comment %}
DATE

This block displays the date and links to Google Calendar.
{% endcomment %}
{% if page.humandate %}
<p id="when">
  <strong>When:</strong>
  {{page.humandate}}.
  {% include workshop_calendar.html %}
</p>
{% endif %}

{% comment %}
SPECIAL REQUIREMENTS

Modify the block below if there are any special requirements.
{% endcomment %}
<p id="requirements">
  <strong>Requirements:</strong> Participants must bring a laptop with a
  Mac, Linux, or Windows operating system (not a tablet, Chromebook, etc.) that they have administrative privileges on. They should have a few specific software packages installed (listed <a href="#setup">below</a>).
</p>

{% comment%}
CODE OF CONDUCT
{% endcomment %}
<p id="code-of-conduct">
<strong>Code of Conduct:</strong>  Everyone who participates in Carpentries activities is required to conform to the <a href="https://docs.carpentries.org/topic_folders/policies/code-of-conduct.html">Code of Conduct</a>. This document also outlines how to report an incident if needed.
</p>


{% comment %}
ACCESSIBILITY

Modify the block below if there are any barriers to accessibility or
special instructions.
{% endcomment %}
<p id="accessibility">
  <strong>Accessibility:</strong> We are committed to making this workshop
  accessible to everybody.
  The workshop organizers have checked that:
</p>
<ul>
  <li>The room is wheelchair / scooter accessible.</li>
  <li>Accessible restrooms are available.</li>
</ul>
<p>
  Materials will be provided in advance of the workshop and
  large-print handouts are available if needed by notifying the
  organizers in advance.  If we can help making learning easier for
  you (e.g. sign-language interpreters, lactation facilities) please
  get in touch (using contact details below) and we will
  attempt to provide them.
</p>

{% comment %}
CONTACT EMAIL ADDRESS

Display the contact email address set in the configuration file.
{% endcomment %}
<p id="contact">
  <strong>Contact</strong>:
  Please email
  {% if page.email %}
  {% for email in page.email %}
  {% if forloop.last and page.email.size > 1 %}
  or
  {% else %}
  {% unless forloop.first %}
  ,
  {% endunless %}
  {% endif %}
  <a href='mailto:{{email}}'>{{email}}</a>
  {% endfor %}
  {% else %}
  to-be-announced
  {% endif %}
  for more information.
</p>

<hr/>

{% comment %} 
SURVEYS - DO NOT EDIT SURVEY LINKS 
{% endcomment %}
<h2 id="surveys">Surveys</h2>
<p>Please be sure to complete these surveys before and after the workshop.</p>
{% if site.carpentry == "swc" %} 
<p><a href="{{ site.swc_pre_survey }}{{ site.github.project_title }}">Pre-workshop Survey</a></p>
<p><a href="{{ site.swc_post_survey }}{{ site.github.project_title }}">Post-workshop Survey</a></p>
{% elsif site.carpentry == "dc" %}
<p><a href="{{ site.dc_pre_survey }}{{ site.github.project_title }}">Pre-workshop Survey</a></p>
<p><a href="{{ site.dc_post_survey }}{{ site.github.project_title }}">Post-workshop Survey</a></p>
{% elsif site.carpentry == "lc" %}
<p><a href="{{ site.lc_pre_survey }}{{ site.github.project_title }}">Pre-workshop Survey</a></p>
<p><a href="{{ site.lc_post_survey }}{{ site.github.project_title }}">Post-workshop Survey</a></p>
{% endif %}

<hr/>


{% comment %}
SCHEDULE

Show the workshop's schedule.  Edit the items and times in the table
to match your plans.  You may also want to change 'Day 1' and 'Day
2' to be actual dates or days of the week.
{% endcomment %}
<h2 id="schedule">Schedule</h2>

{% comment %}
SYLLABUS

Show what topics will be covered.

1. If your workshop is R rather than Python, remove the comment
around that section and put a comment around the Python section.
2. Some workshops will delete SQL.
3. Please make sure the list of topics is synchronized with what you
intend to teach.
4. You may need to move the div's with class="col-md-6" around inside
the div's with class="row" to balance the multi-column layout.

This is one of the places where people frequently make mistakes, so
please preview your site before committing, and make sure to run
'tools/check' as well.
{% endcomment %}
<div class="syllabus">
  <table class="table table-striped">
  <tr>
    <td class="col-md-1"></td>
    <td class="col-md-1"></td>
    <td class="col-md-3"><a href="./setup.html">Setup</a></td>
    <td class="col-md-7">Download files required for the lesson</td>
  </tr>
  <tr>
    <td class="col-md-1"></td>
    <td class="col-md-1"></td>
    <td class="col-md-3"><a href="https://www.surveymonkey.com/r/instructor_training_pre_survey?workshop_id=instructor-training">Pre-training survey</a></td>
    <td class="col-md-7">Please fill out our pre-training survey before the start of the course.</td>
  </tr>
  
     
      
      
       
    
    
    
    <tr>
      <td class="col-md-1">Day 1</td>
      <td class="col-md-1">09:00</td>
      <td class="col-md-3">
        
	1. <a href="./01-welcome/index.html">Welcome</a>
      </td>
      <td class="col-md-7">
        
          
            
              Who are we and how do we approach teaching?

              
              <br/>
              
            
              What should you expect from this workshop?

              
            
          
        
      </td>
    </tr>
    
  
    
    
    
    <tr>
      <td class="col-md-1"></td>
      <td class="col-md-1">09:25</td>
      <td class="col-md-3">
        
	2. <a href="./02-practice-learning/index.html">Building Skill With Practice</a>
      </td>
      <td class="col-md-7">
        
          
            
              How do people learn?

              
              <br/>
              
            
              Who is a typical Carpentries learner?

              
              <br/>
              
            
              How can we help novices become competent practitioners?

              
            
          
        
      </td>
    </tr>
    
  
    
    
    
    <tr>
      <td class="col-md-1"></td>
      <td class="col-md-1">10:25</td>
      <td class="col-md-3">
        
	3. <a href="./03-expertise/index.html">Expertise and Instruction</a>
      </td>
      <td class="col-md-7">
        
          
            
              What type of instructor is best for novices?

              
              <br/>
              
            
              How are we (as instructors) different from our learners and how does this impact our teaching?

              
            
          
        
      </td>
    </tr>
    
  
    
    
    
    <tr>
      <td class="col-md-1"></td>
      <td class="col-md-1">11:10</td>
      <td class="col-md-3">
        
	4. <a href="./04-coffee/index.html">Morning Break</a>
      </td>
      <td class="col-md-7">
        
          Break
        
      </td>
    </tr>
    
  
    
    
    
    <tr>
      <td class="col-md-1"></td>
      <td class="col-md-1">11:25</td>
      <td class="col-md-3">
        
	5. <a href="./05-memory/index.html">Memory and Cognitive Load</a>
      </td>
      <td class="col-md-7">
        
          
            
              What is cognitive load and how does it affect learning?

              
              <br/>
              
            
              How can we design instruction to work with, rather than against, memory constraints?

              
            
          
        
      </td>
    </tr>
    
  
    
    
    
    <tr>
      <td class="col-md-1"></td>
      <td class="col-md-1">12:10</td>
      <td class="col-md-3">
        
	6. <a href="./06-feedback/index.html">Building Skill With Feedback</a>
      </td>
      <td class="col-md-7">
        
          
            
              How can I get feedback from learners?

              
              <br/>
              
            
              How can I use this feedback to improve my teaching?

              
            
          
        
      </td>
    </tr>
    
  
    
    
    
    <tr>
      <td class="col-md-1"></td>
      <td class="col-md-1">12:30</td>
      <td class="col-md-3">
        
	7. <a href="./07-lunch/index.html">Lunch</a>
      </td>
      <td class="col-md-7">
        
          Break
        
      </td>
    </tr>
    
  
    
    
    
    <tr>
      <td class="col-md-1"></td>
      <td class="col-md-1">13:30</td>
      <td class="col-md-3">
        
	8. <a href="./08-motivation/index.html">Motivation and Demotivation</a>
      </td>
      <td class="col-md-7">
        
          
            
              Why is motivation important?

              
              <br/>
              
            
              How can we create a motivating environment for learners?

              
            
          
        
      </td>
    </tr>
    
  
    
    
    
    <tr>
      <td class="col-md-1"></td>
      <td class="col-md-1">14:45</td>
      <td class="col-md-3">
        
	9. <a href="./09-mindset/index.html">Mindset</a>
      </td>
      <td class="col-md-7">
        
          
            
              How does mindset influence learning?

              
              <br/>
              
            
              How should we praise our learners?

              
              <br/>
              
            
              How should we talk about errors?

              
              <br/>
              
            
              What are successful habits of lifelong learners?

              
            
          
        
      </td>
    </tr>
    
  
    
    
    
    <tr>
      <td class="col-md-1"></td>
      <td class="col-md-1">15:15</td>
      <td class="col-md-3">
        
	10. <a href="./10-coffee/index.html">Afternoon Break</a>
      </td>
      <td class="col-md-7">
        
          Break
        
      </td>
    </tr>
    
  
    
    
    
    <tr>
      <td class="col-md-1"></td>
      <td class="col-md-1">15:30</td>
      <td class="col-md-3">
        
	11. <a href="./11-practice-teaching/index.html">Teaching is a Skill</a>
      </td>
      <td class="col-md-7">
        
          
            
              How can I improve my teaching?

              
            
          
        
      </td>
    </tr>
    
  
    
    
    
    <tr>
      <td class="col-md-1"></td>
      <td class="col-md-1">16:40</td>
      <td class="col-md-3">
        
	12. <a href="./12-homework/index.html">Wrap-Up and Homework for Tomorrow</a>
      </td>
      <td class="col-md-7">
        
          
            
              What have we learned today?

              
              <br/>
              
            
              What needs to be done to prepare for tomorrow?

              
            
          
        
      </td>
    </tr>
    
  
     
      
       
        
        
        <tr>
          <td class="col-md-1"></td>
          <td class="col-md-1">17:00</td>
          <td class="col-md-3">Finish</td>
          <td class="col-md-7"></td>
        </tr>
      
       
    
    
    
    <tr>
      <td class="col-md-1">Day 2</td>
      <td class="col-md-1">09:00</td>
      <td class="col-md-3">
        
	13. <a href="./13-second-welcome/index.html">Welcome Back</a>
      </td>
      <td class="col-md-7">
        
          
            
              What have we learned so far?

              
              <br/>
              
            
              What will we focus on today?

              
            
          
        
      </td>
    </tr>
    
  
    
    
    
    <tr>
      <td class="col-md-1"></td>
      <td class="col-md-1">09:10</td>
      <td class="col-md-3">
        
	14. <a href="./14-live/index.html">Live Coding is a Skill</a>
      </td>
      <td class="col-md-7">
        
          
            
              Why do we teach programming using participatory live coding?

              
            
          
        
      </td>
    </tr>
    
  
    
    
    
    <tr>
      <td class="col-md-1"></td>
      <td class="col-md-1">10:20</td>
      <td class="col-md-3">
        
	15. <a href="./15-lesson-study/index.html">Preparing to Teach</a>
      </td>
      <td class="col-md-7">
        
          
            
              How should I prepare to teach?

              
            
          
        
      </td>
    </tr>
    
  
    
    
    
    <tr>
      <td class="col-md-1"></td>
      <td class="col-md-1">11:10</td>
      <td class="col-md-3">
        
	16. <a href="./16-coffee/index.html">Morning Break</a>
      </td>
      <td class="col-md-7">
        
          Break
        
      </td>
    </tr>
    
  
    
    
    
    <tr>
      <td class="col-md-1"></td>
      <td class="col-md-1">11:25</td>
      <td class="col-md-3">
        
	17. <a href="./17-performance/index.html">More Practice Live Coding</a>
      </td>
      <td class="col-md-7">
        
          
            
              How did you change your teaching in response to feedback?

              
            
          
        
      </td>
    </tr>
    
  
    
    
    
    <tr>
      <td class="col-md-1"></td>
      <td class="col-md-1">12:10</td>
      <td class="col-md-3">
        
	18. <a href="./18-management/index.html">Managing a Diverse Classroom</a>
      </td>
      <td class="col-md-7">
        
          
            
              How can I prepare for effective co-teaching?

              
              <br/>
              
            
              What are the challenges of managing a heterogeneous classroom?

              
              <br/>
              
            
              What do I do if there is a Code of Conduct violation?

              
            
          
        
      </td>
    </tr>
    
  
    
    
    
    <tr>
      <td class="col-md-1"></td>
      <td class="col-md-1">12:40</td>
      <td class="col-md-3">
        
	19. <a href="./19-lunch/index.html">Lunch</a>
      </td>
      <td class="col-md-7">
        
          Break
        
      </td>
    </tr>
    
  
    
    
    
    <tr>
      <td class="col-md-1"></td>
      <td class="col-md-1">13:40</td>
      <td class="col-md-3">
        
	20. <a href="./20-checkout/index.html">Checkout Process</a>
      </td>
      <td class="col-md-7">
        
          
            
              What do I need to do to finish certifying as a Carpentries instructor?

              
            
          
        
      </td>
    </tr>
    
  
    
    
    
    <tr>
      <td class="col-md-1"></td>
      <td class="col-md-1">13:55</td>
      <td class="col-md-3">
        
	21. <a href="./21-carpentries/index.html">The Carpentries: How We Operate</a>
      </td>
      <td class="col-md-7">
        
          
            
              How is The Carpentries organized and run?

              
              <br/>
              
            
              What is the difference between SWC, DC, and LC workshops?

              
              <br/>
              
            
              How do you run a Carpentries workshop?

              
            
          
        
      </td>
    </tr>
    
  
    
    
    
    <tr>
      <td class="col-md-1"></td>
      <td class="col-md-1">15:10</td>
      <td class="col-md-3">
        
	22. <a href="./22-coffee/index.html">Afternoon Break</a>
      </td>
      <td class="col-md-7">
        
          Break
        
      </td>
    </tr>
    
  
    
    
    
    <tr>
      <td class="col-md-1"></td>
      <td class="col-md-1">15:25</td>
      <td class="col-md-3">
        
	23. <a href="./23-introductions/index.html">Workshop Introductions</a>
      </td>
      <td class="col-md-7">
        
          
            
              How do you actually start a workshop?

              
            
          
        
      </td>
    </tr>
    
  
    
    
    
    <tr>
      <td class="col-md-1"></td>
      <td class="col-md-1">16:05</td>
      <td class="col-md-3">
        
	24. <a href="./24-practices/index.html">Putting It Together</a>
      </td>
      <td class="col-md-7">
        
          
            
              How are the teaching practices we’ve learned used in our workshops?

              
            
          
        
      </td>
    </tr>
    
  
    
    
    
    <tr>
      <td class="col-md-1"></td>
      <td class="col-md-1">16:25</td>
      <td class="col-md-3">
        
	25. <a href="./25-wrap-up/index.html">Wrapping Up</a>
      </td>
      <td class="col-md-7">
        
          
            
              What can we improve in this training?

              
            
          
        
      </td>
    </tr>
    
  
  
  
  <tr>
    <td class="col-md-1"></td>
    <td class="col-md-1">16:40</td>
    <td class="col-md-3"><a href="https://www.surveymonkey.com/r/instructor_training_post_survey?workshop_id=instructor-training">Post-training survey</a></td>
    <td class="col-md-7">Please fill out our pre-training survey before the start of the course.</td>
  </tr>
  
  
  
  <tr>
    <td class="col-md-1"></td>
    <td class="col-md-1">16:55</td>
    <td class="col-md-3">Finish</td>
    <td class="col-md-7"></td>
  </tr>
  </table>

  <p>
    The actual schedule may vary slightly depending on the topics and exercises chosen by the instructor.
  </p>

</div>


{% comment %}
Collaborative Notes

If you want to use an Etherpad, go to

http://pad.carpentries.org/YYYY-MM-DD-site

where 'YYYY-MM-DD-site' is the identifier for your workshop,
e.g., '2015-06-10-esu'.
{% endcomment %}
{% if page.collaborative_notes %}
<p id="collaborative_notes">
  We will use this <a href="{{page.collaborative_notes}}">collaborative document</a> for chatting, taking notes, and sharing URLs and bits of code.
</p>
{% endif %}

<hr/>


<h2 id="preparation" name="preparation">Preparation</h2>

<p>
  Please read the following before the workshop begins:
</p>
<ol>
  <li><a href="{{ site.training_site }}/papers/science-of-learning-2015.pdf">The Science of Learning</a></li>
</ol>
<p>
  Please also read through <em>one</em> of the episodes below
  carefully, so that you can do some exercises based on it on the
  first day of the class.
</p>
<div class="row">
  <div class="col-md-6">
    <p><strong>Data Carpentry</strong></p>
    <ul>
      <li><a href="{{ site.dc_site }}/OpenRefine-ecology-lesson/01-working-with-openrefine">Faceting and Clustering in OpenRefine</a></li>
      <li><a href="{{ site.dc_site }}/sql-ecology-lesson/01-sql-basic-queries">Basic Queries in SQL</a></li>
      <li><a href="{{ site.dc_site }}/R-ecology-lesson/02-starting-with-data.html">Starting with Data in R</a></li>
      <li><a href="{{ site.dc_site }}/python-ecology-lesson/01-starting-with-data">Starting with Data in Python</a></li>
    </ul>
  </div>
  <div class="col-md-6">
    <p><strong>Software Carpentry</strong></p>
    <ul>
      <li><a href="{{ site.swc_pages }}/shell-novice/03-create/">Working with Files and Directories in the Unix Shell</a></li>
      <li><a href="{{ site.swc_pages }}/git-novice/04-changes/">Tracking Changes in Git</a></li>
      <li><a href="{{ site.swc_pages }}/sql-novice-survey/01-select/">Selecting Data in SQL</a></li>
      <li><a href="{{ site.swc_pages }}/python-novice-inflammation/02-loop/">Repeating Actions with Loops in Python</a></li>
      <li><a href="{{ site.swc_pages }}/r-novice-gapminder/05-data-structures-part2/">Exploring Data Frames in R</a></li>
    </ul>
  </div>
</div>

<hr/>
