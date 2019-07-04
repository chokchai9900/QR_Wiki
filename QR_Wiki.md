# ⚡️QR code (EMVCo Standard)⚡️

* Author : Chokchai Homsombat
* Created : 02-07-2019
* Last Modified : 02-07-2019
* Document version : 0.4 
  *   Ver 0.1 : สร้าง
  *   ver 0.2 : เพิ่มการทดสอบ
  *   ver 0.3 : เพิ่มตารางเปรียบเที่ยบระหว่าง Qr code ของระบบ PromptPay และ ระบบต่างประเทศ
  *   ver 0.4 : เพิ่ม Table of Contents
  *   ver 0.5 : เปลี่ยนแปลงเอกสารทั้งหมด

💯💯💯💯💯💯💯💯💯💯💯💯

---

## Table of Contents
- [--Blank--](-blank-)
  - [--Blank--](-blank-)
- [--Blank--](-blank-)
- [--Blank--](-blank-)
  - [--Blank--](-blank-)
  - [--Blank--](-blank-)
  - [--Blank--](-blank-)
    - [--Blank--](-blank-)
    - [--Blank--](-blank-)
  - [--Blank--](-blank-)
  - [--Blank--](-blank-)
  - [--Blank--](-blank-)
  - [--Blank--](-blank-)
  - [--Blank--](-blank-)
- [--Blank--่](-blank-)
- [--Blank--](-blank-)
  - [--Blank--](-blank-)
- [--Blank--](-blank-)



# Base Example Data Payload Format

ในการเรียง Format ของ QR Code จะใช้ หมายเลขของ Object + ความยาวของข้อมูล เช่น
* Ex : Payload Format Indicator = 000201
    * 00 = ID 
    * 08 = Lenght of data
    * 01234567 = Data

**Note !!🚧** `ข้อมูลแต่ละชนิด จะไม่สามารถมีความยาวได้เกิน มีความยาวได้ไม่เกิน 99 ตัวอักษร ยกเว้นข้อมูลบางชนิด ที่มสามารถมีข้อมูลได้น้อยกว่า 99 ตัวอักษร อ้างอิงตามเอกสาร` [EMV® QR Code Specification for Payment Systems](https://www.emvco.com/wp-content/plugins/pmpro-customizations/oy-getfile.php?u=wp-content/uploads/documents/EMVCo-Merchant-Presented-QR-Specification-v1-1.pdf)

## ตัวย่อและความหมายต่างๆ

| Abbreviation | Description |
|--------------|-------------|
| ans | ตัวอักษรและตัวเลขพิเศษ |
| CRC | ระบบ CRC Checksum |
| ID | รหัสประจำ Object นั้นๆ |
| ISO | มาตรฐานการวัดคุณภาพ |
| N | ตัวเลข |
| QR Code | Quick Response Code |
| S | ตัวอักษร |


# Link Document & Testing Tool

* A. https://www.emvco.com/wp-content/uploads/documents/EMV-Merchant-QR-Guidance-and-Examples-1.0.pdf
* B. https://countrycode.org
* C. http://usa.visa.com/download/corporate/resources/mcc_booklet.pdf
* D. https://www.citibank.com/tts/solutions/commercial-cards/assets/docs/govt/Merchant-Category-Codes.pdf
* E. https://en.wikipedia.org/wiki/ISO_4217
* F. https://en.wikipedia.org/wiki/ISO_3166-1_alpha-2
* G. https://www.emvco.com/wp-content/plugins/pmpro-customizations/oy-getfile.php?u=wp-content/uploads/documents/EMVCo-Merchant-Presented-QR-Specification-v1-1.pdf
* H. https://promptpay.io