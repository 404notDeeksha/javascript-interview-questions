# Object Prototype

Every JavaScript object has a prototype, which is another object that it inherits properties and methods from. The prototype acts as a template object that other objects can inherit from. This is the foundation of JavaScript's inheritance model.

e.g.: objects created with a constructor function inherit from that constructor's prototype property. Built-in types like Array and Date have their own prototypes (Array.prototype, Date.prototype), which in turn inherit from Object.prototype