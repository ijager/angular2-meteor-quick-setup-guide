
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
```

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
