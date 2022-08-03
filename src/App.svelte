<script>
	import Slider from '@bulatdashiev/svelte-slider';
    import { Button, MaterialApp } from 'svelte-materialify';

	
	
	let value=[0];
	let yval = 0;
    let zval = 0;
    let pval = 0;
    let y1val = 0;
    let z1val = 0;
    let res=false;

    let today_date = new Date();
	
	function calcPrice(e) {
		
        
        let xval = value[0]*100 + 300 ;

        yval = ((xval-200)/100)*49+499;

        zval = (((xval-200)/100)*39*12)+4788;

        pval = (yval*12-zval)/zval *100;

        y1val = yval*6/100;

        z1val = 5*zval/100;

        res = true;

        today_date = today_date.getDate() + '-' + (parseInt(today_date.getMonth())+1) + '-' + today_date.getFullYear();
	}

    function reset() {
        value[0] = 0;
        res = false;
    }
	
</script>


<center> 

    <img src='static/logo1.png' alt='Logo loading..'>

    

<div class='slider'>

    <b>Choose number of simultaneous users from below slider</b>

    <form on:submit|preventDefault={calcPrice}>
        
        <center>{value[0]*100 + 300}</center>
        <Slider max='97' bind:value>
        <span slot="left" style="font-size: 20px;">&#xf406;</span>
        </Slider>
        <input type="hidden" bind:value={value[0]} on:change={calcPrice} on:keydown={calcPrice}>


        <br><br> 
        


        <MaterialApp>
        <Button id='buutton' on:click={calcPrice} rounded class="primary-color">Calculate</Button> &nbsp;&nbsp;
        <Button id='button' on:click={reset} rounded class="primary-color">Reset</Button>
        </MaterialApp>
            
    </form>
    
    
    
    {#if res}
    <br>
    <div class='leftalign'><b id="leftalign">Price calculated on :</b> {today_date} <br></div>
    
	<div class='result'>
        
        
        <table>
        <tr><td><b>Monthly Customised Standard Plan Cost</b></td>  <td> {yval.toFixed(2)} $/month </td></tr>
        <br>
        <!-- <tr><td><b>Sales Commission (in monthly plan)</b></td>  <td> {y1val.toFixed(2)} $ </td></tr> -->
        <br>
        <tr><td><b>Annual Customised Standard Plan Cost</b></td>  <td> {zval.toFixed(2)} $/year </td></tr>
        <br>
        <!-- <tr><td><b>Sales Commission (in annual plan)</b></td>  <td> {z1val.toFixed(2)} $</td></tr> -->
        <br>
        <tr><td><b>Savings if you select yearly plan over monthly plan</b></td>  <td> {pval.toFixed(2)} %</td></tr>
        <br>
        
        <br>
        
        </table>
    </div>

    {/if}
    



</div>
<br>
<br>
</center>
<!-- <Ap/> -->

<style>
	.slider {
        
        width: 50%;
        
        margin-top: 6%;
        

        border-radius: 25px;
        border: 2px solid #73AD21;
        padding: 20px;

        //border-style: none;
        height: auto;
        
        
    }

    .result{
        margin-top: 10%;
    }

    .slider b{
        text-align: left;
    }


    img{
        margin-top: 2%;
        width: 10%;
        height: 100%;
        align-items: top;
    }

   

    .leftalign{
        text-align: center;
    }

    td {
        text-align: center;
    }
    
</style>