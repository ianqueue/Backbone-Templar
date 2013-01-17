# Backbone-Templar

Backbone plugin to add a client side template manager.

NOTE: This plugin is highly coupled with Handlebars at the moment, meaning I haven't done the work to create an interface around template compilation yet. I hope to make this more modular with other templating solutions soon.

It also depends on Underscore, Backbone, jQuery and the Backbone-localStorage plugin written by [@jeromegn](https://github.com/jeromegn) which can be found here... https://github.com/jeromegn/Backbone.localStorage

## API

### new Backbone.Templar(templatePaths, options)
  
  Initialize templar...

    var templar = new Templar([
      'mytemplatename1',
      'mytemplatename2',
      ...
    ]);

  Initialize templar with options (defaults shown)...

    var templar = new Templar(templates, {
      url     : 'public/templates/',                 // template base path
      ext     : '.hbs',                              // template file extension
      version : '0.0.1',                             // version number to invalidate old cached templates
      cache   : true,                                // turn localStorage caching on/off
      storage : new Backbone.LocalStorage('Templar') // default local storage plugin
    });


### Backbone.Templar.render(path, el, data [, append])
  
  Render template...

    var templar = new Templar([
      'mytemplatename1',
      'mytemplatename2',
      ...
    ]);

    templar.render({
      path   : 'mytemplatename1',
      el     : $('.myElementToRenderTemplateIn'),
      data   : {
        'name' : 'example'
      }
    });

  or append the compiled template

    templar.render({
      path   : 'mytemplatename1',
      el     : $('.myElementToRenderTemplateIn'),
      data   : {
        'name' : 'example'
      },
      append : true // defaults to false and assumes replacing innerHtml
    });

 