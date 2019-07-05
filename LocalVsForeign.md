# 💢 Local Payment VS Worldwide Payment 💢

สำหรับการชำระเงินนอกประเทศ และในประเทศ โดยใช้ QR Code นั้น จะมีข้อแตกต่างกันไม่มาก โดยถ้าเราสังเกตจากการที่ใช้ QR code Scanner Appcation หรือการ [Decode QR Code](https://zxing.org/w/decode.jspx) ผ่าน Website เราจะพบข้อแตกต่างดังนี้

## Worldwide Payment (MasterCard)

![Image of QR Generator 1](https://i.imgur.com/8N8B4Iq.png)

![Image of QR Generator 2](https://i.imgur.com/b1t6jEc.png)

![Image of QR Generator 3](https://i.imgur.com/imMV1Ti.png)

![Image of QR Generator 4](https://i.imgur.com/jaV7E8M.png)

![Image of QR Generator 5](https://i.imgur.com/e1kA1hM.png)

![Image of QR Generator 6](https://i.imgur.com/Omus4ux.png)

![Image of QR Generator 7](https://i.imgur.com/5kkHUdH.png)


## Local Payment (PromptPay)

![QRPayment](https://github.com/chokchai9900/QR_Wiki/blob/master/Wiki_pic/paymentLocal.jpg)

![QRDecode](https://github.com/chokchai9900/QR_Wiki/blob/master/Wiki_pic/QRDecode.jpg)

### ข้อแต่กต่าง

สังเกตว่าการ Decode Qr Code นั้น สามารถทำให้เห็นข้อมูลภายใน QR Code นั้นๆได้ โดยที่ QR ที่สำหรับใช้จ่ายแบบ Worldwide นั้น จะมีข้อมูลมากมาย ที่แตกต่างคือจะมี Merchant name และ city ด้วย และตัว Merchant Account Information นั้น ของ Promptpay จะถูกกำหนดตายตัวไว้แล้ว แต่ถ้าเป็นของ Mastercard นั้น จะสามารถกำหนดได้เองโดยมีตัวเลือกมากมาย ขึ้นอยู่กับรูปแบบการจ่ายเงินที่นิยมในประเทศนั้น ๆ

| ข้อมูล Object | ระบบ PromptPay | ระบบ Mastercard |
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
