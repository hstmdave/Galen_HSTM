<head>
<body>
<!-- 1. Salesforce Embedded Messaging Snippet -->
<script type='text/javascript'>
  function initEmbeddedMessaging() {
    try {
      embeddedservice_bootstrap.settings.language = 'en_US';
      embeddedservice_bootstrap.init(
        '00DWL000002dfgT',
        'Galen_Messaging',
        'https://healthstream--hstm.sandbox.my.site.com/ESWGalenMessaging1753122143194',
        {
          scrt2URL: 'https://healthstream--hstm.sandbox.my.salesforce-scrt.com'
        }
      );
    } catch (err) {
      console.error('Error loading Embedded Messaging: ', err);
    }
  };
</script>
<script type='text/javascript' src='https://healthstream--hstm.sandbox.my.site.com/ESWGalenMessaging1753122143194/assets/js/bootstrap.min.js' onload='initEmbeddedMessaging()'></script>

<!-- 2. Custom Phone Number Validation Script -->
<script>
  document.addEventListener("DOMContentLoaded", function () {
    const observer = new MutationObserver(() => {
      const phoneInput = document.querySelector('input[name="Phone"]');
      if (phoneInput) {
        const form = phoneInput.closest('form');
        observer.disconnect();

        const validatePhoneNumber = () => {
          const phoneNumber = phoneInput.value.trim();
          const digitsOnly = phoneNumber.replace(/\D/g, '');
          if (digitsOnly.length !== 10 || isNaN(digitsOnly)) {
            alert('Please enter a valid 10-digit phone number.');
            phoneInput.focus();
            return false;
          }
          return true;
        };

        phoneInput.addEventListener('blur', validatePhoneNumber);

        if (form) {
          form.addEventListener('submit', function (e) {
            if (!validatePhoneNumber()) {
              e.preventDefault();
              e.stopPropagation();
            }
          });
        }
      }
    });

    observer.observe(document.body, { childList: true, subtree: true });
  });
</script>

</body>
</head>


