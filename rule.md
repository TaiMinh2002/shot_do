# Rule thuc hien du an ShotDo

## 1. Muc dich tai lieu

Tai lieu nay la bo quy tac bat buoc khi phat trien du an ShotDo.

Muc tieu:
- giu du an di dung huong theo `plan.md` va `feature.md`
- tranh vo cau truc khi them tinh nang moi
- giu code gon, de doc, de bao tri
- dam bao moi thay doi deu dat chat luong truoc khi xem la hoan thanh

Tat ca cong viec tiep theo cua du an phai uu tien tuan theo file nay.

## 2. Thu tu uu tien tai lieu

Neu co xung dot, uu tien theo thu tu sau:
1. `rule.md`
2. `plan.md`
3. `feature.md`
4. cac ghi chu tam thoi trong task

Khong duoc tu y bo qua rule. Neu co truong hop buoc phai lech rule, can dung lai va xin xac nhan truoc.

## 3. Rule ve Flutter version va FVM

### 3.1 Version chuan
- Du an su dung Flutter `3.44.2`.
- Moi thanh vien, moi may, moi CI environment deu phai dong nhat theo version nay.

### 3.2 Cach su dung
- Neu moi truong hien tai khong phai Flutter `3.44.2`, bat buoc dung `FVM`.
- Uu tien chay lenh theo dang:
  - `fvm flutter pub get`
  - `fvm flutter analyze`
  - `fvm flutter test`
  - `fvm dart format .`
  - `fvm dart run build_runner build`

### 3.3 Cam ket thuc thi
- Khong duoc dung `flutter` hoac `dart` global neu no khong map den version `3.44.2`.
- Can xem viec cau hinh `FVM` la mot phan bat buoc cua setup ban dau.
- Nen co file cau hinh version co dinh cho project de tranh sai lech moi truong.

## 4. Rule ve pham vi va huong phat trien

### 4.1 Bat buoc bam scope
- Moi tinh nang moi phai doi chieu voi `plan.md` va `feature.md` truoc khi lam.
- Uu tien MVP truoc, khong nhay sang tinh nang future khi MVP chua on dinh.
- Khong duoc tu y mo rong scope chi vi "lam them cho tien".

### 4.2 Thu tu phat trien
Phai bam uu tien sau:
1. architecture va nen tang
2. image input
3. OCR
4. entity detection MVP
5. action builder
6. history va cloud sync
7. onboarding va polish
8. future features

### 4.3 Khong lam som
- Khong uu tien auto mo app ngan hang.
- Khong uu tien OCR cloud cho moi anh.
- Khong uu tien AI parser phuc tap khi parser rule-based chua on.
- Khong them qua nhieu entity ngoai MVP trong giai doan dau.

## 5. Rule ve kien truc va cau truc thu muc

### 5.1 Kien truc bat buoc
Du an phai giu dung huong:
- `feature-first`
- `clean layers`
- tach ro `presentation`, `application`, `domain`, `data`

### 5.2 Cau truc tong quat phai bam
- `lib/app/`
- `lib/core/`
- `lib/features/`
- `lib/shared/`

### 5.3 Cau truc feature
Moi feature chi duoc phat trien trong vung cua no:
- `presentation/`
- `application/`
- `domain/`
- `data/`

Vi du:
- `lib/features/home/`
- `lib/features/image_input/`
- `lib/features/ocr/`
- `lib/features/entity_detection/`
- `lib/features/actions/`
- `lib/features/history/`
- `lib/features/reminders/`
- `lib/features/settings/`

### 5.4 Cam thay doi tuy tien
- Khong duoc tu y doi cau truc folder da chot.
- Khong duoc tu y doi kieu kien truc khi them feature moi.
- Khong duoc dat logic domain vao UI file.
- Khong duoc dat repository impl trong `presentation`.
- Khong duoc dat widget dung chung vao folder feature neu no duoc nhieu feature tai su dung.

### 5.5 Nguyen tac dat code dung noi
- Code dung chung toan app dat trong `lib/core/` hoac `lib/shared/`.
- Code chi phuc vu mot feature dat trong feature do.
- Widget rieng cua man nao dat trong feature cua man do.
- Utility lien quan mot domain cu the dat trong feature do, khong day het vao `shared`.

## 6. Rule ve quy mo file va to chuc code

### 6.1 Gioi han do dai file
- Moi file code khong duoc vuot qua `600` dong.
- Muc tieu la de doc, de review, de test, de tim loi.

### 6.2 Cach xu ly khi file dai
- Neu file co xu huong qua dai, phai tach thanh file nho hon.
- Tuy nhien khong duoc tach vuon vat vo ly lam phong folder du an.
- Chi tach khi viec tach giup ro vai tro, de test hon, de tai su dung hon.

### 6.3 Ngoai le hop ly
- File generated nhu `*.g.dart`, `*.freezed.dart` khong tinh vao gioi han thu cong.
- File config co tinh chat metadata co the linh hoat hon neu can.

## 7. Rule ve UI va widget

### 7.1 Moi file UI chi co 1 class chinh
- Moi file UI chi duoc co `1 class chinh duy nhat`.
- Khong duoc tao them private class trong cung file UI.
- Khong viet kieu `_HeaderWidget`, `_BodySection`, `_ActionList` trong cung file man hinh.

### 7.2 Cach tach UI dung
- Neu man hinh lon, tach thanh cac widget nho o file rieng.
- Moi widget co trach nhiem ro rang.
- Moi file widget cung nen co 1 class chinh duy nhat.

### 7.3 Nguyen tac doc duoc
- Khong viet mot widget khong lo gom qua nhieu layout trong 1 file.
- Uu tien tach theo block giao dien:
  - screen
  - section
  - card
  - item
  - state view

### 7.4 Trang thai UI
- Can tach ro loading, success, empty, error.
- Khong tron logic xu ly du lieu phuc tap trong `build()`.
- Moi man hinh quan trong phai de nguoi khac doc vao la hieu nhanh cau truc giao dien.

## 8. Rule ve phan tach trach nhiem

### 8.1 Presentation
Chi chiu trach nhiem:
- render UI
- nhan interaction
- show state
- dieu huong UI

### 8.2 Application
Chi chiu trach nhiem:
- use case
- workflow dieu phoi
- goi repository
- map state cho presentation

### 8.3 Domain
Chi chiu trach nhiem:
- entity
- value object
- business rule
- parser rule
- validation rule

### 8.4 Data
Chi chiu trach nhiem:
- datasource
- model
- DTO
- repository implementation
- mapping data vao domain

### 8.5 Cam pha rang buoc
- Khong de UI goi truc tiep Firebase neu da co repository/use case.
- Khong de parser business nam trong widget.
- Khong de Cloudinary upload code nam trong screen.

## 9. Rule ve dung chung va viet rieng

### 9.1 Viet dung chung khi
- logic duoc tai su dung tu 2 feature tro len
- widget duoc tai su dung tu 2 man tro len
- rule xu ly du lieu la cross-feature

### 9.2 Viet rieng khi
- logic chi phuc vu mot feature
- widget chi phuc vu mot screen
- state chi thuoc mot use case cu the

### 9.3 Khong lam qua tay
- Khong abstract som khi chua co nhu cau that.
- Khong dua moi thu vao `shared` chi vi muon "dep".
- Shared phai la shared that, khong phai noi gom code lung tung.

## 10. Rule ve coding style

### 10.1 Nguyen tac chung
- Code phai ro y do.
- Uu tien ten bien, ten class, ten method de hieu thay vi comment dai dong.
- Comment chi viet khi logic khong tu no ro rang.

### 10.2 Dat ten
- Ten file, folder dung `snake_case`.
- Ten class dung `PascalCase`.
- Ten bien, method dung `camelCase`.
- Ten phai theo nghia nghiep vu, tranh ten chung chung nhu `data`, `item`, `temp`, `helper`.

### 10.3 Do phuc tap
- Mot method khong nen qua dai.
- Mot class khong nen om qua nhieu trach nhiem.
- Neu 1 widget hoac class dang lam qua nhieu viec, phai tach.

### 10.4 Hardcode
- Han che hardcode string, spacing, duration, color, radius.
- Gia tri dung chung can dua vao constants/theme/token.

### 10.5 Analyzer va lints
- Phai ton trong `analysis_options.yaml`.
- Khong duoc ignore warning tuy tien.
- Neu can ignore, phai co ly do ro rang va pham vi nho nhat co the.

## 11. Rule ve state management va async flow

### 11.1 Dinh huong
- Uu tien state management nhat quan theo architecture da chot.
- Async pipeline `nhan anh -> OCR -> detect -> build action -> save` phai tach ro cac buoc.

### 11.2 Cam tron lan
- Khong duoc viet mot controller om toan bo logic cua nhieu feature.
- Khong duoc de state toan cuc khong kiem soat.
- Khong duoc de UI tu xu ly async side effect phuc tap neu co the dua xuong application layer.

### 11.3 Error handling
- Moi flow async quan trong phai co:
  - loading
  - success
  - empty neu can
  - error

## 12. Rule ve test va dieu kien hoan thanh

### 12.1 Bat buoc sau moi thay doi
Moi lan:
- them tinh nang moi
- phat trien tiep tinh nang hien co
- fix bug

thi deu bat buoc:
- chay test
- chay analyze
- xu ly het problem truoc khi xem la xong

### 12.2 Lenh can uu tien
- `fvm flutter analyze`
- `fvm flutter test`

Neu co code generation:
- `fvm dart run build_runner build`

Neu co format:
- `fvm dart format .`

### 12.3 Tieu chuan pass
- `flutter analyze` khong con error, warning, issue can xu ly
- `flutter test` pass
- khong de lai code vo, TODO vo chu, hoac bug ro rang

### 12.4 Test theo loai thay doi
- Parser moi: bat buoc co unit test.
- Business rule moi: uu tien co unit test.
- Widget UI quan trong: can co widget test neu hop ly.
- Bug fix: neu co the, phai them test de chan bug quay lai.

### 12.5 Khong duoc danh dau hoan thanh neu
- chua chay analyze
- chua chay test
- van con warnings/issues chua xu ly
- tinh nang chay duoc nhung sai architecture

## 13. Rule ve chat luong nghiep vu san pham

### 13.1 OCR va rieng tu
- OCR mac dinh uu tien local.
- Khong upload anh len cloud neu user chua chon luu hoac dong bo.
- Khong thay doi thong diep rieng tu cua san pham mot cach vo tinh.

### 13.2 Du lieu mo ho
- Moi relative time deu can xac nhan truoc khi tao reminder.
- URL can hien domain truoc khi mo.
- Gia tri tien mo ho chi duoc goi y, khong auto chac chan.

### 13.3 Hanh dong nhay cam
- Khong tu dong goi dien.
- Khong tu dong mo link.
- Khong tu dong tao reminder.
- Khong tu dong thao tac tai chinh.

### 13.4 Uu tien thi truong Viet Nam
Khi viet parser hoac action, can uu tien support:
- cach viet so tien Viet
- cach noi ngay gio bang tieng Viet
- dinh dang so dien thoai Viet Nam
- ngu canh screenshot pho bien tai Viet Nam

## 14. Rule ve Firebase va Cloudinary

### 14.1 Firebase
- Firestore schema phai bam theo `plan.md`.
- Security Rules phai duoc tinh den ngay tu luc thiet ke data.
- Moi user chi duoc truy cap du lieu cua chinh ho.

### 14.2 Cloudinary
- Khong duoc de API secret trong app.
- Uu tien signed upload thong qua backend hoac Cloud Function.
- Chi upload anh khi user chu dong luu/dong bo.

### 14.3 Dong bo du lieu
- Metadata cloud phai map ro voi `scanId`, `userId`, `sourceType`.
- Khong de app upload anh vo danh khong quan ly.

## 15. Rule ve review va thay doi kien truc

### 15.1 Khi them feature moi
Phai tu kiem tra:
- feature nay nam o folder nao
- layer nao chiu trach nhiem
- co dang lam vo rule UI 1 file 1 class khong
- co vuot 600 dong khong
- co phan nao nen shared khong
- co phan nao dang shared vo ly khong

### 15.2 Khi can doi cau truc
Chi duoc doi khi:
- co ly do ro rang
- co anh huong tich cuc dai han
- da duoc xac nhan truoc

Neu chua co xac nhan:
- khong duoc refactor lon
- khong duoc "tien tay doi kien truc"

## 16. Rule ve tai lieu va dong bo kien thuc

### 16.1 Cap nhat tai lieu
Neu thay doi scope, architecture, hoac rule quan trong:
- cap nhat `plan.md` neu anh huong ke hoach
- cap nhat `feature.md` neu anh huong tinh nang
- cap nhat `rule.md` neu thay doi quy tac thuc thi

### 16.2 Khong de tai lieu lech code
- Code va tai lieu phai dong bo.
- Khong de du an chay mot dang, tai lieu viet mot neo.

## 17. Checklist truoc khi coi 1 task la hoan thanh

Mot task chi duoc xem la xong khi da qua het checklist sau:

1. Dung scope trong `feature.md`
2. Dung huong trong `plan.md`
3. Khong vo `rule.md`
4. Khong doi cau truc tuy tien
5. Moi file code <= 600 dong
6. Moi file UI chi co 1 class chinh
7. Logic dung chung dat dung cho
8. Logic rieng dat dung feature
9. Code da format
10. `fvm flutter analyze` sach problem
11. `fvm flutter test` pass
12. Da xu ly cac case loading, error, empty neu can
13. Khong co action nhay cam tu dong trai rule

## 18. Ket luan

`rule.md` la bo khung ky luat de giu ShotDo phat trien on dinh, de doc, de mo rong va khong mat huong.

Moi cong viec ve sau can xem day la rule thuc thi mac dinh cua du an.
