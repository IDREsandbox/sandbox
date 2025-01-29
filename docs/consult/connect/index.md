---
hide:
  - toc
title:  "Connect with OARC Sandbox Research Team | UCLA Technology Sandbox"
description: "Meet the interdisciplinary research team behind UCLA's Technology Sandbox. Learn how to collaborate, access our innovative computing facility, and engage with OARC's experts in digital scholarship."
---

<h1 id="title" tabindex="0">Connect</h1>

<!-- add a search box -->
<input type="text" id="search" class="search" onkeyup="search()" placeholder="Search for people.." tabindex="0">

<!-- two buttons to toggle between gallery view and tag view -->
<span class="btn btn-on" tabindex="0" alt="gallery view" title="gallery view">
	gallery view
</span>
<span class="btn btn-off" tabindex="0" alt="tab view" title="tab view" onclick="window.location.href = 'tags'" onkeydown="if(event.keyCode === 13) { window.location.href = 'tags' }" tabindex="0">
	tag view
</span>

<h2 tabindex="0">Current</h2>
<div class="gallery-current" tabindex="0"></div>

<h2 tabindex="0">Past</h2>
<div class="gallery-past" tabindex="0"></div><hr>
<!-- <div class="gallery"></div>  -->

<script>

// --------------------------------	//
//                            		//
//	  Initialize			    	//
//                            		//
// -------------------------------- //

let section = 'consult'

function init(){

	// --------------------------------	//
	// Loop through project data		//
	// -------------------------------- //
	counter = 0;
	
	// divide the gallery into two sections: Current and Past
	// gallery will be determined by the value in row[2]
	// if the value is 'staff', the gallery item will be added to the current section
	// else, it will be added to the past section
	// document.querySelector('.gallery').innerHTML = '';
	// add current as a title to .gallery






	// document.querySelector('.gallery').insertAdjacentHTML('beforeend',`<h2>Current</h2>`);
	// document.querySelector('.gallery').insertAdjacentHTML('beforeend',`<div class="gallery-current" style='border:1px solid red;'>current here</div><hr>`);
	// document.querySelector('.gallery').insertAdjacentHTML('beforeend',`<h2>Past</h2>`);
	// document.querySelector('.gallery').insertAdjacentHTML('beforeend',`<div class="gallery-past" style='border:1px solid blue;'>past here</div>`);
	
	
	
	// filter data by tag, default is all
	let tag = urlParams.get('tag');
	if (tag) {
		console.log('tag found');
		data[section].forEach(function(row) {
			let status = row[2];
			let tags = row[6].split(',');
			if (tags.map(function(x) { return x.trim() }).includes(tag)) {
				if (status == 'staff') {
					addGalleryItem(row,counter,'.gallery-current')
				} else {
					addGalleryItem(row,counter,'.gallery-past')
				}
			}
			counter++;
		});
		// add the name of the tag next to the search box with an option to clear the filter
		// clear the filter by removing the tag from the url
		document.querySelector('.search').insertAdjacentHTML('afterend',` <a href="?"><span class="tag tag-filter">${tag} x</span></a>`);
		
	} else {
		console.log('no tag found');
		data[section].forEach(function(row) {
			let status = row[2];
			if (status == 'staff') {
				addGalleryItem(row,counter,'.gallery-current')
			} else {
				addGalleryItem(row,counter,'.gallery-past')
			}

			// addGalleryItem(row,counter);
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