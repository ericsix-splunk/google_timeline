================================================================
=     Google Timeline View                              	=
=     Author : Eric Six                                   	=
=     Datasource : Google Timeline Export { json format }   	=
=     *** https://www.google.com/maps/timeline
=     							    	=
=     Notes :                                               	=
=     App has examples using indexed extractions, and       	=
=     standard formatting. Review the props.conf to see     	=
=     what needs to be done for each sourcetype.              	=
=                                                           	=
=     Index Requirements : index named 'google' is required 	=
=     Index Time Extractions : Yes / Depends on sourcetype  	=
=								=
=								=
=     Additional Requirements :                                 = 
=		 Location Tracker App Visualiztion              =
=								=
=								=
=								=
=================================================================

Additional Notes:

	There are two sourcetypes associated with this app.
         - JSON with Indexed Extractions -- json:google:location:indexedextractions
i		This utilizes tstats in the dashboards as an example of how fast
		you can work with indexed extractions.

         - JSON with Search Time Extractions -- json:google:location
		This is the standards method to load data sources.


	The JSON export from Google requires some preprocessing in 
	order to get the data into Splunk cleanly with indexed
	extractions. You can use the following sed commands to clean
	this up. * This is based on GNU sed on linux.

	$ sed  -i -e '/^{/,+0 d;s/  \"locations\" : \[ {/{/; s/  }, /}\n/;$ d'   LocationHistory.json &&
	sed -i -e '$ s/  } ]/}/' LocationHistory.json

	Once you run that, you can load the LocationHistory.json file with the json:google:location:indexedextractions sourcetype.

	Otherwise, you can load the LocationHistory.json as the json:google:location sourcetype.


Thanks to:
	Nate McKervey for the belay, the idea, and the tstats assistance.





    


