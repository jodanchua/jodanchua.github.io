
---
layout: post
title: Bluemix Basics
permalink: /language-translation/
---

<!DOCTYPE html>
<html>
  <head>
    <title>Language Translation – Jordan Chua – web developer</title>
  </head>

  <h1>Language Translation</h1>

  <div class="entry">
    <h2 id="application-development-tutorial">Application Development Tutorial</h2>


<p>Language Translation by Watsons can translate text from one language to another for specific domains</p>

<p>In this tutorial you will learn how to deploy a sample Language Translation Application in Bluemix.  In addition, you will learn  how to to use the API provided by IBM Watson</p>


<h4 id="copy-sample-application">Copy Sample Application</h4>

<p>You will download a copy of a sample application(Translator.war) that you will deploy in your Bluemix account.</p>

<ol>
<li><p>Create the directory <code>translator</code> in the root directory.  </p></li>
<li><p>Download <a href="https://github.com/jodanchua/Language-Translation/raw/master/Translator.war">Translator.war</a> and save it in the <code>translator</code> directory.</p></li>
</ol>

<p><br></p>

<h4 id="deploy-sample-application-in-bluemix-using-the-cf-tool">Deploy Sample Application in Bluemix using the <code>cf</code> tool.</h4>

<ol>
<li><p>Open a terminal window and go to the <code>translator</code> directory.</p></li>
<li><p>Login to your Bluemix account using the <code>cf</code> tool.</p>
<div class="highlight"><pre><code class="language-text" data-lang="text">&gt; cf login -a https://api.ng.bluemix.net -s dev
</code></pre></div>


<p><br></p></li>
<li><p>Upload the sample application to your Bluemix account.</p>
<div class="highlight"><pre><code class="language-text" data-lang="text">&gt; cf push lang_trans-&lt;your_name&gt; -m 256M -p Translator.war
</code></pre></div>
<p><strong>Example:</strong></p>
<div class="highlight"><pre><code class="language-text" data-lang="text">&gt; cf push lang_trans-jords -m 256M -p Translator.war
</code></pre></div>

<p><li>
Go back to the browser tab containing your Bluemix account. In the menu, click DASHBOARD.
</p>
<p>The <code>Applications</code> section of your dashboard shows a widget representing the application <code>lang_trans-&lt;your_name&gt;</code> you deployed earlier.</p>
</li>
</p>

<p><li>
Click the widget of your application to see its overview.
</li></p>
</ol>

<h4 id="add-a-Language-Translation-Service-and-bind-it-to-the-sample-application">Add a Language Translation Service and Bind it to the Sample Application</h4>

<ol>
<li><p>On the left pane, click the <code>Overview</code> link. </p></li>
<li><p>Click the <code>ADD A SERVICE OR API</code> link.  You will be redirected to the <code>Catalog</code> page. </p></li>
<li><p>Look for the <code>Language Translation by IBM Watsons</code> service and click it.</p>
<li><p>Click the <code>CREATE</code> button.</p></li>
<li><p>When asked to restage your application, click the <code>RESTAGE</code> button.  Wait for your application to restage.</p></li>
<li><p>Open another browser tab (do not close the browser tab containing your Bluemix account).  Go to <code>http://language-translation-test.mybluemix.net/</code> to test if the sample application can already connect to the created Language Translation service.</p>

<p><br></p></li>
</ol>

<h4 id="analyze">Analyze How the Sample Application and Language Translation Service Works</h4>
<ol>
<li><p>
 In order for the functions of the Language Translation API to work,  <code> Gradle</code> is required to download the the libraries needed to solve the dependcy problem of API. The following code is required in the <code> build.gradle</code> file:
</p></li>
<div class="highlight"><pre><code class="language-text" data-lang="text">compile 'com.ibm.watson.developer_cloud:java-wrapper:1.1.0'
</code></pre></div>

<p>
After running <code> gradle assemble</code> in the cmd, the dependencies are already resolved, therefore allowing the functions and methods of the Language Translation API to work.  
</p>

<li><p> If you extract the contents of <code>Translator.war</code> you will see the subdirectory <code>\src\main\java\Servlet</code>.  This contains several <code>.java</code> files including <code>LanguageTranslationServlet.java</code>. The <code>LanguageTranslationServlet.java</code> requires the following imports  in order for the functions of the Language Translation API to work.

<div class="highlight"><pre><code class="language-text" data-lang="text">import com.ibm.watson.developer_cloud.language_translation.v2.LanguageTranslation;

import com.ibm.watson.developer_cloud.language_translation.v2.model.TranslationResult;
</code></pre></div>
</p></li>

<li><p>The sample application and the Language Translation service by IBM Watsons is connected using this method provided by the API:
</p></li>

<div class="highlight"><pre><code class="language-text" data-lang="text">LanguageTranslation service = new LanguageTranslation();

service.setUsernameAndPassword("{username}","{password}");
</code></pre></div>

<p> 
The user will be able to authenticate to the Language Translation API by providing the username and password provided in the service credentials of the service. The  service credentials are extracted by a method using the VCAP_SERVICES as discussed in the first lab (Bluemix Basics).
</p>
</ol> 
<h4 id="Launch">Launch the Sample Application </h4>

<ol>
<li><p>
Go to the DASHBOARD of your Bluemix account. On the Applications section, click on the application <code>lang_trans-&lt;your_name&gt;</code> you pushed earlier.
</p>
</li>

<li><p>
Click the <code>Route</code> or <code>URL</code> just below your application name <code>lang_trans-&lt;your_name&gt;</code>.mybluemix.net. This will open up the web application.
</li></p>
</ol>

<h4 id="Run">Run the Sample Application </h4>
<p>
The web application is composed on only one webpage wherein the user can input any <code>ENGLISH</code> word to be translated to <code>SPANISH</code>.
</p>
<ol>
<li><p>
Input the word <code> "Hi" or "Hello" </code>.
</p>

<li><p>
Click the <code> Submit</code> button directly below the textbox. 
</p>

<li><p>
The translated text will be shown in the screen in a few seconds. The output will include the following in JSON format:

<div class="highlight"><pre><code class="language-text" data-lang="text">
Output:
{ "translations": [ { "translation": "Hola" } ], "word_count": 1, "character_count": 5 }
</code></pre></div>

To further enumerate, the output above shows the translated word <code> "Hola"</code>, the word count of the user input <code> "1"</code>, and the number of character/s of the word <code> "5"</code>.  
</p>
</li>

<li><p>
The output generated above was possible because of the function in the <code>LanguageTranslationServlet.java</code>:

<div class="highlight"><pre><code class="language-text" data-lang="text">TranslationResult translated = languageTranslation.translate(request.getParameter("inputText"), "en", "es");
</code></pre></div>

The <code> languageTranslation.translate</code> function above translates the input text of the user from the source language, English <code>"en"</code> to the target language,  Spanish or Español <code>"es"</code> .

<blockquote>
<p><strong>IMPORTANT:</strong>
The sample application that you are using can only translate from <code>English</code> to <code>Spanish</code>. Other languages are also available but it would require you to change the parameter/s of the function. <p><br></p>Other Languages include: Afrikaans: "af",Arabic : "ar", Bashkir: "ba".  
<p><br></p>The function <code>List <IdentifiableLanguages> langs = service.getIdentifiableLanguages();
System.out.println(langs);</code> could be addeded to the source code of  <code>LanguageTranslationServlet.java</code> to list all identifiable languages of the Language Translation service.
</p>
</blockquote>  
</p></li>

<li><p>
You can now try any <code>English</code> word to be translated to <code> Spanish.</code> 
</p></li>
</ol>
<h4 id="delete-the-sample-application-and-postgresql-service">Delete the Sample Application and Language Translation Service</h4>

<ol>
<li><p>Go back to the browser tab containing your Bluemix account.  In the menu, click <code>DASHBOARD</code>.  </p>

<li><p>Click the <code>gear</code> icon in the widget of the sample application.</p></li>
<li><p>Click the <code>Delete App</code> entry.  In the <code>Services</code> tab, make sure that the PostgreSQL service is selected.  In the <code>Routes</code> tab, make sure that the route (i.e., URL) is selected.</p></li>
<li><p>Click the <code>DELETE</code> button.</p></li>
</ol>

<p><br></p>

<h4 id="end-of-tutorial">End of Tutorial</h4>

<a href="https://github.com/jodanchua.github.io/jekyll-now"><i class="svg-icon github"></i></a>

    

  </body>
</html>
