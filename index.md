<head>
<body>
<script type='text/javascript'>
  function initEmbeddedMessaging() {
    try {
      embeddedservice_bootstrap.settings.language = 'en_US';
 
      embeddedservice_bootstrap.init(
        '00DWL000002dfgT', // Your Salesforce Org ID
        'Galen_Messaging', // Your Deployment Name
        'https://healthstream--hstm.sandbox.my.site.com/ESWGalenMessaging1753122143194', // Your ESW Base URL
        {
          scrt2URL: 'https://healthstream--hstm.sandbox.my.salesforce-scrt.com'
        }
      );
    } catch (err) {
      console.error('Error loading Embedded Messaging: ', err);
    }
  }
 
  // Wait for the widget to be ready before applying validation
  window.addEventListener("onEmbeddedMessagingReady", function () {
    // Make the Phone field visible and editable
    embeddedservice_bootstrap.prechatAPI.setVisiblePrechatFields({
      "Phone": {
        value: "",
        isEditableByEndUser: true
      }
    });
 
    // Add validation logic for the Phone field
    embeddedservice_bootstrap.prechatAPI.setPrechatFieldValidation(function (fields) {
      const phone = fields.Phone?.value || "";
      const digitsOnly = phone.replace(/\D/g, '');
 
      // Check for exactly 10 digits and ensure it's not an email or contains letters
      const isValidPhone = /^\d{10}$/.test(digitsOnly) && !/[a-zA-Z@]/.test(phone);
 
      if (!isValidPhone) {
        alert("Please enter a valid 10-digit phone number (numbers only, no letters or email addresses).");
        return false; // Prevents chat from starting
      }
 
      return true; // Allows chat to start
    });
  });
</script>
 
<script type='text/javascript' src='https://healthstream--hstm.sandbox.my.site.com/ESWGalenMessaging1753122143194/assets/js/bootstrap.min.js' onload='initEmbeddedMessaging()'></script>
</body>
</head>


