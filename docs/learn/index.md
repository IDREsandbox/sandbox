---
hide:
  - navigation
  - toc
title: "Learn with OARC Sandbox | UCLA Workshops and Tutorials"
description: "Access a comprehensive library of workshops and tutorials from UCLA's OARC Sandbox. Enhance your skills in digital research, data analysis, and advanced computing techniques."
---
<h1 id="title" tabindex="0">Learn</h1>
<!-- add description -->
<p id="description" tabindex="0">Access a comprehensive library of workshops and tutorials from UCLA's OARC Sandbox. Enhance your skills in digital research, data analysis, and advanced computing techniques.
</p>

<!-- add a search box -->
<input type="text" id="search" class="search" onkeyup="search()" placeholder="Search projects.." tabindex="0">

<!-- two buttons to toggle between gallery view and tag view -->
<span class="btn btn-on" tabindex="0" alt="gallery view" title="gallery view">
	gallery view
</span>
<span class="btn btn-off" tabindex="0" alt="tab view" title="tab view" onclick="window.location.href = 'tags'" onkeydown="if(event.keyCode === 13) { window.location.href = 'tags' }">
	tag view
</span>

<div class="gallery" tabindex="0"></div> 

<script>

// --------------------------------	//
//                            		//
//	  Initialize			    	//
//                            		//
// -------------------------------- //

let section = 'learn'

function init(){
	console.log(data)
	// --------------------------------	//
	// Loop through project data		//
	// -------------------------------- //
	counter = 0;

	// filter data by tag, default is all
	let tag = urlParams.get('tag');
	if (tag) {
		document.querySelector('.gallery').innerHTML = '';
		data[section].forEach(function(row) {
			let tags = row[6].split(',');
			if (tags.map(function(x) { return x.trim() }).includes(tag)) {
				addGalleryItem(row,counter);
			}
			counter++;
		});
		// add the name of the tag next to the search box with an option to clear the filter
		// clear the filter by removing the tag from the url
		document.querySelector('.search').insertAdjacentHTML('afterend',` <a href="?"><span class="tag tag-filter">${tag} x</span></a>`);

	} else {

		let shuffledData = data[section].sort(() => Math.random() - 0.5);
		shuffledData.forEach(function(row) {
			addGalleryItem(row, counter);
			counter++;
		});

	}

	// create the search function
	window.search = function() {
		let input, filter, ul, li, a, i, txtValue;
		input = document.getElementById('search');
		filter = input.value.toUpperCase();
		li = document.querySelectorAll('.gallery-container');
		for (i = 0; i < li.length; i++) {
			a = li[i].getElementsByTagName('a')[0];

			// search by project name, project description, and tags
			let txtValue = a.textContent || a.innerText;
			// search tags, which are in separate span tags of class tag
			let tags = '';
			li[i].querySelectorAll('.tag').forEach(function(tag) {
				tags += tag.textContent;
			});

			if (txtValue.toUpperCase().indexOf(filter) > -1 || tags.toUpperCase().indexOf(filter) > -1) {
				li[i].style.display = '';
			} else {
				li[i].style.display = 'none';
			}
			
		}
	}	
	

}

</script>