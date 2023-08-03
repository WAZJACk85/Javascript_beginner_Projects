# Introduction


This is a relatively simple JS web app that I have created. 


*  It allows you to type and add events or tasks you plan to do in an input bar and then adds them to a list below.

*  You have an add button to add the task;

*  You have a delete button to delete existing tasks;

*  You have an edit button to edit task text;

*  Once you have refreshed the HTML page, it resets the list back to blank;

*  There is one Default task that always stays there as an example;

*  There is a save button that appears once you edit a task to save the changes made.

# Technical Description



# * HTML





# * CSS










# * Javascript


*  window.addEventListener   	// loads after main page (DOM) is loaded. via  'load', () =>
*  Constants 	// are created via querySelectors which are passed through  elements beginning with #.

`


	window.addEventListener('load', () => {
		const form = document.querySelector("#new-task-form");
		const input = document.querySelector("#new-task-input");
		const list_el = document.querySelector("#tasks");




 * An event listener is added to the 'form' variable   ( submit and (e) , are instanciated in the argument or function header ) ;
 * The function args (or header)  starts with {  and therefore the event listener 'form' is the main argument that is passed to the DOM or webpage, other variables
   are passed in sub functions via the head of the JS.
 * Then 'preventDefault' is invoked through e (new variable expressed as a character) .

`
	form.addEventListener('submit', (e) => {
		e.preventDefault();
`
  



*Here in this next section of JS, there are constant variables created and given 'mini functions'  such as  input.value  .  This is then added again via other created variables by being passed through and connected, example:  task_el.classList.add('task');  



		const task = input.value;

		const task_el = document.createElement('div');
		task_el.classList.add('task');

		const task_content_el = document.createElement('div');
		task_content_el.classList.add('content');

		task_el.appendChild(task_content_el);

 
  * const task_input_el = document.createElement('input');

		const task_input_el = document.createElement('input');
		task_input_el.classList.add('text');
		task_input_el.type = 'text';
		task_input_el.value = task;
		task_input_el.setAttribute('readonly', 'readonly');

		task_content_el.appendChild(task_input_el);

		const task_actions_el = document.createElement('div');
		task_actions_el.classList.add('actions');
		
		const task_edit_el = document.createElement('button');
		task_edit_el.classList.add('edit');
		task_edit_el.innerText = 'Edit';

		const task_delete_el = document.createElement('button');
		task_delete_el.classList.add('delete');
		task_delete_el.innerText = 'Delete';

		task_actions_el.appendChild(task_edit_el);
		task_actions_el.appendChild(task_delete_el);

		task_el.appendChild(task_actions_el);

		list_el.appendChild(task_el);

		input.value = '';

		task_edit_el.addEventListener('click', (e) => {
			if (task_edit_el.innerText.toLowerCase() == "edit") {
				task_edit_el.innerText = "Save";
				task_input_el.removeAttribute("readonly");
				task_input_el.focus();
			} else {
				task_edit_el.innerText = "Edit";
				task_input_el.setAttribute("readonly", "readonly");
			}
		});

		task_delete_el.addEventListener('click', (e) => {
			list_el.removeChild(task_el);
		});
	});
});



