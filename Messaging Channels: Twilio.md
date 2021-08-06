Sign up for free on www.twilio.com   
Select programmable messaging service from the options.
In order to connect Twilio to our chatbot we use ngrok

Sign up for free on NGROK account: we use ngrok to get a public URL for our local web application.
 
 **Ngrok for command line Linux**

*step 1* 
We download ngrok by heading towards ngrok.com/download in the Rasaproject folder with all the other files.

*step 2*
We unzip the downloaded file by double clicking and extract here command(Windows in RasaProjct folder)

*step 3*
now open the directory RasaProject in Command line.
now using the command ls(for Linux) check if u can find ngrok.exe file

*step 4*
the file should be present in your RasaProject folder, if it is then
`ngrok http 5005`  
^ command could open up a channel that we would be using further for connecting Twilio with out Bot.

  
**How to use ngrok with Windows and Visual Studio**

*step 1* 
We download ngrok by heading towards ngrok.com/download in the Rasaproject folder with all the other files.

*step 2*
We unzip the downloaded file by double clicking and extract here command(Windows in RasaProjct folder)
   
*step 3*
In command prompt in our rasaproject folder, write 
`ngrok version`
to know if the file has been extracted successfully.

*step 4*
The quickest way to get started with ngrok and Visual Studio is to use an open source extension for Visual Studio that will start ngrok for any web applications that are part of the currently open solution. It will figure out the ports for you and fire up the necessary tunnels.

![image](https://user-images.githubusercontent.com/69692410/128381835-32acf208-d181-4c8d-8e55-6e7a5c594f74.png)

Chose "Start ngrok Tunnel" from the Visual Studio "Tools" menu, ngrok will start, and you'll see your app's new public URL.

![image](https://user-images.githubusercontent.com/69692410/128382014-f28adbd2-94e6-48f3-84e1-04ed362719ab.png)

Here, ngrok gave us the URL of https://a9f03915.ngrok.io. Make sure you've started your application in Visual Studio and then try to open that URL in your twilio browser. It should load the app from your local development machine. Now, you have a URL you can give to anyone or use in the Twilio console, and it will hit the app running on your machine. 

You can leave ngrok running while you are working on your bot. If you stop your bot, ngrok can continue to run and will resume serving traffic to your app when you restart your app. If you do shut down ngrok, then you will be given a new URL when it restarts. This means your ngrok URL will need to be updated each time you restart ngrok.
