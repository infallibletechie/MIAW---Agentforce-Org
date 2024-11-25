<html>
<script type='text/javascript'>
	function initEmbeddedMessaging() {
		try {
			embeddedservice_bootstrap.settings.language = 'en_US'; // For example, enter 'en' or 'en-US'

			embeddedservice_bootstrap.init(
				'00DSB00000FiY6z',
				'MIAW_Agentforce',
				'https://dsb00000fiy6z2af.test1.my.pc-rnd.site.com/ESWMIAWAgentforce1730200100175',
				{
					scrt2URL: 'https://dsb00000fiy6z2af.test1.my.pc-rnd.salesforce-scrt.com'
				}
			);
		} catch (err) {
			console.error('Error loading Embedded Messaging: ', err);
		}
	};
</script>
<script type='text/javascript' src='https://dsb00000fiy6z2af.test1.my.pc-rnd.site.com/ESWMIAWAgentforce1730200100175/assets/js/bootstrap.min.js' onload='initEmbeddedMessaging()'></script>
</html>
