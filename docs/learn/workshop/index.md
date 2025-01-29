<h1 id="title">workshop...</h1>
<span id="secondary-title"></span>
<div id="workshop-container"></div>


<script>
	
// ---------------------------- //
//                            	//
//	  Function to get URL    	//
//                            	//
// ---------------------------- //
function init(){
	console.log("in workshop index...")
	console.log(data)
	// Get URL parameters
	var params = getUrlParams();
	
	// Check if "val" parameter exists and set it as a variable
	var id = params["id"];
	
	// add id to the input
	if (id == undefined) {
		id = "No value found";

	}
	else
	{		
		createWorkshop(id);	
	}
}
	
function createWorkshop(id) {
	// find the workshop in the workshops array
	let workshop = data.learn[id];
	// add the title
	// get the h1 element title
	let title = document.getElementById('title');
	title.innerHTML = workshop[0];
	title.tabIndex = 0;

	// add secondary title
	let secondaryTitle = document.getElementById('secondary-title');
	secondaryTitle.innerHTML = workshop[1];
	secondaryTitle.tabIndex = 0;

	// create a div for the workshop
	let workshopDiv = document.createElement('div');
	workshopDiv.className = 'workshop';

	// add the youtube video
	let video = document.createElement('div');
	video.innerHTML = workshop[7];
	// add alt and title tags
	video.alt = workshop[1];
	video.title = workshop[1];
	video.tabIndex = 0;
	
	workshopDiv.appendChild(video);

	// add the link to the youtube video
	if (workshop[5] != "") {
		let link = document.createElement('a');
		link.href = workshop[5];
		link.innerHTML = "Watch on YouTube";
		link.tabIndex = 0;
		workshopDiv.appendChild(link);
	}	

	// add the description
	let description = document.createElement('p');
	description.innerHTML = workshop[3];
	description.tabIndex = 0;
	workshopDiv.appendChild(description);

	// add the tags
	let tags = workshop[6].split(',');
	let tagContainer = document.createElement('div');
	tagContainer.className = 'tag-container';
	tags.forEach(function(tag) {
		let tagDiv = document.createElement('div');
		tagDiv.className = 'tag';
		tagDiv.innerHTML = tag.trim();
		tagDiv.tabIndex = 0;
		tagContainer.appendChild(tagDiv);
	});
	workshopDiv.appendChild(tagContainer);

	// add the workshop to the page
	document.getElementById('workshop-container').appendChild(workshopDiv);



	
}
</script>