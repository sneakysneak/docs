---
title: Collapse Test
permalink: collapse-test
---

<style type="text/css" rel="stylesheet">

.collapsible {
  background-color: #e85b51;
  color: white;
  cursor: pointer;
  padding: 18px;
  width: 100%;
  border: none;
  text-align: left;
  outline: none;
  font-size: 15px;
}

.active, .collapsible:hover {
  background-color: #f52e20;
}

.collapsible:after {
  content: '\002B';
  color: white;
  font-weight: bold;
  float: right;
  margin-left: 5px;
}

.active:after {
  content: "\2212";
}

.content {
  padding: 0 18px;
  max-height: 0;
  overflow: hidden;
  transition: max-height 0.2s ease-out;
  background-color: #f1f1f1;
}
</style>
<h2>Scripting</h2>

<p>Events:</p>
<button class="collapsible">before_webhook</button>
<div class="content">
  <p><br>Called when a webook request has been received and before anything else is done. Method is used to decide if the request should be continued or return a custom message to the caller.

<h4>Global objects</h4>
<code>method_endpoint</code>: The webhook request URL<br>
<code>method_request_headers</code>: The webhook request headers<br>
<code>method_request</code>: The webhook request body<br>
<code>method_request_parameters</code>: The webhook request parameters<br>
<code>method_response_headers</code>: The response headers for the request<br>
<code>method_response</code>: The response body for the request<br><br>
return: true for the webhook to continue normal execution, false to stop execution of the request and send the response body/headers to the caller
</p>
</div>
<button class="collapsible">after_webhook</button>
<div class="content">
  <p>Called immediately after a Request to a Webook has been received, whether the Cycle is currently running or stopped.

Global object
<code>method_response</code>: object that was POSTed to the Cyclr webhook<br>
<code>cycle_variables</code>: Allows access to Cycle variables. Changes are not persisted.<br>
<code>cycle_step_id</code>: ID of the step that is executing the script.<br>
<code>cycle_id</code>: The ID of the cycle the script is running in<br>
<code>cyclr_account_id</code>: The internal ID of the account the script is running in<br>
<code>external_account_id</code>: The external ID of the account the script is running in<br><br>
return: true for the webhook to continue normal execution, false to ignore the webhook request</p>
</div>
<button class="collapsible">Open Section 3</button>
<div class="content">
  <p>Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat.</p>
</div>

<script>
var coll = document.getElementsByClassName("collapsible");
var i;

for (i = 0; i < coll.length; i++) {
  coll[i].addEventListener("click", function() {
    this.classList.toggle("active");
    var content = this.nextElementSibling;
    if (content.style.maxHeight){
      content.style.maxHeight = null;
    } else {
      content.style.maxHeight = content.scrollHeight + "px";
    } 
  });
}
</script>
