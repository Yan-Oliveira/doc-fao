Administrator Interface
=======================

This package has no administrator interface.


Legacy Credit Card Masking
--------------------------

A console command exists to treat already stored credit card numbers in the system. This command will mask any unmasked valid credit card number in the article database table.

To mask the existing credit card numbers:

1. Make sure that setting ``OTRSCreditCardFilter::ActiveMaskEnabled`` is not enabled.
2. Create one or more tickets with valid credit card information.

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

3. Open the *Ticket Zoom* screen to make sure that the credit card numbers are not masked.
4. Execute the following command in the command line to mask the credit card numbers:

   .. code-block:: bash

      otrs> /opt/otrs/bin/otrs.Console.pl Maint::Ticket::MaskCreditCard --restart yes

5. Refresh the *Ticket Zoom* screen. The article the body will shown as:

   .. code-block:: none

      Issuing Network,Card Number
      JCB,352898xxxxxx5935
      JCB,311260xxxxxx0636
      JCB,309603xxxxxx7728
      JCB,311243xxxxxx6450
      JCB,309601xxxxxx0407
      JCB,352846xxxxxx2367
      JCB,311289xxxxxx1440
      JCB,308881xxxxxx3630

This script starts masking the credit card numbers on last articles first, since they are the most common used, so the results can be seen faster.

.. seealso::

   For more information about the ``Maint::Ticket::MaskCreditCard`` parameters, execute the following command:

   .. code-block:: bash

      otrs> /opt/otrs/bin/otrs.Console.pl Maint::Ticket::MaskCreditCard --help

The architecture of this script is designed to avoid affecting the system performance by working in batches and waiting between each batch. The number of processed articles per batch and the wait time between batches can be fine tuned to match system performance.

The script is also designed to remember last processed article and start again from that, allowing to stop the process at a certain time and resume later. There is an override to force starting again from the beginning.

You could specify an end date so only articles until that date will be processed (e.g. if you started automatic masking at a certain date), also it is possible to specify the number of articles to process per run.
