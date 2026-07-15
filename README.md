# ShotDo

ShotDo la ung dung Flutter giup bien anh chup man hinh thanh cac hanh dong co the thuc hien ngay.

Thay vi nguoi dung phai mo lai anh, doc lai noi dung, nho thong tin va thao tac thu cong, ShotDo se:
- OCR anh chup man hinh
- nhan dien du lieu quan trong
- de xuat hanh dong phu hop
- cho phep luu lai de xem sau

## Bai toan san pham

Nguoi dung thuong chup man hinh de luu:
- lich hen
- so dien thoai
- so tien
- thong tin chuyen khoan
- duong dan

Nhung sau do van phai:
- copy lai du lieu
- tao reminder thu cong
- mo trinh duyet de vao link
- goi dien hoac nhan tin bang tay

ShotDo giai quyet bai toan do bang cach bien screenshot thanh action.

## Muc tieu MVP

Ban MVP tap trung vao 4 nhom du lieu:
- `date/time`
- `phone`
- `money`
- `url`

Action MVP:
- tao reminder
- them vao lich
- goi dien
- nhan SMS
- sao chep du lieu
- mo lien ket sau khi xac nhan
- luu ket qua scan

## Dinh huong ky thuat

- App duoc viet bang Flutter.
- OCR uu tien chay tren thiet bi bang ML Kit.
- Firebase dung lam backend cho auth, sync, history, analytics, reminder metadata.
- Cloudinary dung de luu anh goc va thumbnail khi nguoi dung chon luu hoac dong bo.
- OCR khong phu thuoc upload cloud trong MVP.

## Nguyen tac san pham

- Uu tien luong `Share -> ShotDo -> Phan tich -> Hanh dong`.
- Uu tien quyen rieng tu: OCR local mac dinh.
- Khong tu dong thuc hien action nhay cam.
- Du lieu mo ho bat buoc can xac nhan.
- Uu tien cac format pho bien cua nguoi dung Viet Nam.

## Tai lieu du an

- [plan.md](/Volumes/DATA/flutter/shot_do/plan.md): ke hoach trien khai tong the
- [feature.md](/Volumes/DATA/flutter/shot_do/feature.md): danh sach va pham vi tinh nang
- [rule.md](/Volumes/DATA/flutter/shot_do/rule.md): bo quy tac bat buoc khi phat trien

Thu tu uu tien tai lieu:
1. `rule.md`
2. `plan.md`
3. `feature.md`

## Yeu cau moi truong

- Flutter `3.44.2`
- Dart di kem theo Flutter `3.44.2`
- Uu tien dung `FVM` de khoa version

Neu may hien tai khong dung dung version tren, phai chay du an bang `FVM`.

## Cac lenh phat trien chuan

```bash
fvm flutter pub get
fvm flutter analyze
fvm flutter test
fvm dart format .
```

Neu co code generation:

```bash
fvm dart run build_runner build
```

## Quy tac phat trien quan trong

- Khong duoc tu y doi kien truc va cau truc thu muc da chot.
- Moi feature moi phai bam theo `feature-first + clean layers`.
- Moi file code khong duoc qua `600` dong.
- Moi file UI chi duoc co `1 class chinh duy nhat`.
- Khong viet private widget class trong cung file screen.
- Code dung chung dat trong `lib/core/` hoac `lib/shared/`.
- Code rieng cua tinh nang dat trong feature tuong ung.
- Moi thay doi deu phai qua `analyze` va `test` truoc khi xem la hoan thanh.

Chi tiet day du xem trong [rule.md](/Volumes/DATA/flutter/shot_do/rule.md).

## Cau truc du an muc tieu

```text
lib/
  app/
  core/
  features/
    home/
    image_input/
    ocr/
    entity_detection/
    actions/
    history/
    reminders/
    settings/
  shared/
```

Moi feature can tach ro:
- `presentation/`
- `application/`
- `domain/`
- `data/`

## Scope MVP can lam truoc

1. Setup architecture va nen tang du an
2. Nhan anh tu Photo Picker va Share Intent
3. OCR local bang ML Kit
4. Detect `phone`, `money`, `url`
5. Detect `date/time`
6. Hien ket qua va action buttons
7. Luu lich su scan
8. Dong bo Firebase + upload Cloudinary khi user chon luu
9. Onboarding va polish

## Huong phat trien sau MVP

- nhan dien thong tin chuyen khoan day du
- nhan dien dia chi va mo ban do
- nhan dien ma van don
- nhan dien san pham va deal
- tim kiem lich su nang cao
- reminder center
- iOS Share Extension
- AI parser thong minh hon

## Trang thai hien tai

Project hien dang o giai doan khoi tao va tai lieu hoa scope.

Da co:
- `plan.md`
- `feature.md`
- `rule.md`

Chua co day du:
- scaffold architecture theo feature-first
- setup Firebase
- setup Cloudinary
- OCR pipeline
- UI theo san pham that

## Dinh nghia hoan thanh cho moi task

Mot task chi duoc coi la xong khi:
- dung scope trong `feature.md`
- dung huong trong `plan.md`
- khong vi pham `rule.md`
- code da format
- `fvm flutter analyze` sach issue
- `fvm flutter test` pass

## Ghi chu bao mat

- OCR mac dinh nen chay local.
- Khong upload anh len cloud neu user chua chon luu hoac dong bo.
- Khong de API secret cua Cloudinary trong app.
- Firebase Security Rules phai gioi han user chi truy cap du lieu cua minh.

## Buoc tiep theo de bat dau code

1. Cau hinh `FVM` voi Flutter `3.44.2`
2. Scaffold cau truc `lib/` theo architecture da chot
3. Them package nen tang
4. Setup Firebase
5. Lam flow `Photo Picker`
6. Tich hop OCR bang ML Kit

README nay la diem vao chinh cua du an. Moi thay doi ve scope, rule hoac huong phat trien can duoc dong bo voi cac tai lieu lien quan.
# shot_do
