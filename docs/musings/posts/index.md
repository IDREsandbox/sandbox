<h1 id="title"></h1>
<span id="secondary-title"></span>
<div id="project-container"></div>

<script>
// --------------------------------	//
//                            		//
//	  Function to get project    	//
//                            		//
// -------------------------------- //
function init(){
	// Get URL parameters
	var params = getUrlParams();
	
	// Check if "id" parameter exists and set it as a variable
	var projectid = params["id"];
	
	// add projectid to the input
	if (projectid == undefined) {
		// go 
		projectid = 0
	}
	createProject(projectid);	
}

// --------------------------------	//
//                            		//
//	  Function to create project 	//
//                            		//
// -------------------------------- //
function createProject(projectid) {
	// find the project in the projects array
	let project = data.musings.values[projectid];

	// --------------------------------	//
	// Title and secondary title		//
	// -------------------------------- //
	let title = document.getElementById('title');
	title.innerHTML = project[0];

	// get the secondary title
	let secondaryTitle = document.getElementById('secondary-title');
	secondaryTitle.innerHTML = project[1] + ' - ' + project[2];

	// create a div for the project
	let projectDiv = document.createElement('div');
	projectDiv.className = 'project';

	// --------------------------------	//
	// Project image					//
	// -------------------------------- //
	let image = document.createElement('img');

	if (project[4] == undefined || project[4] == '') {
		project[4] = 'sandbox.png';
	}

	image.src = '../../musings/images/'+project[4]; 
	image.alt = project[0] + ", " + project[1]; 
	image.title = project[0] + ", " + project[1];

	// assign maxheight to the image
	image.style.maxHeight = '500px';
	projectDiv.appendChild(image);

	// --------------------------------	//
	// Description						//
	// -------------------------------- //
	if (project[3] !== undefined) {
		let description = document.createElement('div');
		// give it an id "markdown-content"
		description.id = 'markdown-content';
		description.innerHTML = project[3];
		projectDiv.appendChild(description);



	}	

	// --------------------------------	//
	// Main staff link					//
	// -------------------------------- //
	// if (project[5] !== undefined) {
	// 	// create a paragraph, then put the link in the paragraph, then put the paragraph in the project div
	// 	let linkParagraph = document.createElement('p');
	// 	// add class
	// 	linkParagraph.className = 'btn';
		
	// 	let link = document.createElement('a');
	// 	link.href = project[5];
	// 	link.innerHTML = "More ";
	// 	linkParagraph.appendChild(link);
	// 	projectDiv.appendChild(linkParagraph);
	// }

	// --------------------------------	//
	// YouTube video					//
	// -------------------------------- //
	if (project[9] !== undefined) {
		// add a title
		let videoTitle = document.createElement('h3');
		videoTitle.innerHTML = "Watch";
		projectDiv.appendChild(videoTitle);
		let video = document.createElement('iframe');
		video.src = project[9];
		video.width = "560";
		video.height = "315";
		video.frameborder = "0";
		video.allow = "accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture";
		video.allowfullscreen = true;
		projectDiv.appendChild(video);
		// add description project[10]
		let videoDescription = document.createElement('p');
		videoDescription.innerHTML = project[10];
		projectDiv.appendChild(videoDescription);
	}

	// --------------------------------	//
	// Contributors						//
	// -------------------------------- //
	if (project[7] !== undefined) {
		console.log('contributors exist: ' + project[7])
		let contributorsTitle = document.createElement('h3');
		contributorsTitle.innerHTML = "Contributors";
		projectDiv.appendChild(contributorsTitle);
		let contributors = document.createElement('p');
		contributors.innerHTML = project[7];
		projectDiv.appendChild(contributors);
	}

	// --------------------------------	//
	// Supported by						//
	// -------------------------------- //
	if (project[8] !== undefined) {	
		let supportedByTitle = document.createElement('h3');
		supportedByTitle.innerHTML = "Supported by";
		projectDiv.appendChild(supportedByTitle);
		let supportedBy = document.createElement('p');
		supportedBy.innerHTML = project[8];
		projectDiv.appendChild(supportedBy);
	}

	// --------------------------------	//
	// Tags								//
	// -------------------------------- //
		if (project[6] !== undefined) {
		let tags = project[6].split(',');
		let tagContainer = document.createElement('div');
		tagContainer.className = 'tag-container';
		tags.forEach(function(tag) {
			let tagDiv = document.createElement('div');
			tagDiv.className = 'tag';
			tagDiv.innerHTML = tag.trim();
			tagContainer.appendChild(tagDiv);
		});
		projectDiv.appendChild(tagContainer);
	}

	// add the project to the page
	document.getElementById('project-container').appendChild(projectDiv);

	// --------------------------------	//
	// Image gallery					//
	// -------------------------------- //
	if (project[11] !== undefined) {
		// add a title
		let galleryTitle = document.createElement('h3');
		galleryTitle.innerHTML = "Gallery";
		projectDiv.appendChild(galleryTitle);
		// add the images
		let images = project[11].split(',');
		images.forEach(function(image) {
			let imageDiv = document.createElement('div');
			imageDiv.className = 'glightbox';
			let img = document.createElement('img');
			img.src = '../../work/project/images/'+image.trim();
			img.alt = project[1];
			imageDiv.appendChild(img);
			projectDiv.appendChild(imageDiv);
		});
	}
}


</script>