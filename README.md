# Render-If-Component
This is a JS library for rendering the DOM elements on client side
# Documentation
### Setup ###
`$("[render-if]").RenderIf();`
### Options ###
  //Clear the data from the elements on hide
  
	$("[render-if]").RenderIf({clearOnHide: false}); 
## Using Renderif with different components ##
* Input Text/ Textarea : To use render-if with simple input types just provide the selector inside val function and provide the expression in the render-if attribute.
  * Example - 
  
  `<input id="testInput" class="demoNumberInput" type="text" value="">
  <input id="inputCheckbox" type="checkbox" render-if='val("#testInput") == "test value"' onchange="testChangeFunction();">`
  
  The above checkbox will only render if the value in the input text is 'test value'
* Checkbox : To use render-if with checkbox just provide the selector inside val function and provide true/false value for comparison.
  * Example -  render-if='val("#inputCheckbox") == false'
* Radio Button : To use render-if with radio button just provide the selector (which should be class in case of radio button) inside val function and provide the value you want to compare in the render-if expression. The render-if attribute will only work for those radio buttons which belongs to same class group. Provide same class name to all those radio buttons which should be grouped together.
  * Example - render-if='val(".radioClass") == “employee” ’
* Select list(Picklist-single select) : To use render-if with single select list just provide the selector inside val function and provide the value you want to compare in the render-if expression. 
  * Example - render-if='val("#sourceOptions") == "other"'
* Select list(Picklist-multiple select) : To use render-if with multi select list just provide the selector and value you want to compare inside inVal function if there is a single value you want to compare and if you want to compare multiple values then provide the selector inside val function and provide semicolon separated values you want to compare with in render-if expression.
  * Example - 
    * a) render-if='inVal("#multiSelectInput","other") == true' // For single  value comparison
    * b) render-if='val("#multiSelectInput") == "singing;other"' // For multiple value comparison
## Render If with Visualforce Elements (Salesforce) ##
  * Upload the renderif JS library in static resource and provide the path for the js file.
    * Example - `<script src="{!URLFOR($Resource.RenderIfFile,'RenderIfFile/js/RenderIf.js')}"></script>`
  * Only class selector has to be used while using render-if attribute with apex elements. 
  * Render-if attribute can only be used with those apex elements which supports HTML Pass-through attributes.
  * Code snippet for using render-if with an apex input text - 
   
    `<apex:inputText id="inputDetails" styleClass="inputStyle" value="{!strInputDetails}" html-render-if="val('.selectCategory') ==            'Other'"/>`
## Support for Operators ##
  * Logical Operators : Render-If supports logical AND and logical OR to be used in the render-if expression. With the help of this multiple conditions can be provided in a single render-if expression.
    * Example - 
      
      `<output form="rendererForm" name="DemoOutput" for="demoInputText8">Enter the value : </output>    
      <input id="demoInputText8" style="background-color:#eaeae1;" class="demoInput1" type="text" value="Test value 1" >    
      <output form="rendererForm" name="DemoOutput" for="demoInputText9">Enter the value : </output>      
      <input id="demoInputText9" style="background-color:#eaeae1;" class="demoInput1" type="text" value="Test value 2" >    
      <output id="demoLogical" form="rendererForm" name="DemoOutput" render-if='val("#demoInputText8") == "test value 1" and  	  	       val("#demoInputText9") == "test value 2"'>Rendered if both rendering conditions satisfies</output>  `

  The above output text will render only if both conditions are satisfied
  
  Just like the Logical AND; Logical OR can also be used in the render-if expression
  * Mathematical Operators : Render-if supports mathematical operators to be used in the render-if expression. Operators supported are :     
    `/, *, %, ==, !=, >=, <=, >, <, +, -.` 
    * Example - 
      
	`<output form="rendererForm" name="DemoOutput" for="testNumberInput">Enter State : </output>
       <input id="testNumberInput" class="demoNumberInput" type="text" value="10">
       <input id="inputCheckbox" class="demoInputCheckbox" type="checkbox" render-if='val("#testNumberInput") %2 == 0'>`
      
       The above checkbox will only render if the value entered in the input text is a divisible by 2.

## Important Points ##
  * Pass clearOnHide parameter as true to RenderIf function in order to clear the input values after hiding. The input text/text area will     be set to empty string , checkbox value will be set to false, picklist value will be set to empty string on hiding. 
  * Single and double quotes in the render-if expression are interchangeable.
## Known Issues ##
  * Lower case string has to be used every time while comparing string values
  * For radio buttons the expression should contain the class selector else the component won’t work
  * There is no effect on radio button after setting the clearOnHide parameter as true.
