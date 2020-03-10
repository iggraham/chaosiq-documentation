ChaosIQ is added to your Chaos Toolkit as a [plugin](https://github.com/chaosiq/chaosiq-cloud). The ChaosIQ features can be added to your Chaos Toolkit CLI installation by executing:

```
(chaostk) $ pip install chaosiq-cloud
```

## Sign-in to ChaosIQ with your Credentials

So that your Chaos Toolkit installation can interact with ChaosIQ, you need to set up your credentials using the `chaos signin` command. A token is generated from the  ChaosIQ [Tokens tab](https://console.chaosiq.io/tokens).

![Tokens Page][TokensPage]

[TokensPage]: ./tokens-page.png

Enter a token name and click the `Generate Token` button:

![Copy Token][CopyToken]

[CopyToken]: ./copy-token.png

Click the `Copy To Clipboard` button and the token will be copied to your clipboard, ready to be added to your Chaos Toolkit CLI by signing into ChaosIQ.

Use the `chaos signin` command to connect to ChaosIQ and add your token. When the `chaos signin` command prompts for the token, paste the token from your clipboard:

```
(chaostk) $ chaos signin
  ChaosIQ Cloud url [https://console.chaosiq.io]:
  ChaosIQ Cloud token:
  Experiments and executions will be published to organization 'MyName'
  ChaosIQ Cloud details saved at ~/.chaostoolkit/settings.yaml
```