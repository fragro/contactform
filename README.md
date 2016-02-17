# Contact Form Package for Meteor
This is an easy to use, drop-in package for Meteor that allows you to have a very basic contact form ready-to-go.

## Usage
Add the package with:  
```
meteor add fragro:contactform
```

Configure your settings in a file in the ```server/``` folder and your ```MAIL_URL``` environment variable:
```
	// Email to send to
	contactFormConfig.settings.emailTo = 'test@gmail.com';

	// Name (optional)
	contactFormConfig.settings.fullName = 'Rishi Goomar';

	/* Custom Subject
	*  params contains the following:
	*  name - Name of the person wanting to send a message
	*  email - Email of the person
	*  message - Message they want to send
	*/
	contactFormConfig.settings.customSubject = function(params) {
	  return 'Message from ' + params.name + 'via contact form';
	}
```
Look at [the email package](http://docs.meteor.com/#email) for more information.

Make an empty template that your router will point to and include this:
```
{{> contactForm }}
```
If you want custom error and success templates define them like so:

```
	<template name="customContactSuccessTemplate">
	success
	</template>

	<template name="customContactErrorTemplate">
	error
	</template>
```

and set the template names in the ```client/``` folder during Meteor.startup.

```
	Session.set('successTemplate', 'customContactSuccessTemplate');
	Session.set('errorTemplate', 'customContactErrorTemplate');
```

### Note:
If you have any suggestions, please make an issue for discussion.
