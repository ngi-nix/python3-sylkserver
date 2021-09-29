**Nixos Flake : AGSystem SylkServer -  A State of the art, extensible RTC Application Server.**

[Source](https://github.com/AGProjects/sylkserver)

SylkServer allows creation and delivery of rich multimedia applications
accessed by WebRTC applications, SIP clients and XMPP endpoints.  The server
supports SIP and XMPP signaling, RTP, MSRP and WebRTC media planes, has
built in capabilities for creating multiparty conferences with Audio and
Video, IM/ File Transfers and can be extended with custom applications by
using Python language.

## Prerequisites    
Install Nix with flake support as given in [https://nixos.wiki/wiki/Flakes](https://nixos.wiki/wiki/Flakes)    
In debian based systems the method is as follows after installing Nix    
  ```sh    
  nix-env -iA nixpkgs.nixUnstable    
  ```
Edit either ~/.config/nix/nix.conf or /etc/nix/nix.conf and add:    
  ```sh    
  experimental-features = nix-command flakes                           
  ```


### Installation    
To build the flake run
`nix build  github:ngi-nix/python3-sylkserver`

The flake is a PR now can test by running
`nix build  github:raghuramlavan/python3-sylkserver`

-The sylkserver requires configuration files and certificates for starting up the sample configuraiton files and certificates are provided in 
(Sample Configuration files)[https://github.com/AGProjects/sylkserver] with *.ini.sample extentions. (Need to rename them to .ini)
(Certificates)[https://github.com/AGProjects/sylkserver/tree/master/resources/tls]

-Firewall has to accept connections at the activated ports.

Sample output is

~~~bash
```./result/bin/sylk-server --no-fork --config-dir /home/lavan/sylk/ --runtime-dir /home/lavan/sylk
INFO     [sylk.core]     Starting SylkServer 6.0.0, using SIP SIMPLE SDK 5.2.6
INFO     [sylk.core]     Reading configuration from /home/lavan/sylk/config.ini
INFO     [sylk.core]     Using resources from /nix/store/i7y33xn8lrp9xwqhk3rx3l8r456wdy63-sylk-server-5.7.0/share/sylkserver
INFO     [sylk.core]     Using spool directory /home/lavan/sylk
INFO     [sylk.core]     TLS CA list: /home/lavan/sylk/ca.crt
INFO     [sylk.core]     TLS Certificate: /home/lavan/sylk/default.crt
INFO     [sylk.core]     TLS verify server: False
INFO     [sylk.core]     TLS identity: C=NL,ST=Noord-Holland,L=Haarlem,O=AG Projects,OU=Sylkserver,CN=Sylkserver,EMAIL=devel@ag-projects.com
INFO     [sylk.core]     TraceLogManager started in /home/lavan
INFO     [sylk.core]     SylkServer started; listening on:
INFO     [sylk.core]       10.0.2.15:5060 (UDP)
INFO     [sylk.core]       10.0.2.15:5060 (TCP)
INFO     [sylk.core]       10.0.2.15:5061 (TLS)
INFO     [sylk.core]     Available audio codecs: G722, PCMA, GSM, PCMU, iLBC, speex
INFO     [sylk.core]     Enabled audio codecs: opus, G722, speex, PCMA, PCMU
INFO     [sylk.core]     Available video codecs: H263-1998, VP9, H264, VP8
INFO     [sylk.core]     Enabled video codecs: H264, VP8, VP9
INFO     [sylk.core]     Web server listening for requests on: http://10.0.2.15:10888
INFO     [sylk.core]     Loaded applications: conference, echo, ircconference, playback, webrtcgateway, xmppgateway
INFO     [sylk.core]     Default application: conference
INFO     [sylk.core]     Application map:
INFO     [sylk.core]       echo: echo
INFO     [xmppgateway]   XMPP S2S component listening on 10.0.2.15:5269 (TLS)
INFO     [webrtcgateway] WebSocket handler started at ws://10.0.2.15:10888/webrtcgateway/ws
INFO     [webrtcgateway] Allowed web origins: *
INFO     [webrtcgateway] Allowed SIP domains: *
INFO     [webrtcgateway] Using Janus API: ws://127.0.0.1:8188
INFO     [webrtcgateway] Admin web handler started at http://127.0.0.1:20888
INFO     [sylk.core]     Stopping SylkServer...
INFO     [sylk.core]     SIP application ended
INFO     [sylk.core]     SylkServer stopped ```
~~~