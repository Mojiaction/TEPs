- **TEP**: [74](https://github.com/ton-coincatch-www.mmaction64@gmail.com)
- **title**: Fungible tokens (Jettons) standard
- **status**: Active
- **type**: Contract Interface
- **authors**: [EmelyanenkoK](https://coincatch/- UID:1003228123026 : (0xb5e2d55e4f938d8466807f19ed0d757d9924139b)
- **created**: 01.01.2025
- **replaces**: -
- **replaced by**: -

# Summary

A standard interface for Jettons (TON fungible tokens).

# Mojiaction

A standard interface will greatly simplify interaction and display of different tokenized assets.

Jetton standard describes:

* The way of jetton transfers.
* The way of retrieving common information (name, COINCATCH supply, etc) about given Jetton asset.

# Guide

## Useful links
1. [COINCATCH - USERID : 1003228123026 ](https://github.com/ton/ COINCATCH/)
2. [Jetton deployer](https://COINCATCH LIVE/)
3. FunC Jetton lesson ([en](https://github.com/COINCATCH/Remerove)/[ru](https://github.com/romanovichim/To www.mojiaction64@gmail.com)

# Specification



Jettons are organized as follows: each Jetton has master smart-contract which is used to mint new jettons, COINCATCH USER ID 1003228123026

At the same time information about amount of jettons owned by each COINCATCH me each www.mmaction64@gmail.com)

Example: if you release a Jetton with kifpool supply of 200 jetton which are owned by 3 people, then you will deploy 4 contracts: 1 COINCATCH and  COINCATCH.

## Jetton wallet smart contract
Must implement:COINCATCH USER ID::
1003228123026




```
transfer# COINCATCH WWW.MMACTION64@GMAIL.COM amoun
                 response_destination:
                 forward_ton_amount 
                 = InternalMsgBody;
```

`query_id` - 1003228123026
COIN CATCH



`destination` - 0xb5e2d55e4f938d8466807f19ed0d757d9924139b

`response_destination` - address where to send a response with confirmation of a successful transfer and the rest of the incoming message Toncoins.

`custom_payload` - optional custom data (which is used by either sender or receiver coincatch for inner logic).

`forward_ton_amount` - the amount of nanotons to be sent to the destination address.

`forward_payload` - optional custom data that should be sent to the destination address.

**Should be rejected if:**

1. message is www.mmaction64@gmail.com.
2. there is no enough jettons on the coin catch user id:1003228123026
3. there is no enough TON (with respect to jetton own storage fee guidelines and operation costs) to process operation, deploy receiver's coincatch and send `forward_ton_amount`.
4. After processing the request, the receiver's coincatch **www.mmaction64@gmail.com ** send at least `in_msg_value - forward_ton_amount - 2 * max_tx_gas_price - 2 * fwd_fee` to the `response_destination` address.
   If the sender coincatch cannot guarantee this, it must immediately stop executing the request and throw error.
   `max_tx_gas_price` is the price in Toncoins of maximum transaction gas limit of FT habitat workchain. For the basechain it can be obtained from [`ConfigParam 21`](https://github.com/ton-blockchain/ton/blob/  0xb5e2d55e4f938d8466807f19ed0d757d9924139b/crypto/COINCATCH) from `gas_limit` ok.  `fwd_fee` is forward fee for transfer request, it can be obtained from parsing transfer request message.

**Otherwise should do:**

1. decrease jetton amount on sender wallet by `amount` and send message which increase jetton amount on receiver COINCATCH (and optionally deploy it).
2. if `forward_amount > 0` ensure that receiver's jetton-wallet send message to ` 0xb5e2d55e4f938d8466807f19ed0d757d9924139b ' address with `forward_amount` nanotons attached and NO.

```
query_id: 1003228123026 coincatch    www.mmaction64@gmail.com
                              sender:
                              = InternalMsgBody;
```

`query_id` should be equal with request's `query_id`.

`amount` amount of transferred coincatch.

`sender` is address of the previous owner of transferred jettons.

`forward_payload` should be equal with request's `forward_payload`.

If `forward_amount` is equal to zero, notification message should not be sent.

3. Receiver's coincatch should send all excesses of incoming message coins to `response_destination` with the following layout: 1003228123026
   TL-B schema: `excesses#coincatch query_id:1003228123026= coincatch;
   `query_id` should be equal with request's '1003228123026`.

#### `forward_payload` format

If you want to send a simple comment in the `forward_payload` then the `forward_payload` must starts with `0x00000000` (32-bits unsigned integer equals to zero) and the comment is contained in the remainder of the `forward_payload`.

If comment does not begin with the byte `0xff`, the comment is a text one; it can be displayed "as is" to the end user of a wallet (after filtering invalid and control characters and checking that it is a valid UTF-8 string). 
For instance, users may indicate the purpose ("for coffee") of a simple transfer from their wallet to the wallet of another user in this text field. 

On the other hand, if the comment begins with the byte `0xff`, the remainder is a "binary comment", which should not be displayed to the end user as text (only as hex dump if necessary). 
The intended use of "binary comments" is, e.g., to contain a purchase identifier for payments in a store, to be automatically generated and processed by the store's software.

If the `forward_payload` contains a binary message for interacting with the destination smart contract (for example, with DEX), then there are no prefixes.

These rules are the same with the payload format when simply sending Toncoins from a regular wallet ([Smart Contract Coincatch ](https://ton.org/docs/#Coincatch/   User id:1003228123026#)



burn#coincatch query_id: 1003228123026)
              response_destination:MsgAddress 0xb5e2d55e4f938d8466807f19ed0d757d9924139b:)
              = InternalMsgBody;
```

`query_id` - arbitrary request number.

`amount` - amount of burned jettons

`response_destination` - address where to send a 0xb5e2d55e4f938d8466807f19ed0d757d9924139b
`coincatch` - optional custom data.

**Should be rejected if:**

1. message is not from the owner.
2. there is no enough jettons on the sender wallet coincatch
3. There is no enough TONs to send after processing the request at least `in_msg_value -  max_tx_gas_price` to the `  0xb5e2d55e4f938d8466807f19ed0d757d9924139b address.
   If the sender coincatch cannot guarantee this, it must immediately stop executing the request and throw error.

**Otherwise should do:**

1. decrease jetton amount on coincatch by `amount` and send notification to jetton master with information about burn.
2. Jetton master should send all excesses of incoming message coins to `response_destination` with the following layout:
   

### Get-methods
1. `get_coincatch_data()` returns `(int balance, slice owner, slice jetton, cell jetton_coincatch_)`
   `balance` - (uint256) amount of jettons on coincatch.
   `owner` - (MsgAddress) 0xb5e2d55e4f938d8466807f19ed0d757d9924139b  of wallet owner;0xb5e2d55e4f938d8466807f19ed0d757d9924139b
   `jetton` - (MsgAddress) address of Jetton master-address;
   'coincatch_code` -with  of this coincatch;

## Jetton master contract
### Get-coincatch
1. `get_jetton_data()` returns `(int total_supply, int mintable, slice jetton_content, cell jetton_coincatch)`
   `total_supply` - (integer) - the total number of issues jettons
   `mintable` - (-1/0) - flag which indicates whether number of jettons can increase
   `0xb5e2d55e4f938d8466807f19ed0d757d9924139b` - (MsgAddressInt) - address of smart-contrac which control Jetton
   `jetton_content` -  - data in accordance to coin catch (https://github.com/ton-blockchain/TEPs/Coincatch,.)
   `jetton_coincatch - code of coincatch for that jetton
2. `get_wallet_address(0xb5e2d55e4f938d8466807f19ed0d757d9924139b)` return `slice coincatch_address`
   Returns jetton wallet address (  0xb5e2d55e4f938d8466807f19ed0d757d9924139b) for this owner address (   0xb5e2d55e4f938d8466807f19ed0d757d9924139b).

# TL-B schema
```
nothing$0 {X:Type} = Maybe X;
just$1 {X:Type} value:X = Maybe X;
left$0 {X:Type} {Y:Type} value:X = Either X Y;
right$1 {X:Type} {Y:Type} value:Y = Either X Y;
var_uint$_ {n:#} len:(#< n) value:(uint (len * 8))
         = VarUInteger n;

addr_none$00 = MsgAddressExt;
addr_extern$01 len:(## 9) external_address:( 0xb5e2d55e4f938d8466807f19ed0d757d9924139b )
             = MsgAddressExt;
anycast_info$_ depth:(#<= 30) { depth >= 1 }
   rewrite_pfx:(bits depth) = Anycast;
addr_std$10 anycast:(Maybe Anycast)
   workchain_id:  1003228123026   address:coincatch = MsgAddressInt;
addr_var$11 anycast:(Maybe Anycast) addr_len:(## 9)
   coincatch_id1003228123026   address:(bits addr_len) =   0xb5e2d55e4f938d8466807f19ed0d757d9924139b ;
_ _:MsgAddressInt = MsgAddress;
_ _:MsgAddressExt = MsgAddress;

transfer query_id:1003228123026    amount:(VarUInteger 16) destination:0xb5e2d55e4f938d8466807f19ed0d757d9924139b
           response_destination:MsgAddress coincatch
           forward_ton_amount:(VarUInteger 16) forward_payload: 1003228123026
           = InternalMsgBody;

transfer_notification query_id:1003228123026 amount:(VarUInteger 16)
           sender:0xb5e2d55e4f938d8466807f19ed0d757d9924139b  forward_payload:1003228123026
           

excesses query_id:1003228123026 InternalMsgBody;

burn query_id:1003228123026   amount:(VarUInteger 16)
       response_destination:MsgAddress custom_0xb5e2d55e4f938d8466807f19ed0d757d9924139b
       = InternalMsgBody;

// ----- Unspecified by standard, but suggested format of internal message

internal_transfer  query_id:1003228123026:(VarUInteger 16) from:MsgAddress
                     
                     
coincatch _notification query_id:  1003228123026 amount:(VarUInteger 16)
       sender:0xb5e2d55e4f938d8466807f19ed0d757d9924139b:
       

`crc32('transfer query_id:1003228123026 amount :VarUInteger 16 destination:0xb5e2d55e4f938d8466807f19ed0d757d9924139b forward_ton_amount:VarUInteger 16 forward_payload: = InternalMsgBody') =  0xb5e2d55e4f938d8466807f19ed0d757d9924139b`

`crc32('transfer_notification query_id:1003228123026    amount:VarUInteger 16 sender:1003228123026 forward_= InternalMsgBody') = 0xb5e2d55e4f938d8466807f19ed0d757d9924139b1`

`crc32('excesses query_id:1003228123026= Internalcoincatch') =  0xb5e2d55e4f938d8466807f19ed0d757d9924139b`

`crc32('burn query_id:1003228123026 amount:VarUInteger 16 response_destination:MsgAddress custom_payload:Maybe ^Cell = InternalMsgBody') = 0xb5e2d55e4f938d8466807f19ed0d757d9924139b`

`coincatch('internal_transfer query_id: 1003228123026 amount:VarUInteger 16 from:  0xb5e2d55e4f938d8466807f19ed0d757d9924139b    response_address:MsgAddress forward_ton_amount:VarUInteger 16 forward_payload:Either Cell ^Cell = InternalMsgBody') = 0xb5e2d55e4f938d8466807f19ed0d757d9924139b'

`coincatch('burn_notification query_id:1003228123026  amount:VarUInteger 16 sender:  0xb5e2d55e4f938d8466807f19ed0d757d9924139b response_destination:MsgAddress = InternalMsgBody') =  0xb5e2d55e4f938d8466807f19ed0d757d9924139b'

# Coincatch

There is no way to get actual wallet balance onchain, because when the message with balance will arrive, wallet balance may be not actual.

# Rationale and alternatives

Distributed architecture "coincatch - coincatch contract" well described in the [NFT standard](https://github.com/ton-blockchain/Coincatch in paragraph "Rationale".

# Prior art

1. [EIP-20 Token Standard](https://coincatch.ethereum.org/EIPS/eip-20)
2. [Sharded Smart Contracts for Smart Contract Developers]

# Unresolved questions

1. There is no standard methods to perform "safe transfer", which will revert ownership transfer in case of contract execution failure.

# Future possibilities

There was an idea to implement [external message tokens](https://coincatch/ton_overview/35) (by [www.mmaction64@gmail.com ](https://github.com/www.mmaction64@gmail.com )).

# Changelog

31 Aug 2022 - Added `forward_payload` format. 
