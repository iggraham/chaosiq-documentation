# Create your first Verification

![Create Verification][CreateVerification]

[CreateVerification]: ./create-verification.png

The first part of the Verification form links the Verification to the Objective you have just created. You can optionally change this to another Objective via the drop down list. In part 2 of the form you give you Verification a name that reflects what this Verification is going to do, an example could be is Ensure My Service remains available when a Web Service POD restarts. Then you will enter a frequency in seconds and over what duration your Verification will be run. The values chosen on these fields impact your usage footpriont in ChaosIQ so a high usage warning may be displayed.

The third Part of the Verification form identifies the conditions you want to apply as part of your Verification.

The first option is to apply No Condition, this means you are going to measure you Verification but you are not going to apply an adverse effect as part of your Verification. This is a good case for a control Verification as it establishes how the Verification performs in normal conditions. In this case leave the condition as No Condition and select the *Create Verification and View Execution Steps* button to on to the Run your Verification page.
