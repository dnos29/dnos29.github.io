---
layout: post
title: Convert text to color
tags: [jquery, color, convert]
categories: [Jquery]
---
<style>
    #snackbar {
  visibility: hidden; /* Hidden by default. Visible on click */
  min-width: 250px; /* Set a default minimum width */
  margin-left: -125px; /* Divide value of min-width by 2 */
  background-color: #333; /* Black background color */
  color: #fff; /* White text color */
  text-align: center; /* Centered text */
  border-radius: 2px; /* Rounded borders */
  padding: 16px; /* Padding */
  position: fixed; /* Sit on top of the screen */
  z-index: 1; /* Add a z-index if needed */
  left: 50%; /* Center the snackbar */
  bottom: 30px; /* 30px from the bottom */
}

/* Show the snackbar when clicking on a button (class added with JavaScript) */
#snackbar.show {
  visibility: visible; /* Show the snackbar */
  /* Add animation: Take 0.5 seconds to fade in and out the snackbar. 
  However, delay the fade out process for 2.5 seconds */
  -webkit-animation: fadein 0.5s, fadeout 0.5s 2.5s;
  animation: fadein 0.5s, fadeout 0.5s 2.5s;
}

/* Animations to fade the snackbar in and out */
@-webkit-keyframes fadein {
  from {bottom: 0; opacity: 0;} 
  to {bottom: 30px; opacity: 1;}
}

@keyframes fadein {
  from {bottom: 0; opacity: 0;}
  to {bottom: 30px; opacity: 1;}
}

@-webkit-keyframes fadeout {
  from {bottom: 30px; opacity: 1;} 
  to {bottom: 0; opacity: 0;}
}

@keyframes fadeout {
  from {bottom: 30px; opacity: 1;}
  to {bottom: 0; opacity: 0;}
}
</style>
<div class="form-group">
    <label for="exampleInputEmail1">Email address</label>
    <input type="text" class="form-control" placeholder="Input text to get color" onchange="show_result(this.value)">
</div>
<div style="display: flex; align-items: center;flex-direction: column;">
<button class="btn btn-default" style="margin-bottom: 15px" onclick="coppyToClipBoard()"><i class="fa fa-files-o" aria-hidden="true"></i> Coppy to Clipboard</button>
<input id="result-in" type="text" class="form-control" placeholder="Color" readonly>
</div>
<script>
    function show_result(str){
        // document.getElementById("result").innerHTML =  '#' + intToRGB(hashCode(str));
        document.getElementById("result-in").value =  '#' + intToRGB(hashCode(str));
    }
    function hashCode(str) { // java String#hashCode
        var hash = 0;
        for (var i = 0; i < str.length; i++) {
        hash = str.charCodeAt(i) + ((hash << 5) - hash);
        }
        return hash;
    } 

    function intToRGB(i){
        var c = (i & 0x00FFFFFF)
            .toString(16)
            .toUpperCase();

        return "00000".substring(0, 6 - c.length) + c;
    }
    function coppyToClipBoard() {
        var copyText = document.getElementById("result-in");

        /* Select the text field */
        copyText.select();
        /* Copy the text inside the text field */
        document.execCommand("copy");

        /* Alert the copied text */
        // alert("Copied the text: " + copyText.value);
    }
</script>