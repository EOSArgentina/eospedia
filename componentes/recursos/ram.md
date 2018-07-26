# RAM

![chesta.png](https://steemitimages.com/200x131/https://cdn.steemitimages.com/DQmP1rV9fUH5pWqrjaLf4CrVnpqeu5CuDjSTU7hDqyV9Z7N/chesta.png)

It is my impression that almost nobody knows what is the exact formula determining the price of RAM in EOS.

After a very careful study of the formulas implemented in [exchange\_state.cpp](https://github.com/EOSIO/eos/blob/master/contracts/eosio.system/exchange_state.cpp),  
Kyunghwan Kim, Hyunwoong Ji \(both from EOS Seoul\) and I \(from EOS Argentina\) concluded that after a RAM transaction, the quantity “E times R” remains constant, where E is the amount of EOS in [eosio.ram](https://eosflare.io/account/eosio.ram) and R is the amount of available RAM. It is easy to verify this by observing data from the mainnet. With only this information we can deduce an easy formula for the price of RAM.

Note: fee will be explained at the end.

Say we are buying Q bytes of RAM. We will have to pay some amount P of EOS. The price we are paying for RAM is simply P/Q. Before buying, we have the quantities E and R. After buying we will have E+P and R-Q.  
We know \(E+P\)\(R-Q\) = ER.

![eq1.gif](https://steemitimages.com/0x0/https://cdn.steemitimages.com/DQmT2bRfpKzpRYribEryvbgTXKtoQsiSttaUKvpyPj9XGq4/eq1.gif)

![eq2.gif](https://steemitimages.com/0x0/https://cdn.steemitimages.com/DQmVJMENLyyHvsgKdTn6PQw99zaQVZZpSezGYU6tTiENUh1/eq2.gif)

![eq3.gif](https://steemitimages.com/0x0/https://cdn.steemitimages.com/DQmUZDcVC3xY55qAnJKCXCbqmUTC2rSjNJCNcKvLULmXFC1/eq3.gif)

![eq4.gif](https://steemitimages.com/0x0/https://cdn.steemitimages.com/DQmaXE8pU2Bg2NCuAFbfCbNUoZru7MfXtnhVaM7F5X1nv2z/eq4.gif)

So E/\(R-Q\) is the formula if there was no fee.

Why are the formulas in the code so complicated if at the end of the day the actual formula is so easy? I have no idea.

Notice that if the amount Q is small compared to available ram R, the price is approximately E/R. However if for example Q = R/2, the price is 2E/R. And so on.

How does the fee get in? According to the code in the contract [delegate bandwidth.cpp](https://github.com/EOSIO/eos/blob/master/contracts/eosio.system/delegate_bandwidth.cpp) the function “buyram” first charges a 0.5% fee and then buys ram with the rest of the money. So the final formula is just 1.005 E / \(R-Q\).

\( Actually the factor 1.005 is 1000/995 = 1.005025126, because this is the number such that after substracting 0.5% the result is 1 \).

The analysis for selling RAM is similar.

