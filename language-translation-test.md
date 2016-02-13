---
layout: post
title: test
permalink: /language-translation-test/
---

<!DOCTYPE html>
<html>
  <head>
    <title>Language Translation – Jordan Chua –web developer</title>

        <meta charset="utf-8" />
    <meta content='text/html; charset=utf-8' http-equiv='Content-Type'>
    <meta http-equiv='X-UA-Compatible' content='IE=edge'>
    <meta name='viewport' content='width=device-width, initial-scale=1.0, maximum-scale=1.0'>

    
    <meta name="description" content="web developer">
    <meta property="og:description" content="web developer" />
    
    <meta name="author" content="Jordan Chua" />

    
    <meta property="og:title" content="Bluemix Basics" />
    <meta property="twitter:title" content="Bluemix Basics" />
    

    <!--[if lt IE 9]>
      <script src="http://html5shiv.googlecode.com/svn/trunk/html5.js"></script>
    <![endif]-->

    <link rel="stylesheet" type="text/css" href="http://jodanchua.github.io/style.css" />
    <link rel="alternate" type="application/rss+xml" title="Jordan Chua - web developer" href="http://jodanchua.github.io/feed.xml" />

    <!-- Created with Jekyll Now - http://github.com/barryclark/jekyll-now -->
  </head>

  <body>
    <div class="wrapper-masthead">
      <div class="container">
        <header class="masthead clearfix">
          <a href="http://jodanchua.github.io/" class="site-avatar"><img src="https://raw.githubusercontent.com/barryclark/jekyll-now/master/images/jekyll-logo.png" /></a>

          <div class="site-info">
            <h1 class="site-name"><a href="http://jodanchua.github.io/">Jordan Chua</a></h1>
            <p class="site-description">web developer</p>
          </div>

          <nav>
            <a href="http://jodanchua.github.io/">Blog</a>
            <a href="http://jodanchua.github.io/junit-basics">About</a>
          </nav>
        </header>
      </div>
    </div>

    <div id="main" role="main" class="container">
      <article class="post">
  <h1> Language Translation</h1>

  <div class="entry">
    <h2 id="application-development-tutorial">Application Development Tutorial</h2>

<p> Watsons Language Translation tool can translate text from one language to a  specific domain.  

<p>In this tutorial you will learn how to deploy a sample Language Translation Application in Bluemix.  In addition, you will learn  how to to use the API provided by IBM Watson.</p>

<blockquote>
<p><strong>Prerequisite:</strong></p>

<p>Having a basic background in web application development is required in this tutorial.</p>
</blockquote>

<p><br></p>

<h4 id="create-a-bluemix-account">Create a Bluemix Account</h4>

<ol>
<li><p>Go to <a href="https://ibm.biz/bluemixph">Bluemix</a> and click the <code>SIGN UP</code> button.</p></li>
<li><p>Fill-up and submit the registration form.</p></li>
<li><p>Wait for a confirmation e-mail and follow the instructions in the e-mail to validate your Bluemix registration.</p></li>
</ol>

<p><br></p>

<h4 id="explore-your-bluemix-account">Explore your Bluemix Account</h4>

<ol>
<li><p>Open a web browser and login to your <a href="https://ibm.biz/bluemixph">Bluemix</a> account.</p></li>
<li><p>You will be redirected to your dashboard.  Your dashboard:</p>

<ul>
<li>provides some information regarding your account (e.g., organization, spaces, etc.)</li>
<li>summarizes the amount of resources you have consumed </li>
<li>enumerates the applications, services, containers, and virtual machines you have created.</li>
</ul>

<p><br></p></li>
<li><p>You may have one ore more organizations.  By default, you only have one organization.  The name of this organization is the same as your Bluemix account.</p>

<p>Additional organizations may become available in your Bluemix account when other Bluemix users share his/her organization to you.  The procedure in sharing an organization is not covered in this tutorial.</p>

<p><br></p></li>
<li><p>Each organization has an allotted set of resources.  As an example, your dashboard shows the following:</p>

<table><thead>
<tr>
<th>Resource</th>
<th>Consumed</th>
<th>Total Allocation</th>
</tr>
</thead><tbody>
<tr>
<td>Cloud Foundry Apps</td>
<td>0GB</td>
<td>2GB</td>
</tr>
<tr>
<td>Services and APIs</td>
<td>0</td>
<td>10</td>
</tr>
</tbody></table>

<p>Note that there are other resources in your dashboard not listed above.  In addition, the amount of total allocation may vary depending on the type of account (e.g., trial account, etc.)</p>

<p>Having a total allocation of 2GB for Cloud Foundry apps means that you can have one or more running applications in your account that have a total memory consumption of 2GB.  As an example, if you deploy Application A in Bluemix with a memory allocation of 1GB, you still have 1GB left that can be used for another application (or applications).</p>

<p>For services and APIs, you are given an allocation of 10.  An example of a service is a PostgreSQL database service which you will create later. </p>

<p><br></p></li>
<li><p>The physical location (e.g., location of the data center) of the Bluemix servers that will host your application is referred to as Bluemix regions.  Currently there are three Bluemix regions: <code>United Kingdom</code>, <code>Sydney,</code> and <code>US South</code>.</p>

<p>In this tutorial, you will be using the <code>US South</code> region.  However, in an actual deployment, you may choose any of the available regions.  If you will be deploying several applications, these applications may be deployed in different region (e.g., your first application is in <code>United Kingdom</code>, while the second one is in <code>US South</code>).  However, the total consumed resources in these regions should not exceed the allocation given to your organization (e.g., 2GB memory and 10 services)</p>

<p><br></p></li>
<li><p>Make sure that the current region used by your Bluemix account is <code>US South</code> by  clicking the <code>Person</code> icon on the upper-right corner of your account.  </p>

<blockquote>
<p>Once you select <code>US South</code> it is possible that you will be prompted to create a space.  If you are prompted, enter a space named <code>dev</code>.  This purpose of a space is explained in the next step.</p>
</blockquote></li>
<li><p>Under the <code>US South</code> region, you may deploy one ore more applications.  </p>

<p>As the number of applications you deploy in a region increases, the harder it is to manage your applications.  To help manage them, applications are grouped together in spaces.  As an example, you may create spaces which groups applications belonging to the same phase.  For example, you may create a space called <code>dev</code> and deploy all of your applications that are still under development phase.  You may create a second space called <code>prod</code> for applications that are already in production.</p>

<p>Another way to utilize spaces is to group applications based on projects.  For example, you may create a space called <code>proj1</code> for all projects belonging to project 1.</p>

<p><br></p></li>
<li><p>Verify if you have a <code>dev</code> space at the left side of your dashboard.  If there is no <code>dev</code> space, create one by clicking the <code>Create a Space</code> link. </p>

<p><br></p></li>
</ol>

<h4 id="explore-the-bluemix-catalog">Explore the Bluemix Catalog</h4>

<ol>
<li><p>In the menu, click <code>CATALOG</code>.  The Bluemix Catalog shows the different services and APIs, as well as runtimes and containers that you may create.</p></li>
<li><p>Scroll down until you see <code>PostgreSQL by Compose</code>.  PostgreSQL is a type of relational database.  </p>

<p>In Bluemix, there are services that are very similar.  As an example, in this tutorial, you will be creating a PostgreSQL service.  However, the PostgreSQL service that you will be using is NOT <code>PostgreSQL by Compose</code>.</p>

<p><br></p></li>
<li><p>Scroll down further in the <code>CATALOG</code> page until you see the <code>Bluemix Labs Catalog</code> link.  Click this link.</p></li>
<li><p>Scroll down until you see <code>postgresql</code>.   The <code>postgresql</code> service and the <code>PostgreSQL by Compose</code> service are very similar (i.e., both are PostgreSQL services).  In this tutorial, you will be using <code>postgresql</code>.  When you are asked to create a PostgreSQL service in later steps, make sure to use <code>postgresql</code> and not <code>PostgreSQL by Compose</code>.</p>

<p><br></p></li>
<li><p>Leave your Bluemix account open on the browser.  You will use this again later.</p>

<p><br></p></li>
</ol>

<h4 id="install-the-cloud-foundry-cf-tool">Install the Cloud Foundry (<code>cf</code>) tool.</h4>

<p>Cloud Foundry is an open-source platform as a service cloud technology.  Bluemix is based from Cloud Foundry.  Cloud Foundry has a command-line tool called <code>cf</code> that is used to deploy applications in cloud foundry-based environment.  Since Bluemix is based on Cloud Foundry, the same <code>cf</code> tool can be used to deploy applications in Bluemix.</p>

<ol>
<li><p>Go to the Cloud Foundry <code>cf</code> tool <a href="https://github.com/cloudfoundry/cli/releases">repository</a>.</p></li>
<li><p>Download the appropriate installer (not the binary).</p></li>
<li><p>Install using the default options.</p></li>
<li><p>To test if installation is successful, open a terminal window and issue the following command:</p>
<div class="highlight"><pre><code class="language-text" data-lang="text">&gt; cf
</code></pre></div>
<p><strong>Output:</strong></p>
<div class="highlight"><pre><code class="language-" data-lang="">NAME:
   cf - A command line tool to interact with Cloud Foundry

USAGE:
   [environment variables] cf [global options] command [arguments...] [command options]
   :
   :
</code></pre></div>
<p>You should see the help screen of <code>cf</code> (see above example).</p>

<p><br></p></li>
</ol>

<h4 id="copy-sample-application">Copy Sample Application</h4>

<p>You will download a copy of a sample application that you will deploy in your Bluemix account.</p>

<ol>
<li><p>Create the directory <code>bluemixtemp</code> in the root directory.  Create a subdirectory <code>myfirstapp</code> in <code>bluemixtemp</code>.</p></li>
<li><p>Download <a href="https://github.com/ibmjstart/bluemix-java-postgresql-uploader/releases/download/v1.1/PostgreSQLUpload.war">PostgreSQLUpload.war</a> and save it in the <code>myfirstapp</code> subdirectory.</p></li>
</ol>

<p><br></p>

<h4 id="deploy-sample-application-in-bluemix-using-the-cf-tool">Deploy Sample Application in Bluemix using the <code>cf</code> tool.</h4>

<ol>
<li><p>Open a terminal window and go to the <code>myfirstapp</code> subdirectory.</p></li>
<li><p>Login to your Bluemix account using the <code>cf</code> tool.</p>
<div class="highlight"><pre><code class="language-text" data-lang="text">&gt; cf login -a https://api.ng.bluemix.net -s dev
</code></pre></div>
<blockquote>
<p>When asked for a username (e-mail address) and password, enter the username and password of your Bluemix account.</p>
</blockquote>

<p><strong>Output:</strong></p>
<div class="highlight"><pre><code class="language-" data-lang="">API endpoint: https://api.ng.bluemix.net

Username&gt; -----

Password&gt;
Authenticating...
OK

Targeted space dev

API endpoint: https://api.ng.bluemix.net (API version: 2.40.0)
User:         -----
Org:          -----
Space:        dev
</code></pre></div>
<p>The <code>-a</code> switch allows you to specify the URL of the Bluemix region.  In this tutorial, you are using the <code>US South</code> region.  The URL of this region is <code>https://api.ng.bluemix.net</code>.</p>

<p>The <code>-s</code> switch allows you to specify the space where you will deploy the application.  In this tutorial, you will be deploying the application in the <code>dev</code> space you created earlier.</p>

<p><br></p></li>
<li><p>Upload the sample application to your Bluemix account.</p>
<div class="highlight"><pre><code class="language-text" data-lang="text">&gt; cf push myfirstapp-&lt;your_name&gt; -m 256M -p PostgreSQLUpload.war
</code></pre></div>
<p><strong>Example:</strong></p>
<div class="highlight"><pre><code class="language-text" data-lang="text">&gt; cf push myfirstapp-pong -m 256M -p PostgreSQLUpload.war
</code></pre></div>
<p><strong>Output:</strong></p>
<div class="highlight"><pre><code class="language-text" data-lang="text">:
:
     state     since                    cpu    memory           disk
#0   running   2016-01-14 08:00:15 AM   0.8%   185.1M of 256M   180.9M  
</code></pre></div>
<p>In the example above, the name of the application is <code>myfirstapp-pong</code>.  Replace <code>pong</code> with your name.  The name of your application will be concatenated with string <code>.mybluemix.net</code> and this will be the URL of your application.  As an example, the application <code>myfirstapp-pong</code> is accessible using the URL <a href="http://myfirstapp-pong.mybluemix.net">http://myfirstapp-pong.mybluemix.net</a>.</p>

<blockquote>
<p><strong>IMPORTANT:</strong> If you encounter an error message <code>host is taken</code>, it means that the application name you specified has already been used by another Bluemix user.  Issue the <code>cf push</code> command again but change the name of your application.  In the example above, instead of <code>myfirstapp-pong</code>, it can be <code>myfirstapp-pong2</code>.</p>
</blockquote>

<p>The <code>-m</code> switch allows you to specify the memory allocation of your application.</p>

<p>The <code>-p</code> switch allows you to specify the location of the file containing the sample application.</p>

<p><br></p></li>
<li><p>Go back to the browser tab containing your Bluemix account.  In the menu, click <code>DASHBOARD</code>.  </p>

<p>The <code>Applications</code> section of your dashboard shows a widget representing the application <code>myfirstapp-&lt;your_name&gt;</code> you deployed earlier.</p>

<p>The widget shows some information regarding the application:</p>

<ul>
<li><strong>status</strong>: your application is in a running state</li>
<li><strong>route (a.k.a. URL)</strong>: <code>myfirstapp-&lt;your_name&gt;.mybluemix.net</code></li>
<li><strong>runtime</strong>: Liberty for Java (this is the type of web server hosting your application)</li>
<li><strong>list of services the app is bound to</strong>: currently empty</li>
</ul>

<p>Take note that aside from logging in using the <code>cf</code> tool, the only other command you issued earlier is <code>cf push</code> which deployed your application in your Bluemix account.  You NEVER explicitly created/set-up a web server (e.g., Liberty for Java web server) to host your application.  When you issued the <code>cf push</code> command, Bluemix determined that you want to deploy a Java-based web application and automatically created the necessary web server (which we refer to in Bluemix as <strong>runtime</strong>) to host your application.</p>

<p>Currently the <strong>list of services the app is bound to</strong> is empty but when you add a PostgreSQL service later you will see an icon added in the widget representing the service.</p>

<p><br></p></li>
<li><p>Click the widget of your application to see its overview.</p>

<p>The overview shows the following information:</p>

<ul>
<li><strong>instances</strong>: 1</li>
<li><strong>memory quota</strong>: 256MB</li>
<li><strong>activity log</strong></li>
<li><strong>routes</strong>: <code>myfirstapp-&lt;your_name&gt;.mybluemix.net</code></li>
</ul>

<p>Adjusting the <strong>instances</strong> value allows you to perform horizontal scaling.  For example, if you observe that a deployed application cannot handle anymore the number of users accessing the application then you may increase the number of instances.  However, take note that for every additional instance you add, your application will consume an additional memory space equal to the <strong>memory quota</strong>.  For example, if you have 2 instances and 256MB as the memory quota, then your application consumes 512MB of memory.</p>

<p>Adjusting the <strong>memory quota</strong> value allows you to perform vertical scaling.  </p>

<p><br></p></li>
<li><p>On the left pane, click the <code>Environment Variables</code> link.</p>

<p>Bluemix has a system-defined environment variable called <code>VCAP_SERVICES</code>.  Currently, the value of <code>VCAP_SERVICES</code> is empty.   You will see later the purpose of <code>VCAP_SERVICES</code>.</p>

<p><br></p></li>
<li><p>Open another browser tab (do not close the browser tab containing your Bluemix account).  Go to <code>http://myfirstapp-&lt;your_name&gt;.mybluemix.net</code> to verify that the sample application is successfully deployed.</p>

<blockquote>
<p>If you encounter a <code>404 Not Found: Requested route (&#39;-----.mybluemix.net&#39;) does not exist</code>, it may mean any of the following:
a. you typed the wrong URL (<strong>solution:</strong> double check the URL)
b. your application is not yet running (<strong>solution:</strong> wait for your application to run, refer to the sample output above)
c. your application failed to run (<strong>solution:</strong> look at the error message and issue again the <code>cf push</code> command)</p>
</blockquote>

<p>The sample application allows you to upload a text file in a PostgreSQL database.  You will test if this sample application is correctly running.</p>

<p><br></p></li>
<li><p>Click the <code>Browse</code> button of the sample application and choose any text file.</p>

<blockquote>
<p>Make sure it is a text file and not a binary file.
If you don&#39;t have any text file, just create one and place at least 3 lines of text.</p>
</blockquote>

<p><br></p></li>
<li><p>Click the <code>Upload</code> button.  If the upload operation is successful, the contents of the text file will be saved in a PostgreSQL database.  </p>

<p>HOWEVER, since you have not created any PostgreSQL database yet, you encountered the error <code>No PostgreSQL service URL found. Make sure you have bound the correct services to your app.</code>.  You will fix this error by creating a PostgreSQL server later.</p>

<p><br></p></li>
<li><p>Close the browser tab containing the sample application.</p>

<p><br></p></li>
</ol>

<h4 id="add-a-postgresql-service-and-bind-it-to-the-sample-application">Add a PostgreSQL Service and Bind it to the Sample Application</h4>

<ol>
<li><p>Go back to the browser tab containing your Bluemix account.  On the left pane, click the <code>Overview</code> link. </p></li>
<li><p>Click the <code>ADD A SERVICE OR API</code> link.  You will be redirected to the <code>Catalog</code> page. </p></li>
<li><p>Look for the <code>postgresql</code> service and click it.</p>

<blockquote>
<p><strong>VERY IMPORTANT:</strong>
The <code>postgresql</code> service that you will use in this tutorial is NOT the <code>PostgreSQL by Compose</code>.<br>
<br>
In the <code>Catalog</code> page, scroll down in the <code>CATALOG</code> page until you see the <code>Bluemix Labs Catalog</code> link.  Click this link.
<br>
Look for the service named <code>postgresql</code> and click this service.</p>
</blockquote>

<p><br></p></li>
<li><p>In the <code>Service name</code> text box, type <code>postgresql-myfirstservice</code>.</p></li>
<li><p>Click the <code>CREATE</code> button.</p></li>
<li><p>When asked to restage your application, click the <code>RESTAGE</code> button.  Wait for your application to restage.</p></li>
<li><p>Open another browser tab (do not close the browser tab containing your Bluemix account).  Go to <code>http://myfirstapp-&lt;your_name&gt;.mybluemix.net</code> to test if the sample application can already connect to the created PostgreSQL service.</p>

<p><br></p></li>
<li><p>Click the <code>Browse</code> button of the sample application and choose any text file.</p></li>
<li><p>Click the <code>Upload</code> button.  </p>

<p>This time, the upload is successful.  You will see the contents of the text file displayed on the page.   The sample application is programmed to display the contents of the PostgreSQL service.  Since the contents of the text file is displayed on the page, the contents are successfully saved in the PostgreSQL service.</p>

<p><br></p></li>
</ol>

<h4 id="analyze-how-the-sample-application-communicates-with-postgresql-service">Analyze How the Sample Application communicates with PostgreSQL Service</h4>

<p>Reviewing the procedure above, you did two important tasks: (1) deployed the sample application and (2) created a PostgreSQL service.</p>

<p>It seems impossible for the sample application to be able to communicate with the PostgreSQL service since you have not updated the sample application to use the credentials of the service (e.g., username, password, IP address, port no., etc.).  </p>

<p>However, as demonstrated, you were able to make the sample application to communicate with the service.  This was accomplished by coding the sample application such that the database credentials needed to create the connection string are not hard coded.  Instead it uses the credentials found in the environment variable <code>VCAP_SERVICES</code> which was originally empty earlier.</p>

<ol>
<li><p>Go back to the browser tab containing your Bluemix account.  On the left pane, click the <code>Environment Variables</code> link. </p>

<p>Recall that earlier <code>VCAP_SERVICES</code> is empty.  However, it now contains a value similar to the one you see below:</p>
<div class="highlight"><pre><code class="language-text" data-lang="text">{
   "postgresql-9.1": [
      {
         "name": "postgresql-myfirstservice",
         "label": "postgresql-9.1",
         "plan": "100",
         "credentials": {
            "name": "d318bc5931cd540b694de846b004b3955",
            "host": "198.11.228.48",
            "hostname": "198.11.228.48",
            "port": 5433,
            "user": "u536f68cf365d4ee6a3a3e00cbf209c53",
            "username": "u536f68cf365d4ee6a3a3e00cbf209c53",
            "password": "pdf27393fb94d4d45913cd54751d346ad",
            "uri": "postgres://u536f68cf365d4ee6a3a3e00cbf209c53:pdf27393fb94d4d45913cd54751d346ad@198.11.228.48:5433/d318bc5931cd540b694de846b004b3955"
         }
      }
   ]
}
</code></pre></div>
<p>The value above contains the credentials of the PostgreSQL service.  This value was produced when you created the service earlier.  </p>

<p>Recall that you clicked the <code>ADD A SERVICE OR API</code> link earlier then created the PostgreSQL service.  Adding a service (or API) does two things:
    - create a service
    - bind the service to the application</p>

<p>Binding the PostgreSQL service to the application simply instructs Bluemix to share the credentials of the PostgreSQL service to the sample application.  The credentials are shared by placing the values of the credentials to <code>VCAP_SERVICES</code>.</p>

<p>However, it needs to be emphasized that even if the credentials are shared through the <code>VCAP_SERVICES</code>, this sharing is useless unless the application explicitly use the <code>VCAP_SERVICES</code> environment variable.</p>

<p>You will examine the source code inside <code>PostgreSQLUpload.war</code> to see how <code>VCAP_SERVICES</code> is used.</p>

<p><br></p></li>
<li><p>If you extract the contents of <code>PostgreSQLUpload.war</code> you will see the subdirectory <code>WEB-INF/classes/com/ibm/bluemix/samples</code>.  This contains several <code>.java</code> files including <code>PostgreSQLClient.java</code>.</p>

<blockquote>
<p>You don&#39;t need to extract the contents of the <code>.war</code> file since the contents of the needed files are shown below.  However, you may use tools such as <code>7Zip</code> if you want to extract the contents.</p>
</blockquote>

<p><code>PostgreSQLClient.java</code> has a method called <code>getConnection</code>:</p>
<div class="highlight"><pre><code class="language-java" data-lang="java">    <span class="kd">private</span> <span class="kd">static</span> <span class="n">Connection</span> <span class="nf">getConnection</span><span class="p">(</span><span class="o">)</span> <span class="kd">throws</span> <span class="n">Exception</span> <span class="o">{</span>
        <span class="n">Map</span><span class="o">&lt;</span><span class="n">String</span><span class="o">,</span> <span class="n">String</span><span class="o">&gt;</span> <span class="n">env</span> <span class="o">=</span> <span class="n">System</span><span class="o">.</span><span class="na">getenv</span><span class="o">();</span>

        <span class="k">if</span> <span class="o">(</span><span class="n">env</span><span class="o">.</span><span class="na">containsKey</span><span class="o">(</span><span class="s">"VCAP_SERVICES"</span><span class="o">))</span> <span class="o">{</span>
            <span class="c1">// we are running on cloud foundry, let's grab the service details from vcap_services</span>
            <span class="n">JSONParser</span> <span class="n">parser</span> <span class="o">=</span> <span class="k">new</span> <span class="n">JSONParser</span><span class="o">();</span>
            <span class="n">JSONObject</span> <span class="n">vcap</span> <span class="o">=</span> <span class="o">(</span><span class="n">JSONObject</span><span class="o">)</span> <span class="n">parser</span><span class="o">.</span><span class="na">parse</span><span class="o">(</span><span class="n">env</span><span class="o">.</span><span class="na">get</span><span class="o">(</span><span class="s">"VCAP_SERVICES"</span><span class="o">));</span>
            <span class="n">JSONObject</span> <span class="n">service</span> <span class="o">=</span> <span class="kc">null</span><span class="o">;</span>

            <span class="c1">// We don't know exactly what the service is called, but it will contain "postgresql"</span>
            <span class="k">for</span> <span class="o">(</span><span class="n">Object</span> <span class="n">key</span> <span class="o">:</span> <span class="n">vcap</span><span class="o">.</span><span class="na">keySet</span><span class="o">())</span> <span class="o">{</span>
                <span class="n">String</span> <span class="n">keyStr</span> <span class="o">=</span> <span class="o">(</span><span class="n">String</span><span class="o">)</span> <span class="n">key</span><span class="o">;</span>
                <span class="k">if</span> <span class="o">(</span><span class="n">keyStr</span><span class="o">.</span><span class="na">toLowerCase</span><span class="o">().</span><span class="na">contains</span><span class="o">(</span><span class="s">"postgresql"</span><span class="o">))</span> <span class="o">{</span>
                    <span class="n">service</span> <span class="o">=</span> <span class="o">(</span><span class="n">JSONObject</span><span class="o">)</span> <span class="o">((</span><span class="n">JSONArray</span><span class="o">)</span> <span class="n">vcap</span><span class="o">.</span><span class="na">get</span><span class="o">(</span><span class="n">keyStr</span><span class="o">)).</span><span class="na">get</span><span class="o">(</span><span class="mi">0</span><span class="o">);</span>
                    <span class="k">break</span><span class="o">;</span>
                <span class="o">}</span>
            <span class="o">}</span>

            <span class="k">if</span> <span class="o">(</span><span class="n">service</span> <span class="o">!=</span> <span class="kc">null</span><span class="o">)</span> <span class="o">{</span>
                <span class="n">JSONObject</span> <span class="n">creds</span> <span class="o">=</span> <span class="o">(</span><span class="n">JSONObject</span><span class="o">)</span> <span class="n">service</span><span class="o">.</span><span class="na">get</span><span class="o">(</span><span class="s">"credentials"</span><span class="o">);</span>
                <span class="n">String</span> <span class="n">name</span> <span class="o">=</span> <span class="o">(</span><span class="n">String</span><span class="o">)</span> <span class="n">creds</span><span class="o">.</span><span class="na">get</span><span class="o">(</span><span class="s">"name"</span><span class="o">);</span>
                <span class="n">String</span> <span class="n">host</span> <span class="o">=</span> <span class="o">(</span><span class="n">String</span><span class="o">)</span> <span class="n">creds</span><span class="o">.</span><span class="na">get</span><span class="o">(</span><span class="s">"host"</span><span class="o">);</span>
                <span class="n">Long</span> <span class="n">port</span> <span class="o">=</span> <span class="o">(</span><span class="n">Long</span><span class="o">)</span> <span class="n">creds</span><span class="o">.</span><span class="na">get</span><span class="o">(</span><span class="s">"port"</span><span class="o">);</span>
                <span class="n">String</span> <span class="n">user</span> <span class="o">=</span> <span class="o">(</span><span class="n">String</span><span class="o">)</span> <span class="n">creds</span><span class="o">.</span><span class="na">get</span><span class="o">(</span><span class="s">"user"</span><span class="o">);</span>
                <span class="n">String</span> <span class="n">password</span> <span class="o">=</span> <span class="o">(</span><span class="n">String</span><span class="o">)</span> <span class="n">creds</span><span class="o">.</span><span class="na">get</span><span class="o">(</span><span class="s">"password"</span><span class="o">);</span>

                <span class="n">String</span> <span class="n">url</span> <span class="o">=</span> <span class="s">"jdbc:postgresql://"</span> <span class="o">+</span> <span class="n">host</span> <span class="o">+</span> <span class="s">":"</span> <span class="o">+</span> <span class="n">port</span> <span class="o">+</span> <span class="s">"/"</span> <span class="o">+</span> <span class="n">name</span><span class="o">;</span>

                <span class="k">return</span> <span class="n">DriverManager</span><span class="o">.</span><span class="na">getConnection</span><span class="o">(</span><span class="n">url</span><span class="o">,</span> <span class="n">user</span><span class="o">,</span> <span class="n">password</span><span class="o">);</span>
            <span class="o">}</span>
        <span class="o">}</span>

        <span class="k">throw</span> <span class="k">new</span> <span class="n">Exception</span><span class="o">(</span><span class="s">"No PostgreSQL service URL found. Make sure you have bound the correct services to your app."</span><span class="o">);</span>
    <span class="o">}</span>
</code></pre></div>
<p>The method parses the contents of <code>VCAP_SERVICES</code> and looks for the credentials of the PostgreSQL service.  This approach allowed the sample application to dynamically get the credentials of the service instead of hard coding it.</p>

<p>The use of <code>VCAP_SERVICES</code> explains how the sample application is able to connect to the PostgreSQL service.  However, this did not explain how a database table (that stores the content of text files) was created.  Recall that you never performed a task that explicilty created a table in the PostgreSQL service.</p>

<p><code>PostgreSQLClient.java</code> has another method called <code>createTable</code>:</p>
<div class="highlight"><pre><code class="language-java" data-lang="java">    <span class="kd">private</span> <span class="kt">void</span> <span class="nf">createTable</span><span class="p">(</span><span class="o">)</span> <span class="kd">throws</span> <span class="n">Exception</span> <span class="o">{</span>
        <span class="n">String</span> <span class="n">sql</span> <span class="o">=</span> <span class="s">"CREATE TABLE IF NOT EXISTS posts ("</span> <span class="o">+</span>
                        <span class="s">"id serial primary key, "</span> <span class="o">+</span>
                        <span class="s">"text text"</span> <span class="o">+</span>
                     <span class="s">");"</span><span class="o">;</span>
        <span class="n">Connection</span> <span class="n">connection</span> <span class="o">=</span> <span class="kc">null</span><span class="o">;</span>
        <span class="n">PreparedStatement</span> <span class="n">statement</span> <span class="o">=</span> <span class="kc">null</span><span class="o">;</span>

        <span class="k">try</span> <span class="o">{</span>
            <span class="n">connection</span> <span class="o">=</span> <span class="n">getConnection</span><span class="o">();</span>
            <span class="n">statement</span> <span class="o">=</span> <span class="n">connection</span><span class="o">.</span><span class="na">prepareStatement</span><span class="o">(</span><span class="n">sql</span><span class="o">);</span>
            <span class="n">statement</span><span class="o">.</span><span class="na">executeUpdate</span><span class="o">();</span>
        <span class="o">}</span> <span class="k">finally</span> <span class="o">{</span>         
            <span class="k">if</span> <span class="o">(</span><span class="n">statement</span> <span class="o">!=</span> <span class="kc">null</span><span class="o">)</span> <span class="o">{</span>
                <span class="n">statement</span><span class="o">.</span><span class="na">close</span><span class="o">();</span>
            <span class="o">}</span>

            <span class="k">if</span> <span class="o">(</span><span class="n">connection</span> <span class="o">!=</span> <span class="kc">null</span><span class="o">)</span> <span class="o">{</span>
                <span class="n">connection</span><span class="o">.</span><span class="na">close</span><span class="o">();</span>
            <span class="o">}</span>
        <span class="o">}</span>
    <span class="o">}</span>
</code></pre></div>
<p>The <code>createTable</code> method allowed the tables to be programmatically created (i.e., no need for you to manually create the table).  In usual practices, the database administrator creates the tables.  However, the sample application was designed to programmatically create the table to easily demonstrate the use of a service in Bluemix.</p>

<p><br></p></li>
</ol>

<h4 id="delete-the-sample-application-and-postgresql-service">Delete the Sample Application and PostgreSQL Service</h4>

<p>You may delete applications and services that you don&#39;t anymore need.  This will free up some resources which is essential to accommodate new applications and services you want to deploy in the future.</p>

<ol>
<li><p>Go back to the browser tab containing your Bluemix account.  In the menu, click <code>DASHBOARD</code>.  </p>

<p>Notice that the widget of the sample application got updated.  An icon was added in the widget.  If you will mouse hover on the icon, you will see that the icon refers to the PostgreSQL service you created earlier.  The presence of this icon in the widget of the sample application  means that the service is bound to the application.  </p>

<p>Take note that it is possible that you may have additional services bound to the same application.</p>

<p>In addition, notice that a widget for the PostgreSQL service is also available.  It also has an icon that refers to the sample application.  The presence of this icon in the widget of the PostgreSQL service means that the application may use this service. </p>

<p>Take note that it is possible that you may have additional applications bound to the same service.</p>

<p><br></p></li>
<li><p>Click the <code>gear</code> icon in the widget of the sample application.</p></li>
<li><p>Click the <code>Delete App</code> entry.  In the <code>Services</code> tab, make sure that the PostgreSQL service is selected.  In the <code>Routes</code> tab, make sure that the route (i.e., URL) is selected.</p></li>
<li><p>Click the <code>DELETE</code> button.</p></li>
</ol>

<p><br></p>

<h4 id="end-of-tutorial">End of Tutorial</h4>

  </div>

  <div class="date">
    Written on 
  </div>

  
</article>

    </div>

    <div class="wrapper-footer">
      <div class="container">
        <footer class="footer">
          



<a href="https://github.com/jodanchua.github.io/jekyll-now"><i class="svg-icon github"></i></a>








        </footer>
      </div>
    </div>

    

  </body>
</html>
