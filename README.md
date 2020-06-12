# Ash-s-PhotoEditor
<!DOCTYPE html>
<html>
<head>
	<title>PhotoEditor</title>
	<meta charset="utf-8">
	<meta name="viewport" content="width=device-width">
	<link rel="stylesheet" href="https://bootswatch.com/4/flatly/bootstrap.min.css">
	<style>
		canvas {
  		margin: auto;
  		background: #ececec;
  		width: 100%;
		}
		.btn-disabled {
  		color: #fff !important;
		}
	</style>
</head>
<body>
	<nav class="navbar navbar-dark bg-info mb-5">
  <div class="container">
    <a href="#" class="navbar-brand">Ash Image Editor</a>
  </div>
</nav>
<div class="container">
  <div class="row">
    <div class="col-md-8 m-auto">
      <div class="custom-file mb-3">
        <input type="file" class="custom-file-input" id="upload-file">
        <label for="upload-file" class="custom-file-label">Choose Image</label>
      </div>
      <canvas id="canvas"></canvas>

      <h4 class="text-center my-3">Filters</h4>

      <div class="row my-4 text-center">
        <div class="col-md-3">
          <div class="btn-group btn-group-sm">
            <button class="filter-btn brightness-remove btn btn-info">-</button>
            <button class="btn btn-secondary btn-disabled" disabled>Brightness</button>
            <button class="filter-btn brightness-add btn btn-info">+</button>
          </div>
        </div>

        <div class="col-md-3">
          <div class="btn-group btn-group-sm">
            <button class="filter-btn contrast-remove btn btn-info">-</button>
            <button class="btn btn-secondary btn-disabled" disabled>Contrast</button>
            <button class="filter-btn contrast-add btn btn-info">+</button>
          </div>
        </div>

        <div class="col-md-3">
          <div class="btn-group btn-group-sm">
            <button class="filter-btn saturation-remove btn btn-info">-</button>
            <button class="btn btn-secondary btn-disabled" disabled>Saturation</button>
            <button class="filter-btn saturation-add btn btn-info">+</button>
          </div>
        </div>

        <div class="col-md-3">
          <div class="btn-group btn-group-sm">
            <button class="filter-btn vibrance-remove btn btn-info">-</button>
            <button class="btn btn-secondary btn-disabled" disabled>Vibrance</button>
            <button class="filter-btn vibrance-add btn btn-info">+</button>
          </div>
        </div>
      </div>
      <!-- ./row -->

      <h4 class="text-center my-3">Effects</h4>

      <div class="row mb-3">
        <div class="col-md-3">
          <button class="filter-btn vintage-add btn btn-dark btn-block">
              Vintage
            </button>
        </div>
        <div class="col-md-3">
          <button class="filter-btn lomo-add btn btn-dark btn-block">
              Lomo
            </button>
        </div>
        <div class="col-md-3">
          <button class="filter-btn clarity-add btn btn-dark btn-block">
              Clarity
            </button>
        </div>
        <div class="col-md-3">
          <button class="filter-btn sincity-add btn btn-dark btn-block">
              Sin City
            </button>
        </div>
      </div>

      <div class="row">
        <div class="col-md-3">
          <button class="filter-btn crossprocess-add btn btn-dark btn-block">
              Cross Process
            </button>
        </div>
        <div class="col-md-3">
          <button class="filter-btn pinhole-add btn btn-dark btn-block">
              Pinhole
            </button>
        </div>
        <div class="col-md-3">
          <button class="filter-btn nostalgia-add btn btn-dark btn-block">
              Nostalgia
            </button>
        </div>
        <div class="col-md-3">
          <button class="filter-btn hermajesty-add btn btn-dark btn-block">
              Her Majesty
            </button>
        </div>
      </div>

      <div class="row mt-5">
        <div class="col-md-6">
          <button id="download-btn" class="btn btn-primary btn-block">Download Image</button>
        </div>
        <div class="col-md-6">
          <button id="revert-btn" class="btn btn-danger btn-block">Revert Filters</button>
        </div>
      </div>
    </div>
  </div>
</div>
<script>
	const canvas = document.getElementById("canvas");
const ctx = canvas.getContext("2d");

let img = new Image();
let fileName = "";

const downloadBtn = document.getElementById("download-btn");
const uploadFile = document.getElementById("upload-file");
const revertBtn = document.getElementById("revert-btn");

// Filter & Effects

document.addEventListener("click", e =>//using arrow function here onwards 
{
  if (e.target.classList.contains("filter-btn")) {
    if (e.target.classList.contains("brightness-add")) {
      Caman("#canvas", img, function() {
        this.brightness(5).render();
      });
    } else if (e.target.classList.contains("brightness-remove")) {
      Caman("#canvas", img, function() {
        this.brightness(-5).render();
      });
    } else if (e.target.classList.contains("contrast-add")) {
      Caman("#canvas", img, function() {
        this.contrast(5).render();
      });
    } else if (e.target.classList.contains("contrast-remove")) {
      Caman("#canvas", img, function() {
        this.contrast(-5).render();
      });
    } else if (e.target.classList.contains("saturation-add")) {
      Caman("#canvas", img, function() {
        this.saturation(5).render();
      });
    } else if (e.target.classList.contains("saturation-remove")) {
      Caman("#canvas", img, function() {
        this.saturation(-5).render();
      });
    } else if (e.target.classList.contains("vibrance-add")) {
      Caman("#canvas", img, function() {
        this.vibrance(5).render();
      });
    } else if (e.target.classList.contains("vibrance-remove")) {
      Caman("#canvas", img, function() {
        this.vibrance(-5).render();
      });
    } else if (e.target.classList.contains("vintage-add")) {
      Caman("#canvas", img, function() {
        this.vintage().render();
      });
    } else if (e.target.classList.contains("lomo-add")) {
      Caman("#canvas", img, function() {
        this.lomo().render();
      });
    } else if (e.target.classList.contains("clarity-add")) {
      Caman("#canvas", img, function() {
        this.clarity().render();
      });
    } else if (e.target.classList.contains("sincity-add")) {
      Caman("#canvas", img, function() {
        this.sinCity().render();
      });
    } else if (e.target.classList.contains("crossprocess-add")) {
      Caman("#canvas", img, function() {
        this.crossProcess().render();
      });
    } else if (e.target.classList.contains("pinhole-add")) {
      Caman("#canvas", img, function() {
        this.pinhole().render();
      });
    } else if (e.target.classList.contains("nostalgia-add")) {
      Caman("#canvas", img, function() {
        this.nostalgia().render();
      });
    } else if (e.target.classList.contains("hermajesty-add")) {
      Caman("#canvas", img, function() {
        this.herMajesty().render();
      });
    }
  }
});

// Revert Filters
revertBtn.addEventListener("click", e => {
  Caman("#canvas", img, function() {
    this.revert();
  });
});


uploadFile.addEventListener("change", () => {

  const file = document.getElementById("upload-file").files[0];

  const reader = new FileReader();

  if (file) {

    fileName = file.name;
    reader.readAsDataURL(file);
  }

  reader.addEventListener(
    "load",
    () => {

      img = new Image();

      img.src = reader.result;

      img.onload = function() {
        canvas.width = img.width;
        canvas.height = img.height;
        ctx.drawImage(img, 0, 0, img.width, img.height);
        canvas.removeAttribute("data-caman-id");
      };
    },
    false
  );
});


downloadBtn.addEventListener("click", () => {
  
  const fileExtension = fileName.slice(-4);


  let newFilename;


  if (fileExtension === ".jpg" || fileExtension === ".png") {

    newFilename = fileName.substring(0, fileName.length - 4) + "-edited.jpg";
  }


  download(canvas, newFilename);
});

function download(canvas, filename) {
 
  let e;

  const link = document.createElement("a");

 
  link.download = filename;
  link.href = canvas.toDataURL("image/jpeg", 0.8);
 
  e = new MouseEvent("click");

  link.dispatchEvent(e);
}
</script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/camanjs/4.1.2/caman.full.js"></script>
</body>
</html>
