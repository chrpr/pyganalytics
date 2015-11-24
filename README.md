# pyganalytics 

A first cut at basic code to harvest specific dimensions 
and metrics from Google Analytics.

##### Installation

See reqiurements.pip for a list of dependencies. If you're running 
Ananconda, you can create a new environment with:

		% conda create --name pyganalytics python=2.7
		% activate pyganalytics (WIN)
		% source activate pyganalytics (Linux)

Otherwise, use Virtual Environment:

		% virtualenv --no-site-packages pyganalytics
		% source pyganalytics/bin/activate (Linux)

And install Requirements

		% pip install -r requirements.pip

##### Setup

You'll need to set up authentication. 

* Create and authorize a project at Developers Console: console.developers.google.com
* Rename client_secret.json.template to client_secret.json
* Add Client ID & Client Secret values from Developers Console 
* On first use, you will be prompted to authorize the app via a browser window.

##### Usage

* Rename config.yml.template to config.yml
* Add the ID for the _view_ you want to analyze
	* Under Analytics, select "Admin"
	* Select an Account, Property, and View
	* Click "View Settings"
	* Copy and paste "View ID" into config.yml
* By default, this configuration gives counts of pageviews by page
	* You can change your metrics (only supports one at a time)
	* You can change dimensions (supports a comma separated list)
* Requires 3 arguments:
	* Output file name
	* Configuration yml file (supports multiple configurations)
	* Start Date (date to begin harvesting from)
	* End Date (default is current date)


       		# python analytics.py -o test.csv -c nyu.yml -f 2015-11-01


* By default, it runs in "weekly mode", but if you see "sampling", can be changed to daily.
	* Change rrule.WEEKLY to rrule.DAILY
    * Change timedelta(days=6) to timedelta(days=0)