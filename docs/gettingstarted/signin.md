
So that your Chaos Toolkit installation can communicate with ChaosIQ, you need to set up your credentials using the `chaos signin` command.

First generate a token from the  ChaosIQ Tokens tab. The details for generating tokens are covered in the [Tokens section](/tokens/generate-token)


Use the `chaos signin` command to connect to ChaosIQ and add your token. When the `chaos signin` command prompts for the token, paste the token from your clipboard:

```
(chaostk) $ chaos signin
  ChaosIQ Cloud url [https://console.chaosiq.io]:
  ChaosIQ Cloud token:
  Experiments and executions will be published to organization 'MyName'
  ChaosIQ Cloud details saved at ~/.chaostoolkit/settings.yaml
```

Your Chaos toolkit will now publish executions to ChaosIQ.