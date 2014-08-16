<h1.
<a name="user-content-database-as-a-service-dbaas" class="anchor" href="#database-as-a-service-dbaas" aria-hidden="true"><span class="octicon octicon-link"></span></a>Database as a Service (DBaaS)</h1>

<h1>
<a name="user-content-introduction" class="anchor" href="#introduction" aria-hidden="true"><span class="octicon octicon-link"></span></a>Introduction</h1>

<p>This is an implementation of a database as a service api written in python + django. It will try to follow some hypermedia concepts throughout the api calls.</p>

<p>Below: Screenshot from the admin user.</p>

<p>image 1: Listing databases and their summary informations</p>

<p><a href="/globocom/database-as-a-service/blob/master/doc/img/manage_dbs.png" target="_blank"><img src="/globocom/database-as-a-service/raw/master/doc/img/manage_dbs.png" alt="Listing databases and their summary informations" title="Listing databases and their summary informations" style="max-width:100%;"></a></p>

<p>image 2: example database view and all its credentials</p>

<p><a href="/globocom/database-as-a-service/blob/master/doc/img/manage_one_db.png" target="_blank"><img src="/globocom/database-as-a-service/raw/master/doc/img/manage_one_db.png" alt="alt text" title="exampledb database view and all its credentials" style="max-width:100%;"></a></p>

<h1>
<a name="user-content-requirements" class="anchor" href="#requirements" aria-hidden="true"><span class="octicon octicon-link"></span></a>Requirements</h1>

<p>DBaaS requires the following:</p>

<ul class="task-list">
<li>python &gt;= 2.7.5</li>
<li>virtualenv &gt;= 1.7.2</li>
<li>virtualenvwrapper &gt;= 3.5</li>
<li>mysql server and client, version 5.5.x</li>
<li>mongo client (used by the clone feature)</li>
<li>redis (broker for async tasks with celery)</li>
<li>and all packages in requirements.txt file (there is a shortcut to install them)</li>
</ul><h1>
<a name="user-content-setup-your-local-environment" class="anchor" href="#setup-your-local-environment" aria-hidden="true"><span class="octicon octicon-link"></span></a>Setup your local environment</h1>

<pre><code>mkvirtualenv dbaas
workon dbaas
</code></pre>

<p>Install the required python packages.</p>

<pre><code>make pip
</code></pre>

<p>Install redis and start celery</p>

<pre><code>make run_celery
</code></pre>

<p>Create the tables structure (see the next item)</p>

<h2>
<a name="user-content-db" class="anchor" href="#db" aria-hidden="true"><span class="octicon octicon-link"></span></a>DB</h2>

<p>DBaaS uses south to maintain the migrations up-to-date. However, you can
just run syncdb to create the table structures. There is a shortcut to help you with that, including 
some minimum operational data on DB.</p>

<pre><code>make reset_data
</code></pre>

<h2>
<a name="user-content-running-all-tests" class="anchor" href="#running-all-tests" aria-hidden="true"><span class="octicon octicon-link"></span></a>Running all tests</h2>

<p>Before running the test, makes sure that you have mongod running and a user admin created with password 123456.</p>

<pre><code>db = db.getSiblingDB('admin')

db.addUser( { user: "admin",
              pwd: "123456",
              roles: [ "userAdminAnyDatabase", "clusterAdmin", "readWriteAnyDatabase", "dbAdminAnyDatabase" ] } )
</code></pre>

<p>Then install all the required packages</p>

<pre><code>make pip
</code></pre>

<p>Run it!</p>

<pre><code>make test
</code></pre>

<h2>
<a name="user-content-running-the-project" class="anchor" href="#running-the-project" aria-hidden="true"><span class="octicon octicon-link"></span></a>Running the project</h2>

<pre><code>make run
</code></pre>

<p>In your browser open the URL: http://localhost:8000/admin/</p>

<h3>
<a name="user-content-running-celery" class="anchor" href="#running-celery" aria-hidden="true"><span class="octicon octicon-link"></span></a>Running celery</h3>

<p>To run celery locally use the following command</p>

<pre><code>cd {APP DIR}
make run_celery
</code></pre>

<h1>
<a name="user-content-documentation" class="anchor" href="#documentation" aria-hidden="true"><span class="octicon octicon-link"></span></a>Documentation</h1>

<h2>
<a name="user-content-definitions" class="anchor" href="#definitions" aria-hidden="true"><span class="octicon octicon-link"></span></a><a href="/globocom/database-as-a-service/blob/master/doc/definitions.md">Definitions</a>
</h2>

<h2>
<a name="user-content-quickstart" class="anchor" href="#quickstart" aria-hidden="true"><span class="octicon octicon-link"></span></a><a href="/globocom/database-as-a-service/blob/master/doc/quickstart.md">Quickstart</a>
</h2>

<h2>
<a name="user-content-api" class="anchor" href="#api" aria-hidden="true"><span class="octicon octicon-link"></span></a><a href="/globocom/database-as-a-service/blob/master/doc/API.md">API</a>
</h2>

<h2>
<a name="user-content-drivers" class="anchor" href="#drivers" aria-hidden="true"><span class="octicon octicon-link"></span></a><a href="/globocom/database-as-a-service/blob/master/doc/drivers.md">Drivers</a>
</h2>

<h2>
<a name="user-content-changelog" class="anchor" href="#changelog" aria-hidden="true"><span class="octicon octicon-link"></span></a><a href="/globocom/database-as-a-service/blob/master/doc/changelog.md">Changelog</a>
</h2></article>
  </div>

  </div>
</div>

<a href="#jump-to-line" rel="facebox[.linejump]" data-hotkey="l" style="display:none">Jump to Line</a>
<div id="jump-to-line" style="display:none">
  <form accept-charset="UTF-8" class="js-jump-to-line-form">
    <input class="linejump-input js-jump-to-line-field" type="text" placeholder="Jump to line&hellip;" autofocus>
    <button type="submit" class="button">Go</button>
  </form>
</div>

        </div>

      </div><!-- /.repo-container -->
      <div class="modal-backdrop"></div>
    </div><!-- /.container -->
  </div><!-- /.site -->


    </div><!-- /.wrapper -->

      <div class="container">
  <div class="site-footer">
    <ul class="site-footer-links right">
      <li><a href="https://status.github.com/">Status</a></li>
      <li><a href="http://developer.github.com">API</a></li>
      <li><a href="http://training.github.com">Training</a></li>
      <li><a href="http://shop.github.com">Shop</a></li>
      <li><a href="/blog">Blog</a></li>
      <li><a href="/about">About</a></li>

    </ul>

    <a href="/" aria-label="Homepage">
      <span class="mega-octicon octicon-mark-github" title="GitHub"></span>
    </a>

    <ul class="site-footer-links">
      <li>&copy; 2014 <span title="0.06045s from github-fe127-cp1-prd.iad.github.net">GitHub</span>, Inc.</li>
        <li><a href="/site/terms">Terms</a></li>
        <li><a href="/site/privacy">Privacy</a></li>
        <li><a href="/security">Security</a></li>
        <li><a href="/contact">Contact</a></li>
    </ul>
  </div><!-- /.site-footer -->
</div><!-- /.container -->


    <div class="fullscreen-overlay js-fullscreen-overlay" id="fullscreen_overlay">
  <div class="fullscreen-container js-suggester-container">
    <div class="textarea-wrap">
      <textarea name="fullscreen-contents" id="fullscreen-contents" class="fullscreen-contents js-fullscreen-contents js-suggester-field" placeholder=""></textarea>
    </div>
  </div>
  <div class="fullscreen-sidebar">
    <a href="#" class="exit-fullscreen js-exit-fullscreen tooltipped tooltipped-w" aria-label="Exit Zen Mode">
      <span class="mega-octicon octicon-screen-normal"></span>
    </a>
    <a href="#" class="theme-switcher js-theme-switcher tooltipped tooltipped-w"
      aria-label="Switch themes">
      <span class="octicon octicon-color-mode"></span>
    </a>
  </div>
</div>



    <div id="ajax-error-message" class="flash flash-error">
      <span class="octicon octicon-alert"></span>
      <a href="#" class="octicon octicon-x close js-ajax-error-dismiss" aria-label="Dismiss error"></a>
      Something went wrong with that request. Please try again.
    </div>


      <script crossorigin="anonymous" src="https://assets-cdn.github.com/assets/frameworks-12d5fda141e78e513749dddbc56445fe172cbd9a.js" type="text/javascript"></script>
      <script async="async" crossorigin="anonymous" src="https://assets-cdn.github.com/assets/github-a61187924f7160c9ea470f937aa5fb3d3dc74191.js" type="text/javascript"></script>
      
      
        <script async src="https://www.google-analytics.com/analytics.js"></script>
  </body>
</html>

