# Eye & Water Reminder App

**Ung dung nhac nho cham soc mat va uong nuoc** - Developed by **Pham Le Ngoc Son**

---

## Gioi thieu

**Eye & Water Reminder** la ung dung Android duoc phat trien boi **Pham Le Ngoc Son**, giup nguoi dung bao ve suc khoe mat va duy tri thoi quen uong nuoc deu dan hang ngay.

Trong thoi dai so, viec ngoi truoc man hinh may tinh va dien thoai qua lau co the gay hai cho mat va khien co the thieu nuoc. Ung dung nay se tu dong nhac nho ban:

- Nghi ngoi mat dinh ky de giam cang thang thi giac (Digital Eye Strain)
- Uong nuoc deu dan de dam bao co the luon du nuoc

---

## Tinh nang chinh

- **Nhac nho cham soc mat**: Dat lich nhac nghi mat theo tan suat tuy chinh
- **Nhac nho uong nuoc**: Thiet lap nhac nho uong nuoc trong ngay
- **Tuy chinh linh hoat**:
  - Mot lan duy nhat
  - Hang ngay
  - Hang gio (dung gio)
  - Moi X phut (toi thieu 15 phut)
  - Chon ngay cu the trong tuan
- **Tieu de nhac nho tuy chinh**: Tu dat ten cho tung nhac nho
- **Chon ngay va gio bat dau**: Giao dien chon thoi gian truc quan
- **Bat/Tat nhac nho**: De dang quan ly trang thai nhac nho
- **Goi y va phan hoi**: Gui goi y cai thien ung dung truc tiep tu trong app
- **Giao dien Material Design 3**: Hien dai, than thien voi nguoi dung
- **Splash Screen**: Man hinh khoi dong voi hieu ung loading
- **Thong bao thong minh**: Xu ly quyen thong bao cho Android 13+
- **Tiet kiem pin**: Su dung WorkManager de lap lich nen hieu qua

---

## Cong nghe su dung

| Thanh phan | Cong nghe |
|---|---|
| **Ngon ngu** | Kotlin |
| **Kien truc** | MVVM (Model-View-ViewModel) + Clean Architecture |
| **Giao dien** | Jetpack Compose |
| **Luu tru cuc bo** | Room Database |
| **Dependency Injection** | Hilt (Dagger) |
| **Xu ly bat dong bo** | Kotlin Coroutines & Flow |
| **Tac vu nen** | WorkManager |
| **Backend** | Firebase Firestore (luu tru goi y nguoi dung) |
| **Kiem tra chat luong** | Detekt (phan tich tinh), ktlint |
| **Kiem thu** | JUnit, Mockito, MockK, Turbine, Truth |
| **Do phu test** | JaCoCo |
| **CI/CD** | GitHub Actions |

---

## Kien truc du an

Ung dung duoc xay dung theo mo hinh **Clean Architecture** voi su tach biet ro rang giua cac tang:

```
com.alpha.myeyecare/
|
|-- common/                          # Tien ich va hang so dung chung
|   |-- constants/
|   |   |-- AppDestinations.kt       # Dinh nghia cac diem den Navigation
|   |   +-- ReminderTypes.kt         # Dinh nghia loai nhac nho
|   +-- utils/
|       |-- ExtensionFunctions.kt    # Ham mo rong tien ich
|       +-- UtilFunctions.kt         # Ham tien ich chung
|
|-- data/                            # Tang du lieu (Data Layer)
|   |-- local/                       # Luu tru cuc bo
|   |   |-- converters/
|   |   |   +-- Converters.kt        # Chuyen doi kieu du lieu cho Room
|   |   |-- dao/
|   |   |   +-- ReminderDao.kt       # Data Access Object
|   |   |-- entities/
|   |   |   +-- Reminder.kt          # Entity cua Room Database
|   |   +-- ReminderDatabase.kt      # Cau hinh Room Database
|   +-- repository/                  # Hien thuc Repository
|       |-- ReminderRepositoryImpl.kt
|       +-- SuggestionRepositoryImpl.kt
|
|-- di/                              # Dependency Injection
|   |-- AppModule.kt                 # Module chinh cua ung dung
|   |-- DatabaseModule.kt            # Module cau hinh Database
|   +-- RemoteModule.kt              # Module cau hinh Firebase
|
|-- domain/                          # Tang logic nghiep vu (Domain Layer)
|   |-- model/                       # Cac model du lieu
|   |   |-- DayOfWeek.kt
|   |   |-- ReminderDetails.kt
|   |   |-- ReminderFrequency.kt
|   |   +-- Suggestion.kt
|   |-- repository/                  # Giao dien Repository (abstraction)
|   |   |-- ReminderRepository.kt
|   |   +-- SuggestionRepository.kt
|   +-- useCases/                    # Cac Use Case
|       |-- CheckReminderStatusUseCase.kt
|       |-- GetReminderDetailsUserCase.kt
|       |-- SaveReminderUseCase.kt
|       +-- SaveSuggestionsUseCase.kt
|
|-- presentation/                    # Tang giao dien (Presentation Layer)
|   |-- navigation/
|   |   +-- NavGraph.kt              # Dinh nghia Navigation Graph
|   +-- ui/
|       |-- common/
|       |   +-- CommonUI.kt          # Cac thanh phan UI dung chung
|       |-- detailScreen/
|       |   |-- SetupReminderScreen.kt    # Man hinh cai dat nhac nho
|       |   +-- SetupReminderViewModel.kt
|       |-- home/
|       |   +-- HomeScreen.kt        # Man hinh chinh
|       |-- splash/
|       |   |-- SplashScreen.kt      # Man hinh khoi dong
|       |   +-- SplashViewModel.kt
|       |-- suggestion/
|       |   |-- SuggestionSubmissionViewModel.kt
|       |   +-- UserSuggestionScreen.kt   # Man hinh gui goi y
|       +-- theme/
|           |-- Color.kt             # Dinh nghia mau sac
|           |-- Theme.kt             # Dinh nghia theme
|           +-- Type.kt              # Dinh nghia kieu chu
|
|-- worker/                          # Xu ly tac vu nen
|   |-- ReminderScheduler.kt         # Lap lich nhac nho
|   +-- ReminderWorker.kt            # Worker thuc thi nhac nho
|
|-- MainActivity.kt                  # Activity chinh
+-- MyApplication.kt                 # Application class (Hilt entry point)
```

---

## Anh chup man hinh

| Man hinh chinh | Cai dat nhac nho | Goi y |
|---|---|---|
| <img src="screenshots/Home-Screen.png" height="400"/> | <img src="screenshots/Set-Reminder-Screen.png" height="400"/> | <img src="screenshots/Suggestions-Screen.png" height="400"/> |

**Mo ta cac man hinh:**

1. **Splash Screen**: Man hinh khoi dong voi logo ung dung va thanh tien trinh loading
2. **Home Screen**: Man hinh chinh hien thi 2 tuy chon - Nhac nho mat va Nhac nho uong nuoc
3. **Setup Reminder Screen**: Man hinh cai dat chi tiet cho nhac nho (tan suat, ngay gio, tieu de...)
4. **Suggestion Screen**: Man hinh gui phan hoi va goi y cai thien ung dung

---

## Quy trinh CI/CD

Du an tich hop **GitHub Actions** de dam bao chat luong code:

| Buoc | Mo ta |
|---|---|
| **Debug Build Check** | Kiem tra code co bien dich thanh cong hay khong |
| **Detekt Check** | Phan tich tinh code Kotlin, dam bao code sach va de bao tri |
| **Unit Tests** | Chay unit test va kiem tra do phu code (yeu cau >= 80%) |

Quy trinh nay tu dong chay khi co **Pull Request** hoac **push** vao nhanh `main`.

---

## Yeu cau he thong

- **Android**: API 24 (Android 7.0 Nougat) tro len
- **Target SDK**: 35 (Android 15)
- **JDK**: 17 (de build du an)
- **Gradle**: 8.x (Kotlin DSL)

---

## Huong dan cai dat va chay du an

### Buoc 1: Clone repository

```bash
git clone https://github.com/phamlengocson/Eye-Water-Reminder-App.git
cd Eye-Water-Reminder-App
```

### Buoc 2: Mo du an

Mo du an bang **Android Studio** (phien ban moi nhat duoc khuyen nghi).

### Buoc 3: Dong bo Gradle

Android Studio se tu dong dong bo cac dependency. Neu khong, chon **File > Sync Project with Gradle Files**.

### Buoc 4: Cau hinh Firebase

Du an su dung Firebase Firestore cho tinh nang goi y. Ban can:
1. Tao du an tren [Firebase Console](https://console.firebase.google.com/)
2. Tai file `google-services.json` va dat vao thu muc `app/`
3. Bat Firestore Database trong Firebase Console

### Buoc 5: Build va chay

- Chon thiet bi/emulator Android (API >= 24)
- Nhan **Run** hoac su dung lenh:

```bash
./gradlew assembleDebug
```

---

## Kiem thu

### Chay unit tests

```bash
./gradlew testDebugUnitTest
```

### Tao bao cao do phu code (JaCoCo)

```bash
./gradlew clean testDebugUnitTest jacocoTestReport
```

Bao cao se duoc tao tai: `app/build/reports/jacoco/jacocoTestReport/`

### Chay kiem tra Detekt

```bash
./gradlew detekt
```

---

## Thong tin phien ban

| Phien ban | Ma phien ban | Ngay phat hanh |
|---|---|---|
| 1.1.0 | 2 | 27/08/2025 |
| 1.0.0 | 1 | 19/08/2025 |

---

## Tac gia

**Pham Le Ngoc Son**

- **Vai tro**: Developer & Owner
- **Du an**: Eye & Water Reminder App
- **Cong nghe chuyen mon**: Android Development, Kotlin, Jetpack Compose, Clean Architecture

---

## Giay phep

Du an nay thuoc quyen so huu cua **Pham Le Ngoc Son**. Moi quyen duoc bao luu.

Copyright (c) 2025 Pham Le Ngoc Son. All rights reserved.
