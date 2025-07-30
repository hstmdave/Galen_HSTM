<head>
<body>
<script type='text/javascript'>
	function initEmbeddedMessaging() {
	try {
	embeddedservice_bootstrap.settings.language = 'en_US'; // For example, enter 'en' or 'en-US'

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

 
  <!-- Custom Phone Validation Script -->
  <script>
  const observer = new MutationObserver(() => {
    const phoneInput = document.querySelector('input[name="tel"]');
    if (phoneInput) {
      const form = phoneInput.closest('form');
      observer.disconnect();

      phoneInput.setAttribute("pattern", "^\\(?\\d{3}\\)?[-.\\s]?\\d{3}[-.\\s]?\\d{4}$");
      phoneInput.setAttribute("title", "Please enter a valid phone number (e.g., 123-456-7890)");

      const validatePhone = () => {
        const value = phoneInput.value.trim();
        const phoneRegex = /^\(?\d{3}\)?[-.\s]?\d{3}[-.\s]?\d{4}$/;
        if (!phoneRegex.test(value)) {
          alert("Please enter a valid phone number (e.g., 123-456-7890).");
          phoneInput.focus();
          return false;
        }
        return true;
      };

      phoneInput.addEventListener('blur', validatePhone);

      if (form) {
        form.addEventListener('submit', (e) => {
          if (!validatePhone()) {
            e.preventDefault();
            e.stopPropagation();
          }
        });
      }
    }
  });

  observer.observe(document.body, { childList: true, subtree: true });

  </script>

</body>
</head>


