## Frontend Multiwarning (FMW) for eBao Life System

### About FMW
It is a module written for the eBao Life System to provide:

* A single endpoint at backend for form validation (vRules required)
* A convenient, unified and automatic error display on frontend upon validation failures, without page reload

### Prerequisites

* vRules
* jQuery v1.11

### Installation 

* Pull the latest from SVN trunk and you should find the following in `ls-pub`:
	* ValidateVRulesAction.java
	* Multiwarning.jsp
* No other installations needed


### One-minute Usage
1. Include the javascript module by the line in your jsp

	~~~jsp
	<%@ include file=“/ls/pub/Multiwarning.jsp” %>
	~~~
1. Depends on your usage, you might want to submit the form with another name. In this case `form1` is submitted to the validation endpoint at server. Add the following lines to your jsp as well:

	~~~html
	<script>
	var form1MW = new Multiwarning({
	  form: $(form1),
	  endpointURL: "<url:prefix/>/validateVRules.do?ruleFilePath="
	    +encodeURIComponent("/vrules/validation/party/maintain_basic_info/orgPartyRole.vrules.xml")
	    +"&formName="
	    +encodeURIComponent("com.ebao.ls.pty.ctrl.partyrole.PartyRoleForm"),
	  onValidationPass: function(){
	    submitForm('submitOrgPartyRole.do')
	  }
	})
	</script>
	~~~
	
	You must supply which **vRule config file** and to which **form** you are validating against, in the `endPointURL` as parameters.

	You can specify what function to call upon validation passes at `onValidationPass` option.
	
1. Lastly, bind the FMW to your button:
	
	~~~jsp
	<Field:button type="confirm" name="submit" value="MSG_104549" onclick="form1MW.validate(this)" />
	~~~
	
	Passing a `this` allows the FMW to access/change the properties of the button
	
	

### Troubleshooting

1. If you have pulled the latest code from trunk but still don't see any changes in version number *(see [API references][API ref] on how to check version number)*, remove the `tmp` folder in your `modulexxx-local-web-app/target` and re-run `jetty:run`


### [API references][API ref]

[API ref]: ./docs/API.md