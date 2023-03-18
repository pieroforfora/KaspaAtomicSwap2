# kaspaatomicswap

please donate:

**kaspa:qq4ecuffdwner5kd3gucgt5zhe4wq69crj4shdk32smva6vcj4nsqhl8rj3dx**

really,

please donate:

**kaspa:qq4ecuffdwner5kd3gucgt5zhe4wq69crj4shdk32smva6vcj4nsqhl8rj3dx**


something is working.


This is a work in progress, not really usable, please read and understand the code. 


to have this working you have to use 
https://github.com/someone235/kaspad/tree/fix-ExtractAtomicSwapDataPushes
branch


download it locally and use replace method in the go.mod file


```
Usage: kaspaatomicswap [flags] cmd [cmd args]


Commands:

  initiate <participant address> <amount>

  participate <initiator address> <amount> <secret hash>

  redeem <contract> <contract transaction> <secret>

  refund <contract> <contract transaction>

  extractsecret <redemption transaction> <secret hash>

  auditcontract <contract> <contract transaction>

  auditcontractonline <contract> <contract transaction>

  daemon

  pushtx <tx>


Flags:

  -devnet

    	use devnet network

  -kaspad string

    	host[:port] of kaspad RPC server (default "localhost:16610")

  -kaspawallet string

    	host[:port] of kaspawallet  RPC server (default "localhost:8082")

  -ltInitiate int

    	min initiate locktime in hours  (default 48)

  -ltPartecipate int

    	min partecipate locktime in hours (default 24)

  -secretSize int

    	min partecipate locktime in hours (default 32)

  -testnet

    	use testnet network

  -verbose

    	verbose

```




start daemon:

**go run main.go -devnet daemon**

usage examples:

**initiate**

curl -X POST localhost:8080/initiate    -H 'Content-Type: application/json'    -d '{"RecipientAddress":"kaspadev:qzn2lc5y930aq0wtz44ptclxl3duypp4282u00upsefewvuapy97sntz038xe","Amount":"1"}'


{"Secret":"30774f7a21c3825cbd6ffab1e2176598abc0e59c4802e70c5f9e7960af640908","SecretHash":"94a3b3eff91d5eff58eb7135a9606e4297cac180d183da823c9d245dd1aa4867","Contract":"6382012088a82094a3b3eff91d5eff58eb7135a9606e4297cac180d183da823c9d245dd1aa48678876aa20e8fbe1a1b4043dc4706a813b5ff9a8c0bcf1dc4baca3ee8868f5444588af073d670608cfe5658601b076aa20e2fa7101f2bcf2f2e02727ac003676f7925151df9c62c647b5a0e6d72f111e876888ac","ContractTransactionID":"","ContractTransaction":"126e0a260a220a2017d42090590c3f6c7621395db86ab323a0158fe48cde0d1b6a93268dbd61c87410011242417fc6dd2dacd77a9b1e0ac3392f7420e55355b667831c7e4158a63f6bfbe8182b7bd41d759f85a98956819fe8615765336a6b88e1e98b1535bcc796c203c98f040120011a2c0880c2d72f12250a23aa2063efa56a29ddfffbdeee5417ea89e5ccda35350bc1580824c273846c232429cb871a2d08a0d192f2b90112240a22208176445904cf3ed5ecc514c585c61d88e65f6a34886ba8edb4ff2dd26c0f57c2ac2a160a140000000000000000000000000000000000000000","TransactionFee":"60000"}



**partecipate**

curl -X POST localhost:8080/partecipate    -H 'Content-Type: application/json'    -d '{"RecipientAddress":"kaspadev:qzn2lc5y930aq0wtz44ptclxl3duypp4282u00upsefewvuapy97sntz038xe","Amount":"1","SecretHash":"94a3b3eff91d5eff58eb7135a9606e4297cac180d183da823c9d245dd1aa4867"}'


{"Secret":"","SecretHash":"94a3b3eff91d5eff58eb7135a9606e4297cac180d183da823c9d245dd1aa4867","Contract":"6382012088a82094a3b3eff91d5eff58eb7135a9606e4297cac180d183da823c9d245dd1aa48678876aa20e8fbe1a1b4043dc4706a813b5ff9a8c0bcf1dc4baca3ee8868f5444588af073d670680bbe5658601b076aa20362409d3da2c369b5fa44b7c3bd353432b019846ae9a1b3dd1a160d4a5b253376888ac","ContractTransactionID":"","ContractTransaction":"126c0a240a220a20706da79faac561251802febe0cb02023bfb49d1a643c5f6ddd308b95e2258c1a124241e1276ed8c12d744d84089ef4f99493c1ba6971fb5e096b5617702630e5480b2f10eb2e0e956ca761412885dc1ff29080641979a3759a4f826a340317ee1d49a00120011a2c0880c2d72f12250a23aa20d84d73f736831fa29a9cd274f7ef2011c832b385fe61325ea665b3054c0e998f871a2d08a0d192f2b90112240a222073035b16c4a77c6859ccdfd09d4e024b7e17590fd8a3b5b30afbd5a2255feea3ac2a160a140000000000000000000000000000000000000000","TransactionFee":"60000"}



**redeem**

curl -X POST localhost:8080/redeem    -H 'Content-Type: application/json'    -d '{"Contract":"6382012088a82094a3b3eff91d5eff58eb7135a9606e4297cac180d183da823c9d245dd1aa48678876aa20e8fbe1a1b4043dc4706a813b5ff9a8c0bcf1dc4baca3ee8868f5444588af073d670680bbe5658601b076aa20362409d3da2c369b5fa44b7c3bd353432b019846ae9a1b3dd1a160d4a5b253376888ac","ContractTransaction":"126c0a240a220a20706da79faac561251802febe0cb02023bfb49d1a643c5f6ddd308b95e2258c1a124241e1276ed8c12d744d84089ef4f99493c1ba6971fb5e096b5617702630e5480b2f10eb2e0e956ca761412885dc1ff29080641979a3759a4f826a340317ee1d49a00120011a2c0880c2d72f12250a23aa20d84d73f736831fa29a9cd274f7ef2011c832b385fe61325ea665b3054c0e998f871a2d08a0d192f2b90112240a222073035b16c4a77c6859ccdfd09d4e024b7e17590fd8a3b5b30afbd5a2255feea3ac2a160a140000000000000000000000000000000000000000","Secret":"30774f7a21c3825cbd6ffab1e2176598abc0e59c4802e70c5f9e7960af640908"}'


{"SpendTransaction":"12ac020a240a220a207f766d1898b85cfc2a76b6a96a6e28a2bba2a9517b392d67f5eef9babf62682012810241a72a6be2a9a15a5b00caa59c7f8c3b0b7d39846fc5dd99fa6222f1ee49271e8d18622815fa040b026d8198911407048839cd3011b90baa3c18da0f7e27f0cf7e0120a6afe2842c5fd03dcb156a15e3e6fc5bc2043551d5c7bf81865397339d090be82030774f7a21c3825cbd6ffab1e2176598abc0e59c4802e70c5f9e7960af640908514c7a6382012088a82094a3b3eff91d5eff58eb7135a9606e4297cac180d183da823c9d245dd1aa48678876aa20e8fbe1a1b4043dc4706a813b5ff9a8c0bcf1dc4baca3ee8868f5444588af073d670680bbe5658601b076aa20362409d3da2c369b5fa44b7c3bd353432b019846ae9a1b3dd1a160d4a5b253376888ac20011a2b08a0edd32f12240a2220a6afe2842c5fd03dcb156a15e3e6fc5bc2043551d5c7bf81865397339d090be8ac2a160a140000000000000000000000000000000000000000","SpendTransactionID":"","TransactionFee":"60000"}



**refund**

curl -X POST localhost:8080/refund    -H 'Content-Type: application/json'    -d '{"Contract":"6382012088a82094a3b3eff91d5eff58eb7135a9606e4297cac180d183da823c9d245dd1aa48678876aa20e8fbe1a1b4043dc4706a813b5ff9a8c0bcf1dc4baca3ee8868f5444588af073d670680bbe5658601b076aa20362409d3da2c369b5fa44b7c3bd353432b019846ae9a1b3dd1a160d4a5b253376888ac","ContractTransaction":"126c0a240a220a20706da79faac561251802febe0cb02023bfb49d1a643c5f6ddd308b95e2258c1a124241e1276ed8c12d744d84089ef4f99493c1ba6971fb5e096b5617702630e5480b2f10eb2e0e956ca761412885dc1ff29080641979a3759a4f826a340317ee1d49a00120011a2c0880c2d72f12250a23aa20d84d73f736831fa29a9cd274f7ef2011c832b385fe61325ea665b3054c0e998f871a2d08a0d192f2b90112240a222073035b16c4a77c6859ccdfd09d4e024b7e17590fd8a3b5b30afbd5a2255feea3ac2a160a140000000000000000000000000000000000000000"}'


{"SpendTransaction":"128b020a240a220a207f766d1898b85cfc2a76b6a96a6e28a2bba2a9517b392d67f5eef9babf62682012e0014128485997542e9dad234fc07043ad77d719e49041de55bc05b8b9053055a13fb3f621e7c6e349092e386fce8f3cdfd673fa783a512267fc13043a8e49b35485d101205dd3355dcd78ba619ada8c8c1103065c4cda992e4e877a78e51dcea67f9f26ed004c7a6382012088a82094a3b3eff91d5eff58eb7135a9606e4297cac180d183da823c9d245dd1aa48678876aa20e8fbe1a1b4043dc4706a813b5ff9a8c0bcf1dc4baca3ee8868f5444588af073d670680bbe5658601b076aa20362409d3da2c369b5fa44b7c3bd353432b019846ae9a1b3dd1a160d4a5b253376888ac20011a2b08a0edd32f12240a22205dd3355dcd78ba619ada8c8c1103065c4cda992e4e877a78e51dcea67f9f26edac2080f796afe6302a160a140000000000000000000000000000000000000000","SpendTransactionID":"","TransactionFee":"60000"}


**extract-secret**

curl -X POST localhost:8080/extractsecret    -H 'Content-Type: application/json'    -d '{ "Transaction":"12ac020a240a220a207f766d1898b85cfc2a76b6a96a6e28a2bba2a9517b392d67f5eef9babf62682012810241a72a6be2a9a15a5b00caa59c7f8c3b0b7d39846fc5dd99fa6222f1ee49271e8d18622815fa040b026d8198911407048839cd3011b90baa3c18da0f7e27f0cf7e0120a6afe2842c5fd03dcb156a15e3e6fc5bc2043551d5c7bf81865397339d090be82030774f7a21c3825cbd6ffab1e2176598abc0e59c4802e70c5f9e7960af640908514c7a6382012088a82094a3b3eff91d5eff58eb7135a9606e4297cac180d183da823c9d245dd1aa48678876aa20e8fbe1a1b4043dc4706a813b5ff9a8c0bcf1dc4baca3ee8868f5444588af073d670680bbe5658601b076aa20362409d3da2c369b5fa44b7c3bd353432b019846ae9a1b3dd1a160d4a5b253376888ac20011a2b08a0edd32f12240a2220a6afe2842c5fd03dcb156a15e3e6fc5bc2043551d5c7bf81865397339d090be8ac2a160a140000000000000000000000000000000000000000","SecretHash":"94a3b3eff91d5eff58eb7135a9606e4297cac180d183da823c9d245dd1aa4867"}'


{"Secret":"30774f7a21c3825cbd6ffab1e2176598abc0e59c4802e70c5f9e7960af640908"}



**audit**

curl -X POST localhost:8080/auditcontract    -H 'Content-Type: application/json'    -d '{"Contract":"6382012088a820e24e1fd112d0c6389119aa37db7ef8ed1cd89e6a840a75bb706be11efe725c668876aa20e8fbe1a1b4043dc4706a813b5ff9a8c0bcf1dc4baca3ee8868f5444588af073d6706c04c14708601b076aa20deae4af6fb570cec9b8a927b7cbb5422f823ed89f3b1406fe605d1ef3efc6d5d6888ac",
"ContractTx":"126c0a240a220a2046deb970b220b9fe04c72006842dea3921b7d6927e0bb85de8758e44715df278124241a9069fd3082be638c648ef8c02c1a318538389bb4af80b4b5e85897c0c39b71c89ee1fd43def9b538c5b6b7819c3f4032c50421fde2f4c20f4479eeaa46717ee0120011a2c0880c2d72f12250a23aa20308effdff6521e67bbec4c0f4000c61298b08cdff249da769c52149e54fad606871a2d08a0d192f2b90112240a22205235d974492df699906928067145bcf8624716820c8e163df41874dfef51d32eac2a160a140000000000000000000000000000000000000000"}'


{"ContractAddress":"kaspadev:pqcgal7l7efpueama3xq7sqqccff3vyvmleynknkn3fpf8j5lttqvunlnks6h","RecipientAddress":"0xc0000728f0","RecipientBlake2b":"e8fbe1a1b4043dc4706a813b5ff9a8c0bcf1dc4baca3ee8868f5444588af073d","ContractAmount":"100000000","RefundAddress":"0xc000374e50","RefundBlake2b":"deae4af6fb570cec9b8a927b7cbb5422f823ed89f3b1406fe605d1ef3efc6d5d","SecretHash":"e24e1fd112d0c6389119aa37db7ef8ed1cd89e6a840a75bb706be11efe725c66","LockTime":"1676917624000","TxId":"62616432653966303836303162363033366436306137396534346230336239643734363065333863333063356139373331613434343861393963353739353264","DaaScore":"42780","VSPBS":"42813","IsSpendable":"true"}


**pushtx**

curl -X POST localhost:8080/pushtx    -H 'Content-Type: application/json'    -d '{"Tx":"126c0a240a220a20dfb9c6da21dbf6699b8d2dfa16ce9918eb9906af4fe6b27f45ac712b6b88b0d4124241a9b64a89a32f34b3abfb558318f175fcf8a865d270bde03c427f41397bf687c2230bd48a573c45629878d5f036be7070ad5c5a4a5a62bdb0b3082ad5dee6ee640120011a2c0880c2d72f12250a23aa20a5161cf3332c61423b5568ce5ab50c9fce5b304b709977395f6bab237d23d65e871a2d08a0d192f2b90112240a2220f31c38ca0a5d6631756ef7a5fc6d345062480e55d27d579b770aacc575dcdf04ac2a160a140000000000000000000000000000000000000000"}'


{"TxId":"599e07d44b417170372ec9dd2868ff1dfc5c4ec7a924f96dd1b2ccfac8b4c387"}


