---
tistoryBlogName: yobine
tistoryTitle: Obsidian 노트, 컴퓨터 외 기기들과 동기화(Sync)하기
tistoryTags: "#Obsidian, #옵시디언, #note, #노트, #동기화, #Sync"
tistoryVisibility: "3"
tistoryCategory: "1161798"
tistoryPublished: 2023-09-25T18:04
tistoryPostId: "595"
tistoryPostUrl: https://yobine.tistory.com/595
---
다음 내용은 Obsidian 의 정식 Help 싸이트 내용을 ChatGPT 로 번역 후 수정된 내용입니다. Help 싸이트: [Sync your notes across devices - Obsidian Help](https://help.obsidian.md/Getting+started/Sync+your+notes+across+devices) 

Obsidian 을 사용하여 Tistory 글 작성은 두번째 이며, 그동안 작성했던 글을, 컴퓨터에만 저장하기 보다는, 외부 클라우드 저장소를 통해 저장하고 불러 들여오고 하면 편할 것 같다는 생각을 하게 되었는데, 마침, 내가 사용하는 PC 외 다른 기기들 (아이폰, 집PC, 회사PC 등) 과 동기화 할 수 있는 방법이 검색되어 해당 내용을 적용해 보며 공유합니다.

동기화란, Obsidian 으로 기록/작성 된 최신의 노트 들을 내가 사용하는 모든 기기 (랩탑 이나 아이폰 등)에서 읽고 작성할 수 있는 기능입니다. 

기본적으로 Obsidian 에서 제공하는 [Obsidian Sync](https://help.obsidian.md/Obsidian+Sync/Introduction+to+Obsidian+Sync) 와 애플의 [iCloud Drive](https://help.obsidian.md/Getting+started/Sync+your+notes+across+devices#iCloud%20Drive) 가 있으며, 이 중 다른 기기 간에 노트를 동기화하는 가장 쉬운 방법은 - [Obsidian Sync](https://help.obsidian.md/Obsidian+Sync/Introduction+to+Obsidian+Sync) 를 사용하는 것입니다. 이미 - [Obsidian Sync](https://help.obsidian.md/Obsidian+Sync/Introduction+to+Obsidian+Sync)  구독(유로)을 가지고 있다면 - [Obsidian Sync](https://help.obsidian.md/Obsidian+Sync/Introduction+to+Obsidian+Sync)  설정 방법을 참조하십시오.

다른 동시에 여러 동기화 서비스를 사용하는 것(예: Obsidian Sync 및 Dropbox)은 데이터 손실, 손상 및 기타 문제를 일으킬 수 있으므로 주의해야 합니다. 다른 서비스와 함께 Obsidian Sync를 사용하는 방법에 대해 자세히 알아보려면 [여기](https://help.obsidian.md/Obsidian+Sync/Obsidian+Sync+and+third-party+services) 를 확인하십시오.

## 여러 PC 가 노트 동기화 하기

만약 Obsidian 을 모바일 기기에서 사용하지 않는다면, 로컬 폴더를 클라우드 저장소로의 동기화를 위해 다음과 같은 클라우드 서비스를 사용할 수 있습니다.

- Dropbox
- Google Drive
- iCloud Drive
- OneDrive
- Syncthing

노트를 동기화하려면 사용 중인 서비스의 지침을 따라 로컬 파일 시스템의 폴더를 동기화하고, 그런 다음 모든 데스크톱 기기에서 기존 Valut 로 폴더를 열면 됩니다.

## 아이폰, 아이패드 와 노트 동기화 하기

iPhone 및 iPad에서 노트 동기화 iPhone 또는 iPad에서 노트를 동기화 하기 위해 다음 클라이드 저장소를 공식적으로 지원합니다:

- [Obsidian Sync](https://help.obsidian.md/Obsidian+Sync/Introduction+to+Obsidian+Sync)
- [iCloud Drive](https://help.obsidian.md/Getting+started/Sync+your+notes+across+devices#iCloud%20Drive)

참고: 다음 서비스들을 통한 아이폰, 아이패드와 노트 동기화 지원은 되지 않습니다. 이러한 서비스를 사용하여 iOS 기기에서 노트를 동기화하는 방법을 발견하면 커뮤니티 채널에서 알려주세요.

- Dropbox
- Google Drive
- OneDrive
- Syncthing
- iCloud Drive

## iCloud Drive

Obsidian은 로컬 파일 시스템으로 iCloud Drive를 사용할 수 있습니다.

macOS에서 iCloud Drive를 사용할 때, 데스크톱 앱의 설치 버전을 v0.13.0 이상으로 업데이트해야 합니다.

노트: iCloud 저장 공간 한도를 초과하지 마십시오. 동기화가 중지될 수 있습니다.

## iCloud Drive에 새로운 Vault 만들기 

iPhone 또는 iPad에서 iCloud Drive에 새 Vault 를 만들려면 다음 단계를 따르십시오:

1. 새로운 Vault 만들기를 탭합니다.
2. Vault name에 Vault의 이름을 입력하십시오.
3. Store in iCloud를 활성화합니다.
4. Create를 탭합니다.

Obsidian은 iCloud Drive 내부에 새 폴더를 생성합니다. 컴퓨터에서 iCloud Drive 폴더를 Vault로 열려면 다음을 수행하십시오:

1. 컴퓨터에서 Obsidian을 엽니다.
2. Open folder as vault의 오른쪽에서 Open을 선택합니다.
3. iCloud Drive → Obsidian으로 이동합니다.
4. 동기화하려는 Vault 이름으로 폴더를 선택합니다.

## 기존 Vault 와 iCloud Drive 동기화하기

기존 Vault를 iCloud Drive로 동기화하려면, 우선, iCloud Drive에 비어 있는 Vault를 만들고 다른 기기의 노트를 비어 있는 Vault로 이동해야 합니다.

iCloud Drive에 새로운 비어 있는 Vault를 만들려면 다음을 수행하십시오:

1. Create new vault를 탭합니다.
2. Vault name에 동기화하려는 Vault와 동일한 이름을 입력합니다.
3. Store in iCloud를 활성화합니다.
4. Create를 탭합니다.

노트를 새 iCloud Drive 폴더로 이동하려면 다음을 수행하십니다:

1. 컴퓨터에서 iCloud Drive 폴더를 엽니다.
2. Obsidian 폴더를 엽니다. 몇 분이 걸릴 수 있습니다.
3. 기존 Vault의 파일을 Vault 이름으로 된 폴더로 이동합니다.

iCloud는 파일을 모바일 기기로 동기화합니다. Vault의 크기에 따라 몇 분이 걸릴 수 있습니다.

## Working Copy

Working Copy 노트를 [Git](https://git-scm.com/) 리포지토리에 저장하는 경우 [Working Copy](https://apps.apple.com/us/app/working-copy-git-client/id896694807) 라는 iOS용 Git 클라이언트를 사용하는 것을 추천합니다.

[Working Copy](https://apps.apple.com/us/app/working-copy-git-client/id896694807) 를 사용하여 동기화하는 방법:

1. iPhone 또는 iPad에 비어 있는 Vault 를 만듭니다.
2. Setup Folder Sync 동작을 사용하고 비어 있는 Vault 를 선택합니다.
3. Working Copy 앱을 사용하여 Vault에 대한 변경 사항을 커밋하고 푸시합니다.

참고: 이 방법은 공식으로 지원하지 않지만 몇몇 사용자가 Working Copy를 사용하여 노트를 성공적으로 동기화했다고 보고했습니다.

## X 사용으로 동기화 불가능한 이유

많은 사용자들이 파일 동기화에 다른 서비스를 사용을 원하는 것을 잘 알고 있습니다.

Obsidian은 iOS 의 다른 Markdown 편집기와는 다르게 작동합니다. 1Writer 및 iA Writer와 같은 편집기는 한 번에 하나의 노트에 액세스하며 내장 문서 지원을 사용할 수 있습니다.

반면에 Obsidian 의 많은 기능들이 Vault 전체에 대한 액세스를 필요로 합니다.. 예를 들어 파일 이름을 변경하면 Obsidian은 해당 파일에 링크된 Vault 내의 모든 파일을 업데이트 합니다.

지원되는 위치 이외의 수천 개의 노트로 이루어진 전체 폴더 구조를 읽고 수정하고 모니터링하는 시스템을 구현하는 것은 복잡합니다. 이러한 제한은 앞으로 해결할 예정 입니다.

개발자라면 각 개별 동기화 서비스에 대한 Web API를 사용하는 플러그인을 만들 수 있습니다.

## 내 Vault는 어디에 저장되나요? 

Vault 를 만들 때 iCloud Drive를 사용하지 않는다면 Obsidian은 해당 Vault를 Obsidian 앱의 로컬 파일 시스템에 저장합니다. 다른 앱인 Working Copy와 같이 Obsidian 폴더를 파일 시스템에서 선택하여 Vault에 액세스할 수 있습니다.

**주의: Obsidian 앱을 삭제할 때 iOS에서 로컬 파일 시스템에 저장된 노트가 삭제됩니다. Obsidian 앱을 삭제하기 전에 노트를 백업하십시오.**

## Android에서 노트 동기화

Android 기기에서 노트를 동기화하는 가장 쉬운 방법은[Obsidian Sync](https://help.obsidian.md/Obsidian+Sync/Introduction+to+Obsidian+Sync) 를 사용하는 것입니다.

Obsidian은 Android 기기의 로컬 폴더에 노트를 저장하므로, 폴더 동기화를 허용하는 어떠한 앱을 사용할 수 있습니다. 

- [Dropsync](https://play.google.com/store/apps/details?id=com.ttxapps.dropsync) 
- [FolderSync](https://play.google.com/store/apps/details?id=dk.tacit.android.foldersync.lite) 

Obsidian은 Documents 폴더 내의 Obsidian 폴더를 생성합니다. Documents/Obsidian 하위의 모든 폴더는 Obsidian Vault로 간주됩니다.


> 일부 클라우드 저장소 서비스인 OneDrive와 같은 서비스는 파일을 사용할 때만 다운로드하고 나중에 로컬에서 제거하여 공간을 확보할 수 있게 해줍니다. 이 파일들은 더 이상 로컬에서 사용할 수 없기 때문에 Obsidian Sync는 이 파일들이 삭제된 것으로 간주하고 원격 보트에서 제거합니다. 
> 
> Files On-Demand 및 유사한 기능과 함께 Obsidian Sync를 사용하려면 서비스를 구성하여 항상 파일을 장치에 보존하도록 해야 합니다.
