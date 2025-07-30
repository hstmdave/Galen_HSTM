<head>
<body>
<!-- 1. Salesforce Embedded Messaging Snippet -->
<script type='text/javascript'>
  function initEmbeddedMessaging() {
    try {
      embeddedservice_bootstrap.settings.language = 'en_US';

      embeddedservice_bootstrap.init(
        '00DWL000002dfgT', // Your Salesforce Org ID
        'Galen_Messaging', // Your Deployment Name
        'https://healthstream--hstm.sandbox.my.site.com/ESWGalenMessaging1753122143194', // Your ESW Base URL
        {
          scrt2URL: 'https://healthstream--hstm.sandbox.my.salesforce-scrt.com',

          // Pre-Chat API Configuration
          prechatFormDetails: [
            {
              label: "Phone",
              value: "",
              transcriptFields: ["Phone"],
              displayToAgent: true,
              required: true
            }
          ],
          prepopulatedPrechatFields: {
            Phone: ""
          },
          onPrechatSubmit: function(prechatFields) {
            const phone = prechatFields.Phone || "";
            const digitsOnly = phone.replace(/\D/g, '');
            if (digitsOnly.length !== 10) {
              alert("Please enter a valid 10-digit phone number.");
              return false; // Prevents chat from starting
            }
            return true;
          }
        }
      );
    } catch (err) {
      console.error('Error loading Embedded Messaging: ', err);
    }
  }
</script>

<script type='text/javascript' src='https://healthstream--hstm.sandbox.my.site.com/ESWGalenMessaging1753122143194/assets/js/bootstrap.min.js' onload='initEmbeddedMessaging()'></script>

</body>
</head>


