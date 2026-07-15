# Tinh nang du an ShotDo

## 1. Muc tieu tai lieu

Tai lieu nay mo ta ro nhung tinh nang ma du an ShotDo se co, trong do tach biet:
- tinh nang MVP can lam truoc
- tinh nang nen bo sung sau MVP
- gia tri nguoi dung cua tung nhom tinh nang

Muc tieu la giup qua trinh phat trien khong bi dan trai, uu tien dung thu tu, va giu san pham tap trung vao bai toan "anh chup man hinh biet hanh dong".

## 2. Tam nhin san pham

ShotDo la ung dung bien anh chup man hinh thanh cac hanh dong co the lam ngay.

Thay vi nguoi dung phai:
- mo lai anh
- doc lai thong tin
- nho du lieu
- copy thu cong
- mo tung app khac de xu ly

ShotDo se:
- doc noi dung trong anh
- nhan dien thong tin quan trong
- de xuat cac hanh dong phu hop
- cho phep luu lai de xem sau

## 3. Nguyen tac uu tien tinh nang

Tat ca tinh nang deu can tuan theo cac nguyen tac sau:
- Uu tien toc do thao tac it buoc.
- Uu tien quy trinh tu nhien cua nguoi dung Android: chup anh -> chia se -> xu ly.
- Uu tien quyen rieng tu: OCR local mac dinh.
- Khong tu dong thuc hien hanh dong nhay cam neu chua co xac nhan.
- Tap trung xu ly tot ngon ngu va thoi quen su dung cua nguoi Viet.

## 4. Nhom tinh nang MVP can lam truoc

Day la nhung tinh nang can co de app co the demo, test voi nguoi dung that, va chung minh duoc gia tri cot loi.

### 4.1 Tinh nang nhan anh

#### Muc tieu
Nguoi dung dua anh chup man hinh vao app nhanh nhat co the.

#### Tinh nang MVP
- Chon anh tu Android Photo Picker.
- Nhan anh qua Android Share Intent.
- Hien preview anh truoc khi phan tich.
- Kiem tra file hop le truoc khi OCR.

#### Gia tri
- Giam do friction.
- Dung voi thoi quen chup anh roi share ngay.
- Khong can xin quyen doc toan bo thu vien anh.

#### Dieu kien hoan thanh MVP
- Nguoi dung co the chon anh tu trong app.
- Nguoi dung co the share anh tu app khac vao ShotDo.
- Anh duoc dua vao man hinh phan tich ma khong loi voi case thong thuong.

### 4.2 Tinh nang OCR van ban

#### Muc tieu
Chuyen noi dung trong screenshot thanh text co the xu ly duoc.

#### Tinh nang MVP
- OCR text tren thiet bi bang ML Kit.
- Doc duoc van ban tieng Viet co ky tu Latin.
- Lay raw text tu anh.
- Hien trang thai dang phan tich.
- Xu ly loi khi anh mo, anh khong co text, hoac OCR that bai.

#### Gia tri
- Day la nen tang cua toan bo san pham.
- OCR local nhanh hon, rieng tu hon, chi phi thap hon.

#### Dieu kien hoan thanh MVP
- App doc duoc text tu cac screenshot ro net.
- Co loading state va error state ro rang.
- Nguoi dung xem duoc raw text neu can.

### 4.3 Tinh nang nhan dien ngay gio

#### Muc tieu
Phat hien thong tin lich hen tu screenshot va chuyen thanh reminder hoac calendar action.

#### Tinh nang MVP
- Nhan dien ngay/thang/nam ro rang.
- Nhan dien gio ro rang nhu `14:30`, `8h`, `8 gio toi`.
- Ho tro mot so cum tu tuong doi pho bien:
  - `mai`
  - `chieu mai`
  - `toi nay`
  - `thu hai tuan sau`
- Chuyen doi thanh gia tri thoi gian chuan hoa.
- Hien muc do confidence.
- Bat buoc xac nhan voi du lieu tuong doi hoac mo ho.

#### Hanh dong MVP
- Tao reminder.
- Them vao lich.
- Sao chep thoi gian da chuan hoa.

#### Gia tri
- Day la nhom use case rat thuc te voi chat, lich hop, thong bao, uu dai co han.

#### Dieu kien hoan thanh MVP
- App detect duoc cac format ngay gio pho bien.
- Cac truong hop `mai`, `chieu mai`, `toi nay` deu can xac nhan truoc khi tao nhac.
- Khong tu dong tao reminder khi confidence thap.

### 4.4 Tinh nang nhan dien so dien thoai

#### Muc tieu
Cho phep nguoi dung thao tac nhanh voi so dien thoai tim thay trong screenshot.

#### Tinh nang MVP
- Nhan dien cac dinh dang:
  - `0987654321`
  - `0987 654 321`
  - `+84 987 654 321`
  - `024 1234 5678`
- Chuan hoa gia tri thanh dinh dang de thao tac.
- Van giu `rawValue` de nguoi dung doi chieu.

#### Hanh dong MVP
- Goi dien.
- Nhan SMS.
- Sao chep so.

#### Gia tri
- Rat hop voi screenshot tu chat, banner, bai dang, thong tin lien he.

#### Dieu kien hoan thanh MVP
- App detect on dinh so di dong va so ban.
- So co ma quoc gia `+84` duoc normalize dung.
- Hanh dong call/SMS/copy hoat dong dung.

### 4.5 Tinh nang nhan dien so tien

#### Muc tieu
Doc va chuan hoa cac gia tri tien te pho bien trong ngu canh Viet Nam.

#### Tinh nang MVP
- Nhan dien:
  - `250.000d`
  - `250,000 VND`
  - `250k`
  - `1tr2`
  - `50 nghin`
  - `1.200.000`
- Chuan hoa thanh gia tri so va text de hien thi.
- Danh dau truong hop mo ho can xac nhan.

#### Hanh dong MVP
- Sao chep so tien.
- Luu so tien vao ket qua scan.

#### Gia tri
- Huu ich cho screenshot chuyen khoan, gia san pham, hoa don, uu dai.
- Tao diem khac biet ro so voi OCR thong thuong.

#### Dieu kien hoan thanh MVP
- Parser xu ly tot cac shorthand pho bien cua nguoi Viet.
- Case mo ho nhu `2 cu` khong duoc auto-chuan hoa manh tay.

### 4.6 Tinh nang nhan dien URL

#### Muc tieu
Giup nguoi dung mo nhanh link tu screenshot ma khong phai go lai.

#### Tinh nang MVP
- Nhan dien:
  - `https://...`
  - `http://...`
  - `www.example.com`
- Noi lai link neu bi xuong dong trong OCR output.
- Chuan hoa protocol neu can.

#### Hanh dong MVP
- Mo lien ket.
- Sao chep link.
- Luu de xem sau.

#### Gia tri
- Hop voi screenshot bai viet, thong bao, chat, QR page info, email.

#### Dieu kien hoan thanh MVP
- Hien domain truoc khi mo.
- Khong tu dong redirect khi chua xac nhan.

### 4.7 Tinh nang hien thi ket qua phan tich

#### Muc tieu
Chuyen ket qua OCR thanh giao dien de hieu, de bam, de xac nhan.

#### Tinh nang MVP
- Hien thumbnail anh.
- Hien tung the theo loai thuc the.
- Hien confidence neu can.
- Hien nut action tuong ung.
- Hien nut xem toan bo van ban.
- Hien trang thai "khong tim thay thong tin phu hop" neu OCR co text nhung khong map duoc action.

#### Gia tri
- Day la noi bien cong nghe thanh gia tri that cho nguoi dung.

#### Dieu kien hoan thanh MVP
- Sau khi OCR xong, nguoi dung thay ngay danh sach action ro rang.
- Khong can doc raw text moi thao tac duoc.

### 4.8 Tinh nang xac nhan du lieu mo ho

#### Muc tieu
Tranh thao tac sai voi du lieu nhay cam hoac khong chac chan.

#### Tinh nang MVP
- Danh dau entity confidence thap/trung binh.
- Hien dialog xac nhan truoc khi:
  - tao reminder
  - mo URL
  - xu ly so tien mo ho
- Cho phep sua gia tri truoc khi xac nhan o cac case can thiet.

#### Gia tri
- Tang do tin tuong vao san pham.
- Giam rui ro hanh dong sai.

#### Dieu kien hoan thanh MVP
- Mọi relative time deu co buoc xac nhan.
- URL luon co buoc xem truoc domain.

### 4.9 Tinh nang luu ket qua scan

#### Muc tieu
Nguoi dung xem lai duoc nhung gi da xu ly truoc do.

#### Tinh nang MVP
- Luu ban ghi scan.
- Luu raw text, entities, actions co the thuc hien.
- Co danh sach lich su da luu.
- Mo lai chi tiet mot scan record.

#### Gia tri
- Screenshot khong chi duoc xu ly mot lan, ma tro thanh tai nguyen co the tim lai.

#### Dieu kien hoan thanh MVP
- Sau khi luu, nguoi dung thay scan trong lich su.
- Mo lai duoc ket qua va thong tin da detect.

### 4.10 Tinh nang dong bo du lieu

#### Muc tieu
Giu du lieu khong bi mat khi doi may hoac cai lai app.

#### Tinh nang MVP
- Luu metadata vao Firestore.
- Upload anh len Cloudinary khi nguoi dung chon luu.
- Luu URL anh, thumbnail, raw text, entities.

#### Gia tri
- Tao nen tang cho history cloud, tim kiem, nhac viec, da thiet bi.

#### Dieu kien hoan thanh MVP
- Record luu len cloud thanh cong.
- App doc lai duoc record da luu.

### 4.11 Tinh nang onboarding co ban

#### Muc tieu
Giup nguoi dung hieu ngay app dung de lam gi.

#### Tinh nang MVP
- 3 man hinh onboarding ngan.
- Giai thich:
  - app doc screenshot va de xuat hanh dong
  - co the share anh truc tiep vao app
  - OCR chu yeu xu ly tren thiet bi

#### Gia tri
- Giam do kho hieu cua mot san pham moi.

#### Dieu kien hoan thanh MVP
- Nguoi dung moi mo app lan dau se hieu luong su dung chinh.

## 5. Tinh nang quan trong nhung co the lam ngay sau MVP

Nhom nay co gia tri cao, nhung co the de sau khi MVP da chay on dinh.

### 5.1 Luu lien he
- Tao contact moi tu so dien thoai detect duoc.
- Dien san ten neu OCR nhan dien duoc dong ten ben canh.

Ly do de sau MVP:
- Can xu ly permission va UX ky hon.

### 5.2 Them su kien lich native day du
- Tao calendar event voi title, note, location.
- Cho nguoi dung chon lich dich.

Ly do de sau MVP:
- Tao event day du phuc tap hon reminder don gian.

### 5.3 Tim kiem lich su theo OCR text
- Tim theo tu khoa.
- Filter theo loai du lieu: lich hen, lien he, tien, link.

Ly do de sau MVP:
- Can toi uu indexing du lieu da luu.

### 5.4 Man hinh reminders rieng
- Danh sach reminder da tao tu ShotDo.
- Mo nguoc lai scan record goc.

Ly do de sau MVP:
- Can dong bo state giua app, local notification, backend.

### 5.5 Dang nhap nguoi dung
- Anonymous sign-in ban dau.
- Google sign-in o phase sau.

Ly do de sau MVP:
- Co the de app chay local truoc, roi them cloud sync sau.

## 6. Huong phat trien sau nay

Day la roadmap mo rong de ShotDo khong chi la OCR app, ma tro thanh cong cu "hieu screenshot".

### 6.1 Nhan dien thong tin chuyen khoan day du

#### Tinh nang
- Nhan dien ten ngan hang.
- Nhan dien so tai khoan.
- Nhan dien chu tai khoan.
- Nhan dien so tien.
- Nhan dien noi dung chuyen khoan.
- Gom thanh mot transfer card co cau truc.

#### Hanh dong
- Sao chep so tai khoan.
- Sao chep so tien.
- Sao chep noi dung.
- Sao chep tat ca.

#### Gia tri
- Rat phu hop voi thi truong Viet Nam.
- Tao su khac biet ro voi app OCR chung.

### 6.2 Nhan dien dia chi va mo ban do

#### Tinh nang
- Nhan dien dia chi Viet Nam.
- Tach thanh phan co ban: so nha, duong, quan/huyen, tinh/thanh pho.

#### Hanh dong
- Mo Google Maps.
- Sao chep dia chi.
- Luu dia diem.

### 6.3 Nhan dien ma van don va don vi giao hang

#### Tinh nang
- Nhan dien ma van don.
- Nhan dien ten don vi van chuyen.

#### Hanh dong
- Sao chep ma.
- Mo trang tracking neu support duoc.

### 6.4 Nhan dien san pham va deal

#### Tinh nang
- Nhan dien ten san pham.
- Nhan dien gia.
- Nhan dien thoi han khuyen mai.

#### Hanh dong
- Nhac truoc khi het deal.
- Luu vao wishlist.
- Theo doi gia sau nay.

### 6.5 Nhan dien email, tai khoan, ma so

#### Tinh nang
- Email
- Ma don hang
- Ma dat cho
- Ma OTP khong tu dong dien

#### Hanh dong
- Sao chep nhanh.
- Mo ung dung lien quan neu phu hop.

### 6.6 OCR nang cao hon

#### Tinh nang
- OCR server-side cho anh kho.
- Image enhancement truoc OCR.
- Support anh chup tu camera, khong chi screenshot.

#### Luu y
- Chi nen mo rong khi da can bang duoc giua chi phi, toc do va rieng tu.

### 6.7 iOS Share Extension

#### Tinh nang
- Nhan anh share truc tiep tu Photos, Safari, chat app tren iPhone.

#### Gia tri
- Mo rong tap nguoi dung.

### 6.8 AI parser thong minh hon

#### Tinh nang
- Hieu ngu canh cau van phuc tap.
- Gom nhieu dong thanh mot y nghia.
- Goi y action dua tren toan bo screenshot, khong chi tung entity rieng le.

Vi du:
- "Mai 2h gap Nam o tang 5" -> goi y 1 reminder co title day du
- "Chuyen khoan 250k cho An truoc 5h" -> nhan dien vua tien vua deadline

## 7. Thu tu uu tien phat trien tinh nang

Thu tu nen lam de ra gia tri nhanh nhat:

1. Nhan anh tu picker va share intent
2. OCR local
3. Detect phone, money, URL
4. Detect date/time
5. Result screen + action buttons
6. Luu ket qua local/cloud
7. Onboarding
8. History va tim kiem
9. Reminder center
10. Chuyen khoan, dia chi, van don, product intelligence

## 8. Tieu chi danh gia MVP thanh cong

MVP duoc coi la thanh cong neu:
- nguoi dung dua anh vao app de dang
- OCR doc duoc phan lon screenshot co text ro
- app detect tot 4 nhom entity chinh
- nguoi dung thuc hien duoc action ngay tai man hinh ket qua
- du lieu mo ho luon duoc xac nhan truoc
- nguoi dung luu va mo lai duoc lich su scan

## 9. Pham vi khong nen lam som

De tranh loang san pham, chua nen uu tien som:
- auto mo app ngan hang
- auto dien form tai app ngoai
- OCR cloud cho moi anh
- qua nhieu loai entity ngay tu ban dau
- workflow AI qua phuc tap khi du lieu thuc te chua du

## 10. De xuat cach su dung tai lieu nay

Co the dung `feature.md` theo 3 cach:
- Lam tai lieu scope de chot MVP.
- Lam checklist cho backlog task.
- Lam tai lieu giao tiep khi can bo sung wireframe, schema, hoac estimate.

Neu muon, buoc tiep theo minh co the tao them:
- `roadmap.md` de chia sprint/phase chi tiet
- `architecture.md` de mo ta clean architecture va folder structure
- backlog task ban dau cho Flutter + Firebase + Cloudinary
