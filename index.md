<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Embedded Messaging</title>
</head>
<body>
    <script type='text/javascript'>
        function initEmbeddedMessaging() {
            try {
                embeddedservice_bootstrap.settings.language = 'en_US'; 

                window.addEventListener("onEmbeddedMessageSent", (event) => {
                    console.log("START:: Message Sent");
                    
                    const tempContent = event.detail;
                    const { conversationEntry } = tempContent;

                    if (conversationEntry?.sender?.role) {
                        const { role: strRole, entryPayload } = conversationEntry.sender;
                        console.log('strRole =>', strRole);
                        console.log('entryPayload =>', JSON.stringify(entryPayload));

                        if (strRole === 'EndUser' && entryPayload) {
                            try {
                                const entryPayloadObj = JSON.parse(entryPayload);
                                const result = entryPayloadObj?.abstractMessage?.staticContent?.text;
                                
                                console.log('result -->', result);
                                const optOutKeywords = [ 'end', 'stop' ];
                                
                                if (optOutKeywords.includes(result)) {
                                    embeddedservice_bootstrap.userVerificationAPI
                                        .clearSession()
                                        .then(() => {
                                            console.log("Session cleared successfully.");
                                        })
                                        .catch((error) => {
                                            console.error("Error clearing session:", error);
                                        })
                                        .finally(() => {
                                            console.log("clearSession finally.");
                                        });
                                }
                            } catch (e) {
                                console.error("Failed to parse entryPayload:", e);
                            }
                        }
                    }
                    console.log("END:: Message Sent");
                });

                embeddedservice_bootstrap.init(
                    '00DKj00000BqFBw',
                    'Messaging_for_In_App_and_Web',
                    'https://mduraipand-250112-382-demo.my.site.com/ESWMessagingforInAppa1736797486907',
                    {
                        scrt2URL: 'https://mduraipand-250112-382-demo.my.salesforce-scrt.com'
                    }
                );
            } catch (err) {
                console.error('Error loading Embedded Messaging: ', err);
            }
        }
    </script>
    <script 
        type='text/javascript' 
        src='https://mduraipand-250112-382-demo.my.site.com/ESWMessagingforInAppa1736797486907/assets/js/bootstrap.min.js' 
        onload='initEmbeddedMessaging()'>
    </script>
</body>
</html>
