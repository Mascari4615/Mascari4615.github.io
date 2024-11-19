---
title: "WitchMendokusai DevLog 04"
# description: ""
categories: [📀Post, 🥥WitchMendokusai]
tags: [WitchMendokusai, "마녀: 귀찮아"]
image: "/assets/project/WitchMendokusai/ScreenShot/240514_104350.png"
hidden: true

date: 2024-04-19. 00:24
# last_modified_at: 2024-04-25. 21:55
# last_modified_at: 2024-05-02. 05:44
# last_modified_at: 2024-05-04. 03:40
# last_modified_at: 2024-05-22. 20:47
last_modified_at: 2024-08-29. 21:51
---

{% include embed/youtube.html id='BnGTGZ-eqCU' %}

## 📀 빌드 에러

---

![오류 오류 오류](/assets/img/post/2024/240419_00.png)  
테스트를 위해 빌드를 돌려봤는데, 오류가 잔뜩이다.  

이유는 내가 지금까지 구현한 방법으로는, 게임 데이터 스크립터블 오브젝트들을 빌드 후에 불러올 수 없기 때문이다.  

그동안 사용한 방법은 아래과 같다.  

먼저 에디터 타임에 유니티 프로젝트 경로에 위치한 스크립터블 오브젝트들을 로드하고,  
이를 매니저 스크립터블 오브젝트의 딕셔너리에 저장해 썼었다.  

```cs
public class SOManager : ScriptableObject
{
    [field: SerializeField] public Dictionary<Type, Dictionary<int, DataSO>> DataSOs { get; private set; } = new();
    // ...
}
```

![보면 잘 들어가 있는데](/assets/img/post/2024/240419_01.png)  
로그를 찍어보면 잘 들어가있는 걸 확인할 수 있다.  

이 방법은 에디터 상에서는 문제가 없지만,  
유니티에서 `Dictionary`는 직렬화되지 않기 때문에, 빌드 후에는 `DataSOs`가 텅텅 비어있게 된다.  

(`[field: SerializeField]`는 나의 코드 스타일 상 같이 붙여둔 것인데, 실제로 아무런 영향을 주지 않는다.)  
(생각해보니 이거 지워둬야겠네.)  

어쨌거나, 그럼 이 문제를 어떻게 해결할 수 있을까?  

직렬화 가능한 커스텀 딕셔너리를 만들어서 해결해볼 수도 있겠지만,  
나는 이참에 `Addressable`을 한 번 써보기로 했다.  

`Addressable`을 이용하면 런타임에 에셋을 로드할 수 있다.  
또한 빌드/런타임 메모리 관리가 가능하고, 새 빌드 없이도 리소스를 갱신할 수 있게 해준다.  

비록 당장 `Addressable`을 사용하는 이유는 단순 런타임 에셋 로드 때문이지만,  
미리 기반을 다져둔다면, 추후 확장성을 비롯해 `Addressable`의 여러 이점을 얻을 수 있을 것이다.  

.. 근데 사실 작은 프로젝트라 당장 굳이 `Addressable`을 사용할 이유는 크게 없다.  

다만 언젠가 써보고 싶었던 것이기도 하고,  

언젠가 내 게임의 코드를 전부 공개하고픈 욕심도 있어서,  
깃 레포에 코드만 올려서 공개하고 실제 아트적인 에셋들은 어드레서블로 불러오는.. 그런 계획이 있는 것이 이유다.  

... 그냥 써보는거지 뭐 !  

### 💿 Addressable

런타임에 데이터를 로드하기 위한 방법으로 크게 3가지가 있다.  

먼저 `Resources` 폴더를 사용하는 방법이 있다.  
가장 간단하고 직관적이지만, 빌드에 포함되기에 빌드 용량이 커지고, 한 번 빌드하면 수정이 불가능 하다는 단점이 있다.  

이를 보완하기 위해 `AssetBundle`이라는 방법이 나왔다.  
`AssetBundle`은 외부에서 런타임에 데이터를 로드하기 때문에, 빌드 용량도 작아지고, 외부에서 수정도 가능하게 됐다.  
이런 여러 장점이 있었지만, 문자열로 경로를 지정해야해서 관리가 어렵고, 종속성 관리가 어렵다는 문제가 있었다.  

그래서 또 이런 단점들을 보완하기 위해 `Addressable`이라는 방법이 나온 것이다.  
`Addressable`은 `AssetBundle`을 기반으로 하면서, 이를 좀 더 쉽고 편리하게 사용할 수 있게 해준다.  

기존 문자열로 경로를 지정하는 방식 대신, `Address`를 통해 에셋을 참조하고,  
여러 종속성 문제도 자동으로 해결해준다. (이부분은 좀 더 공부해봐야겠다.)  

[참고 : '어드레서블 에셋 시스템 - 개념: 등장 배경, vs 에셋번들'](https://planek.tistory.com/22)  

### 💿 구현

```cs
public class UILoading : Singleton<UILoading>
{
    [SerializeField] private Image progressBar;
    private readonly List<AsyncOperationHandle> handles = new();

    public IEnumerator Loading()
    {
        gameObject.SetActive(true);
        progressBar.fillAmount = 0f;

        LoadAssetsAsync();

        while (true)
        {
            float totalPercent = 0;
            foreach (var handle in handles)
                totalPercent += handle.PercentComplete;
            progressBar.fillAmount = totalPercent / handles.Count;

            Debug.Log($"Loading... {progressBar.fillAmount * 100}%");

            if (handles.All(handle => handle.IsDone))
                break;

            yield return null;
        }
        Debug.Log($"Loading... {progressBar.fillAmount * 100}%");

        //foreach (var handle in handles)
        //    Addressables.Release(handle);

        progressBar.fillAmount = 1f;
        gameObject.SetActive(false);
    }

    private void LoadAssetsAsync()
    {
        SOManager.Instance.DataSOs.Clear();

        LoadAsset<QuestData>("QUEST_DATA");
        // 각 타입별로 로드.. (생략)

        void LoadAsset<T>(string label) where T : DataSO
        {
            var handle = Addressables.LoadAssetsAsync<T>(label, null);
            handle.Completed += OnAssetsLoaded;
            handles.Add(handle);
        }
    }

    private void OnAssetsLoaded<T>(AsyncOperationHandle<IList<T>> obj) where T : DataSO
    {
        if (obj.Status == AsyncOperationStatus.Succeeded)
        {
            List<T> assets = obj.Result.ToList();
            SOManager.Instance.DataSOs[typeof(T)] = new();

            foreach (T asset in assets)
            {
                Debug.Log($"Loaded {asset.name}");
                SOManager.Instance.DataSOs[typeof(T)].Add(asset.ID, asset);
            }
        }
    }
}
```

게임을 시작하기 전에, 잠깐 로딩 화면을 띄워주는 `UILoading`을 만들었다.  
이 로딩 화면에서 `Addressable`을 사용해 에셋들을 로드한다.  

큰 이해를 가지고 구현한 것은 아니지만, 간단하게 `Addressable`을 사용해보았다.  

.. 근데 한 가지 고민스러운 게 있다면,  
당장은 로컬로 에셋을 로드하고 있는데 이렇게 되면 `Addressable`을 사용하는 의미가 없다.  

`Addressable`과 서버를 연결하는 작업을 조만한 진행해야겠다.  

## 📀 Private 레포지토리 Public로 변환

---

전부터 레포지토리를 Public으로 전환하고 싶었다.  
이유라면, 다른 사람들에게 내 코드와 게임을 보여주고 싶기 때문이다.  

최근 실력적으로 많은 부족함을 느낀다.  
현업 경험이 전무하고, 나혼자 개발하다보니 내가 짜는 코드가 아름다운지 잘모르겠다.  
내 코드를 공개함으로써, 다른 사람들의 피드백을 받고 더 좋은 실력을 가지고 싶다.  

그리고, 나는 많은 사람들이 참여하는 게임을 만들고 싶다.  

물론 나의 세계관이 많이 들어가는 게임이지만,  
다른 사람들도 몰입할 수 있는 게임을,  
다른 사람들도 참여하고 싶다면 얼마든지 참여할 수 있는 그런 게임을 만들고 싶다.  

그러기 위한 첫 걸음이다.  

### 💿 파일 정리

먼저 레포지토리에 올라가 있는 파일들을 정리했다.  

단순히 필요없는 파일들을 지울 뿐만 아니라,  
저작권상 재배포가 불가능한 파일들은 히스토리에서도 지웠다.  

아래 명령으로 가능하다.  

```sh
git filter-branch -f --index-filter "git rm --cached --ignore-unmatch 파일명" --prune-empty --tag-name-filter cat -- --all
git filter-branch -f --index-filter "git rm -r --cached --ignore-unmatch 폴더명" --prune-empty --tag-name-filter cat -- --all
```

이때 파일명은 경로과 확장자를 포함한 전체 파일명이어야 한다.  

만약 경로에 공백이 있으면, 이스케이프 문자를 사용해야 한다.  
예를 들어 `파 일 명`이라면 `파\ 일\ 명`으로 써야 한다.  

또한 파일명 뒤에 `*`를 붙이면, 해당 파일명으로 시작하는 모든 파일을 지울 수 있다.  
예를 들어 `ABC*`이라면, `ABC`로 시작하는 모든 파일을 지운다.  

이렇게 지운 파일들은 아래와 같다.

- 저작권상 재배포가 불가능한 파일들
  - 임시 텍스쳐, 아이콘들
  - 폰트 (픽셀로보로보, 긱블말랑이체)
  - 사운드
  - 스카이박스
- 필요없는 파일들
  - 프로젝트에 같이 포함해뒀던 빌드 파일
  - 더 이상 쓰지 않거나 지웠지만, 깃 히스토리에 남은 에셋 (조이스틱, KiwiCoder 행동트리)
- 개인 정보가 들어있는 파일들
  - 구글 플레이 게임즈, 구글 플레이 설정 파일
  - 플레이팹 설정 파일
  - .keystore 파일

이후 아래 명령으로 백업 참조들을 삭제하고, 불필요한 객체들을 정리했다.  

```sh
git rm -rf .git/refs/original/
git reflog expire --all
git gc --aggressive --prune=all

git push origin --force --all
```

이렇게 하면, 깃허브 잔디에도 삭제한 커밋 이력이 반영된다.  

[참고 : 'git에서 잘못 올린 파일의 이전 내역을 전부 제거하는 방법'](https://opendeveloper.tistory.com/entry/git%EC%97%90%EC%84%9C-%EC%9E%98%EB%AA%BB-%EC%98%AC%EB%A6%B0-%ED%8C%8C%EC%9D%BC%EC%9D%98-%EC%9D%B4%EC%A0%84-%EB%82%B4%EC%97%AD%EC%9D%84-%EC%A0%84%EB%B6%80-%EC%A0%9C%EA%B1%B0%ED%95%98%EB%8A%94-%EB%B0%A9%EB%B2%95)  
[참고 : '경로에 공백(띄어쓰기)이 있을 때 cd, git add 방법'](https://markme-inur.tistory.com/74)  
[참고 : '.gitignore가 작동하지 않을때 대처법'](https://jojoldu.tistory.com/307)  

### 💿 잔디가 왜 이래 **!**

![154 커밋이](/assets/img/post/2024/240426_00.png)  
![912 커밋으로 보여요](/assets/img/post/2024/240426_01.png)  

그런데 깃 히스토리를 수정하면서 `Rewrite`한 커밋 이력들이 남아있는 건지,  
위 사진처럼 깃허브 프로필 `Contribution activity(잔디)`에 비정상적으로 많은 커밋이 기록됐다.  
레포지토리를 보면 지금까지 154개의 커밋을 했는데, 프로필에서는 912개의 커밋으로 보인다.  

큰 문제는 아니지만, 다른 사람이 보기에는 이거 뭐지? 싶을 것 같아서 지워주기로 했다.  

![912 커밋으로 보여요](/assets/img/post/2024/240426_02.png)  

딱히 내가 직접 해결할 수 있는 방법은 없는 것 같고, 문의를 통해서 `Contribution` 기록을 갱신받아 해결했다.  

그런데.. 이후 지워야 할 파일을 하나 더 발견해버렸다..  
해당 파일을 지웠더니 다시 커밋 기록이 엄청 늘어났다..  

당장 다시 갱신 요청하기는 좀 미안하고, 다른 파일도 찾아본 다음에 나중에 다시 한 번 문의 넣어야 할 듯 ㅎㅎ..  

### 💿 파일 수정/추가

파일 삭제를 완료하고, 이제 삭제한 파일들을 대체할 에셋들을 추가했다.  
파일(에셋)들은 모두 라이센스 상 재배포 가능한 것들로 구성했다.  

- `DOTween` (기존 `Feel` 에셋 대체)
- `Unified-Universal-Blur` (기존 `Translucent Image - Fast UI Background Blur` 에셋 대체)
- 사운드 및 스프라이트 (기존 사운드 및 스프라이트 대체)
  - `PROTODOME`의 Album들 (CC BY-NC-ND 3.0)
  - `ArtisticDube`의 `RPG Sound Pack` (CC0)
  - `NathanGibson`의 `UI Sound Pack` (CC BY 4.0)
  - `Havi Averilla Xavier(Shade)`의 `16x16 Assorted RPG Icons`, `16x16 Weapon RPG Icons` (CC0 1.0)
  - `Beast Pixels`의 `Crafting Materials`, `Weapons and Tools` (CC0 1.0)
  - `Midhil M(Leo Red)`의 `Lucid Icons` (CC0 1.0)

FMOD 라이센스를 지키기 위해,  
게임 로그인 화면에 FMOD 로고를 추가하고,  
설정창에 FMOD의 간단한 크레딧을 추가했다.  

### 💿 README.md

크레딧을 적기 위해, `README.md` 파일도 수정했다.  

이미 위에서 언급한 에셋들 뿐만 아니라,  
기존에 수정해서 사용하고 있던 에셋들에 대한 크레딧도 추가했다.  

- [Rito님의 행동트리](https://rito15.github.io/posts/behavior-tree/)
- [Rito님의 인벤토리](https://github.com/rito15/Unity-RPG-Inventory)
- 빌보드 쉐이더

당장은 크레딧 밖에 없다.  
추후에는 게임에 대한 설명, 사용법, 라이센스 등을 추가할 예정이다.  

일단 이정도로 레포지토리를 정리하고, 레포지토리를 Public으로 전환했다 !  
다음 목표는, 개발 문서를 작성하고, 첫 알파 릴리스를 해보는 것이다.  

## 📀 Git LFS

---

새 사운드들을 추가하고 커밋을 하려니, FMOD의 빌드 파일이 너무 커서 커밋이 안됐다.  
Git LFS를 쓰면 그냥 업로드를 할 수 있었지만, 이전 `Wakgreed` 프로젝트 레포지토리에서 LSF 용량을 전부 쓰는 바람에 새로운 파일을 추가할 수 없었다.  

![꽉꽉](/assets/img/post/2024/240503_00.png)  

FMOD 빌드 파일을 `.gitignore`로 제외하는 수도 있었지만,  
다른 사람이 내 레포지토리를 받고 바로 실행할 수 있는 환경을 만들고 싶어서 그럴 수는 없다.  

그래서 LFS 용량을 확보하기로 했다.  

찾아보니 LFS 용량은, LFS 오브젝트를 삭제하더라도 그 용량이 회수되지 않는다.  
직접 LFS 용량을 줄이기 위해서는, 레포지토리를 삭제하고 다시 레포지토리를 만드는 방법 밖에 없다고 한다.  
하지만 `Wakgreed`는 나의 첫 게임 프로젝트이기도 하고, 여러 모로 의미있는 프로젝트라 지울 수는 없었다..  

다른 방법으로는 위에서 `Contribution activity(잔디)`를 갱신했던 것처럼,  
깃허브에 문의를 넣어서 서버에 저장된 LFS 용량을 회수해달라고 요청하는 방법이 있다.  

이를 위해서는 해당 레포지토리에서 LFS 오브젝트로 등록된 파일들을 히스토리에서 제거해줄 필요가 있다고 한다.  
어떤 오브젝트가 LFS로 등록되었는지는 `git lfs ls-files --all --long` 명령어로 확인할 수 있고,  
히스토리에서 제거하는 방법은 위에서 언급한 `git filter-branch` 명령어를 사용하면 된다.  

![Git LFS](/assets/img/post/2024/240503_01.png)  

스크린샷에는 없지만, `Wakgreed` 레포지토리에서는 폰트 관련 파일들이 LFS로 등록되어 있었다.  
이왕 지우는 김에 레포지토리 자체 용량을 잡아먹던 FMOD 빌드 파일이라던지, 테스트용 빌드 파일들도 히스토리에서 지웠다.  

![텅텅](/assets/img/post/2024/240503_02.png)  

이후 문의를 넣어보니 빠르게 LSF 용량을 회수해주셨다.  
이제 FMOD 빌드 파일을 LFS로 올릴 수 있게 됐다.  

`Wakegreed` 레포지토리도 `Rewrite`로 인해 커밋 목록이 비정상적으로 많아져서,  
문의 넣을 때 `Contribution activity(잔디)`도 갱신해달라고 같이 요청했다.  

.. 이런거 직접 문의해야만 할 수 있는건가?  
기능이 제공되면 좋겠다..  

[참고 : 'Github LFS 저장공간 확보'](https://red-tiger.tistory.com/44)  

![To Be Continued..](/assets/img/post/embed/ToBeContinued.png)  
