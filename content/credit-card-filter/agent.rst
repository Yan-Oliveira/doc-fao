Agent Interface
===============

This package has no agent interface.


Mask Credit Card
----------------

This feature is a complete subsystem that allows the following:

- Automatically show a warning message next to a credit card number (not storable).
- Mask credit card numbers for new tickets and articles.
- Mask credit card numbers contained in articles already stored in the system.

The credit card detection mechanism requires credit card numbers of 13, 15 or 16 digits. These credit card numbers should be at least potentially valid numerically, which means they pass the `Luhn algorithm <http://en.wikipedia.org/wiki/Luhn_algorithm>`__ test.

For the current version only a subgroup of all potentially valid credit card number are detected. This is the list of the credit cards numbers that are considered valid:

- Visa 16 digits starting with a 4.
- Visa 13 digits starting with a 4.
- MasterCard 16 digits starting with 51 to 55.
- Discover 16 digits starting with 6011, 6121-29 to 6229-25, 644 to 649 or 65.
- JCB 16 digits starting with 3088, 3096, 3112, 3158, 3337 or 3528 to 3589.
- JCB 15 digits starting with 1800, 2100 or 2131.
- American Express 15 digits starting with 34 or 37.

For successful detection, the digits of these credit card numbers are allowed without separation or with a single separator in groups of digits as 4-4-4-4, 4-4-4-3, 4-4-4-1 or 4-6-5 (the last combination for American Express only). Allowed separators are ``-``, ``+``, ``/``, ``.`` or a combination thereof.

Valid credit card numbers that are a subset of a bigger number are not considerate as credit card numbers. This is to avoid false positives, e.g. a serial number that contains a (not intentionally) valid credit card number. Valid credit card numbers should be enclosed by at least one non-numeric character.


Active Credit Card Masking
--------------------------

When this feature is enabled, every article will be scanned for valid credit card numbers before it is saved on the database. In case of any findings in subject or body, all but the first six and the last four digits will be replaced by a configurable masking character.

.. seealso::

   The behavior can be changed with the following settings in the system configuration:

   - ``OTRSCreditCardFilter::ActiveMaskEnabled``
   - ``OTRSCreditCardFilter::MaskedCharacter``

For example *1234-5678-9012-3456* becomes *1234-56xx-xxxx-3456*.

.. warning::

   This procedure is permanent and irreversible!

To use this feature:

1. Create a ticket with the following article body:

   .. code-block:: none

      Issuing Network,Card Number
      JCB 15 digit,180061388939823
      JCB 15 digit,180079668437698
      JCB 15 digit,180001434886883
      JCB 15 digit,180044208063503
      JCB 15 digit,180010497338476
      JCB 15 digit,210004248524033
      JCB 15 digit,210012319871803
      JCB 15 digit,180094846333594
      JCB 15 digit,210084424984649
      JCB 15 digit,210012951351973
      JCB 15 digit,210008094074787
      JCB 15 digit,210081171733450

2. Open the *Ticket Zoom* screen to see the created ticket. The body of the article will shown as:

   .. code-block:: none

      Issuing Network,Card Number
      JCB 15 digit,180061xxxxx9823
      JCB 15 digit,180079xxxxx7698
      JCB 15 digit,180001xxxxx6883
      JCB 15 digit,180044xxxxx3503
      JCB 15 digit,180010xxxxx8476
      JCB 15 digit,210004xxxxx4033
      JCB 15 digit,210012xxxxx1803
      JCB 15 digit,180094xxxxx3594
      JCB 15 digit,210084xxxxx4649
      JCB 15 digit,210012xxxxx1973
      JCB 15 digit,210008xxxxx4787
      JCB 15 digit,210081xxxxx3450

3. You can also try with valid credit card numbers in the subject or fetch a mail with valid credit card information using a postmaster account.


Credit Card Warning Message
---------------------------

1. Make sure that setting ``OTRSCreditCardFilter::ActiveMaskEnabled`` is not enabled.
2. Make sure that setting ``OTRSCreditCardFilter::WarningTextEnabled`` is enabled.
3. Define your custom message in setting ``OTRSCreditCardFilter::WarningText`` in the system configuration.
4. Create a ticket with the following article body:

   .. code-block:: none

      Issuing Network,Card Number
      JCB,3528988095245935
      JCB,3112606824580636
      JCB,3096030869937728
      JCB,3112437499296450
      JCB,3096010732100407
      JCB,3528461498782367
      JCB,3112892137191440
      JCB,3088814635323630

5. Open the *Ticket Zoom* screen. The warning message should appear next to the credit card number.

   .. code-block:: none

      Issuing Network,Card Number
      JCB,3528988095245935 Reminder: You should not store credit card numbers in this product!
      JCB,3112606824580636 Reminder: You should not store credit card numbers in this product!
      JCB,3096030869937728 Reminder: You should not store credit card numbers in this product!
      JCB,3112437499296450 Reminder: You should not store credit card numbers in this product!
      JCB,3096010732100407 Reminder: You should not store credit card numbers in this product!
      JCB,3528461498782367 Reminder: You should not store credit card numbers in this product!
      JCB,3112892137191440 Reminder: You should not store credit card numbers in this product!
      JCB,3088814635323630 Reminder: You should not store credit card numbers in this product!

You can also try with valid credit card numbers in the subject or fetch a mail with valid credit card information using a postmaster account.
