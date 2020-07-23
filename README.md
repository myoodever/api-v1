# Welcome to API-v1!

# API EndPoint : https://api-v1.banktopup.com

# วิธีการลงทะเบียนบัญชี

1. /api/v1/scb/register ส่งข้อมูลต่างๆไปเพิ่มเพิ่มบัญชี จากนั้นระบบจะตอบกลับมาด้วย deviceid เช่น ba8ff1f5-7ba6-4678-83fe-8abf004eab4c
2. /api/v1/scb/register/:deviceid ใส่ deviceid จากขั้น 1. จะเป็น /api/v1/scb/register/ba8ff1f5-7ba6-4678-83fe-8abf004eab4c แบบนี้ขั้นตอนนี้ส่ง otp เพื่อลงทะเบียน เสร็จแล้วระบบจะให้ deviceid แล้วนำสิ่งนี้ไปเก็บไว้ ถ้าหายหรือใช้ไม่ได้ก็ต้องลงทะเบียนใหม่ อารมแบบลงบัญชีในแอปใหม่ เก็บไปใช้ได้เรื่อยๆ
3. วิธีเช็คว่า deviceid เรามันพังหรือใช้ได้มั้ย ใช้วิธีนี้ /api/v1/scb/check_device ส่งข้อมูลไปที่นี่

# วิธีการดึงรายการ

1./api/v1/scb/transactions พร้อมด้วยข้อมูลระบบจะส่งรายการกลับมาให้

# API (Method : POST)

<<<<<<< HEAD
| #                              | param                                                                                                                                                                                                                                                                                    |
| ------------------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| /api/v1/scb/check_device       | {"deviceid":"deviceid ของบัญชีที่จะเช็ค"}                                                                                                                                                                                                                                                |
| /api/v1/scb/register           | {"identification":"1849XXXXXXXXX เลขบัตรประชาชน","year":"2001 ปี ค.ส.","month":"01 เลขเดือน 2 หลัก","day":"31 เลขวัน 2 หลัก","pin":"123456 PIN","mobile_phone_no":"06XXXXXXXX เบอร์","account_no":"42XXXXXXXX เลขบัญชี","device_brand":"VIVO ชื่อมือถือ","device_code":"M00001 เลขรุ่น"} |
| /api/v1/scb/register/:deviceid | {"otp":"otp ที่รับจากมือถือ"}                                                                                                                                                                                                                                                            |
| /api/v1/scb/login              | {"deviceid":"xxx","pin":"xxxxx","account_no":"xxxxxxxx"}                                                                                                                                                                                                                                 |
| /api/v1/scb/transactions       | { "deviceid":"xxx", "pin":"xxxxx", "account_no" :"xxxxxxxx", "previous_day":7, "page_number":1, "page_size":20 }                                                                                                                                                                         |
| /api/v1/scb/verification       | { "deviceid": "xxx", "pin": "xxxxx", "account_no": "xxxxxxxx", "account_to": "xxxxxxxx", "bank_code": "bankCode ดูได้จาก bank list", "amount": 1.00 }                                                                                                                                    |
| /api/v1/scb/transfer           | { "deviceid": "xxx", "pin": "xxxxx", "account_no": "xxxxxxxx", "account_to": "xxxxxxxx", "bank_code": "bankCode ดูได้จาก bank list", "amount": 1.00 }                                                                                                                                    |
=======
| #                              | param     | อธิบาย                                                                                                                                                                                                                                                                            |
| ------------------------------ | ------ |---|  
| /api/v1/scb/check_device       | {"deviceid":"deviceid ของบัญชีที่จะเช็ค"}    | เช็คว่า deviceid ยังใช้ได้หรือป่าว                                                                                                                                                                                                                                             |
| /api/v1/scb/register           | {"identification":"1849XXXXXXXXX เลขบัตรประชาชน","year":"2001 ปี ค.ส.","month":"01 เลขเดือน 2 หลัก","day":"31 เลขวัน 2 หลัก","pin":"123456 PIN","mobile_phone_no":"06XXXXXXXX เบอร์","account_no":"42XXXXXXXX เลขบัญชี","device_brand":"VIVO ชื่อมือถือ","device_code":"M00001 เลขรุ่น"} |ลงทะเบียนบัญชี deviceid ใหม่   ขั้นตอน 1                                           | 
| /api/v1/scb/register/:deviceid | {"otp":"otp ที่รับจากมือถือ"}  | ลงทะเบียนบัญชี otp ขั้นตอน 2                                                                                                                                                                                            |
| /api/v1/scb/login              | {"deviceid":"xxx","pin":"xxxxx","account_no":"xxxxxxxx"}   | ไม่ต้องสนใจ                                                                                                                                                                                                                               |
| /api/v1/scb/transactions       | { "deviceid":"xxx", "pin":"xxxxx", "account_no" :"xxxxxxxx", "previous_day":7, "page_number":1, "page_size":20 }    | ดึงรายการ                                                                                                                                                                     |
| /api/v1/scb/verification       | { "deviceid": "xxx", "pin": "xxxxx", "account_no": "xxxxxxxx", "account_to": "xxxxxxxx", "bank_code": "bankCode ดูได้จาก bank list", "amount": 1.00 }     | เช็คก่อนโอน                                                                                                                                |
| /api/v1/scb/transactions       | { "deviceid": "xxx", "pin": "xxxxx", "account_no": "xxxxxxxx", "account_to": "xxxxxxxx", "bank_code": "bankCode ดูได้จาก bank list", "amount": 1.00 }   |  โอนเงิน                                                                                                                                  |
>>>>>>> a73e77fe9aca37ff74e3d4e49399e41398a47a89

# HTTP Header

    Content-Type : application/json
    x-auth-license : license ของท่าน

# Bank List

| bankCode | bankAbbrevEn | bankNameTh                                    |
| -------- | ------------ | --------------------------------------------- |
| 014      | null         | ธนาคารไทยพาณิชย์ จำกัด (มหาชน)                |
| 034      | BAAC         | ธนาคารเพื่อการเกษตรและสหกรณ์การเกษตร          |
| 025      | BAY          | ธนาคารกรุงศรีอยุธยา จำกัด (มหาชน)             |
| 002      | BBL          | ธนาคารกรุงเทพ จำกัด (มหาชน)                   |
| 022      | CIMB         | ธนาคารซีไอเอ็มบี ไทย จำกัด (มหาชน)            |
| 017      | CITI         | ธนาคารซิตี้แบงก์                              |
| 032      | DB           | ธนาคารดอยช์แบงก์                              |
| 033      | GHB          | ธนาคารอาคารสงเคราะห์                          |
| 030      | GSB          | ธนาคารออมสิน                                  |
| 031      | HSBC         | ธนาคารฮ่องกงและเซี่ยงไฮ้ จำกัด                |
| 070      | ICBC         | ธนาคารไอซีบีซี (ไทย) จำกัด (มหาชน)            |
| 066      | ISBT         | ธนาคารอิสลามแห่งประเทศไทย                     |
| 004      | KBANK        | ธนาคารกสิกรไทย จำกัด (มหาชน)                  |
| 069      | KK           | ธนาคารเกียรตินาคิน จำกัด (มหาชน)              |
| 006      | KTB          | ธนาคารกรุงไทย จำกัด (มหาชน)                   |
| 073      | LHBANK       | ธนาคารแลนด์ แอนด์ เฮ้าส์ จำกัด (มหาชน)        |
| 039      | MHCB         | ธนาคารมิซูโฮ คอร์ปอเรต                        |
| 020      | SCBT         | ธนาคารสแตนดาร์ดชาร์เตอร์ด (ไทย) จำกัด (มหาชน) |
| 018      | SMBC         | ธนาคารซูมิโตโม มิตซุย แบงกิ้ง คอร์ปอเรชั่น    |
| 065      | TBANK        | ธนาคารธนชาต จำกัด (มหาชน)                     |
| 071      | TCRB         | ธนาคารไทยเครดิต เพื่อรายย่อย จำกัด (มหาชน)    |
| 011      | TMB          | ธนาคารทหารไทย จำกัด (มหาชน)                   |
| 067      | TSCO         | ธนาคารทิสโก้ จำกัด (มหาชน)                    |
| 024      | UOB          | ธนาคารยูโอบี จำกัด (มหาชน)                    |

# Errors

| Code | MsgTH                                         |
| ---- | --------------------------------------------- |
| 100  | สำเร็จ                                        |
| 101  | ข้อมูลที่สมบูรณ์                              |
| 102  | ไม่พบหน้านี้                                  |
| 103  | ข้อผิดพลาดจาก SCB                             |
| 104  | บัตรประชาชน หรือ วันเดือนปีเกิด ไม่ถูกต้อง    |
| 105  | เบอร์ ไม่ถูกต้อง                              |
| 106  | ไม่พบ session register นี้                    |
| 107  | OTP ไม่ถูกต้อง                                |
| 108  | ข้อผิดพลาดจาก SCB 0x1                         |
| 109  | PIN หรือ รหัสผ่านไม่ถูกต้อง                   |
| 110  | เพิ่มอุปกรณ์ไม่สำเร็จ 0x1                     |
| 111  | เพิ่มอุปกรณ์ไม่สำเร็จ 0x2                     |
| 112  | PIN หรือ รหัสผ่านไม่ถูกต้อง                   |
| 113  | ไม่พบ License นี้                             |
| 114  | License นี้โดน Ban                            |
| 115  | เกิดข้อผิดพลาดในการดึงรายการ                  |
| 116  | DeviceID ไม่ตรงตาม License โปรด reigster ใหม่ |
| 199  | ข้อผิดพลาดอื่นๆ                               |

# Resp

    "error": {
    	"code": 100, code การตอบกลับ
    	"data": null, //null เมื่อ ไม่ error
    	"msg_th": "สำเร็จ" ภาษาไทย
    },

    "result": {
    	ข้อมูล
    }
