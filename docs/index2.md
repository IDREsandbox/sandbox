---
hide:
  - navigation
  - toc
  - footer
search: false
---

<style>
html, body {
  margin: 0;
  padding: 0;
  width: 100%;
  height: 100%;
  overflow: hidden;
}
.body-background {
  width: 100%;
  height: 100%;
  background-size: cover;
  background-position: center;
  background-repeat: no-repeat;
}
.page-content {
  width: 100%;
  height: 100%;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: flex-end;
  padding: 20px;
  box-sizing: border-box;
  color: #fff;
  font-family: Arial, sans-serif;
}
.site-logo {
  margin-top: 20px;
}
.tagline {
  font-weight: bold;
  font-size: 2rem;
  text-align: right;
}
.paragraph {
  text-align: right;
  max-width: 300px;
}
.links {
  margin-top: 20px;
  text-align: right;
}
.links a {
  margin-left: 10px;
  text-decoration: none;
  color: white;
  font-weight: bold;
}
</style>

<div id="bgContainer" class="body-background">
  <div class="page-content">
    <div class="site-logo">
      <img src="logo.png" alt="Site Logo" height="50">
    </div>
    <div>
      <div class="tagline">Bringing your research to life</div>
      <p class="paragraph">
        Explore new ideas with interactive workshops, hands-on experimentation, 
        and expert support in our Technology Sandbox.
      </p>
    </div>
    <div class="links">
      <a href="learn/">Learn</a>
      <a href="work/">Work</a>
      <a href="musings/">Musings</a>
      <a href="consult/">Consult</a>
    </div>
  </div>
</div>

<script>
function init() {
    // document.addEventListener('dataLoaded', function() {
    //     if (!data.work || !data.work || data.work.length === 0) {
    //         console.warn('No valid "work" sheet data found.');
    //         return;
    //     }
    console.log("generating random image...");
        let randomIndex = Math.floor(Math.random() * data.work.length);
        let image = data.work[randomIndex][4] || 'sandbox.png';
        console.log('Random image selected:', image);
        document.getElementById('bgContainer').style.backgroundImage =
            'url("./work/images/' + image + '")';
    // });
}

// init();
</script>