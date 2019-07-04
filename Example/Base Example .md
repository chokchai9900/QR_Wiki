# Base Example

เป็นแบบเริ่มต้นสำหรับการสร้าง QR Code เพื่อการเงิน โดยในรูปแบบนี้ จะไม่สนภาษี ค่าธรรมเนียม หรืออื่นๆที่นอกเหนือจากการจ่างเงินที่ผู้จ่ายสามารถระบุจำนวนเงินได้

## Table of Contents

- [🔥ของมันต้องมี🔥](#🔥ของมันต้องมี🔥)
- [แล้ว Object แต่ละอย่างมันคืออะไร มาจากไหน ⁉️](#แล้ว-Object-แต่ละอย่างมันคืออะไร-มาจากไหน-⁉️)
  - [Payload Format Indicator](#Payload-Format-Indicator)
  - [Point of Initiation Method](#Point-of-Initiation-Method)
  - [Merchant Account Information](#Merchant-Account-Information)
    - [ระบบทางการเงินภายนอกประเทศ](#ระบบทางการเงินภายนอกประเทศ)
    - [ระบบทางการเงินภายในประเทศ](#ระบบทางการเงินภายในประเทศ)
  - [Merchant Category Code](#Merchant-Category-Code)
  - [Transaction Currency](#Transaction-Currency)
  - [Country Code](#Country-Code)
  - [Merchant Name & Merchant City](#Merchant-Name-&-Merchant-City)
  - [Cyclic Redundancy Check](#Cyclic-Redundancy-Check)
- [ความต่างระหว่าง QR Code ของระบบ PromptPay และ ระบบต่างประเทศ](#ความต่างระหว่าง-QR-Code-ของระบบ-PromptPay-และ-ระบบต่างประเทศ)
- [ทดสอบกับเถอะ ❗️❗️❗️❗️](#ทดสอบกับเถอะ-❗️❗️❗️❗️)
  - [ผลทดสอบ](#ผลทดสอบ)
- [Link Document & Testing Tool](#Link-Document-&-Testing-Tool)

# 🔥ของมันต้องมี🔥 !!
ในการสร้าง QR Code แบบ Base Example นั้น จำเป็นจะต้องมี Object ตามตารางนี้ พร้อมตัวอย่าง....

| ข้อมูล Object | ID | Format | ข้อมูลตัวอย่าง |
|------|--------|-----------|---------|
| Payload Format Indicator | "00" | N | "01" | 
| Point of Initiation Method | "01" | N | "11" Or "12" |
| Merchant Account Information | "02" | ans | "4000123456789012" |
| Merchant Category Code | "52" | N | "5251" |
| Transaction Currency | "53" | N |"840" |
| Country Code | "58" | ans | "US" |
| Merchant Name | "59" | ans | "ABC Hammers" |
| Merchant City | "60" | ans | "New York" |
| Cyclic Redundancy Check (CRC) | "63" | ans | Calculated using the algorithm defined in [EMV MERCHANT QR] |

# แล้ว Object แต่ละอย่างมันคืออะไร มาจากไหน ⁉️

## Payload Format Indicator
Payload Format Indicator คือ การระบุ version ของมาฐานนั้นๆ ในที่นี้ยังเป็น version 0.1 อยู่ จึงต้อง fix เป็น 01 ฉนั้น จะได้เป็น
```
Ex : " 000201 "
```

## Point of Initiation Method
Point of Initiation Method เป็นการระบุว่าเป็น QR Code ในรูปแบบใด ซึ่งในขณะนี้ มีรูปแบบย่อยเพียง 2 รูปแบบคือ 

* 11 = สำหรับการขาย/จ่ายหลายครั้ง ใช้เพียง QR Code เดียว 
* 12 = สำหรับการขายครั้งเดียว เช่น การจ่ายสำหรับ 1 ใบเสร็จเท่านั้น แล้วจะต้องสร้าง QR Code ใหม่ทุกๆครั้งที่มีการสั่งจ่ายต่อ 1 ใบเสร็จ จะได้เป็น
```
Ex : " 010211 "
```

## Merchant Account Information
Merchant Account Information คือข้อมูลของร้านค้านั้นๆ หรือข้อมูลของผู้ขาย ถ้าหากการสั่งจ่าย ใช้ระบบทางการเงินของ Visa หรือ mastercard จะต้องทำการ Register กับทางบริการของบริษัทนั้นๆ และบริการต่างๆ จะมีเลข ID ที่ถูกสงวนไว้เฉพาะอยู่แล้ว หลักๆ จะมี 2 ประเภทคือ  ระบบทางการเงินภายนอกประเทศ และในประเทศ

### ระบบทางการเงินภายนอกประเทศ
มีรายชื้อผู้ให้บริการ และ ID ดังนี้ 

| ID | Description |
|----|---------|
| “02”-“03” | สงวนไว้เพื่อระบบ Visa |
| “04”-“05” | สงวนไว้เพื่อระบบ Mastercard |
| “06”-“08” | สงวนไว้โดยระบบ EMVCo |
| “09”-“10” | สงวนไว้เพื่อระบบ Discover |
| “11”-“12” | สงวนไว้เพื่อระบบสงวนไว้เพื่อระบบ Amex |
| “13”-“14” | สงวนไว้เพื่อระบบ JCB |
| “15”-“16” | สงวนไว้เพื่อระบบ UnionPay |
| “17”-“25” | สงวนไว้โดยระบบ EMVCo |
| “26”-“51” | สงวนไว้เพื่อเครือข่ายการชำระเงินอื่นๆที่นอกเหนือจากข้างต้น |
 
 ถ้าหากเป็นบริการของ Visa จะขึ้นต้นด้วย 02 ตามด้วย ID ของบริการนั้นๆ เช่น 02 และตามด้วยจำนวนความยาวของข้อมูล เช่น หากความยาวของข้อมูลมี 10 ตัวอักษร จะได้เป็น
```
Ex : "02020123456789"
```
### ระบบทางการเงินภายในประเทศ
หรือ PromptPay Systems จะแบ่งเป็น 2 ฟิลด์ คือ 
* หมายเลขแอปพลิเคชั่น จะระบุถึง หมายเลขที่ใช้อ้างอิงถึงบัตรสมาร์ทการ์ดต่างๆ เช่นเลข visa เลขบัตร mastercard เลขบัตรประชาชน เป็นต้น ID ย่อยคือ "00" ความยาว "16" มีความยาวได้ไม่เกิน 99 ตัวอักษร สมมุตว่า ( application ID ) คือ "A000000677010111" 
    * ในกรณีที่ใช้ Application ID นี้  เพื่อระบุว่า QR Code นี้ เป็นบริการของ PromptPay
    จะได้เป็น
```
Ex : "0016A000000677010111" 
```
* หมายเลข PromptPay จะใช้หมายเลข PromptPay โดยตรง โดยจะมี ID ย่อย ดังนี้
1. หากใช้หมายเลขโทรศัพท์ จะมี ID ย่อยคือ "01" นำหน้าด้วย 00 แล้วตามด้วยรหัสประเทศ คือ 66 (รหัสประเทศอ้างอิงจาก [COUNTRY CALLING CODE](https://countrycode.org) โดยประเทศไทยจะใช้ +66 แต่ในการสร้าง QR Code ไม่ต้องใส่ + เข้าไป )

## Merchant Category Code
Merchant Category Code เป็นรหัสในการระบุประเภทของร้านค้า หรือผู้ขาย 
(ในตอนนี้ ผู้เขียนค้นพบแค่ 3 ผู้ให้บริการ ที่เปิดเผย list คือ [VISA](http://usa.visa.com/download/corporate/resources/mcc_booklet.pdf) , [MasterCard](https://www.mastercard.us/content/dam/mccom/en-us/documents/rules/quick-reference-booklet-merchant-edition.pdf) , [CitiBank](https://www.citibank.com/tts/solutions/commercial-cards/assets/docs/govt/Merchant-Category-Codes.pdf))

ID หลักคือ "52" ความยาว "04" จะได้เป็น
```
Ex : "5204XXXX"
```
## Transaction Currency
Transaction Currency อ้างอิงตามมาตรฐาน [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) โดยของประเทศไทยใช้เป็นสกุลเงิน Thai bath ก็คือ "764" ID คือ "53" ความยาว "03" จะได้เป็น
```
5303764
```

## Country Code
Country Code คือรหัสประจำปะเทศ โดยใช้ตัวอักษรสองตัว อ้างอิงตามมาตรฐาน [ISO 3166-1 alpha 2](https://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) เช่น ของประเทศไทยคือ TH ID คือ "58" ความยาว "02" จะได้เป็น
``` 
5802TH
```
## Merchant Name & Merchant City
Merchant Name & Merchant City เป็นชื่อที่จะบ่งบอกว่า ร้านค้าชื่ออะไร จากเมือง หรือประเทศใด จะแสดงเป็น Display name ในหน้าของ application 
* Merchant Name ID คือ "59" ความยาวขึ้นอยู่กับชื่อของร้าน มีความยาวได้ไม่เกิน 99 ตัวอักษร
Ex Merchant name : WTF Digital ความยาว = "11" 
จะได้เป็น
```
Ex : "5911WTF Digital"
```  
* Merchant City ID คือ "60" ความยาวขึ้นอยู่กับชื่อของเมือง มีความยาวได้ไม่เกิน 99 ตัวอักษร
Ex Merchant City : Nicaragua ความยาว = "09"
```
Ex : "6009Nicaragua"
```

## Cyclic Redundancy Check
ข้อมูลนี้ต้องอยู่ท้ายสุดเสมอ โดยค่า check sum เป็นการคำนวณจากข้อมูลทั้งหมด รวมถึงหมายเลขฟิลด์ของ check sum และความยาวของฟิลด์ check sum เอง 
กระบวนการหาค่า check sum ใช้ CRC-16 และ ค่าคงที่ polynomial 0x1021 (XMODEM)พร้อมกับค่าเริ่มต้น 0xFFFF 

ส่วนตัวไลบรารีสำหรับคำนวน สามารถใช้ pycrc16 ได้โดยตรง
ID ของ Object คือ "63" ความยาว "04"
Ex : CRC 8888 จะได้เป็น
```
Ex : "63048888"
```
# ความต่างระหว่าง QR Code ของระบบ PromptPay และ ระบบต่างประเทศ

ในที่นี้ เราขอยกตัวอย่างระบบต่างประเทศเป็นระบบของ Visa

| ข้อมูล Object | ระบบ PromptPay | ระบบ Visa |
|-------------|----------------|---------|
| Payload Format Indicator | :white_check_mark: | :white_check_mark: |
| Point of Initiation Method | :white_check_mark: | :white_check_mark: |
| Merchant Account Information | :white_check_mark: | :white_check_mark: |
| Merchant Category Code | :white_large_square: | :white_check_mark: |
| Transaction Currency | :white_check_mark: | :white_check_mark: |
| Country Code | :white_check_mark: | :white_check_mark: |
| Merchant Name | :white_large_square: | :white_check_mark: |
| Merchant City | :white_large_square: | :white_check_mark: |
| Cyclic Redundancy Check (CRC) | :white_check_mark: | :white_check_mark: |


# ทดสอบกับเถอะ ❗️❗️❗️❗️

เราจะใช้เบอร์ 0918695214 เป็นเบอร์สำหรับทดสอบ เพื่อจะได้เห็นภาพ

![Picture](https://github.com/chokchai9900/QR-payment-info/blob/master/Capture.PNG)

หากผู้อ่านต้องการทดสอบ สามารถคลิกได้ที่ [ทดสอบสร้าง QR code PromptPay](https://promptpay.io)

## ผลทดสอบ

เมื่อใช้หมายเลขโทรศัพท์ไปสร้างในเว็บไซต์แล้ว จะได้QR code ดังนี้

![QR Code](https://promptpay.io/0918695214.png)

`ในกรณีนี้ จะไม่มี Merchant Name & Merchant City เนื่องจากเป็นระบบ PromptPay ซึ่งไม่มีให้กรอกข้อมูลในสองส่วนนี้`

เมื่อนำไป Decode จะได้ตัวเลขตามนี้

```
00020101021129370016A000000677010111011300669186952145802TH5303764630471E4
```

ซึ่ง จำแนกได้ตามนี้

| Data | Description |
|------|-------------|
| 000201  | ver. |
| 010211  | type | 
| 2937  | Merchant account information |
|* 0016A000000677010111  |* application ID |
|* 01130066918695214 |* PromptPay Accout ("ID card" or "phone number") |
| 5802TH | Country Code |
| 5303764 | Transaction Currency |
| 630471E4 | Cyclic Redundancy Check |

ซึ่งสังเกตได้ว่า 4 ตัวแรกจะเป็น ID และ ความยาวของข้อมูล 

ส่วนนอกจากนั้น จะเป็นข้อมูลทีมีทั้งตัวเลขและตัวหนังสือ ซึ่งมันคือข้อมูลประจำ Object นั้นเอง

ส่วน Object ที่มี * ข้างหน้า คือObjectที่เป็นObjectย่อยของ Merchant account information