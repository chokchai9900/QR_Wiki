# Transaction Amount Provided Example 



## Table of Contents

- [🔥ของมันต้องมี🔥](#🔥ของมันต้องมี🔥)
- [แล้ว Object แต่ละอย่างมันคืออะไร มาจากไหน ⁉️](#แล้ว-Object-แต่ละอย่างมันคืออะไร-มาจากไหน-⁉️)
  - [Payload Format Indicator](#Payload-Format-Indicator)
  - [Point of Initiation Method](#Point-of-Initiation-Method)
  - [Merchant Account Information](#Merchant-Account-Information)
  - [Merchant Category Code](#Merchant-Category-Code)
  - [Transaction Currency](#Transaction-Currency)
  - [Transaction Amount](#Transaction-Amount)
  - [Country Code](#Country-Code)
  - [Merchant Name & Merchant City](#Merchant-Name-&-Merchant-City)
  - [Cyclic Redundancy Check](#Cyclic-Redundancy-Check)


# 🔥ของมันต้องมี🔥 !!

Object ที่จำเป็นในการสร้าง QR Code ใน Template นี้ มีดังนี้

| ข้อมูล Object | ID | Format | ข้อมูลตัวอย่าง |
|------|--------|-----------|---------|
| Payload Format Indicator | "00" | N | "01" | 
| Merchant Account Information | "02" | ans | "4000123456789012" |
| Merchant Category Code | "52" | N | "5251" |
| Transaction Currency | "53" | N |"840" |
| Transaction Amount | "54" | ans |"10" |
| Country Code | "58" | ans | "US" |
| Merchant Name | "59" | ans | "ABC Hammers" |
| Merchant City | "60" | ans | "New York" |
| Cyclic Redundancy Check (CRC) | "63" | ans | Calculated using the algorithm defined in [EMV MERCHANT QR] |

สังเกตว่าจะมีข้อแตกต่างจากแบบแรกคือ จะมี Transaction Amount ก็คือค่าเงินที่ต้องจ่าย โดยจะมี ID ของ  Object คือ "54" มีความยาวได้ไม่เกิน "99" โดยการทำงานนั้น เมื่อเราใช้ App เพื่อสแกนสำหรับจ่าย จะทำการ interface เป็นชื่อผู้ค้า ชื่อเมือง และจำนวนเงินที่ต้องจ่าย ตามรูป

![Picture Ex02](https://github.com/chokchai9900/QR_Wiki/blob/master/Wiki_pic/ex02.PNG)


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
Merchant Account Information คือข้อมูลของร้านค้านั้นๆ หรือข้อมูลของผู้ขาย ถ้าหากการสั่งจ่าย ใช้ระบบทางการเงินของ Visa หรือ mastercard จะต้องทำการ Register กับทางบริการของบริษัทนั้นๆ และบริการต่างๆ จะมีเลข ID ที่ถูกสงวนไว้เฉพาะอยู่แล้ว 

```
Ex : "400012345678901" 
```

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

## Transaction Amount
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
