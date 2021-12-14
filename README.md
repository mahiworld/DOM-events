# DOM-events

var button = document.getElementById("enter");
var input = document.getElementById("userinput");
var ul = document.querySelector("ul");

function inputlength(){
	return input.value.length;
}

function addListAfterClick(){
	if(inputlength()>0){
		createListElement();
	}
}

function addListAfterKeypress(event){
	if(inputlength()>0 && event.which ===13){
		createListElement();
    }
}



function createListElement(){
	var li = document.createElement("li");
	li.appendChild(document.createTextNode(input.value));
	addDelButton(li);
	ul.appendChild(li);
	input.value="";
}
function addDelButton(parent) {
var buttonElem = parent.appendChild(document.createElement("button"));
buttonElem.classList.add("delete");
buttonElem.innerHTML = "Delete";
}


function toggleClassDoneOnAndOff(event) {
    if (event.target.tagName === "LI") {
        event.target.classList.toggle("done");
    }
}

function delItem(event) {
    if (event.target.className === "delete") {
        event.target.parentElement.remove();
    }
}

function ulClick(event){
	toggleClassDoneOnAndOff(event);
	delItem(event);
}

ul.addEventListener("click",ulClick);
//ul.addEventListener("click", delItem);
//ul.addEventListener("click", toggleClassDoneOnAndOff);

button.addEventListener("click", addListAfterClick);

input.addEventListener("keypress", addListAfterKeypress);
