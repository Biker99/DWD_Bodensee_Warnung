# DWD_Bodensee_Warnung
DWD Warnings for "Bodensee" filtered - leading to picture selection.

This tool loads the warnings.json from DWD and searches for "STARKWIND" or "STURM" in the three regions of "Bodensee".
The result is used to select the matching picture. This picture replaces an intially loaded default picture. 

Use this tool to visualize the DWD Sturmwarnung indications on the lake of constance in your Homepage.

 Hinweis und Beschreibung zum JSON vom DWD:
 - "time", "start" und "end" ist in Millie-Sekunden angegeben (time in milliseconds, between the CURRENT TIME and MIDNIGHT, JANUARY 1, 1970 UTC(coordinated universal time))
 - Warnregionen 909187999 hier ist gleich "Kreis und Stadt Rosenheim"
   weitere Information gibts beim DWD.
 - "event":"STURM" und "event":"STARKWIND" sind spezifika für Gewässer.
 - für Gewässer(hier im Code umgesetzt) gibt es nur eine event Meldung pro region. 
   Bei Regionen über "Land" können es auch mehrere events gleichzeitig sein (z.B. "ERGIEBIGER DAUERREGEN" und "DAUERREGEN") (das ist hier im Code nicht berücksichtigt!)
 
 DWD Warnmessage: warnings.json (Beispiel vom 18.7.2021)
	https://www.dwd.de/DWD/warnungen/warnapp/json/warnings.json
 
    warnWetter.loadWarnings({
      "time":1624808640000,
			"warnings":{
			  "909187999":
				  [{
					  "regionName":"Kreis und Stadt Rosenheim",
						"end":1626645600000, 
						"start":1626595560000,
						"type":2,
						"state":"Bayern",
						"level":4,
						"description":"Nach bisher beobachteten Niederschlagsmengen ...",
				==>	"event":"ERGIEBIGER DAUERREGEN",
						"headline":"Amtliche UNWETTERWARNUNG vor ERGIEBIGEM DAUERREGEN",
						"instruction":"ACHTUNG! Hinweis auf mögliche Gefahren: Infolge des Dauerregens ...!",
						"stateShort":"BY",
						"altitudeStart":null,
						"altitudeEnd":null
					},
					{
						"regionName":"Kreis und Stadt Rosenheim",
						"end":1626613200000,
						"start":1626595560000,
						"type":2,
						"state":"Bayern",
						"level":3,
						"description":"Es tritt Dauerregen wechselnder Intensität auf. Dabei ...",
				==>	"event":"DAUERREGEN",
						"headline":"Amtliche WARNUNG vor DAUERREGEN",
						"instruction":"",
						"stateShort":"BY",
						"altitudeStart":null,
						"altitudeEnd":null
					}
				]},
			"vorabInformation":{},
			"copyright":"Copyright Deutscher Wetterdienst"
		});	
