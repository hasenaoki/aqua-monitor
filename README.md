Aqua Monitor shows how the Earth's surface water has changed during the last 30 years.

http://aqua-monitor.appspot.com

See also the following Nature Climate Change paper: http://nature.com/nclimate/journal/v6/n9/full/nclimate3111.html

The website shows static map by default, visualizing surface water changes which occurred during 1985-2016 as explained in the above paper (see supplementary materials). 

A dynamic mode can be turned on for a more detailed analysis. In this mode, the surface water changes are computed on-the-fly using parameters provided by the user. Additionally, percentile composite images are generated for two selected years.

The following Google Earth Engine script can be used to generate surface water changes on-the-fly: https://code.earthengine.google.com/b2213fa2838a5e1d7d16a5ec5b758210. And the following was used to generate scatic maps: https://code.earthengine.google.com/211b8491e1770136316d9df7f7e5ee20. 

The results presented in the paper include a few additional clean-up steps (noise clean-up in the mountains using HAND mask, deforestation-like changes). But they were excluded during static map generation.

# How to build?

Install Node.js, which is used by build scripts to compile sources and prepare everything for deployment.

Then run the following commands:

* npm install - downloads and installs all packages required to build the app (see packages.json)
* bower install - downloads and installs all client-side packages (see bower.json)

After that, run:

* gulp build - compiles everything (minifies code, generates styles, etc.) and places results in dist/

The resulting dist/ directory can be used to deploy everything as a Google App Engine app.

Use "gulp watch" to monitor sources continuously during development - they will be automatically compiled into dist/ on every change. 
See gulpfile.babel.js for the rules used to do this.

# How to run and deploy?

To deploy the Aqua Monitor under Google App Engine. The following files need to be added / modified:

* app/privatekey.pem - add your service account key, this is used by Python backend.
* app/config_web.py - add your client id, secret, and a refresh token, used at runtime to generate access to GEE for the JavaScript code. 



