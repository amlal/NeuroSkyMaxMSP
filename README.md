Still working on this one, getting input from a NeuroSky MindWave Mobile.

So far, the project relies on the tcpClient external Java class, found here: http://cycling74.com/toolbox/tcpclient/

Connects via TGSP, more here: http://developer.neurosky.com/docs/doku.php?id=thinkgear_socket_protocol

Max 6 SHA-1 code generated on Max.app/Contents/MacOS/Max: a4785a4ca03023bbe8528985b44644757f0f2ed0

Still have a bug where you need to open MindWaveMobile to get data stream...

Neurosky. class refers to Neurosky MindWave Mobile
Epoch. class refers to Emotiv Epoch

.Routing patches are used to route the parameters from each to an outlet. The rely on receiving input data in a named convention. Neurosky.TGCSunpack sends the appropriate Neurosky data, but need to send Epoch from a patch.

NOTE: raw EEG data exists for both headsets, so there is a naming convention to follow for sending/receiving their data. Neurosky is rawer, Epoch is rawEEG
