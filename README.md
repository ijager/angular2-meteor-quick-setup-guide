# angular2-meteor-quick-setup-guide

Guide to quickly setup a angular2-meteor project.

This guide is based on the [official angular2-meteor tutorial](https://www.angular-meteor.com/tutorials/socially/angular2/bootstrapping), on the [Angular2 Hereos tutorial](https://angular.io/docs/ts/latest/tutorial/)  and on information from various issues. 

First we create our meteor project.

````
meteor create [project]
cd [project]
````

## Packages

Inside the project we first have to remove blaze and add the angular2-meteor compilers and runtime.
````
meteor remove blaze-html-templates
meteor add angular2-compilers barbatus:angular2-runtime 
````

Next we add the @angular, the latest meteor-node-stubs and the angular2-meteor npm packages. 
````
meteor npm install --save @angular/compiler @angular/core @angular/common
meteor npm install --save meteor-node-stubs
meteor npm install --save angular2-meteor angular2-meteor-auto-bootstrap angular2-meteor-polyfills
````
After this do another meteor npm install to check if everything from package.json has been installed, but everything should be there already.
````
meteor npm install
````

## Files

Now we're ready to create a Angular2 style app. 

First get rid of these placeholder files:
````
- client/main.css (delete)
- client/main.html (delete)
- client/main.js (delete)
- server/main.js (delete)
````

In the project root we need to add `tsconfig.json` for the typescript compiler with the following inside.

````
{
  "compilerOptions": {
    "experimentalDecorators": true,
    "module": "commonjs",
    "target": "es5",
    "isolatedModules": false,
    "moduleResolution": "node",
    "emitDecoratorMetadata": true,
    "removeComments": false,
    "noImplicitAny": false,
    "sourceMap": true
  },
  "filesGlob": [
    "client/**/*.ts",
    "server/**/*.ts",
    "typings/**/*.d.ts",
    "collections/**/*.ts"
  ],
  "exclude": [
    "node_modules"
  ]
}
````

now add `client/main.ts`, `client/app.component.ts` and `client/index.html`.

*client/main.ts*
````
import { bootstrap } from 'angular2-meteor-auto-bootstrap';

import { AppComponent } from './app.component';

bootstrap(AppComponent);
````

*client/app.component.ts*
````
import { Component } from '@angular/core';

@Component({
  selector: 'app',
  template: 'Hello World'
})
export class AppComponent {}
````

*client/index.html*
````
<body>
<app>Loading...</app>
</body>
````

If we now run `meteor` the browser should show Hello World on [http://localhost:3000](http://localhost:3000)

## Typings

To enable Typescript typechecking we have to install typings for our dependencies.
If you haven't already, install typings globally and make sure its version is >= 1.04.
````
sudo npm install typings -g
typings --version
````
Then in the project root install typings for es6 and meteor
````
typings init
typings install es6-promise --save
typings install dt~es6-shim --global --save
typings install registry:env/meteor --global
````
