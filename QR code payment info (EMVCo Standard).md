    
    
    short note for QR code for payment (Promptpay)
///////////////////////////////////////////////////////

Ex : 00020101021129370016A000000677010111011300660000000005802TH530376463048956
Ex : https://www.blognone.com/node/95133

xx  yy
xx = Field  yy = length

00 02   Format = N
    01 -> หมายเลขเวอร์ชั่น 
    = 000201

01 02   Format = N
    11 -> ประเภทของ QR
    = 010211

29 37 -> ( merchant account information ) Format = ans
    0016 ->     1. app id (AID)   
                    - A000000677010111
                2. Merchant Category Code (หมายเลข promptpay) 

                -http://portailgroupe.afnor.fr/public_espacenormalisation/ISOTC68SC7/18245%20-%20Merchant%20category%20codes%20Tables%20-%202014-07-10%20clean%20version.pdf (afnor Merchant Category Code list)

                -https://usa.visa.com/dam/VCOM/download/merchants/visa-merchant-data-standards-manual.pdf (visa Merchant Category Code list)

                    - 0113 + 00 + 66000000000 (phone number : 000-000-0000 )
                if use phone number 
                    01 = phone number type + 13 + 00
                        +
                    66 = country code number
                if use ID card
                    02 = ID card type 

                    = 29370016A00000067701011101130066000000000

58 02 -> country code   Format = ans
    TH = Thailand Country
    = 5802TH
    - https://en.wikipedia.org/wiki/ISO_3166-1_alpha-2

53 03 -> Currency   Format =  ans
    764 = Thai Bath ( ISO 4217 https://en.wikipedia.org/wiki/ISO_4217 )
    = 5303764

63 04 -> Check sum (CRC-16 & polynomial 0x1021 (XMODEM) + default ("0xFFFF") ) Format = ans
    8956 = Checksum output 
    = 63048956

    QR Code = 00020101021129370016A000000677010111011300660000000005802TH530376463048956

-----------------------------------------------------------------------------------------------

Ex : https://github.com/PayMaya/PayMaya-EMV-QR/tree/master/Merchant-Presented
    (PayMaya EMV Merchant Presented QR Code)

        
    short note for QR code for payment (Non - Promptpay)
///////////////////////////////////////////////////////

The following data objects are intended to be used and processed:
• Payload Format Indicator
• Merchant Account Information
• Merchant Category Code
• Transaction Currency
• Country Code
• Merchant Name
• Merchant City
_________________________________________________________________________________________
|Data Object                   |  ID   |  Format  |     Example Value                   |
-----------------------------------------------------------------------------------------
|Payload Format Indicator      | "00"  |    N     |        "01"                         |
|Merchant Account Information  | "02"  |   ans    |   "4000123456789012"                |
|Merchant Category Code        | "52"  |    N     |        "5251"                       |
|Transaction Currency          | "53"  |    N     |        "840"                        |
|Country Code                  | "58"  |   ans    |         "US"                        |
|Merchant Name                 | "59"  |   ans    |     "ABC Hammers"                   |
|Merchant City                 | "60"  |   ans    |      "New York"                     |
|Cyclic Redundancy Check (CRC) | "63"  |   ans    |    Calculated using the algorithm   |
|                              |       |          |    defined in [EMV MERCHANT QR]     |
-----------------------------------------------------------------------------------------