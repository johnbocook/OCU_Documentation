Whitespace and Formatting
----------------------------

### Indentation
* Use hard tabs set to three (3) spaces.
* Do not mix tabs and spaces.

### Spaces
* Use spaces after commas in arguments lists
* *Do not use spaces* before commas in argument lists

**Good**
```cfm
<cfscript>

   public void function sayHi(string name, numeric age) output="false" {
      //do stuff
   }

</cfscript>
```

**Bad**
```cfm
<cfscript>

   public void function sayHi(string name , numeric age) output="false" {
      //do stuff
   }

</cfscript>
```

* *Do not use spaces* before or after parenthesis when defining and calling
   functions
* *Do* put a space between a parenthesis and **if**, **while**
* *Do* put a space after a closing parenthesis and an open curly brace

**Good**
```cfm
<cfscript>

   local.sum = add(left=1, right=2);
   if (local.sum > 10) {
      // Do stuff
   }

</cfscript>
```

**Bad**
```cfm
<cfscript>

   local.sum = add ( left=1, right=2 );
   if(local.sum > 10){
      // Do stuff
}

</cfscript>
```

* *Do* use spaces between operators and operands in expresions

**Good**
```cfm
<cfscript>

local.sum = 1 + 4 + local.somethingElse;

</cfscript>
```

**Bad**
```cfm
<cfscript>

   local.sum = 1+4+local.somethingElse;

</cfscript>
```

* *Do not* use spaces around equal signs when calling functions using named
   arguments
* *Do not* use spaces around equal signs when defining default values for
   arguments in function declarations

**Good**
```cfm
<cfscript>

   public string function doStuff(string name="Adam") output="false" {
   
   }
   
   local.result = doStuff(name="Bob");

</cfscript>
```

**Bad**
```cfm
<cfscript>

   public string function doStuff(string name = "Adam") output="false" {
   
   }

   local.result = doStuff(name = "Bob");

</cfscript>
```

### Curly and Square Braces
* All open curly braces for function declarations, **try/catch** blocks, **while**,
   **if**, and structure variable declarations go on the same line as the
   statement/expression they are attached to
* All closing curly braces go on the next line
* Open curly braces for structures defined inside an array may start on their
   own line
* All open square braces go on the same line as the statement/expression they
   are attached to

**Good**
```cfm
<cfscript>

   if (isValid) {
      // Do stuff
   }

   try {
      // dangerous code
   } catch {
      // log me!
   }

   local.claim = {
      id=1,
      token="12345",
      associated=[1, 2, 3],
      nonAssociated=[
         4,
         5,
         6
      ]
   };          

   local.people = [
      {
         name: "Adam",
         age: 36
      }
   ];

</cfscript>
```

**Bad**
```cfm
<cfscript>

   if (isValid)
   {
      // Do stuff
   }
   
   try
   {
      // dangerous code
   }
   catch
   {
      // log me!
   }
   
   local.claim =
   {
      id=1,
      token="12345",
      associated=
      [
         1,
         2,
         3
      ],
      nonAssociated=
      [4,5,6]
   };
   
   local.people =
   [{
      name: "Adam",
      age: 36
   }];

</cfscript>
```

### CFML/Script Conventions
* ColdFusion tags should be **Lower case** with an equivalent closing tag, or be self-closing
* All tags must be indented one level from their parent in both ColdFusion and HTML tags

**Good**
```cfm
<p>
   <cfif viewData.customer.hasModule(name="SomeModule")>
      <cfset text = "Text 1" />
   <cfelse>
      <cfset text = "Text 2" />
   </cfif>

   <cfoutput>#text#</cfoutput>
</p>
```

**Bad**
```cfm
<p><CFIF viewData.customer.hasModule("SomeModule")>
<cfset text = "Text 1"><cfelse><cfset text = "Text 2">
<cfoutput>#text#</cfoutput></p>
```

### Quotes
ColdFusion **allows using** both double and single quotes for working with strings.

* Always use double quotes when possible 
* Use single quotes when creating strings that contain double quotes and
   would require excessive escaping.

Casing and Naming
--------------------

### 2.1 Casing Definitions
* **Lower case** - All charaters are lower cased. Example: ```mynamehere```
* **Upper case** - All charaters are upper cased. Example: ```MYNAMEHERE```
* **Pascal case** - First letter of each word upper cased, starting with an upper
   case letter. Example: ```MyNameHere```
* **Camel case** - First letter of each word upper cased, starting with a lower
   case letter. Example: ```myNameHere```

### Variable Names
* All variable names should be **camel case**

**Example**
```cfm
<cfscript>

   local.payPeriod = "Bi-weekly";
   local.allCustomerSettings = [];

</cfscript>
```

### Function Names
* Function names are **Camel case**. Example: ```deleteRecordByID()```

### Abbreviations & Acroyms
Avoid abbreviations and acroyms when possible unless well known such as SSN, URL, Fasfa, ID

### Component File Names
* Components (CFC files) names use **Pascal case**. Example: ```TokenMapper.cfc```

### CFM File Names
* Filenames with a CFM extension should be **Camel case**. Example: ```permissionManager.cfm```
* Directory names are **Lower Case**

### Scopes
* All scope names should **Lower case**

**Example**
```cfm
<cfscript>

   public string function boldAName(required string name) output="false" {
      return "<strong>#arguments.name#</strong>";
   }
   
   request.myBoldedName = boldAName(name="Adam");
   
   session.name = "Adam";
   session.boldedName = request.myBoldedName;

</cfscript>
```
