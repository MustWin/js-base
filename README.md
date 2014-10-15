# Dev Practices

## Follow these guidelines
https://github.com/claudio-silva/grunt-angular-builder/wiki/Writing-build-enabled-code

## Code organization

 * Angular Modules live in app/scripts/angular, these are built by angular-builder automagically
 * Non-Angular Modules live in app/scripts/vendor, these are built in index.html

# Setup
## Install Dependencies

`npm install -g yo`
`npm install`
`bower install`

## Turn it on
`grunt serve`

## Release to the Rails repo
`grunt build`

# Make sure we don’t cache the index.html file wherever we serve it from

ApplicationController
```
  def no_cache
    response.headers[“Cache-Control”] = “no-cache, no-store, max-age=0, must-revalidate”
    response.headers[“Pragma”] = “no-cache”
    response.headers[“Expires”] = “Fri, 01 Jan 1990 00:00:00 GMT”
  end
```
IndexController
```
  def index
    no_cache
    render :file => File.join(Rails.root, 'public', 'index.html'), :layout => false
  end
```
Router
```
root 'index#index'
```

