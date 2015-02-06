## PyAgent
A python agent designed to fulfill your needs on any remote server.
Create Hooks to connect with outside world or do actions to manage your system.
The plugins can be on any language you like.
Remember that some third party plugins may or may not work on some operating systems check each plugin for particularities.

##Installation (Debian based)

You're gonna need composer for this one. And PHP 5 installed.

    # apt-get install python
    
Once you're finished all this commands you can now execute:

    ./bin/agent

## Daemon
This app has a daemon ready to go. There are two ways to use this daemon as a real daemon or as a cronjob
depending on your needs.

## Events
An event is a moment on the daemon life where you want to execute some action or hook

- startup
- first-time
- now

## Actions
In PHP agent the actions are when you want to execute some commands in the daemon mode usually when an event occurs. 

```json
{
  "name": "example-copy-action",
  "_event": "startup",
  "_action": "shell",
  "_params": "cp /usr/local/file.txt /usr/local/file2.txt"
}
```

## Hooks
A hook is a specialized type of action that sends the action result to a web-service on a server and allows specifying
 whether the hook is passive or active the possibility that this server returns some kind of feedback to the agent.

```json
{
  "name": "example-copy-hook",
  "type": "active",
  "url": "http://myserver.com/hooks",
  "_event": "startup",
  "_action": "shell",
  "_params": "cp /usr/local/file.txt /usr/local/file2.txt"
}
```
        
## Plugins
We have a lot of plugins and growing, each plugin could be an event or action.

### External plugins
The external plugins can be written in any language and basically must return a response in json format with the response of the plugin. The params will be passed as arguments.
