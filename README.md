The Real StackCoin
================================

http://www.realstackcoin.org (tbd)

Copyright (c) 2009-2013 Bitcoin Developers

Copyright (c) 2013-2014 RonPaulCoin Developers (colinistheman,onaboat,Tranz,Dajackal)

Copyright (c) 2014 RealStackCoin Developers

-- community built from the ground up --

Wof-work algorithm:
 - Scrypt
 - Maxcoins: 134.4 billion
 - Premine: <to figure out>
 - 2.0 minute block targets
 - subsidy halves in N (~21k blocks) blocks (~every month )
 - 1 000 000 coin per block
 - KGW implementation


Testing
-------

Testing and code review is the bottleneck for development; we get more pull
requests than we can review and test. Please be patient and help out, and
remember this is a security-critical project where any mistake might cost people
lots of money.

### Automated Testing

Developers are strongly encouraged to write unit tests for new code, and to
submit new unit tests for old code.

Unit tests for the core code are in `src/test/`. To compile and run them:

    cd src; make -f makefile.unix test

Unit tests for the GUI code are in `src/qt/test/`. To compile and run them:

    qmake BITCOIN_QT_TEST=1 -o Makefile.test bitcoin-qt.pro
    make -f Makefile.test
    ./ronpaulcoin-qt_test

