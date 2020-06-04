![Verification Run][CreateVerification]

[CreateVerification]: ./images/create-verification.png


ChaosIQ will display the Run Verification page showing the Chaos Verify command with a URL selecting your Verification. To run the Verification select the *Copy* button, which will capture the command in your clipboard.  Open the terminal window where you set up your Chaos Toolkit and paste in the Chaos Verify command and select enter to run it. The command should run the Verification and publish the results to ChaosIQ. If you go to the Verifications page and select your Verification, you should be able to see the current state of the
Verification.

![Verification Running][VerificationRunning]

[VerificationRunning]: ./images/verification-running.png

 The Insights page will give you a view of your Verifications that have completed. This will give you an indication of the timeline of the Verification and a view of the events that occurred when the Verification was running. It is from the insights page that you should be able to learn the impact of your Verification and determine what actions are required. To view the results select the Insights menu option.

 ![Verification Insights][Verification Insights]

 [Verification Insights]: ./images/verification-insights.png

 That's your first Verification created, run and published to ChaosIQ. The results are now made available on the Insights page.  From the Insights page you can select the Details button and you can see the details view of the insight.

 ![Insight Details][Insight details]

 [Insight details]: ./images/insight-details.png

 The details view includes information about the Objective, the Measurement used and the Verification. It shows the Verification Run Timeline that includes a timeline chart of samples.

 Next steps are to add Conditions to your Verification to see what, if any, impact this might have on your Objective.