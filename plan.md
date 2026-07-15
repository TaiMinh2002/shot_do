# Ke hoach trien khai du an ShotDo

## 1. Tong quan san pham

### 1.1 Tam nhin
ShotDo la ung dung Flutter giup bien anh chup man hinh thanh cac hanh dong co the thuc hien ngay, thay vi nguoi dung phai tu doc, nho va nhap lai thong tin.

### 1.2 Bai toan can giai quyet
Nguoi dung thuong chup man hinh de luu:
- lich hen
- so dien thoai
- so tien
- thong tin chuyen khoan
- duong dan

Nhung sau do van phai thao tac thu cong nhu sao chep, tao nhac, them lich, goi dien, mo link. ShotDo se OCR anh, phan tich thuc the va hien thi cac action phu hop.

### 1.3 Muc tieu MVP
Ban MVP chi tap trung vao 4 nhom du lieu:
- ngay gio
- so dien thoai
- so tien
- URL

Action MVP:
- tao loi nhac
- them vao lich
- goi dien
- nhan SMS
- sao chep gia tri
- mo lien ket sau khi nguoi dung xac nhan
- luu ket qua de xem lai

## 2. Nguyen tac san pham

### 2.1 Nguyen tac trai nghiem
- Uu tien luong `Share -> ShotDo -> Phan tich -> Hanh dong`.
- Han che xin quyen rong; uu tien Android Photo Picker thay vi doc toan bo thu vien.
- Khong tu dong thuc hien action nhay cam.
- Moi ket qua co do tin cay; du lieu mo ho bat buoc xac nhan.

### 2.2 Nguyen tac ky thuat
- OCR uu tien chay tren thiet bi de giam chi phi va tang toc do.
- Backend chi dung cho dong bo, luu tru metadata, lich su, reminder, analytics va user state.
- Anh goc chi dua len cloud khi nguoi dung chon luu hoac can dong bo.

## 3. Pham vi MVP va ngoai MVP

### 3.1 Trong pham vi MVP
- Chon anh bang Photo Picker.
- Nhan anh tu Share Intent tren Android.
- OCR text tu anh chup man hinh.
- Trich xuat `date/time`, `phone`, `money`, `url`.
- Chuan hoa du lieu theo ngu canh Viet Nam.
- Hien thi danh sach the action theo tung thuc the.
- Luu ket qua da xu ly.
- Dong bo du lieu nguoi dung len Firebase.

### 3.2 Ngoai MVP
- Tu dong dien thong tin vao app ngan hang.
- Nhan dien san pham chinh xac.
- Nhan dien dia chi, ma van don, email, transfer card day du.
- iOS Share Extension ngay o phase dau.
- OCR server-side cho anh phuc tap.

## 4. Kien truc tong the

### 4.1 Kien truc muc cao
1. Flutter app nhan anh tu Photo Picker hoac Share Intent.
2. App tien xu ly anh: resize, normalize orientation, compress neu can.
3. OCR bang ML Kit Text Recognition tren thiet bi.
4. Entity Detection tach cac thuc the co cau truc.
5. Action Builder tao danh sach hanh dong theo tung thuc the.
6. Neu nguoi dung chon luu:
   - upload anh len Cloudinary
   - luu metadata va ket qua OCR vao Firebase
7. Firebase dong bo lich su, action da luu, reminder, cai dat va analytics.

### 4.2 Vai tro cua Firebase
Firebase dung lam backend cho:
- Firebase Authentication: dang nhap an danh hoac Google o phase sau
- Cloud Firestore: luu user, scan history, parsed entities, saved actions
- Firebase Cloud Functions: xu ly tac vu backend nhe, webhook, cleanup, sync
- Firebase Cloud Messaging: thong bao nhac viec neu can
- Firebase Analytics / Crashlytics: theo doi su dung va loi

### 4.3 Vai tro cua Cloudinary
Cloudinary dung cho:
- luu anh goc nguoi dung da chon luu
- tao thumbnail va version toi uu
- truy cap CDN nhanh cho man hinh lich su
- bien doi anh khi can preview kich thuoc nho

Luu y:
- Khong dua Cloudinary vao OCR pipeline bat buoc cua MVP.
- OCR van nen xu ly local de dung voi thong diep "du lieu duoc xu ly tren thiet bi".
- Chi upload khi nguoi dung chu dong luu ket qua hoac bat dong bo anh.

## 5. De xuat cau truc code Flutter

### 5.1 Kien truc ung dung
Nen ap dung `feature-first + clean layers`:

- `lib/app/`
- `lib/core/`
- `lib/features/onboarding/`
- `lib/features/home/`
- `lib/features/image_input/`
- `lib/features/ocr/`
- `lib/features/entity_detection/`
- `lib/features/actions/`
- `lib/features/history/`
- `lib/features/reminders/`
- `lib/features/settings/`
- `lib/shared/`

### 5.2 Layer trong moi feature
- `presentation/`: screen, widget, state
- `application/`: use case, coordinator
- `domain/`: entity, value object, rule
- `data/`: datasource, model, repository impl

### 5.3 State management
De xuat dung `Riverpod` vi:
- de tach state theo feature
- de test
- hop voi async pipeline OCR -> parse -> action

Neu ban da quen Bloc thi Bloc van duoc, nhung neu lam moi tu dau thi Riverpod se gon hon.

## 6. Danh sach tinh nang chi tiet theo module

### 6.1 Onboarding
- 3 man onboarding gioi thieu gia tri san pham
- giai thich quy trinh share anh vao app
- nhan manh xu ly local va quyen rieng tu

### 6.2 Image Input
- chon anh bang Android Photo Picker
- nhan anh tu Share Intent
- validate format anh
- luu file tam de OCR

### 6.3 OCR
- doc text tu anh
- lay block, line, raw text
- giu lai toa do neu can cho phase sau
- luu raw OCR text vao local state

### 6.4 Entity Detection
- detect `date/time`
- detect `phone`
- detect `money`
- detect `url`
- score confidence
- chuan hoa output

### 6.5 Action Builder
- map entity -> action
- date/time -> reminder, calendar, copy
- phone -> call, sms, copy, save contact
- money -> copy, save
- url -> open, copy, save for later

### 6.6 Result Screen
- hien thumbnail anh
- hien raw text khi nguoi dung can xem
- hien danh sach the action
- cho phep chinh sua truoc khi xac nhan voi data mo ho

### 6.7 Saved History
- luu ban ghi scan
- filter theo loai entity
- search theo OCR text
- mo lai ket qua va anh goc

### 6.8 Reminders
- danh sach reminder da tao tu app
- deep link ve scan record goc
- dong bo voi Firestore

## 7. Thiet ke du lieu

### 7.1 Firestore collections de xuat

`users/{userId}`
- displayName
- photoUrl
- createdAt
- lastActiveAt
- settings

`scan_records/{scanId}`
- userId
- originalImageUrl
- thumbnailUrl
- localOnly
- rawText
- detectedLanguage
- confidenceSummary
- sourceType (`share_intent`, `photo_picker`)
- createdAt
- updatedAt

`scan_records/{scanId}/entities/{entityId}`
- type (`date_time`, `phone`, `money`, `url`)
- rawValue
- normalizedValue
- confidence
- startIndex
- endIndex
- metadata

`saved_actions/{actionId}`
- userId
- scanId
- entityId
- actionType
- payload
- status
- createdAt

`reminders/{reminderId}`
- userId
- scanId
- title
- remindAt
- sourceText
- createdAt
- status

### 7.2 Cloudinary folder strategy
- `shotdo/users/{userId}/originals/`
- `shotdo/users/{userId}/thumbs/`

Metadata nen gan:
- `scanId`
- `userId`
- `sourceType`
- `createdAt`

## 8. Luong xu ly chi tiet

### 8.1 Luong chinh
1. Nguoi dung share anh hoac chon anh.
2. App luu anh tam vao local cache.
3. App resize anh neu kich thuoc qua lon.
4. OCR text bang ML Kit.
5. Parser tach line va raw text.
6. Entity detector tim pattern va tinh confidence.
7. Action builder tao list action.
8. UI hien ket qua de nguoi dung xac nhan.
9. Neu nguoi dung chon luu:
   - upload anh len Cloudinary
   - luu record vao Firestore
10. Neu nguoi dung tao reminder:
   - luu local
   - dong bo Firebase

### 8.2 Luong du lieu mo ho
Neu confidence trong khoang `0.65 - 0.89`:
- hien hop xac nhan
- cho phep chinh sua gia tri
- chi tao action sau khi user dong y

Neu confidence `< 0.65`:
- khong goi y action nguy hiem
- chi hien raw text hoac "co the la..."

## 9. Xu ly domain dac thu Viet Nam

### 9.1 So tien
Can viet bo parser rieng cho:
- `250k`
- `1tr2`
- `50 nghin`
- `1.500.000d`
- `250,000 VND`

Rule:
- `k` = nghin
- `tr` = trieu
- `1tr2` = 1.200.000
- gia tri mo ho nhu `2 cu` chi nen danh dau "can xac nhan"

### 9.2 Thoi gian
Can support:
- `mai luc 8h`
- `chieu mai`
- `toi nay`
- `thu hai tuan sau`
- `khoang 8 gio toi`

Can co bang rule:
- sang = 08:00 fallback
- chieu = 15:00 fallback
- toi = 20:00 fallback

Tat ca relative time deu can man hinh xac nhan truoc khi tao reminder.

### 9.3 So dien thoai
Can normalize:
- `+84 987 654 321` -> `0987654321`
- van luu song song `rawValue` va `normalizedValue`

### 9.4 URL
Can xu ly:
- `www.example.com`
- URL xuong dong
- domain thieu protocol

Action mo link phai hien domain truoc khi mo.

## 10. Bao mat va rieng tu

### 10.1 Nguyen tac
- OCR local mac dinh
- upload anh la tuy chon
- khong tu dong mo link, goi dien, tao reminder khi chua xac nhan

### 10.2 Firebase Security Rules
- moi user chi doc/ghi du lieu cua chinh ho
- validate field bat buoc
- khong cho ghi overwrite userId cua nguoi khac

### 10.3 Cloudinary Security
De xuat:
- upload thong qua signed upload tu backend hoac Cloud Function
- tranh embed API secret trong app
- gioi han folder theo `userId`

## 11. De xuat package Flutter

### 11.1 Core
- `flutter_riverpod`
- `go_router`
- `freezed`
- `json_serializable`
- `intl`
- `collection`

### 11.2 Image + OCR
- `image_picker` hoac package tuong thich Photo Picker
- `receive_sharing_intent`
- `google_mlkit_text_recognition`
- `image`
- `path_provider`

### 11.3 Firebase
- `firebase_core`
- `firebase_auth`
- `cloud_firestore`
- `firebase_analytics`
- `firebase_crashlytics`
- `firebase_messaging`
- `cloud_functions`

### 11.4 Utilities
- `url_launcher`
- `flutter_contacts`
- `permission_handler` chi khi that su can
- `shared_preferences` hoac `hive`
- `device_calendar` neu can them lich native

## 12. Ke hoach trien khai theo phase

### Phase 0 - Khoi tao nen tang
Muc tieu:
- setup architecture Flutter
- setup Firebase project
- setup Cloudinary environment
- chuan hoa folder structure

Cong viec:
- tao project Firebase dev
- them Android app vao Firebase
- cau hinh `google-services.json`
- them packages nen tang
- setup router, theme, dependency base
- tao file env va config wrapper

Deliverable:
- app chay duoc voi skeleton man hinh
- ket noi Firebase thanh cong

### Phase 1 - Input anh
Muc tieu:
- app nhan anh tu picker va share intent

Cong viec:
- home screen
- photo picker flow
- Android share intent flow
- image preview screen
- temp file handling

Deliverable:
- user dua duoc anh vao app tu 2 nguon

### Phase 2 - OCR pipeline
Muc tieu:
- doc duoc van ban tu screenshot

Cong viec:
- xu ly resize/rotate
- integrate ML Kit
- luu raw OCR output
- loading state + error state

Deliverable:
- app hien duoc raw text sau khi phan tich anh

### Phase 3 - Entity detection MVP
Muc tieu:
- detect 4 loai entity chinh

Cong viec:
- viet regex + heuristics cho `phone`, `money`, `url`
- viet parser cho `date/time`
- build confidence score
- viet unit test cho parser tieng Viet

Deliverable:
- app tra ra danh sach entity da chuan hoa

### Phase 4 - Action builder + ket qua
Muc tieu:
- bien entity thanh hanh dong co the bam

Cong viec:
- result card UI
- action dispatcher
- copy / call / sms / open link
- reminder confirm dialog
- open calendar flow

Deliverable:
- user co the thuc hien action tu ket qua OCR

### Phase 5 - Luu lich su + dong bo cloud
Muc tieu:
- luu ket qua va dong bo du lieu

Cong viec:
- upload anh len Cloudinary khi user chon luu
- tao `scan_record` tren Firestore
- luu entities, actions, reminders
- danh sach history + search co ban

Deliverable:
- co man hinh lich su va doc lai ket qua da luu

### Phase 6 - Hoan thien MVP
Muc tieu:
- on dinh hoa, tracking va release noi bo

Cong viec:
- onboarding
- analytics
- crashlytics
- polish UX
- test tren nhieu kieu screenshot
- viet README va checklist release

Deliverable:
- ban MVP co the demo va test user that

## 13. Ke hoach test

### 13.1 Unit test
- parser so tien Viet Nam
- parser so dien thoai
- parser URL
- parser thoi gian tuong doi
- confidence scoring

### 13.2 Widget test
- home screen
- loading screen
- result card rendering
- confirmation dialog

### 13.3 Manual QA
- screenshot chat
- screenshot chuyen khoan
- screenshot co link
- screenshot co nhieu thuc the cung luc
- anh mo, lech, kich thuoc lon

## 14. Rui ro ky thuat va cach giam thieu

### 14.1 Nhan dien thoi gian tieng Viet kho
Giam thieu:
- rule-based parser truoc
- bat xac nhan voi du lieu relative

### 14.2 OCR sai voi anh mo hoac font la
Giam thieu:
- resize va tang contrast neu can
- cho user xem raw text

### 14.3 Ranh gioi rieng tu du lieu
Giam thieu:
- OCR local
- chi upload khi user luu
- thong bao ro trong onboarding va settings

### 14.4 Cloudinary upload security
Giam thieu:
- signed upload qua backend
- khong de secret trong app

## 15. Uoc luong thu tu thuc hien

Neu lam MVP theo cach gon va tap trung, thu tu uu tien nen la:
1. setup Firebase + architecture
2. photo picker + share intent
3. OCR local
4. detect phone/money/url
5. detect date/time
6. result action screen
7. luu Firestore + upload Cloudinary
8. history + reminders
9. onboarding + polish

## 16. Dinh nghia thanh cong cho MVP

MVP duoc xem la dat khi:
- nguoi dung dua duoc screenshot vao app trong duoi 2 thao tac
- app OCR thanh cong voi da so screenshot co text ro
- app detect on dinh 4 loai entity chinh
- nguoi dung bam action truc tiep tu ket qua
- co the luu va mo lai lich su scan
- du lieu nhay cam khong bi tu dong thuc hien khi chua xac nhan

## 17. Huong mo rong sau MVP

- nhan dien thong tin chuyen khoan day du
- nhan dien dia chi va mo ban do
- tracking ma van don
- iOS share extension
- AI parser nang cao cho cac cau mo ho
- nhan dien san pham / deal / wishlist
- gom nhieu screenshot thanh mot workflow

## 18. De xuat buoc tiep theo ngay bay gio

Buoc hop ly nhat de bat dau:
1. setup Firebase cho app Flutter
2. chot architecture va package
3. lam `Photo Picker`
4. tich hop `ML Kit OCR`
5. viet parser MVP cho `phone`, `money`, `url`, `date/time`

Neu muon, buoc tiep theo minh co the lam tiep cho ban:
- scaffold cau truc `lib/features/...`
- cap nhat `pubspec.yaml`
- setup Firebase packages
- tao skeleton cho OCR pipeline MVP
