# Render-If-Component
This is a JS library for rendering the DOM elements on client side
# Documentation
### Setup ###
$("[visibly]").RenderIf();
### Options ###
  `clearOnHide: false  //Clear the data from the elements on hide`
## Using Renderif with different components ##
* Input Text/ Textarea : To use render-if with simple input types just provide the selector inside val function and provide the expression in the visibly attribute.
  * Example - visibly='val("#testNumberInput") == “test value” '
* Checkbox : To use render-if with checkbox just provide the selector inside val function and provide true/false value for comparison.
  * Example -  visibly='val("#inputCheckbox") == false'
* Radio Button : To use render-if with radio button just provide the selector (which should be class in case of radio button) inside val function and provide the value you want to compare in the visibly expression. The visibly attribute will only work for those radio buttons which belongs to same class group. Provide same class name to all those radio buttons which should be grouped together.
  * Example - visibly='val(".radioClass") == “employee” ’
* Select list(Picklist-single select) : To use render-if with single select list just provide the selector inside val function and provide the value you want to compare in the visibly expression. 
  * Example - visibly='val("#sourceOptions") == "other"'
* Select list(Picklist-multiple select) : To use render-if with multi select list just provide the selector and value you want to compare inside inVal function if there is a single value you want to compare and if you want to compare multiple values then provide the selector inside val function and provide semicolon separated values you want to compare with in visibly expression.
  * Example - 
    * a) visibly='inVal("#multiSelectInput","other") == true' // For single  value comparison
    * b) visibly='val("#multiSelectInput") == "singing;other"' // For multiple value comparison
## Render If with Apex Elements ##
  * Only class selector has to be used while using visibly attribute with apex elements. 
  * Visibly attribute can only be used with only those apex elements which supports HTML Pass-through attributes.
  * Code snippet for using visibly with an apex input text - 
   `<apex:inputText id="inputDetails" styleClass="inputStyle" value="{!strInputDetails}" html-visibly="val('.selectCategory') ==            'Other'"/>`

## Important Points ##
  * Pass clearOnHide parameter as true to RenderIf function in order to clear the input values after hiding. The input text/text area will     be set to empty string , checkbox value will be set to false, picklist value will be set to empty string on hiding. 
  * Single and double quotes in the visibly expression are interchangeable.
## Known Issues ##
  * Lower case string has to be used every time while comparing string values
  * For radio buttons the expression should contain the class selector else the component won’t work
  * There is no effect on radio button after setting the clearOnHide parameter as true.
