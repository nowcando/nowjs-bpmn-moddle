# nowjs-bpmn-moddle

 [![npm version](https://badge.fury.io/js/nowjs-bpmn-moddle.svg)](https://www.npmjs.com/package/nowjs-bpmn-moddle)
 [![Downloads](https://img.shields.io/npm/dm/nowjs-bpmn-moddle.svg)](https://www.npmjs.com/package/nowjs-bpmn-moddle)
 [![Gitter](https://badges.gitter.im/nowcando/nowjs-bpmn-moddle.svg)](https://gitter.im/nowcando/nowjs-bpmn-moddle?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge)
  CI-Master: [![Build Status](https://travis-ci.org/nowcando/nowjs-bpmn-moddle.svg?branch=master)](https://travis-ci.org/nowcando/nowjs-bpmn-moddle) , CI-Develop: [![Build Status](https://travis-ci.org/nowcando/nowjs-bpmn-moddle.svg?branch=develop)](https://travis-ci.org/nowcando/nowjs-bpmn-moddle)


This project defines the [NowJs](https://www.nowcando.com) namespace extensions for BPMN 2.0 as a [moddle](https://github.com/bpmn-io/moddle) descriptor.


## Usage

Use it together with [bpmn-moddle](https://github.com/bpmn-io/bpmn-moddle) to validate NowJs BPMN 2.0 extensions.

```javascript
var BpmnModdle = require('bpmn-moddle');

var nowjsModdle = require('nowjs-bpmn-moddle/resources/nowjs');

var moddle = new BpmnModdle({ nowjs: nowjsModdle });

var serviceTask = moddle.create('bpmn:ServiceTask', {
  'javaDelegate': 'my.company.SomeDelegate'
});
```


## Building the Project

To run the test suite that includes XSD schema validation you must have a Java JDK installed and properly exposed through the `JAVA_HOME` variable.

Execute the test via

```
npm test
```

Perform a complete build of the application via

```
npm run all
```

## [bpmn-js](https://github.com/bpmn-io/bpmn-js) Extension

We include an extension that makes [bpmn-js](https://github.com/bpmn-io/bpmn-js) copy and replace mechanisms aware of NowJs properties.

```js
var BpmnJS = require('bpmn-js/lib/Modeler'),
    nowjsExtensionModule = require('nowjs-bpmn-moddle/lib'),
    nowjsModdle = require('nowjs-bpmn-moddle/resources/nowjs');

var modeler = new BpmnJS({
    additionalModules: [
      nowjsExtensionModule
    ],
    moddleExtensions: {
      nowjs: nowjsModdle
    }
  });
```

This extension hooks into the copy mechanism provided by the BPMN editor and ensures NowJs properties are kept and or dropped on copy and element replace.

## License

Use under the terms of the [MIT license](http://opensource.org/licenses/MIT).

## Important:
 The most of codes obtained from [https://github.com/camunda/camunda-bpmn-moddle](https://github.com/camunda/camunda-bpmn-moddle)
