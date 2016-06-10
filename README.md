# angular2-meteor-quick-setup-guide

Guide to quickly setup a angular2-meteor project.

This guide is based on the [official angular2-meteor tutorial](https://www.angular-meteor.com/tutorials/socially/angular2/bootstrapping) and on information from various issues. 

First we create our meteor project

````
meteor create [project]
cd [project]
````

Inside the project root we add `tsconfig.json` for the typescript compiler

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



