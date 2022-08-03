<script>
	import Slider from '@bulatdashiev/svelte-slider';
    import Ap from './App2.svelte';
	
	let val=[300,10000];
	let value=[0];
	let yval = value+12;

    let inpu = value[0];

    let xval = (value+300)*100
	
	function calcPrice() {
		alert('Hi');
        const formData = new FormData(e.target);
        alert(inpu);
	}
	
	
	
</script>
<center>
<div class='slider'>

    <form on:submit|preventDefault={calcPrice}>
        <Slider name={['inpu', 'input-2']} range />
        <button>Submit</button>
    </form>
    





	<b>Choose value of X from slider below</b>
    <br>
    <center>{(value[0]*100) + 300}</center>
<Slider  max="97" bind:value/>
<br>

You have choose, X = {(value[0]*100) + 300}
<br>
<br>
Value of y = {10}

</div>
</center>
<!-- <Ap/> -->

<style>
	.slider {
        float: center;
        width: 50%;
        display:grid;
        margin-top: 10%;
    }
</style>