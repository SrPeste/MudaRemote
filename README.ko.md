[English](README.md) | [Français](README.fr.md) | [简体中文](README.zh-CN.md) | [日本語](README.ja.md) | [한국어](README.ko.md)

# ✨ MudaRemote: Mudae 고급 자동화 ✨

[![Discord TOS Violation - **주의해서 사용하세요**](https://img.shields.io/badge/Discord%20TOS-VIOLATION-red)](https://discord.com/terms) ⚠️ **계정 정지 위험!** ⚠️

**🛑🛑🛑 경고: 셀프 봇 - 잠재적인 Discord 서비스 약관 위반! 계정 정지 위험! 🛑🛑🛑**
**🔥 본인 책임 하에 사용하세요! 🔥 저희는 귀하의 계정에 대해 취해진 어떠한 조치에 대해서도 책임지지 않습니다. 😱**

---

## 🚀 MudaRemote: Mudae 경험 향상 (책임감 있게 사용하세요!)

MudaRemote는 Discord 봇 Mudae의 다양한 작업을 자동화하도록 설계된 Python 기반 셀프 봇입니다. 실시간 스나이핑 및 지능형 클레임과 같은 기능을 제공합니다. **그러나 셀프 봇 사용은 Discord 서비스 약관에 위배되며 계정 정지 또는 차단으로 이어질 수 있습니다.** 극도로 주의하여 사용하고 관련 위험을 이해하십시오.

### ✨ 핵심 기능:

*   **🎯 외부 스나이핑 (위시리스트, 시리즈 및 카케라 값):**
    *   **위시리스트 스나이핑:** *다른 사람*이 뽑은 캐릭터가 위시리스트에 있는 경우 자동으로 클레임합니다 (지연 시간 설정 가능).
    *   **시리즈 스나이핑:** *다른 사람*이 뽑은 캐릭터가 시리즈 위시리스트에 있는 경우 자동으로 클레임합니다 (지연 시간 설정 가능).
    *   **카케라 값 스나이핑:** *다른 사람*이 뽑은 캐릭터의 카케라 값 (임계값 이상인 경우) 에 따라 자동으로 클레임합니다.
*   **🟡 외부 카케라 반응 스나이핑 (신규!):** *모든* Mudae 메시지에 있는 카케라 반응 버튼을 자동으로 클릭합니다.
*   **😴 스나이프 전용 모드:** 봇 인스턴스를 롤 명령을 보내지 않고 외부 스나이프만 수신하고 실행하도록 구성합니다.
*   **⚡ 반응형 자체 롤 스나이핑:** *자신의* 롤에서 뽑은 캐릭터가 기준 (위시리스트, 시리즈, 카케라 값) 에 일치하는 경우 즉시 클레임합니다. 현재 롤 배치를 중단합니다.
*   **👯 다중 계정 지원:** 여러 봇 인스턴스를 동시에 실행하며, 각 인스턴스는 자체 구성을 가집니다.
*   **🤖 자동화된 롤링 및 일반 클레임:** 롤 명령을 처리하고 롤 완료 후 최소 카케라 값에 따라 일반 클레임을 수행합니다.
*   **🥇 지능형 클레임 로직:** `$rt`를 사용하여 잠재적인 두 번째 클레임을 수행합니다.
*   **🔄 자동 롤 및 클레임 재설정 감지:** Mudae의 재설정 타이머를 모니터링하고 작업을 최적화하기 위해 기다립니다.
*   **🔑 키 모드:** 메인 캐릭터 클레임 권한이 쿨다운 중일 때도 카케라 수집을 위해 지속적으로 롤링할 수 있습니다.
*   **⏱️ 사용자 정의 가능한 지연 및 롤 속도:** 일반적인 작업 지연 및 롤 명령 속도를 조정합니다.
*   **🗂️ 쉬운 프리셋 구성:** `presets.json` 파일을 통해 다른 계정/시나리오의 모든 설정을 관리합니다.
*   **📊 콘솔 로깅:** 봇 작업 및 상태에 대한 명확하고 색상으로 구분된 실시간 출력.

---

## 🛠️ 설정 가이드

1.  **🐍 Python:** Python 3.8 이상이 설치되어 있는지 확인하십시오. ([Python 다운로드](https://www.python.org/downloads/))
2.  **📦 종속성:** 터미널 또는 명령 프롬프트를 열고 다음을 실행하십시오:
    ```bash
    pip install discord.py-self inquirer
    ```
3.  **📝 `presets.json`:** 스크립트와 동일한 디렉토리에 `presets.json`이라는 파일을 생성하십시오. 여기에 봇 구성을 추가하십시오. 사용 가능한 모든 옵션은 아래 예시를 참조하십시오.
4.  **🚀 실행:** 터미널에서 스크립트를 실행하십시오:
    ```bash
    python mudae_bot.py
    ```
    (다른 경우 `mudae_bot.py`를 스크립트의 실제 파일 이름으로 바꾸십시오).
5.  **🕹️ 프리셋 선택:** 나타나는 대화형 메뉴에서 실행할 구성된 봇을 선택하십시오.

---

### `presets.json` 구성 예시:

```json
{
  "YourBotAccountName": {
    // --- 필수 설정 ---
    "token": "YOUR_DISCORD_ACCOUNT_TOKEN", // Discord 계정 토큰. 극비로 유지하십시오!
    "channel_id": 123456789012345678,     // Mudae 명령을 위한 Discord 채널 ID.
    "roll_command": "wa",                  // 선호하는 Mudae 롤 명령 (예: wa, hg, w, ma). "rolling"이 true인 경우에만 사용됩니다.
    "delay_seconds": 1,                    // 일부 봇 작업 간의 일반적인 지연 (초) (예: $tu 파싱 전). "rolling"이 true인 경우에만 사용됩니다.
    "mudae_prefix": "$",                   // Mudae가 서버에서 사용하는 접두사 (일반적으로 "$").
    "min_kakera": 50,                      // 일반 (롤 배치 후) 캐릭터 클레임의 최소 카케라 값. "rolling"이 true인 경우에만 사용됩니다.

    // --- 핵심 작동 모드 ---
    "rolling": true,                       // (기본값: true) true인 경우 봇은 롤링, 클레임, $tu 확인 등을 수행합니다.
                                           // false인 경우 봇은 스나이프 전용 모드로 전환됩니다: 롤링 없음, $tu 확인 없음, 외부 스나이프만 수신합니다.

    // --- 선택적 설정 (일부는 "rolling: true"에 따라 달라집니다) ---
    "key_mode": false,                     // (기본값: false) true이고 "rolling"이 true인 경우, 캐릭터 클레임 권한이 없어도 카케라 수집을 위해 롤링합니다.
    "start_delay": 0,                      // (기본값: 0) 메뉴에서 선택된 후 봇이 시작하기 전의 지연 (초).
    "roll_speed": 0.4,                     // (기본값: 0.4) 개별 롤 명령 간의 지연 (초). "rolling"이 true인 경우에만 사용됩니다.

    // 외부 스나이핑 설정 (다른 사람이 롤링한 캐릭터/카케라용 - "rolling" 상태와 관계없이 구성된 경우 항상 활성화됩니다)
    "snipe_mode": true,                    // (기본값: false) 외부 위시리스트 스나이핑 (하트 클레임)을 활성화합니다.
    "wishlist": ["Character Name 1", "Character Name 2"], // 하트 스나이핑을 위한 캐릭터 이름 목록.
    "snipe_delay": 2,                      // (기본값: 2) 외부 위시리스트 스나이프 및 외부 카케라 값 스나이프를 클레임하기 전의 지연 (초).

    "series_snipe_mode": true,             // (기본값: false) 외부 시리즈 스나이핑 (하트 클레임)을 활성화합니다.
    "series_wishlist": ["Series Name 1"],  // 하트 스나이핑을 위한 시리즈 이름 목록.
    "series_snipe_delay": 3,               // (기본값: 3) 외부 시리즈 스나이프를 클레임하기 전의 지연 (초).

    "kakera_reaction_snipe_mode": false,   // (기본값: false) 외부 카케라 반응 스나이핑 (카케라 버튼 클릭)을 활성화합니다.
    "kakera_reaction_snipe_delay": 0.75,   // (기본값: 0.75) 외부 카케라 반응을 클릭하기 전의 지연 (초).

    // 반응형 스나이핑 설정 (자신의 롤에서 얻은 캐릭터/카케라용 - "rolling: true"인 경우에만 활성화됩니다)
    "reactive_snipe_on_own_rolls": true,   // (기본값: true) 자신의 롤 중에 즉각적인 반응형 하트 클레임 및 카케라 클릭을 활성화/비활성화합니다.
                                           // true인 경우, 위시리스트, 시리즈_위시리스트 및 kakera_snipe_threshold (kakera_snipe_mode가 true인 경우)를 하트 클레임의 기준으로 사용합니다.
                                           // 이러한 반응형으로 클레임된 캐릭터의 카케라도 클릭됩니다.
                                           // false인 경우, 자신의 롤에 대한 모든 클레임/카케라 클릭은 롤 배치가 완료된 후에 발생합니다.

    // 카케라 임계값 설정 (반응형 자체 롤 하트 클레임 및 외부 카케라 값 하트 스나이프 모두에 사용됩니다)
    "kakera_snipe_mode": true,             // (기본값: false) true인 경우, `kakera_snipe_threshold`를 다음 하트 클레임의 기준으로 활성화합니다:
                                           //    1. 자신의 롤 중에 즉각적인 반응형 하트 클레임 ("rolling" 및 reactive_snipe_on_own_rolls가 true인 경우).
                                           //    2. 지연된 외부 카케라 값 전용 하트 스나이프 (`snipe_delay` 사용).
    "kakera_snipe_threshold": 100,         // (기본값: 0) `kakera_snipe_mode`가 true인 경우 위에서 언급된 하트 클레임을 트리거하는 최소 카케라 값.

    // 기타 ("rolling: true"인 경우에만 활성화됩니다)
    "snipe_ignore_min_kakera_reset": false // (기본값: false) true인 경우, 롤 후 일반 클레임의 경우 클레임 재설정이 1시간 미만으로 남았다면 min_kakera는 사실상 0이 됩니다.
                                           // 이는 반응형 스나이핑 또는 외부 카케라 값 스나이핑 임계값에 영향을 미치지 않습니다.
  }
  // 여기에 쉼표로 구분하여 다른 계정에 대한 프리셋을 추가하십시오.
}
```

---

## 🎮 Discord 토큰 얻기 🔑

셀프 봇은 Discord 계정 토큰을 필요로 합니다. **이 토큰은 귀하의 계정에 대한 완전한 접근 권한을 부여합니다 – 극비로 유지하십시오! 공유하는 것은 비밀번호를 넘겨주는 것과 같습니다.** 이 봇을 대체 계정에서 사용하는 것이 좋습니다.

1.  **웹 브라우저에서 Discord를 엽니다** (예: Chrome, Firefox). *데스크톱 앱이 아닙니다.*
2.  개발자 도구를 열려면 **F12**를 누르십시오.
3.  **`Console`** 탭으로 이동하십시오.
4.  다음 코드 스니펫을 콘솔에 붙여넣고 Enter를 누르십시오:
    ```javascript
    window.webpackChunkdiscord_app.push([
    	[Symbol()],
    	{},
    	req => {
    		if (!req.c) return;
    		for (let m of Object.values(req.c)) {
    			try {
    				if (!m.exports || m.exports === window) continue;
    				if (m.exports?.getToken) return copy(m.exports.getToken());
    				for (let ex in m.exports) {
    					if (m.exports?.[ex]?.getToken && m.exports[ex][Symbol.toStringTag] !== 'IntlMessagesProxy') return copy(m.exports[ex].getToken());
    				}
    			} catch {}
    		}
    	},
    ]);

    window.webpackChunkdiscord_app.pop();
    console.log('%cWorked!', 'font-size: 50px');
    console.log(`%cYou now have your token in the clipboard!`, 'font-size: 16px');
    ```
5.  토큰이 클립보드에 복사됩니다. `presets.json` 파일의 `"token"` 필드에 조심스럽게 붙여넣으십시오.

---

## 🤝 기여

기여를 환영합니다! 문제 보고, 기능 제안 또는 프로젝트 저장소에 풀 리퀘스트 제출을 자유롭게 하십시오.

**🙏 Discord 계정에 대한 잠재적인 위험을 충분히 인지하고 이 도구를 책임감 있고 윤리적으로 사용하십시오. 🙏**

**즐거운 (그리고 조심스러운!) Mudae 활동 되세요!** 😉

---
**라이선스:** [MIT 라이선스](LICENSE)
