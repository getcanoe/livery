# Livery
This is a small client written in Nodejs that can be run on any computer turning that machine into a PoW worker "slave" that connects to a Canoe backend and registers itself ready to perform PoW for the Canoe wallets.

## How it works
When running this client connects to a Canoe backend using MQTT over WSS and registers as ready to perform PoW. Then the backend will send PoW requests and Livery will perform them by calling the ordinary RPC HTTP call that the Nano node uses, and other PoW implementations. When the result comes back, Livery publishes it to the Canoe backend which in turn sends it out to the proper wallet where it originated.

The advantages of using pub/sub over WSS is that no changes in local router or firewalls are needed.

## How do I start?
1. Install Livery and optionally a PoW implementation. Livery has raiblocks-pow inside, so it can perform PoW itself, but if you have a GPU or similar, you may want to use an even faster implementation.

2. Talk to someone operating a Canoe backend and get a username/password for your Livery. To begin with we don't allow anonymous workers to just connect willy-nilly.

3. Edit `livery.conf` with proper credentials and run livery. Watch it perform an initial test-PoW. It will report if all works!

4. Livery will log whenever it performs a job, so you can see how many it har performed and how long each took etc.

