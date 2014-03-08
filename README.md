GPUCoin
================================

http://www.gpucoin.net

Copyright (c) 2009-2013 Bitcoin Developers

Copyright (c) 2014 GPUCoin Developers

Proof-of-work algorithm:
 - Symbol: GPUC
 - Scrypt: Nfactor, N starting at 2048)
 - Maxcoins: 13,500,000,000
 - Premine: 400,000,000
 - 1 minute block targets
 - Subsidy initial reward: 20,000
  - block 0-200 : 0 reward
  - block 200-720: 1 reward (+1 day ahead of mining launch)
 - Subsidy halves in 250,000 blocks (roughly 173 days, or 1/2 a year)
   - halving happens 4 times
   - this means 1-250000 + startoffset = 20000 reward
     - 250k-500k = 10000 reward
     - 500k-750k = 5000 reward
     - 750-1m = 2500 reward
     - 1m + = 1250 reward    
 - Confirmation needed: 12 (due to 1 min blocks)
 - COINBASE_Maturity: 100
 - KGW implementation
 
 - everything else: pretty much litecoin coin and paste.
 
 
default Port 8623  / 18623 for test net
default RPC port 8622 


Development plan
-------

Coding:
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
  - (done) nfactor schedule

Internal Testing:  
  - testing phase on intranet using linux CLI daemon
    - (done) test client mining (cpu)
    - (done) test rewards    
    - (done) test send/receive    
    - (done) test GPU mining - solo 
    - (done)test KGW              
         
Final Modifications:
  - (done) Get PNG logo & graphics from GPUC, and populate QT folder
  - (done) Change address prefix from S to G
  - (done) Add launch Seed nodes to DNSseed main.cpp hard code
  - (done) Fix windows build on makefile 
  - (done) Build windows_alpha client
  - (done) Test windows alpha client,     
  - (done) <push to github as code complete ahead of real deployment>  
  - (in progress : cryptowest team reviewing) get code reviews  
  - (done) test send on test network.

Real Genesis blocks, and fork prevention:  
 - (done)Update to launch pszTimestamp
 - (done)Update to launch nTime to curent POSIX time 
 - (done)Create *real* genesis hash, merkle root, and get nonce
 - (done)Mine to 179 blocks
 - (done)Get checkpoints, and update checkpoints.cpp
 - (done) Settle on final node IP address hardcodes, and any changes to DNS seed host addresses
 
Deployment:   
 - (done) Build Final Windows 
 - Build OSX client
 - (done) Deploy on VPS behind firewall: DNSSeed, and Seed node
 - (done) Setup IP tables, etc.

Final Test: 
 - (done) Test Run DNSseed and make sure it can ping seed nodes, and shows as available 
 - (done) Test that DNS seed is working using nslookup
 - (done) Test Final windows build can connect immediately from fresh start (no previous blockdb)
 - (done) Test Final windows build sends / receive coins working 
 - (done) Test GPU mining against "real" network for blocks 200-210 (reward=1)
 - (done) Send private build to GPUC
 - (done) Send 400M premine coins to GPUC's wallet
 
Final Launch: 
 - AI: GPUC - he has client now - Upload windows build to mega, 
 - Push code post launch code to github 
 - "Launch Post"


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

