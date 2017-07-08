# PageTagger Library

### Install
Download the js/PageTaggerLib folder and add it to your project.

### Dependencies
jQuery 1.9.1: http://jquery.com/

SelectorGadget: https://github.com/cantino/selectorgadget

### Demo
1. Clone/download source code from this project.
2. Navigate to chrome://extensions/ in your Chrome browser.
3. Click Load unpacked extension... and load the CSSSelector folder.
4. There is now a new chrome extension icon in the top right of your browser.
5. Navigate to any page you want to scrape and test it out.
Ex: https://www.linkedin.com/groups/1976445/profile


## Basic Usage
```javascript
var pageTagger = new PageTagger();
pageTagger.init();

// select names
pageTagger.select('name');
// .... user tags elements on page
pageTagger.acceptSelection();

// select something else
pageTagger.select('someTag');
pageTagger.acceptSelection();

var result = pageTagger.result();
console.log(result);
```

Result will contain data scraped from the page
```javascript
{
	selectors:
	{
		name: 'span.entity-name-text',
		someTag: 'span.entity-mgmt-role'
	},
	data:[
		{
			name: 'Maggie W',
			someTag: 'Group Owner'
		},
		{...},
		...
	]
}
```
Check js/main.js to see a similar implementation of PageTagger.

### Reference
#### init()
Initialize PageTagger Object
#### select([tagName])
	tagName - optional name for this selection group. If no tagName is provided - a default name will be used in the results object.
Initiates the selection process. User can click on any element on the page. The library will find and highligh all matching elements. User can click on a highlighted element to remove it from the selector, or click on an unhighlighted element to add it to the selector.
#### acceptSelection([tagName])
Accepts all highlihted elements. Ends selection process for this tagName
#### result()
Returns object with results
NOTE: you may need to run ```localStorage.clear();``` after each use to clear all data that PageTagger stores locally in the browser.

### Custom Styles
Edit CustomSelectionStyle.css to change how selected elements are highlighted on screen.
