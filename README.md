## What is it?
P4RA Server is a Fortnite private server for older fortnite versions.

## How to use it?
1) Install [NodeJS](https://nodejs.org/en/) and [Fiddler](https://telerik-fiddler.s3.amazonaws.com/fiddler/FiddlerSetup.exe)
2) Run install.bat
3) Run start.bat
4) Open Fiddler and Go to Tool > Options > HTTPS - Turn Decrypt HTTPS traffic and Ignore server certificate errors on - Press Actions and Press Trust Root Certificate, now a          Messagebox should pop up. Press Yes and after you get an Message that you added fiddlers root certificate you can press ok. And Again press ok to close the Options. Go to          Fiddler Script and paste this code:
```
   import System;
   import System.IO;
   import System.Threading;
   import System.Web;
   import System.Windows.Forms;
   import Fiddler;
    
   class Handlers
   {
       static function OnBeforeRequest(oSession: Session) {
           if (oSession.hostname.Contains(".ol.epicgames.com"))
           {
               if (oSession.HTTPMethodIs("CONNECT"))
               {
                   oSession["x-replywithtunnel"] = "FortniteTunnel";
                   return;
               }
               oSession.fullUrl = "http://127.0.0.1:9999" + oSession.PathAndQuery;
           }
       }
   }  
   ```
5) Now you can Start your Fortnite version

## Credits
Credits to [Lawin Server](https://github.com/Lawin0129/LawinServer) [Lawin](https://github.com/Lawin0129)
