<html>
<script type='text/javascript'>
	function initEmbeddedMessaging() {
		try {
			embeddedservice_bootstrap.settings.language = 'en_US'; // For example, enter 'en' or 'en-US'
			//Hiding Chat Button on page load
   			embeddedservice_bootstrap.settings.hideChatButtonOnLoad = true;

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

<button 
	style="position: fixed; bottom: 25px;right: 25px;border-radius: 12px;" 
	onclick="launchChat()">
 	<img src="https://www.infallibletechie.com/wp-content/uploads/2024/11/bot_120.png"/>
  	&nbsp;&nbsp;&nbsp;
	Hi, How can I help you?
</button>

<script>
    function launchChat() {
        embeddedservice_bootstrap.utilAPI.launchChat()
            .then(() => {
                console.log( 
			'Successfully launched Messaging' 
		);
            }).catch(() => {
                console.log( 
			'Some error occurred when launching Messaging' 
		);
            }).finally(() => {
                console.log( 
			'Successfully launched Messaging - Finally' 
		);
            });
    }
</script>
</html>
