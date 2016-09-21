# Minimal Meteor + Angular 2.0.0 Project

This guide shows how to create a minimal Meteor project with Angular 2.0.0 dependencies. This project does not make use of angular2-meteor glue. 

## Create Project

First we create our meteor project.

````
meteor create [project]
cd [project]
````

## Packages

Inside the project we first have to remove blaze and add the `angular2-compilers` package (typescript compiler).
````
meteor remove blaze-html-templates
meteor add angular2-compilers
````

Add the following `package.json` to the root of your project and run `meteor npm install`. This should install all necessary NPM packages.

package.json:
````
{
  "name": "meteor-angular-minimal",
  "private": true,
  "scripts": {
    "start": "meteor run"
  },
  "dependencies": {
    "@angular/common": "^2.0.0",
    "@angular/compiler": "^2.0.0",
    "@angular/core": "^2.0.0",
    "@angular/platform-browser": "^2.0.0",
    "@angular/platform-browser-dynamic": "^2.0.0",
    "core-js": "^2.4.1",
    "meteor-node-stubs": "^0.2.3",
    "reflect-metadata": "^0.1.8",
    "rxjs": "^5.0.0-beta.12",
    "zone.js": "^0.6.25"
  }
}
````

# Source Files

Next we add the following source files to the client folder. Don't forget to first remove all existing `*.js` files. 

client/index.html:
````
<body>
  <app>Loading...</app>
</body>
````

client/app.component.ts:
````
import "reflect-metadata";
import { Component } from '@angular/core';

@Component({
  selector: 'app',
  template: 'Hello World'
})
export class AppComponent {}
````

client/app.module.ts:
````
import { NgModule } from '@angular/core';
import { BrowserModule } from '@angular/platform-browser';

import { AppComponent } from './app.component';

@NgModule({
  declarations: [
    AppComponent,
  ],
  imports: [
    BrowserModule,
  ],
  bootstrap: [AppComponent],
})
export class AppModule { }
````

client/main.browser.ts:
````
import "reflect-metadata";
import "zone.js/dist/zone";

import { platformBrowserDynamic } from '@angular/platform-browser-dynamic';
import { AppModule } from './app.module';

const platform = platformBrowserDynamic();

platform.bootstrapModule(AppModule);
````

Finally, add `tsconfig.json` for the typescript compiler and run `meteor`

tsconfig.json:
````
{
  "compilerOptions": {
    "target": "es5",
    "module": "commonjs",
    "moduleResolution": "node",
    "sourceMap": true,
    "emitDecoratorMetadata": true,
    "experimentalDecorators": true,
    "removeComments": false,
    "noImplicitAny": false
  }
}
````
