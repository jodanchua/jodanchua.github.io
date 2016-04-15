---
layout: post
title: VCAP
permalink: /vcap/
---
<html>
  <head>
    <title>VCAP - Voting for Visually Handicapped</title>
  </head>
<p>Access our VCAP folder <a href="https://github.com/int-argc/VCAP.git">here.</a> </p>
<p>Download PPT <a href=" ">here.</a> </p>

  <h1><center><b>VCAP <br>Voting for Visually Handicapped </b></center></h1>


  <div class="entry">
    <h2 id="application-development-tutorial">Application Background</h2>



<p>
<b>VCAP</b>, also known as “Voting for Visually Handicapped”, is designed to allow blind voters to vote independently without the need of a helper or buddy while voting. With this application, they will simply choose their selected candidate by listening to the audio of the currently selected candidate. </p>

<p><b>Target Users</b> : COMELEC and Visually Handicapped Voters </p>

<p>
<b>Purpose for COMELEC use:</b>

This would give the COMELEC a more efficient database as votes from the visually handicapped would directly be forwarded to the database, thus recording the number of votes each candidate has acquired so far.
</p>

<p>
<b>Purpose for Visually Handicapped Voters:</b>

This would allow visually handicapped voters to vote independently without the need of a “buddy” or proxy to assist them in voting, as they would just have to listen to the audio of the candidate’s name they are currently selecting. 

</p>

<h4 id="copy-sample-application">Copy the project from Github</h4>

<p>You will clone our VCAP repository hosted in our Github account.</p>

<ol>
<li><p>Create the directory <code>VCAP</code> in the root directory, and go to that directory. </p>
<div class="highlight"><pre><code class="language-text" data-lang="text">&gt; mkdir VCAP  
</code></pre></div>

<div class="highlight"><pre><code class="language-text" data-lang="text">&gt; cd VCAP
</code></pre></div>


<li><p>Clone the  <a href="https://github.com/int-argc/VCAP">repository</a> in the <code>VCAP</code> directory.
</p>

<div class="highlight"><pre><code class="language-text" data-lang="text">&gt; git clone https://github.com/int-argc/VCAP
</code></pre></div>
</li>

<li> Go to project root.
<div class="highlight"><pre><code class="language-text" data-lang="text">&gt; cd VCAP
</code></pre></div>
</li>
</ol>

<h4 id="deploy-sample-application-in-bluemix-using-the-cf-tool">Deploy the Application in Bluemix .</h4>

<ol>
<li><p>Build the sample application.
<div class="highlight"><pre><code class="language-text" data-lang="text">&gt; gradle assemble
</code></pre></div>
</p></li>
<li><p>Login to your Bluemix account using the <code>cf</code> tool.</p>
<div class="highlight"><pre><code class="language-text" data-lang="text">&gt; cf login -a https://api.ng.bluemix.net -s dev
</code></pre></div>


<p><br></p></li>
<li><p>Upload the  application to your Bluemix account.</p>
<div class="highlight"><pre><code class="language-text" data-lang="text">&gt; cf push VCAP-&lt;your_name&gt; -m 256M -p vcap.war
</code></pre></div>
<p><strong>Example:</strong></p>
<div class="highlight"><pre><code class="language-text" data-lang="text">&gt; cf push vcap-jords -m 256M -p vcap.war
</code></pre></div>

<p><li>
Go back to the browser tab containing your Bluemix account. In the menu, click DASHBOARD.
</p>
<p>The <code>Applications</code> section of your dashboard shows a widget representing the application <code>vcap-&lt;your_name&gt;</code> you deployed earlier.</p>
</li>
</p>

<p><li>
Click the widget of your application to see its overview.
</li></p>
</ol>

<h4 id="add-a-Language-Translation-Service-and-bind-it-to-the-sample-application">Add Object Storage, Text to Speech, and Redis  Services and Bind it to the  Application</h4>

<ol>
<li><p>On the left pane, click the <code>Overview</code> link. </p></li>
<li><p>Click the <code>ADD A SERVICE OR API</code> link.  You will be redirected to the <code>Catalog</code> page. </p></li>

<li><p>Look for the <code>Object Storage</code> , <code>Text to Speech</code>, and <code>Redis Experimental</code>service and bind each of the services to the <code>VCAP </code> application.

<blockquote>
<p><strong>IMPORTANT:</strong>
For <code>Redis Experimental</code> service, it is located under <code>Bluemix Labs Catalog</code> at the end of the <code>Catalog</code> page.</blockquote>  
</p></li>

<li><p>When asked to restage your application, click the <code>RESTAGE</code> button.  Wait for your application to restage.</p></li>
<li><p>Open another browser tab (do not close the browser tab containing your Bluemix account).  Go to  <code>vcap-&lt;your_name&gt;.mybluemix.net</code> to test if the application can already connect to the created services.</p>

<p><br></p></li>
</ol>


<h4 id="Launch">Launch the Sample Application </h4>

<ol>
<li><p>
Go to the DASHBOARD of your Bluemix account. On the Applications section, click on the application <code>vcap-&lt;your_name&gt;</code> you pushed earlier.
</p>
</li>

<li><p>
Click the <code>Route</code> or <code>URL</code> just below your application name <code>vcap-&lt;your_name&gt;</code>.mybluemix.net. This will open up the web application.
</li></p>
</ol>


<h4 id="delete-the-sample-application-and-postgresql-service">Delete the  Application and Services</h4>

<ol>
<li><p>Go back to the browser tab containing your Bluemix account.  In the menu, click <code>DASHBOARD</code>.  </p>

<li><p>Click the <code>gear</code> icon in the widget of the sample application.</p></li>
<li><p>Click the <code>Delete App</code> entry.  For each of the services,  click the <code>Services</code> tab. In the <code>Routes</code> tab, make sure that the route (i.e., URL) is selected.</p></li>
<li><p>Click the <code>DELETE</code> button.</p></li>
</ol>

<p><br></p>

<h4 id="end-of-tutorial">End of Tutorial</h4>

<a href="https://github.com/jodanchua.github.io/jekyll-now"><i class="svg-icon github"></i></a>

    

  </body>
</html>
