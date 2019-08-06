# SILENTTRINITY

<p align="center">
  <img src="https://user-images.githubusercontent.com/5151193/45964397-e462e280-bfe2-11e8-88a7-69212e0f0355.png" width=400 height=400 alt="ST"/>
</p>

SILENTTRINITY is modern, asynchronous, multiplayer & multiserver C2/post-exploitation framework powered by Python 3 and .NETs DLR.

Some of the main features that distinguish SILENTTRINITY are:
- Client & Teamserver are built in Python 3.7, heavy use of Asyncio provides ludicrous speeds. Additionally all communication happens in real-time using Websockets.
- Focus on usability with an extremely modern CLI powered by [prompt-toolkit](https://github.com/prompt-toolkit/python-prompt-toolkit)
- The SILENTTRINITY implant/agent is somewhat unique as it uses embedded .NET scripting languages to dynamically evaluate & call .NET APIs, this allows for much greater flexibilty and stealth over traditional C# based payloads
- Listeners, Modules, Stagers and C2 Channels are fully modular allowing operators to easily build their own  
- Extensive logging, every action is logged to a file
- Future proof, HTTPS/HTTP listeners are built on [Quart](https://gitlab.com/pgjones/quart) & [Hypercorn](https://gitlab.com/pgjones/hypercorn) which also support HTTP2 & Websockets

## Setup & Requirements

- Python >= 3.7 is required.
- Client & Teamserver have only been tested on Mac & Linux systems, however they *should* work on Windows as well.

If your system has an older version of Python installed it is *highly* reccommended to use [pyenv](https://github.com/pyenv/pyenv) to install Python >= 3.7.

Clone the repo and use [pipenv](https://github.com/pypa/pipenv) to install the dependencies for the Client & Teamserver:

```bash
#~ https://github.com/byt3bl33d3r/SILENTTRINITY
#~ pip3 install pipenv && pipenv install && pipenv shell
```

Start a Teamserver, the default port is 5000:
```bash
python3 teamserver.py <teamserver_ip> <teamserver_password>
```

Connect to a Teamserver:

**Note the wss:// (two s's) in the URL which indicates an encrypted websocket connection (TLS), without this all traffic from the client to the teamserver will be in cleartext!** 

```bash
python3 st.py wss://username:<teamserver_password>@<teamserver_ip>:5000
```

Alternatively, run ```st.py``` without any arguments and connect to a Teamserver manually using the CLI menu:
```
[0] ST ≫ teamservers
[0] ST (teamservers) ≫ connect -h
        Connect to the specified teamserver(s)

        Usage: connect [-h] <URL>...

        Arguments:
            URL   teamserver url(s)

[0] ST (teamservers) ≫ connect wss://username:<teamserver_password>@<teamserver_ip>:5000
```

## Documentation

Coming Soon(™), for now make wild use the ```help``` command and the ```-h``` flag :)

## Author

Marcello Salvati [@byt3bl33d3r](https://twitter.com/byt3bl33d3r)

## Acknowledgments & Contributors

**(In no particular order)**

- [@C_Sto](https://twitter.com/C__Sto) for helping me with some of the .NET ECDHE implementation details and keeping my sanity
- [@davidtavarez](https://twitter.com/davidtavarez) for making some amazing contributions including a cross-platform stager
- [@mcohmi](https://twitter.com/mcohmi) a.k.a daddycocoaman, code contributions including modules
- [@cobbr_io](https://twitter.com/cobbr_io) for writing SharpSploit which was heavily used as a reference throughout building a lot of the implant code & modules.

If I missed anyone I apologize, feel free to contact me via Twitter and/or Email and I'll get it sorted out asap.