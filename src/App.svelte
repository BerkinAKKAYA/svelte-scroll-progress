<script>
	let progress = 0;
	let height = 0;

	UpdateHeight();

	window.onresize = UpdateHeight;
	document.onscroll = UpdateProgress;

	function UpdateHeight() {
		height = document.body.offsetHeight - window.innerHeight;
		UpdateProgress();
	}
	function UpdateProgress() {
		progress = Math.round(window.scrollY * 100 / height);
	}
</script>

<div id="bar">
	<div id="fill" style="width: {progress}%"></div>
</div>

<div id="textDisplay">
	<h1>{progress}%</h1>
</div>

<style>
	#bar {
		width: 100%;
		height: 10px;
		position: sticky;
		top: 0;
		background: rgba(0,0,0,0.5);
		box-shadow: 0 0 10px rgba(0,0,0,0.5);
	}
	#fill {
		transition: width 1s ease;
		height: 100%;
		background-color: whitesmoke;
	}
	#textDisplay {
		width: 100%;
		height: 100vh;
		position: sticky;
		top: 0;
	}
	h1 {
		position: absolute;
		left: 50%;
		top: 50%;
		transform: translate(-50%, -50%);
		color: white;
		text-shadow: 0 0 10px #666;
		font-family: monospace;
		font-size: 10em;
		pointer-events: none;
		user-select: none;
	}
	@media (max-width: 600px) {
		h1 { font-size: 6em }
	}
</style>