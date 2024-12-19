스팀덱(Steam Deck)에 Yuzu 에뮬레이터를 설치하려면 Linux 기반의 스팀덱 운영 체제에서 Yuzu를 수동으로 설정해야 합니다. 아래는 스팀덱에서 Yuzu 설치 및 설정 방법입니다.

---

### 1. **스팀덱의 데스크톱 모드로 전환**

1. **전환하기:**
    - 스팀덱의 `전원` 버튼을 눌러 전원 메뉴를 엽니다.
    - **"데스크톱 모드로 전환"**을 선택합니다.
2. 데스크톱 환경에 진입한 후, Yuzu 설치를 시작합니다.

---

### 2. **필요한 도구 설치**

1. **Discover Store 열기:**
    - 데스크톱 모드에서 **Discover Software Center**를 실행합니다.
    - `Konsole` (터미널 앱)도 사용할 수 있습니다.
2. **종속성 설치:** 터미널을 열고 아래 명령어를 입력하여 Yuzu 실행에 필요한 종속성을 설치합니다:
    
    bash
    
    Copy code
    
    `sudo pacman -Syu sudo pacman -S qt5-base libx11 libxcb vulkan-icd-loader`
    

---

### 3. **Yuzu 다운로드**

1. **Yuzu 공식 사이트**로 이동:
    
    - [Yuzu Download](https://yuzu-emu.org/) 페이지에서 Linux 버전을 다운로드합니다.
    - 파일 형식은 `.AppImage` 또는 `.tar.xz`일 수 있습니다.
2. **파일 복사:**
    
    - 다운로드한 파일을 **스팀덱의 홈 디렉토리**로 복사합니다.

---

### 4. **.AppImage 파일 설치 방법**

(AppImage는 설치가 간단하며 권장됩니다.)

1. **권한 부여:** 터미널에서 실행 권한을 부여합니다:
    
    bash
    
    Copy code
    
    `chmod +x yuzu-*.AppImage`
    
2. **실행:** 파일을 실행합니다:
    
    bash
    
    Copy code
    
    `./yuzu-*.AppImage`
    

---

### 5. **.tar.xz 파일 설치 방법**

(tar.xz는 압축 해제 후 수동으로 설정해야 합니다.)

1. **압축 해제:** 터미널에서 다음 명령어를 실행합니다:
    
    bash
    
    Copy code
    
    `tar -xf yuzu-*.tar.xz cd yuzu`
    
2. **실행:** 디렉토리에서 실행합니다:
    
    bash
    
    Copy code
    
    `./yuzu`
    

---

### 6. **스팀에 Yuzu 추가 (게임 모드에서 실행)**

1. **Yuzu를 스팀에 추가:**
    
    - 데스크톱 모드에서 **Steam 클라이언트**를 열고 `게임` > **"비 Steam 게임 추가"**를 클릭합니다.
    - Yuzu 실행 파일을 찾아 추가합니다.
2. **Yuzu 실행하기:**
    
    - 스팀의 **게임 라이브러리**에서 Yuzu를 실행할 수 있습니다.

---

### 7. **펌웨어 및 키 파일 설정**

1. **Yuzu 설정 디렉토리 열기:**
    
    - Yuzu는 일반적으로 `~/.local/share/yuzu/` 경로에 설정 파일을 저장합니다.
    - 필요시 파일 관리자를 열어 해당 폴더를 찾아 이동합니다.
2. **키 파일 복사:**
    
    - `prod.keys`와 `title.keys`를 `~/.local/share/yuzu/keys`에 복사합니다.
3. **펌웨어 설치:**
    
    - 펌웨어 파일을 `~/.local/share/yuzu/nand/system/Contents/registered` 폴더에 복사합니다.

---

### 8. **최적화 및 Vulkan 설정**

1. **Vulkan 사용:** Yuzu 실행 후 설정에서 그래픽 백엔드를 Vulkan으로 변경하면 성능이 향상됩니다.
    
2. **컨트롤러 매핑:** Yuzu 설정에서 스팀덱의 버튼을 올바르게 매핑합니다.
    

---

### 9. **테스트**

1. 스팀덱의 **게임 모드**로 돌아가 Yuzu를 실행합니다.
2. 게임을 추가하고 정상적으로 실행되는지 확인합니다.