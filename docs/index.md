# WhatsApp API documents

In this documentation you will find information about working with the API of our service for sending and receiving messages from WhatsApp.

 - ## API Documentation
    - [Overview](api/index.md) - This page provides general information about our API, including the basic principles of
      operation and the general structure of requests and responses.
    - Account
        - [Account - overview](api/account/index.md) - General information about working with the account.
        - [Get account settings (instance)](api/account/get-settings.md) - Instructions for retrieving account settings.
        - [Set account settings (instance)](api/account/set-settings.md) - Instructions for configuring account settings.
        - [Reboot account (instance)](api/account/reboot.md) - Instructions for rebooting the account.
        - [Get QR code](api/account/qr.md) - Instructions for obtaining a QR code.
    - Sending
        - [Sending - overview](api/sending/index.md) - General information about the message sending process.
        - [Send text](api/sending/text.md) - Instructions for sending text messages.
        - [Send image](api/sending/image.md) - Instructions for sending images.
    - Receiving
        - [Receiving - overview](api/receiving/index.md) - General information about the message receiving process.
        - Incoming notification format
            - [Overview](api/receiving/notifications-format/index.md) - General information about the format of incoming notifications.
            - Incoming messages
                - [Incoming messages - overview](api/receiving/notifications-format/incoming-message/index.md) - General information about incoming messages.
                - [Text](api/receiving/notifications-format/incoming-message/text.md) - Information about incoming text messages.
                - [Text or text with URL](api/receiving/notifications-format/incoming-message/extended-text.md) - Information about incoming messages with text or text with URLs.
                - [Image](api/receiving/notifications-format/incoming-message/image.md) - Information about reactions to incoming messages.
            - Outgoing messages
                - [Overview](api/receiving/notifications-format/outgoing-message/index.md) - General information about sent messages.
                - [Messages sent from phone](api/receiving/notifications-format/outgoing-message/phone.md) - Information about messages sent from a phone.
                - [Outgoing message status](api/receiving/notifications-format/outgoing-message/status.md) - Information about the statuses of sent messages.
    - Service methods
        - [Service methods - overview](api/service/index.md) - General information about service methods.
        - [Check Whatsapp availability](api/service/check-whatsapp.md) - Instructions for checking WhatsApp availability.
    - [Rate limiter](api/rate-limiter.md) - Information about API request rate limiting.
- ## Partners
    - [Partners - overview](partners/index.md) - General information for partners.
    - [Create instance](partners/instance-creation.md) - Instructions for creating an instance.
    - [Delete instance partner account](partners/instance-removed.md) - Instructions for deleting a partner account instance.
    - [Get all instances of an account created by partner](partners/instance-reveiver.md) - Instructions for retrieving all instances of an account created by a partner.