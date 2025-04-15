## Skills survey - UI Developer

#### Instructions:
Providing your answers back to us in this markdown document would be preferable, but not necessary.
However, if composing a different document format, please do not re-order or re-phrase the questions.

#### Questions:

- Easy: (you shouldn't need Google for these)
  - js:
    - What's the difference between a variable that is: `null`, `undefined` or undeclared? How would you go about checking for any of these states?
        
        - Answer: null means, variable defined value with null
        - Answer: undefined means, variable defined but the value has not been initialized.
        - Answer: typeof myVar === 'undefined'
        - Answer: myVar === null
        - Answer: if (this['test'] == undefined) {
                  	console.log('Undeclared');
                  }
                  if (!this.hasOwnProperty('test')) {
                  	console.log('Undeclared');
                  }
            
    
    - What is a closure, and how and why would you use one?
    Answer: Closure is to create a scope or context, encapslate the state.
    Answer: To avoid scoping problem in JavaScript. You maight see this in callbacks or Asyncronus code. 
    
    
    - What is `this`? How is `this` used? Discuss at least 2 ways that you can change `this` (in either ES5 or ES6)?
    Answer: `this` relate to scope or context in JavaScrit
    Answer: `this` is to control accessing context
    Answer: In ES5, can use call, apply or bind
    Answer: In ES6, can use let or arrow function
    
    
    
  - css:
    - What is the order of greatest to least specificity?
      - classes
      - ids
      - inline style attributes
      - elements
      
      Answer: From greatest to least specificity, 
      inline style attributes, ids, classes, elements   
      
      
    - What's the difference between:
      ```css
      .shopping-list.list-item {
          // ...
      }
        Answer: element must have both classes

      .shopping-list .list-item {
          // ...
      }
        Answer: it can be any list-item that is a descendent of shopping-list

      .shopping-list > .list-item {
          // ...
      }
        Answer: list-item element must be a direct child of shopping-list element
      ```
      
    - What's the difference between `display: none` and `visibility: hidden`, and when would choose one over the other?
    Answer: none means does not exist in DOM, hidden means in DOM but can not see it.
    Answer: To avoid areas of the UI jupping aroud when you adjust these properties.
    
    
    - What are other ways to visually hide content?
    Answer: move it off screen
    Answer: Set hight or width as zero
    Answer: change the color (dangerous for clickable items)
    Answer: change transparent
    Answer: use JavaScript to remove a node (harsh technique)
    
	
- Medium: (feel free to use what online resources you need, ...awesome if you can do this w/o though)
  - js:
    - Just for kicks, let's implement our own util library, create a 'util' module with the following util functions:
      - `unique()`

        ```javascript
        uniqueList = util.unique(['a', 'b', 'c', 'b', 'd', 'a', 'd', 'e']);
        // ['a', 'b', 'c', 'd', 'e']
        ```

var util = (function() {
	return {
		unique: function (arr) {
			const result = [];
			for (let i = 0; i < arr.length; i++) {
				let item = arr[i];
				if (result.indexOf(item) < 0) {
					result.push(item);
				}
			}
			return result;
		}
	}
})();

let result = util.unique(['a', 'b', 'c', 'b', 'd', 'a', 'd', 'e']);
console.log(result);



      - `extend()`

        ```javascript
        homer = util.extend({name: 'Homer'}, {occupation: 'Nuclear Safety Inspector'});
        // {name: 'Homer', occupation: 'Nuclear Safety Inspector'}
        homer = util.extend(homer, {kids: [{name: 'Bart'}, {name: 'Lisa'}, {name: 'Maggie'}]});
        //  { name: 'Homer',
        //    occupation: 'Nuclear Safety Inspector',
        //    kids: [
        //      { name: 'Bart' },
        //      { name: 'Lisa' },
        //      { name: 'Maggie' }]
        //  }
        ```
        
        
       var util = (function() {
       	return {
       		extend: function (obj1, obj2) {
       			//return Object.assign(obj1, obj2);
       			return {...obj1, ...obj2}
       		}
       	}
       })();
       
       var homer = util.extend({name: 'Homer'}, {occupation: 'Nuclear Safety Inspector'});
       console.log(JSON.stringify(homer));
       
       homer = util.extend(homer, {kids: [{name: 'Bart'}, {name: 'Lisa'}, {name: 'Maggie'}]});
       console.log(JSON.stringify(homer));
 
        
        

        - Using the testing framework of your choice write the spec to test your implementation of the above functions

  - css:
    - Have a look at the following jsfiddle: http://jsfiddle.net/mipark2csco/o9v5rdpa/2/
      - fork this guy (hit 'Fork')
      - make the following changes, and save a new jsfiddle for each task (hit 'Update'), and paste your saved links back here:
        - horizontally center the box
        http://jsfiddle.net/a4pa63Ld/2/
        
        - right-align the box
        http://jsfiddle.net/a4pa63Ld/3/
        
        - align the box in the bottom-right corner
        http://jsfiddle.net/a4pa63Ld/4/
        
        - horizontally and vertically center the box
        
    - Have a look at the following jsfiddle: https://jsfiddle.net/mipark2csco/v4k5rjag/
      - fork this guy (hit 'Fork')
      - make the following changes, and save a new jsfiddle for each task (hit 'Update'), and paste your saved links back here:
        - vertically center the three boxes
        https://jsfiddle.net/5kzu3bje/1/
        
        - horizontally center the three boxes
        https://jsfiddle.net/5kzu3bje/2/
        
        - space the three boxes evenly horizontally, and center them vertically
        https://jsfiddle.net/5kzu3bje/3/


