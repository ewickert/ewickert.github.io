---
layout: post
title: Prefering Asynchronous Sockets in C#
---

# Introduction
Known to everyone in the world (except for me apparently) using one thread for
each socket in your application is *incredibly* slow. Working on an application
that has to do some socket level networking, I had tried using this naive 
implementation:

```csharp
var handler = Sock.Accept();
new Thread(() => {
    handler.Send(Message);
    handler.Recieve(Message, NumBytes);
}).Start();
```

I figured that this implementation would be fast enough, especially given that
I was transmitting fairly small messages for the most part. What I didn't account
for is that given a substantial message volume, the time spent creating new
`Thread`s and the time they wasted waiting for data to show up would start to add 
up. So confronted with a program that couldn't handle anywhere near the number
of connections I needed, I went and looked for another solution.

# Async Is Much Faster

I found out that it is generally understood that the using synchronous I/O, and
one thread per socket is way too slow to be any use. The answer is to use the
asyncronous calls. For just about every I/O method on a `Socket` there is a
`Begin` equivalent that does the same thing asyncronously. So I changed my basic
implementation to something like this:

```csharp
while(true)
{
    Sock.BeginAccept(AcceptCallback, Sock)
}

void AcceptCallback(IAsyncResult ar)
{
    var sock = ar.AsyncState as Socket;
    var handler = sock.EndAccept(sock.EndAccept(ar));
    var state = new StateObject();
    state.buffer = new byte[12];
    handler.BeginRecieve(state.buffer, 0, 12, SocketFlags.None,RecieveCallback, state);
}

void RecieveCallback(IAsyncResult ar)
{
    // Recieve code goes here...
}

// This object should contain whatever kind of state you need to maintain between
// async calls.
public class StateObject
{
    public byte[] buffer;
}
```

Using the API this way allows the framework and operating system to do the hard
work of keeping threads from being idle too long and wasting time. This boosts
the performance of the networking parts of you application, and allows you to
handle signifigantly more connections.

# Conclusion

This is apparently a pretty common knowledge in the .NET world. It's new to me though, and hopefully, this may be found by some poor new developer who has spent the last
couple of hours wondering why his application can't handle nearly the number of 
connections he thinks it should.
