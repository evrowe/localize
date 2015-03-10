#Localize.js

Localize.js is a lightweight client-side library meant to enable easy localization in client-side web applications. Localization dictionaries can be sourced from an API or a local file. Supports All modern browsers and IE8+

##Usage

Minimal setup and initialization follows the following pattern:

    // Create a new instance of the Localize class
    var Localization = new Localize();

    // Run initial setup to do basic configuration
    Localization.setupLocalize({
      basePath: '/path/to/endpoint',
      currentLocale: 'en-US',
      defaultContext: 'UI-COMMON'
    });

    // Grab some content
    Localization.getLocalizedData({
      context: 'UI-COMMON',
      pathSuffix: 'common.json'
    });

At this point, the Localize class will be set up and ready for you to fetch localized text. This is usable in your Javascript code and your HTML. Also included is a handlebars helper for Ember applications.


###Text replacement in javascript
Getting localized text in your javascript is performed by calling the `fetch()` method on the class and supplying it with a key.

    Localization.fetch('someKey');

### Text replacement in HTML
To localize text in your HTML, you can use any arbitrary element (`<span>` tags are recommended) with a class name of `localize-me`. This element will also need a `data-key` attribute containing the translation key.

    <span class="localize-me" data-key="someKey"></span>

To replace these tags in your HTML, call the `replaceAll()` method. You can override the default class name by setting `replacementClassName: 'foo'` in the options hash.

    // Default, basic usage
    Localization.replaceAll();

    // Substitute an alternate class name and dictionary context
    Localization.replaceAll({
      replacementClassName: 'change-this',
      replacementModule: 'UI-BASIC'
    });

### Text replacement in Handlebars/Ember
Text localization is as simple as invoking the `localize` helper in your handlebars templates. Localize.js does the rest.

    {{localize "someKey"}}