## Data Objects ภายใต้ the Root ใน QR Code

| Name | ID | Format | Length | Presence | Comment |
|------|----|--------|--------|----------|---------|
| Payload Format Indicator | `"00"` | N | "02" | M | ดูต่อที่ - [Payload Format Indicator](https://github.com/chokchai9900/QR-payment-info/blob/master/README.md) |
| Point of Initiation Method | `"01"` | N | "02" | O | ดูต่อที่ - [Point of Initiation Method](https://github.com/chokchai9900/QR-payment-info/blob/master/README.md) |
| Visa Merchant Account Information | `"02"`-`"03"` | ans | var. up to "99" | O | Objects สงวนไว้เพื่อบริการของ Visa |
| MasterCard Merchant Account Information | `"04"`-`"05"` | ans | var. up to "99" | O | Objects สงวนไว้เพื่อบริการของ Mastercard |
| RFU for EMVCo | `"06"`-`"08"` | ans | var. up to "99" | O | Objects สงวนไว้เพื่อบริการของ EMVCo |
| Discover Merchant Account Information | `"09"`-`"10"` | ans | var. up to "99" | O | Objects สงวนไว้เพื่อบริการของ Discover |
| Amex Merchant Account Information | `"11"`-`"12"` | ans | var. up to "99" | O | Objects สงวนไว้เพื่อบริการของ Amex |
| JCB Merchant Account Information | `"13"`-`"14"` | ans | var. up to "99" | O | Objects สงวนไว้เพื่อบริการของ JCB |
| UnionPay Merchant Account Information | `"15"`-`"16"` | ans | var. up to "99" | O | Objects สงวนไว้เพื่อบริการของ UnionPay |
| RFU for EMVCo | `"17"`-`"25"` | ans | var. up to "99" | O | Objects สงวนไว้เพื่อบริการของ EMVCo |
| RFU for PPMI | `"26"` | ans | var. up to "99" | O | Objects สงวนไว้เพื่อบริการของ PPMI |
| P2P Merchant Account Information | `"27"` | ans | var. up to "99" | O | ดูข้อมูลต่อที่ - [Payment แบบ P2P]() |
| RFU for PPMI | `"28"`-`"51"` | ans | var. up to "99" | O | Objects สงวนไว้เพื่อบริการของ PPMI |
| Merchant Category Code | `"52"` | N | "04" | M | ใช้มาตรฐานของ ISO 18245 เป็นตัวกำหนด |
| Transaction Currency | `"53"` | N | "03" | M | ดูต่อที่ -[Transaction Currency](https://github.com/chokchai9900/QR-payment-info/blob/master/README.md) |
| Transaction Amount | `"54"` | ans | var. up to "13" | C | เป็นข้อมูลที่เอาไว้ระบุจำนวนเงินที่ต้องจ่าย ณ QR Code นั้นๆ |
| Tip or Convenience Indicator | `"55"` | N | "02" | O | เป็นข้อมูลที่ไว้จัดเก็บค่าทิป หรือ ค่าธรรมเนียม โดยจะมี ID ย่อย อีกคือ "01" สำหรับจำนวนทิป และ "02" สำหรับจำนวนค่าธรรมเนียม |
| Value of Convenience Fee Fixed | `"56"` | ans | var. up to "13" | C | เป็นข้อมูลสำหรับใส่ค่าธรรมเนียมแบบกำหนดตายตัว |
| Value of Convenience Fee Percentage | `"57"` | ans | var. up to "05" | C | เป็นข้อมูลสำหรับใส่ค่าธรรมเนียมแบบร้อยละ ( "%" ) |
| Country Code | `"58"` | ans | "02" | M |Country Code คือรหัสประจำปะเทศ โดยใช้ตัวอักษรสองตัว อ้างอิงตามมาตรฐาน ISO 3166-1 alpha 2 เช่น ของประเทศไทยคือ TH ID |
| Merchant Name | `"59"` | ans | var. up to "25" | M | คือชื่อของผู้ค่า เป็น Display name เพื่อแสดงให้ผู้จ่ายรู้ ว่า QR Code นี้ มาจากผู้ค่าชื่ออะไร |
| Merchant City | `"60"` | ans | var. up to "15" | M | คือชื่อเมืองของผู้ค้า หรือ เมืองที่ตั้งของร้านค้า เป็น Dispaly เช่นเดียวกันกับ Merchant name |
| Postal Code | `"61"` | ans | var. up to "10" | O | ถ้าในประเทศไทย นี่คือรหัสไปรษณีย์ สำหรับแต่ละประเทศนั้น ก็จะมีรหัส Postal Code ประจำเมืองต่างๆเช่นเดียวกัน หากมีค่านี้อยู่ อาจจะใช้เป็น Display postal code เพื่อแสดงให้ผู้จ่ายรู้ |
| Additional Data Field Template | `"62"` | S | var. up to "99" | O | ดูต่อที่ ตาราง Data Objects for Additional Data Field Template (ID `"62"`) |
| Merchant Information - Language Template | `"64"` | S | var. up to "99" | O | ดูต่อที่ ตาราง Data Objects for Merchant Information - Language Template (ID `"64"`) |
| RFU for EMVCo | `"65"`-`"79"` | S | var. up to "99" | O | Objects สงวนไว้เพื่อบริการของ EMVCo |
| BayadCenter Template | `"80"` | S | var. up to "99" | O | See section Data Objects for BayadCenter Template (ID `"80"`) |
| Unreserved Templates | `"81"`-`"99"` | S | var. up to "99" | O | RFU |
| CRC | `"63"` | ans | "04" | M | See section Requirements > CRC (ID `"63"`) |

## Data Objects for P2P Merchant Account Information (ID `"27"`)

| Name | ID | Format | Length | Presence | Comment |
|------|----|--------|--------|----------|---------|
| Globally Unique Identifier | `"00"` | ans | "12" | M | `"com.p2pqrpay"` |
| Acquirer ID | `"01"` | ans | "11" | M | As defined by [ISO 9362] and assigned by the Acquirer. `"PAPHPHM1XXX"` - PayMaya |
| Payment Type | `"02"` | ans | "8" | M | `"99964403"` – InstaPay Transfer |
| Merchant ID | `"03"` | ans | "15" | O | Receiver-assigned, if applicable, to authenticate the QR transaction. For P2P, this may be omitted. |
| Merchant Credit Account | `"04"` | ans | "19" | M | Creditor Account Number. _Note: This may be any Receiver-provided information that would enable it to identify the merchant account where payment shall be credited. Receiver may use actual account detail, a token, an alias or a masked/encrypted information to represent the actual account number_ |
| Mobile Number | `"05"` | ans | "15" | O | Mobile Number of Merchant as defined by [E.164]. May be used for notification. Format: +[country code][subscriber number] e.g. +639188450195|

## Data Objects for Additional Data Field Template (ID `"62"`)

| Name | ID | Format | Length | Presence | Comment |
|------|----|--------|--------|----------|---------|
| Bill Number | `"01"` | ans | var. up to "25" | O | The invoice number or bill number. This number could be provided by the merchant or could `"***"` to indicate to the mobile application to prompt the consumer to input a Bill Number. For example, the Bill Number may be present when the QR Code is used for a bill payment. |
| Mobile Number | `"02"` | ans | var. up to "25" | O | The mobile number could be provided by the merchant or could `"***"` to indicate to the mobile application to prompt the consumer to input a Mobile Number. For example, the Mobile Number to be used for multiple use cases, such as mobile top-up and bill payment. |
| Store Label | `"03"` | ans | var. up to "25" | O | A distinctive value associated to a store. This value could be provided by the merchant or could `"***"` to indicate to the mobile application to prompt the consumer to input a Store Label. For example, the Store Label may be displayed to the consumer on the mobile application identifying a specific store. |
| Loyalty Number | `"04"` | ans | var. up to "25" | O | Typically, a loyalty card number. This number could be provided by the merchant, if known, or could `"***"` to indicate to the mobile application to prompt the consumer to input their Loyalty Number. |
| Reference Label | `"05"` | ans | var. up to "25" | C | Any value as defined by the merchant or acquirer in order to identify the transaction. This value could be provided by the merchant or could `"***"` to indicate to the mobile app to prompt the consumer to input a transaction Reference Label. For example, the Reference Label may be used by the consumer mobile application for transaction logging or receipt display. |
| Customer Label | `"06"` | ans | var. up to "25" | O | Any value identifying a specific consumer. This value could be provided by the merchant (if known), or could `"***"` to indicate to the mobile application to prompt the consumer to input their Customer Label. For example, the Customer Label may be a subscriber ID for subscription services, a student enrollment number, etc. |
| Terminal Label | `"07"` | ans | var. up to "25" | C | A distinctive value associated to a terminal in the store. This value could be provided by the merchant or could `"***"` to indicate to the mobile application to prompt the consumer to input a Terminal Label. For example, the Terminal Label may be displayed to the consumer on the mobile application identifying a specific terminal. |
| Purpose of Transaction | `"08"` | ans | var. up to "25" | C | Any value defining the purpose of the transaction. This value could be provided by the merchant or could `"***"` to indicate to the mobile application to prompt the consumer to input a value describing the purpose of the transaction. For example, the Purpose of Transaction may have the value "International Data Package" for display on the mobile application. |
| Additional Customer Data Request | `"09"` | ans | var. up to "25" | O | Contains indications that the mobile application is to provide the requested information in order to complete the transaction. The information requested should be provided by the mobile application in the authorization without unnecessarily prompting the consumer. For example, the Additional Consumer Data Request may indicate that the consumer mobile number is required to complete the transaction, in which case the mobile application should be able to provide this number (that that mobile application has previously stored) without unnecessarily prompting the consumer. One or more of the following characters may appear to indicate that the corresponding data should be provided in the transaction initiation to complete the transaction: `"A"`: Address of the consumer, `"M"`: Mobile number of the consumer, `"E"`: Email address of the consumer. If more than one character is included, it means that each data object corresponding to the character is required to complete the transaction. Note that each unique character should appear only one. |
| RFU for EMVCo | `"10"`-`"49"` | S | var. up to "99" | O | Objects สงวนไว้เพื่อบริการของ EMVCo |
| Bill Details Template | `"50"` | S | var. up to "99" | O | See section Data Objects for Bill Details Template (ID `"62"` Sub-ID `"50"`) |
| RFU for PayMaya | `"51"`-`"99"` | S | var. up to "99" | O | Objects สงวนไว้เพื่อบริการของ PayMaya |

### Data Objects for Bill Details Template (ID `"62"` Sub-ID `"50"`)

| Name | ID | Format | Length | Presence | Comment |
|------|----|--------|--------|----------|---------|
| Globally Unique Identifier | `"00"` | ans | "20" | M | `"com.paymaya.billspay"` |
| Biller Slug | `"01"` | ans | var. up to "13" | M | PayMaya biller & service identifier. |

## Data Objects for Merchant Information - Language Template (ID `"64"`)

| Name | ID | Format | Length | Presence | Comment |
|------|----|--------|--------|----------|---------|
| Language Preference | `"00"` | ans | "02" | M | |
| Merchant Name - Alternate Language | `"01"` | S | var. up to "25" | M | May be used by a mobile application to present the Merchant Name in an alternate language |
| Merchant City - Alternate Language | `"02"` | S | var. up to "15" | O | May be used by a mobile application to present the Merchant Name in an alternate language | 
| RFU for EMVCo | `"03"`-`"99"` | S | var. up to "99" | O | Objects สงวนไว้เพื่อบริการของ EMVCo |

## Data Objects for BayadCenter Template (ID `"80"`)

| Name | ID | Format | Length | Presence | Comment |
|------|----|--------|--------|----------|---------|
| Globally Unique Identifier | `"00"` | ans | "15" | M | `"com.bayadcenter"` |
| Biller Code | `"01"` | N | "05" | M | BayadCenter biller identifier | 
| Service Code | `"02"` | ans | "05" | M | BayadCenter biller service identifier |
| ATM / Phone Reference No. | `"03"` | N | `"16"` | O | Meralco |
| Meralco Reference No. | `"04"` | N | `"26"` | O | Meralco |
| Phone Number | `"05"` | N | var. up to "15" | O | PLDT, Sun, BayanTel, ABS-CBN Mobile, Finaswide, Home Credit |
| Service | `"06"` | ans | "02" | O | `"PL"`": PLDT Landline, `"PD"`: PLDT DSL, `"PU"`: PLDT Ultera |
| Product | `"07"` | ans | "01" | O | `"b"`: Ultera, `"c"`: Smart Cellular, `"b"`: Smart Bro |
| Telephone Number | `"08"` | N | var. up to "11" | O | Ultera, Smart Cellular, Smart Bro, Globe, Innove, Maxicare, Global Dominion, Tanay Rural Bank |
| Service Reference Number | `"09"` | N | var. up to "10" | O | Ultera, Smart Bro | 
| Due Date | `"10"` | ans | var. up to "10" | O | Sun, Laguna Water, Innove, Sky Cable, Destiny Cable, Sky Affiliates, Manila Memorial Park, Maxicare, PhilamLife, Manulife, Sony Life, Fortune Medicare, Equicom, Pru Life U.K., Pag-Ibig Membership Savings, Philhealth, Eternal Plans, Cocolife, Extraordinary, PANELCO III, BENECO, INEC, PANELCO I, MARWADIS, Meycauayan Water, Norzagaray Water District, PELCO 2 |
| Account Name | `"11"` | ans | var. up to "52" | O | Globe, Innove, Sun Life Plans, Sun Life Canada, Sky Affiliates, Manila Memorial Park, Manulife ChinaBank, Aeon, Pilipinas Teleserv (NSO), RCBC Bankard, Pru Life U.K., Prime Water, Eternal Plans, Cocolife, Extraordinary, Sta. Lucia Waterworks, CableLink, Liberty Broadcasting Network, Asian Vision |
| RAP | `"12"` | ans | "4" | O | Maynilad |
| External Entity Name | `"13"` | ans | "5" | O | Cignal |
| Last Name | `"14"` | ans | var. up to "26" | O | Cignal, Maxicare, Fortune, Medicare, Finaswide, Caritas Financial, Caritas Health, Equicom, Sterling Bank, Philippine Prudential, VECO, DVOLT, CLPC, SEZ, MEZ, BEZ, Philhealth, SSS, NBI, POEA, PRC, PAL EXPRESS, HomeMark, ChinaTrust, Asia Link, Global Dominion, Tanay Rural Bank, PANELCO III, BENECO, PANELCO I, MARWADIS, Meycauayan Water, Norzagaray Water District |
| First Name | `"15"` | ans | var. up to "26" | O | Cignal, Maxicare, Fortune, Medicare, Finaswide, Caritas Financial, Caritas Health, Equicom, Sterling Bank, Philippine Prudential, VECO, DVOLT, CLPC, SEZ, MEZ, BEZ, Philhealth, SSS, NBI, POEA, PRC, PAL EXPRESS, HomeMark, ChinaTrust, Asia Link, Global Dominion, Tanay Rural Bank, PANELCO III, BENECO, PANELCO I, MARWADIS, Meycauayan Water, Norzagaray Water District |
| Middle Initial/Middle Name | `"16"` | ans | var. up to "2" | O | Cignal, Maxicare, Fortune, Medicare, Finaswide, Caritas Financial, Caritas Health, Equicom, Sterling Bank, Philippine Prudential, Philhealth, SSS, HomeMark, ChinaTrust, Asia Link, Global Dominion, Tanay Rural Bank, PANELCO III, PANELCO I, MARWADIS, Meycauayan Water, Norzagaray Water District |
| Payment Type | `"17"` | ans | var. up to "2" | O | Pag-Ibig, PhilHealth, SSS |
| Bill Date | `"18"` | ans | var. up to "10" | O | Sky Cable, Destiny Cable, RCBC Bankard, Pag-Ibig, Philhealth, PANELCO III |
| Contact Number | `"19"` | N | var. up to "12" | O | Caritas Financial, Caritas Health, Equicom, Pag-Ibig, NBI, POEA, PRC, HomeMark, CableLink |
| Payment Option | `"20"` | ans | "01" | O | Pag-Ibig | 
| Period From | `"21"` | ans | var. up to "7" | O | Pag-Ibig, Philhealth |
| Period To | `"22"` | ans | var. up to "7" | O | Pag-Ibig, Philhealth |
| Region | `"23"` | ans | "01" | O | Pag-Ibig |
| Member Type | `"24"` | ans | var. up to "3" | O | Philhealth
| Company Name | `"25"` | ans | var. up to "52" | O | Philhealth, SSS |
| SPA Number | `"26"` | N | var. up to "15" | O | Philhealth |
| Contribution Date Range (From) | `"27"` | ans | var. up to "7" | O | SSS |
| Contribution Date Range (To) | `"28"` | ans | var. up to "7" | O | SSS |
| SSS Amount | `"29"` | ans | var. up to "13" | O | SSS |
| EC Amount | `"30"` | ans | var. up to "13" | O | SSS |
| Loan Type | `"31"` | ans | var. up to "02" | O | SSS |
| Payor Type | `"32"` | ans | "01" | O | SSS |
| Loan Account No | `"33"` | N | var. up to "10" | O | SSS |
| Rel Type | `"34"` | ans | var. up to "02" | O | SSS |
| Payor Name | `"35"` | ans | var. up to "52" | O | NHMFC, Cebu Pacific |
| Booking No | `"36"` | ans | var. up to "6" | O | Air Asia |
| Serial Number | `"37"` | N | var. up to "12" | O | Easy Trip |
| Service Type | `"38"` | N | "01" | O | Sky Cable, Destiny Cable, Cablelink |
| Plan Type | `"39"` | ans | "01" | O | Sun Life Plans |
| Product Type | `"40"` | ans | var. up to "04" | O | Sun Life Canada |
| Payment Entry | `"41"` | ans | var. up to "03" | O | NHMFC |
| Borrower Name | `"42"` | ans | var. up to "52" | O | NHMFC |
| Customer Name | `"43"` | ans | var. up to "52" | O | Bayantel |
| Affiliate | `"44"` | ans | var. up to "07" | O | Sky Affiliates |
| Bill Number / Bill Invoice Number | `"45"` | N | var. up to "15" | O | Prime Water, Sta. Lucia Waterworks, Meycauayan Water, Norzagaray Water District |
| SOACL Number | `"46"` | ans | var. up to "10" | O | Fortune Medicare |
| Account Type | `"47"` | ans | "01" | O | Fortune Medicare |
| Premium Amount | `"48"` | ans | var. up to "13" | O | Cocolife |
| Loan Amount | `"49"` | ans | var. up to "13" | O | Cocolife |
| Name | `"50"` | ans | var. up to "52" | O | Home Credit, INEC |
| Particular | `"51"` | ans | var. up to "8" | O | HomeMark |
| Reference Type | `"52"` | ans | var. up to "6" | O | ChinaTrust |
| Cons Name | `"53"` | ans | var. up to "52" | O | BPI |
| Power Company | `"54"` | ans | var. up to "04" | O | CLPC, SEZ, BEZ |
| Bill Amount | `"55"` | ans | var. up to "13" | O | PANELCO III |
| Share Capital | `"56"` | ans | var. up to "13" | O | PANELCO III |
| Affiliate Branch | `"57"` | ans | var. up to "07" | O | Asian Vision |
| Meter Number | `"58"` | ans | var. up to "15" | O | PANELCO I |
| Expiration Date | `"59"` | ans | var. up to "10" | O | PANELCO I |
| RFU for BayadCenter | `"60"`-`"99"` | ans | var. up to "70" | O | Objects สงวนไว้เพื่อบริการของ BayadCenter |
