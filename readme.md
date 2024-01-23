# Deno WebRTC Communications 

# Warning! 
## Recent issues with using BroadcastChannel
For some unknown reason, all of my applications that use Deno BroadcastChannel    
no longer work reliably!  I'm not sure why this is so, but the problem has surfaced in many of my applications that use BC.

# Do Not Use until further notice.

This library is a support service for a Deno Deploy app:    
https://github.com/nhrones/FreshDiceRTC

I built this because I was having many issues with determinism of the Deploy WebSockets and SSE.   

I decided to simply use Deploy as an app and signal server, and then just rely on WebRTC for real-time game-events. This worked extremely well!   

<br/>

 ![Alt text](./media/Signaling.png)
 
<br/>

This lib includes:    
  *  A Deno-Deploy Signal Service     
        *  Client =  signaling.ts    
        *  Server + Signal-service = FreshDiceRTC -> routes/api/sse.ts    
  *  WebRTC connection module    
  *  A Peer management module

The main issue with this architecture is that all peers are responsible for maintaining a syncronized state. 
 
<br/>

![Alt text](./media/comms.png)
 
<br/>

## See it: 
Open two instances of https://fresh-dice.deno.dev/

After the second instance(Peer) establishes a connection, the signal-server is no longer required.  All further game communication is via the established `WebRTC-dataChannel`.      
You can view the RTC coms logs by opening the chrome devtools console.    
