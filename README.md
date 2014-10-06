<h1>STILL UNDER DEVELOPMENT</h1>

Series of patches to get data from MindWave Mobile and Emotive Epoch into Max MSP, including flexible parameter routing and visualization. 

<h2>DEPENDENCIES</h2><br />
This project relies on the tcpClient external Java class, found here: http://cycling74.com/toolbox/tcpclient/ Follow the instructions as to where to place this in your Max folder. <br />
These patches communicate with Neurosky's ThinkGear Connector software using ThinkGear Socket Protocol (TGSP). You must have ThinkGear Connector installed, download here: http://developer.neurosky.com/docs/doku.php?id=thinkgear_connector_tgc (see 'Latest Builds'). More info on TGSP: http://developer.neurosky.com/docs/doku.php?id=thinkgear_socket_protocol


<h2>STEPS</h2> <br />
1. Get tcpClient Java class installed (see above)<br />
2. Download and install ThinkGearConnect (see above) <br />
3. Make sure the folder with these patches is in your Max path somewhere or add it as its own path (see Options->File Preferences). This is to get the supplied externs working.<br />
4. Open ThinkGear Connector<br />
5. Connect your MindWave Mobile<br />
6. Open patch NeuroSkyInput. It should connect to ThinkGear Connector automatically, if you click the system tray dropdown, you should see "1 connected application"<br />
7. <h3>BUG</h3>: Open MindWaveMobile Tutorial. For some reason, ThinkGear Connector won't spit out data until this step is done. Trying to figure out which message I'm supposed to send that I'm missing.<br />
8. After this you should see data streaming into Max! …Hopefully?<br />


Max 6 SHA-1 code generated on Max.app/Contents/MacOS/Max: a4785a4ca03023bbe8528985b44644757f0f2ed0


'Neurosky.' class refers to Neurosky MindWave Mobile
'Epoch.' class refers to Emotiv Epoch

'.Routing' patches are used to route the parameters from each to an outlet. The rely on receiving input data in a named convention. Neurosky.TGCSunpack sends the appropriate Neurosky data. TODO Still need to set up a patch for Epoch

<h3>NOTE:</h3> raw EEG data exists for both headsets, so there is a naming convention to follow for sending/receiving their data. Neurosky is rawer, Epoch is rawEEG

<h3>NOTE:>/h3> output range of EEG Power values is currently unscaled, and struggling with this - ranges as high as 600,000 have been seen


<h2>PATCH LIST AND EXPLANATION:</h2><br />
CopyFrom: pre-loaded bpatchers to copy for use in your patches<br />
Epoch.Routing: flexible parameter routing from Emotiv Epoch. To be used in bpatcher, found in CopyFrom<br />
Neurosky.Routing: flexible parameter routing from NeuroSky MindWave Mobile. To be used in bpatcher, found in CopyFrom<br />
Neurosky.TGCSunpack: unpacks JSON-based dictionaries sent over TCP/IP from ThinkGearConnector. This is the heart of the patch. It outputs the parameters to individual outlets, as well as all of the EEG Power values in one packed list. All parameters are also sent within Max, allowing use of Neurosky.Routing and Neurosky.Vizualizer without any patch cables<br />
Neurosky.Vizualizer: Vizualizes output of MindWave Mobile. Still need to do some work on ranges…<br />
NeuroSkyInput: open this to connect to ThinkGear Connector and see visualization. Basic example patch, essentially<br />
NeurSkyOSC: ignore<br />
oldVizualizer: ignore<br />

Somewhat based on this project: https://github.com/trentbrooks/BrainWaveOSC
