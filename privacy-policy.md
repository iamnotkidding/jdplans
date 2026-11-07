# jdPlans 개인정보처리방침

시행일: 2026년 11월 7일

jdPlans(이하 "앱")는 회원가입 · 로그인이 없고, 광고 · 분석 도구를 넣지 않았으며, **개발자가 운영하는 서버가 없습니다.**
사용자가 만든 내용은 사용자의 기기 안에만 저장되고 개발자에게 전송되지 않습니다.

## 1. 기기 안에만 저장하는 정보
계획표와 항목(일정 · 금액 · 메모 · 일기 · 가계부 · 차량 기록 · 투약 기록 등), 사진 · 파일 사본, 음성 메모, 위치 기록,
사람 · 명함의 얼굴 특징, 계정 · 비밀번호, 공구함의 측정 사진은 **사용자의 기기 안 데이터베이스 · 앱 폴더에만** 저장됩니다.
개발자는 이 내용에 접근할 수 없습니다. 계획표나 앱을 지우면 기기에서 함께 지워집니다.

Android 기기 백업이 켜져 있으면 운영체제가 앱 데이터를 사용자의 Google 계정 백업 또는 새 기기 이전에 포함할 수 있습니다
(비밀번호는 기기 키로 암호화되어 다른 기기에서는 풀리지 않습니다). 이 백업은 Google 정책에 따라 처리되며 개발자에게 전달되지 않습니다.

## 2. 인터넷을 쓰는 기능 (사용자가 그 기능을 쓸 때만)
앱은 아래 기능을 쓸 때만, 적힌 정보만 해당 서비스로 보냅니다. 각 서비스의 처리는 그 서비스의 정책을 따릅니다.

| 기능 | 받는 곳 | 보내는 정보 |
|---|---|---|
| 일기 날씨 | Open-Meteo (api.open-meteo.com · archive-api.open-meteo.com) | 소수 둘째 자리(약 1km)로 줄인 위도 · 경도, 날짜 |
| 장소 찾기 (장소 · 위치 계획표) | 휴대폰의 지오코더, 결과가 없으면 OpenStreetMap Nominatim | 사용자가 입력한 장소 이름 |
| 지도 (위치 기록 · 사진 지도) | OpenStreetMap 지도 서버 | 화면에 보이는 지도 구역 번호 (기록한 위치 목록은 보내지 않음) |
| 관심 주식 시세 | 네이버 증권 | 사용자가 추가한 종목 코드 · 검색어 |
| 관심 소식 | Google 뉴스, (사용자가 키를 넣은 경우) 네이버 검색 API | 사용자가 정한 관심 주제 낱말. 네이버 키는 기기에만 저장 |
| 링크 지켜보기 | 사용자가 적은 웹 주소 | 그 페이지를 읽어 오는 일반 웹 요청 |
| 얼굴 알아보기 준비 | Google Play 서비스 (ML Kit 모듈 내려받기) | 기기의 Play 서비스가 모듈을 받음 (얼굴 사진은 보내지 않음) |

계획표 · 일기 · 메모 · 사진 · 위치 기록 등 사용자 내용은 위 서비스로 보내지 않습니다.

## 3. 공유 · 인쇄 · 저장 (사용자가 고를 때만)
인쇄 · PDF · 이미지 공유, 계획표 파일(.jdplan) 보내기, 파일 보관함의 공유는 사용자가 고른 앱으로만 전달됩니다.
"블루투스로 보내기"는 계획표 하나를 사용자가 고른 근처 기기로 직접 보냅니다(인터넷 · 서버를 거치지 않음).
"사진 앱에 저장"은 이미지를 기기의 사진 폴더(Pictures/jdPlans)에 저장합니다.
"전체 백업"은 계획표 · 위치 기록 · 사진 · 파일 보관함 · 음성 메모 · 앱 설정을 파일 하나(.jdbackup)로 묶어 사용자가 고른 곳에만 저장합니다.
비밀번호 보관함의 비밀번호와 앱 잠금 번호 · 패턴은 넣지 않습니다. 백업 파일을 다른 사람과 나누면 그 안의 위치 기록 · 사진도 함께 전해지니 조심해 주세요.

## 4. 권한과 쓰는 곳
- **위치**: 운동 체크의 "확인", 장소 정하기, 일기 날씨에서 지금 위치를 한 번 읽습니다.
  **위치 기록** 계획표에서 기록을 켠 동안에만 알림을 띄운 채(포그라운드 서비스) 정한 간격마다 위치를 읽어 기기 안에만 쌓습니다. 백그라운드 위치 권한은 요청하지 않습니다.
- **사진 위치 (ACCESS_MEDIA_LOCATION)**: 사진 스크랩에서 사용자가 고른 사진의 촬영 위치(EXIF)를 읽어 지도에 표시합니다.
- **카메라**: 사진을 찍을 때, "사람 · 명함"에서 "카메라로 비춰 알아보기"를 연 동안만 씁니다.
  얼굴 특징은 휴대폰 안에서만 계산(ML Kit 얼굴 찾기 · TensorFlow Lite · 앱에 든 MobileFaceNet 모델)해 기기 안에만 저장합니다. 다른 사람의 얼굴은 그 사람의 동의를 받아 등록해 주세요.
- **마이크**: 음성 메모를 녹음하는 동안, 한글 · 영어 "따라 하기"를 누른 동안만 씁니다. 녹음은 기기 안에만 저장합니다.
  "글로 바꾸기" · "따라 하기"는 휴대폰에 설치된 음성 인식 서비스(예: Google 음성 인식)를 쓰며, 그 처리는 해당 서비스의 정책을 따릅니다.
- **근처 기기 (블루투스)**: 블루투스로 계획표를 주고받을 때만 씁니다. 기기 찾기는 위치를 알아내지 않도록(neverForLocation) 선언했습니다.
- **알림 · 정확한 알람 · 부팅 후 다시 걸기**: 사용자가 켠 일정 · 메모 알림, 링크 지켜보기 알림에만 씁니다.
- **미디어 재생 (포그라운드 서비스)**: 영어 문장 · 글자 읽어 주기를 화면이 꺼져도 이어 들을 때 씁니다.
- **생체 인증 · 화면 잠금**: 잠근 계획표를 열 때 안드로이드 확인 창만 띄우며, 지문 · 얼굴 정보는 앱이 받지 않습니다.
  앱 4자리 번호 · 패턴은 되돌릴 수 없게 바꾼 값(PBKDF2)으로만 저장합니다.
- 사진 · 파일은 사용자가 갤러리 앱 · 운영체제의 선택 창에서 고른 것만 씁니다.

## 5. 아동
앱에는 아이와 함께 쓰는 계획표 · 학습 게임이 있지만, 개인정보를 수집하지 않으므로 아동의 개인정보도 수집하지 않습니다. 광고가 없습니다.

## 6. 데이터 삭제
앱에서 계획표 · 기록을 지우거나 앱을 삭제하면 기기 안의 데이터가 삭제됩니다. 개발자 서버에 남는 데이터는 없습니다.

## 7. 변경 · 문의
방침이 바뀌면 이 문서의 시행일을 고칩니다. 개인정보 · 앱 사용에 관한 문의는 아래 메일로 보내 주세요.

- 문의 메일: red.aengmoo@gmail.com

---

# jdPlans Privacy Policy (English)

Effective: November 7, 2026

jdPlans has no account or sign-in, contains no ads or analytics, and **the developer runs no server.** Everything you create stays on your device and is never sent to the developer.

**Stored only on your device:** plans and entries (schedules, money, memos, diary, ledger, car log, medication log, …), copies of photos and files, voice memos, location logs, face features for "People & business cards", saved account passwords (encrypted with an Android Keystore key), and Toolbox measurement photos. Deleting a plan or uninstalling removes them. If Android backup is on, the OS may include app data in your Google backup or device transfer; this is handled by Google, not the developer.

**Internet, only when you use the feature, sending only what is listed:**
- Diary weather — Open-Meteo: latitude/longitude rounded to ~1 km, and the date.
- Place search — the phone's geocoder, otherwise OpenStreetMap Nominatim: the place name you typed.
- Maps — OpenStreetMap tile servers: the visible map tile numbers (never your location log).
- Stock prices — Naver Finance: the stock codes and search words you add.
- News — Google News and, if you entered your own key, the Naver Search API: your topic words (the key stays on the device).
- Link watch — the web addresses you enter.
- Face recognition setup — Google Play services downloads the ML Kit module (no face photos are sent).

**Sharing:** printing, PDF/image sharing, plan files and file sharing go only to the app you choose; "Send via Bluetooth" sends one plan directly to a nearby device. "Full backup" saves plans, location logs, photos, stored files, voice memos and app settings into one file (.jdbackup) only where you choose — vault passwords and app lock codes are not included. Anyone you give a backup file to can see the locations and photos in it.

**Permissions:** location (place check, weather, and — only while you turn on a Location log, with a notification — at your chosen interval; no background-location permission), photo location (to map photos you pick), camera (taking photos, on-device face recognition), microphone (voice memos, "repeat after me"; speech-to-text uses the phone's installed speech service), nearby devices (Bluetooth transfer, neverForLocation), notifications and exact alarms (reminders you set), media-playback foreground service (reading sentences aloud), biometrics/screen lock (opening locked plans; the app never receives biometric data).

**Children:** the app includes plans and learning games used with children, but it collects no personal data from anyone and shows no ads.

**Contact:** red.aengmoo@gmail.com
