.. _Chap8-DeviceFingerprintIntegration:

==========================================
Chapter 8 - Device Fingerprint Integration
==========================================
--------
Overview
--------
Introduction
  The device fingerprint identifies devices through information collected by a client run on an end user"s computer. 
  This client generates a blackbox that contains all device information available.

Description
  Web applications obtain device information by sourcing dynamically generated JavaScript from HiPay TPP. 
  The JavaScript determines what information is available and generates a blackbox from all available sources.

Blackbox content
  A black box will typically:
  - Range up to 4,000 bytes (the average length being just under 1,000 bytes)
  - Contain alphanumeric values and the special characters: + / ; =
  - Begin with 0200, 0400, 0500 or 0600

-------------------------
Generate blackbox content
-------------------------
Description
  To integrate the client you must specify a hidden field that the JavaScript will populate. 
  This adds the black box as another field to be submitted along the other details in the form.		
		
**Recommendation**

=======================================================================================  =======================================================================================================================================================
YOU MUST        																	     YOU MUST NOT
=======================================================================================  =======================================================================================================================================================
1. Include a hidden form field with an ID "ioBB" that will be populated with the value.  1. DO NOT call HiPay TPP fingerprint JavaScript BEFORE including the hidden "ioBB" form field. 
2. Call the HiPay TPP fingerprint JavaScript function to obtain the blackbox content:    2. DO NOT cache or use local copies of the JavaScript
*https://secure-gateway.allopass.com/gateway/toolbox/fingerprint*.                       JavaScript is dynamically generated for each customer and so caching of the script may cause unrelated devices to be identified as the same computer.
                                                                                         The script also uses domain cookies to identify devices across subscribers.
=======================================================================================  =======================================================================================================================================================

-------
Example
-------

Blackbox generation
		
.. code-block:: xml
    :linenos:

   	<form name="test">
   	<!-- hidden field to store blackbox -->
   	  <input type="text" name="device_fingerprint" id="ioBB">
   	</form>    
   	<!-- Include JavaScript fingerprint library -->
   	<script language="javascript" src="https://secure-gateway.allopass.com/gateway/toolbox/fingerprint">
   	</script>
