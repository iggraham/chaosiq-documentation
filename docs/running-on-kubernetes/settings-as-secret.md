This section explains how to configure and use this operator for running
ChaosIQ verifications and experiments.

To be able to fetch assets from ChaosIQ, as well as pushing back results,
for both experiments and verifications, you'll need to setup a settings file
with a valid token and selected targeted organization & team.

Please refer to these documentation links, to [signin to ChaosIQ]
[SignInChaosIQ] with a token and select your default [organization]
[SelectDefaultOrg] and [team][SelectDefaultTeam].

By default, the settings file can be located at:
`~/.chaostoolkit/settings.yaml`

Then, you'll need to load these settings into Kubernetes, as a secret:
```bash
$ kubectl -n chaostoolkit-run \
    create secret generic chaostoolkit-settings \
    --from-file=~/.chaostoolkit/settings.yaml
```
Please refer to the official [documentation][PassSettingsAsSecret] for more
information on how to pass settings to the experiment with the operator.

You might have multiple organizations and teams, even possibly tokens, to use.
In that case, it's best to uniquely name your secret, as example:
`chaostoolkit-settings-<my-org>-<my-team>`
This will allow you to use multiple verifications and experiments from various
teams within the same namespace in your Kubernetes cluster. However, you'll
need to specify the settings secret name to the Chaos Experiment, as
described in the [documentation][PassSettingsAsSecret].

[SignInChaosIQ]: /gettingstarted/signin
[SelectDefaultOrg]: /organizations-and-teams/switching-organizations
[SelectDefaultTeam]: /organizations-and-teams/switching-teams
[PassSettingsAsSecret]: https://docs.chaostoolkit.org/deployment/k8s/operator/#pass-chaos-toolkit-settings-as-a-kubernetes-secret