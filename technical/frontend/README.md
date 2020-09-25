# Openstad Frontend
The openstad frontend is primarly built upon the ApostropheCMS, there are also a few react application that are run as modules inside ApostropheCMS.

The main repo is found here: https://github.com/Amsterdam/openstad-frontend

## In page editing
On of the main reasons ApostropheCMS was chosen because it easily allows for in page editing allowing for highly dynamic page.


## Multisite
We have a custom implementation of ApostropheCMS multisite, this allows one installation to run multiple domains. As explainend in the architecture section this works together with the API and Kubernetes to make it all work. With every domain request the frontend server checks if the domain exists in cached config, if not present make a call to the Openstand API if such a domain exists, if yes it will create an express server if not it will return a 404

## ApostropheCMS documentation
In ApostropheCMS almost everything is written as a module, found in a lib/modules folder, can be a widget hat can be displayed on a page, a custom page or any other of the possible extension of other ApostropheCMS functionality.

The documentation of ApostropheCMS is comprehensive and good place to start if you want to create your own modules: http://apostrophecms.org/.


## The Openstad version of ApostropheCMS
We have bundled the ApostropheCMS as an Openstad CMS local npm pacakage. This package lives in the packages/cms folder and the modules are overrideable just like ApostropheCMS modules. Create the files you want to override directly under lib/modules.

This is a core feature of the ApostropheCMS and because of the way we bundled it works for both the ApostropheCMS modules and the Openstad modules. [ApostropheCms module pattern](https://docs.apostrophecms.org/core-concepts/technical-overview.html#apostrophe-s-module-pattern-inheritance-and-moog)

For now  treat it as a local NPM package, in the future this will be moved to an external NPM package (@openstad/cms).

There are multiple ways to add or modify modules. It depends on what you want to achieve and how you run the project.  

**1. Add new module to the root project in lib/modules:**
- Create new module in `lib/modules`
- Create index.js file in you modules folder (e.g. `lib/modules/custom-module/index.js`), example:
```js
module.exports = {  
  label: 'custom module',
  construct: function(self, options) {
    
  }
};
```
- Add the new module to your project in the index.js:
```js
var apos = openstadCms.site({
  bundles: ['@openstad/cms'],
  // See lib/modules for basic project-level configuration of our modules
  // responsible for serving static assets, managing page templates and
  // configuring user accounts.

  modules: { 
    'custom-module': {}
   }
});
```

**2. Override existing Openstad or Apostrophe module**
To override or extend an existing module you can add the files under lib/modules. 
**example:
If you want to modify the html of the agenda-widgets you only need to create the `lib/modules/agenda-widgets/views/widget.html` file and you're free to change the html structure.
```html
<style>
  {{data.widget.formattedContainerStyles}}
</style>

<div id="{{data.widget.containerId}}" class="agenda">
{% for item in data.widget.items %}
  <div class=" {{'agenda-period' if (item.period === true) or (item.period === 'period') else 'agenda-day' }}">
    <div>
      <h3> {{item.title | sanitize | safe}} </h3>
      {% if item.actionText %}
      {{item.actionText}}
      {% endif %}
    </div>
  </div>
{% endfor %}
</div>
``` 

Override/extend for example the section-widgets: `lib/modules/section-widgets/index.js`
```js
module.exports = {
  construct(self, options) {
    const superGetContentWidgets = self.getContentWidgets;

    self.getContentWidgets = (req) => {
      const contentWidgets = superGetContentWidgets(req);

      contentWidgets['custom-content-widget'] = {
        readOnly: false,
        edit: true,
      };

      return contentWidgets;
    }
  }
};

```

Override/extend a javascript module file `lib/modules/resource-form-widgets/public/js/map.js`
```js
apos.define('resource-form-widgets', {
    
    construct: function(self, options) {
       console.log('do something special');
    }
});
```

**3. Create a standalone module and install this as a npm dependency**

It's also possible to make your own standalone packages for the Openstad project. You need to create a package and publish it to npm and add the dependency in your package.json.

For more information please refer to the Apostrophe documentation: https://docs.apostrophecms.org/core-concepts/modules/more-modules.html#packaging-apostrophe-modules-together-creating-bundles


**4. Create a Pull request in the openstad/cms package if you want to change something directly in the core module:**
Everyone is invited to contribute to the `@openstad/cms` core package. [contribute](/technical/contributing.md)
