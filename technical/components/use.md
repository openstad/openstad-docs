# Openstad Components - use and configuration

To use a component it needs to be loaded in your page.

A basic setup could look like this:

```
<!-- load react -->
<script src="https://unpkg.com/react@16/umd/react.development.js"></script>
<script src="https://unpkg.com/react-dom@16/umd/react-dom.development.js"></script>

<!-- load openstad component -->
<link rel="stylesheet" type="text/css" href="/components/dist/css/choices-guide.css"/>
<script src="/components/dist/choices-guide.js"></script>
<script>

 window.addEventListener('load', function(e) {

   // configure
   var config = {
     divId: "choices-guide",
     siteId: 1,
     choicesGuideId: 1,
     api: {
       "url": "https://api.openstad.nlsvgtr.nl",
     },
   };

   // load in page
   var element = document.querySelector('.openstad-component-choices-guide');
   OpenStadComponents['choices-guide'].ChoicesGuide.renderElement(element, config);

 });

</script>

<!-- container div -->
<div class="openstad-component-choices-guide"></div>

```

## Configuration

All elements need information about the openstad-ecosystem API server they should use.

```
{
  api: {
    url: "API_URL",
  }
}

```

User login is assumed to be handled by the containg website; information about the user should be passed in the config.

```
{
  user: {
    fullName: "Niels Vegter",
    role: "admin"
  },
  api: {
    url: "API_URL",
    isUserLoggedIn: true,
    headers: {
      "X-Authorization": "Bearer JWT"
    }
  }
}

```

All elements need basic information about their context.
```
{
  divId: "choices-guide",
  siteId: 1,
}
```

More specific information per component can be found in the per-component documentation and in the examples.


## Examples

The _examples_ directory should be helpful.

