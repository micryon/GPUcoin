GPUCoin
================================

http://www.gpucoin.net

Copyright (c) 2009-2013 Bitcoin Developers

Copyright (c) 2014 GPUCoin Developers

Proof-of-work algorithm:
 - Symbol: GPUC
 - Scrypt (w/Nfactor schedule: TBD)
 - Maxcoins: 13,500,000,000
 - Premine: 400,000,000
 - 1 minute block targets
 - Subsidy halves in 250,000 blocks (roughly 173 days, or 1/2 a year)
   - halving happens 4 times
 - Subsidy initial reward: 20,000
  - block 0-200 : 0 reward
  - block 200-720: 1 reward (+1 day ahead of mining launch) 
 - Confirmation needed ?
 - KGW implementation
 
default Port 8623  / 18623 for test net
default RPC port 8622 


Development plan
-------

  - (done) Temporarily remove checkpoints 
  - (done) Change ports
  - (done) Update GPUcoin_seeder with ports.
  - (done) All name changes, and symbol changes: GPUC
  - (done) Change max coins amount, and original COIN amount
  - (done) Change KGW retarget time
  
  - (done) Add in DNSSeed address, and hardcoded 3 node seed addresses, 3 data center VPSes: 2 in US, and 1 in canada
  - (done) Revert fix micro, milli units (this was changed before to avoid integer overflows for 100B+coins)
  - (done) Update subsidy schedule
  
    - (done) change confirmations needed to account for 60second blocktimes changed to 12
  - nfactor schedule
  - Add in graphics


  - Build windows_alpha client
  *Deploy alpha test client on VPS
  - <push to github as code complete ahead of deployment>

Behind firewall:
  
  - temp change Pow to smallest possible, temp change nfactor/block schedules
  - Mine to block 10000, remove temp changes
  
  - create *real* genesis hash, and real starttime stamp
  - reset everything.  
  - Update merkle hash root
  - Mine up to block 200
  
  - Build windows and OSX client release
  
  - push to github on launchday


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
    ./GPUcoin-qt_test

