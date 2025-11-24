# 🎧 DevFocus: Generative Flow State Timer

**DevFocus**는 개발자와 디자이너의 몰입(Flow State)을 위해 설계된 **웹 기반 생성형 앰비언트 타이머**입니다.
정해진 음악을 반복 재생하는 것이 아니라, 알고리즘에 의해 실시간으로 생성되는 무한한 사운드스케이프를 제공합니다.

(스크린샷)

## ✨ Key Features

### 1\. Generative Ambient Engine (생성형 오디오)

  - **Brian Eno's Phasing Logic:** 브라이언 이노의 'Music for Airports'에서 영감을 받은 위상 변화 기법을 적용했습니다. 서로 다른 소수(Prime Number) 주기를 가진 루프들이 겹치고 어긋나며, 이론상 수년 동안 반복되지 않는 멜로디 패턴을 만듭니다.
  - **Stochastic Sequencing:** 모든 음표는 확정된 것이 아니라 확률(Probability)에 의해 연주됩니다. 이는 음악이 예측 불가능하면서도 자연스러운 '여백'을 갖게 합니다.

### 2\. Developer-Centric UI/UX

  - **Terminal Style Logging:** 오디오 엔진 내부에서 발생하는 이벤트(Note Trigger, Loop Cycle)를 터미널 로그 형태로 시각화하여, 개발자에게 익숙하고 편안한 시각적 피드백을 제공합니다.
  - **Direct Input Timer:** 팝업이나 복잡한 설정 없이, 타이머 숫자를 클릭하여 바로 시간을 수정할 수 있는 직관적인 인터페이스를 구현했습니다.
  - **Dark Mode Optimization:** 장시간 모니터를 보는 환경을 고려하여 GitHub Dark Dimmed 테마와 유사한 색상 팔레트(Low Contrast)를 사용했습니다.

## 🛠 Technical Implementation

이 프로젝트는 외부 무거운 프레임워크 없이 **Vanilla JS**와 **Tone.js** (Web Audio API Wrapper) 만으로 구현되었습니다.

### Audio Architecture

  * **PolySynth (Pad Layer):** `Sine` 파형 기반의 신디사이저로, 긴 Attack/Release 타임을 주어 구름처럼 부드러운 배경음을 형성합니다.
  * **FMSynth (Modular Layer):** 유로랙(Eurorack) 모듈러 신스의 불규칙성을 모방하기 위해 FM 합성을 사용한 짧은 'Blip' 사운드를 간헐적으로 생성합니다.
  * **Pink Noise (Texture):** 너무 정적인 디지털 사운드의 차가움을 없애기 위해, 미세한 핑크 노이즈를 바닥에 깔아 아날로그적인 질감을 더했습니다.

### Sound Sculpting (LPF)

장시간 청취 시 귀의 피로를 최소화하기 위해 **Master Chain에 1000Hz Low-Pass Filter**를 적용했습니다. 날카로운 고음역대를 의도적으로 깎아내어, 음악이 전경(Foreground)으로 튀어나오지 않고 배경(Background)에 머물도록 설계했습니다.

### Code Snippet (Core Logic)

```javascript
// Example: Using Prime Number Intervals for Phasing
const loopIntervals = ["7n", "11n", "13n"]; // 7, 11, 13 beat subdivisions

new Tone.Loop(time => {
    // 60% probability to play a note
    if (Math.random() < 0.6) {
        // ...trigger sound...
    }
}, "7n").start(0);
```

## 🚀 How to Run

이 프로젝트는 단일 HTML 파일로 구성되어 있어 별도의 빌드 과정이 필요 없습니다.

1.  Clone the repository:
    ```bash
    git clone https://github.com/YOUR_USERNAME/DevFocus.git
    ```
2.  Open `index.html` in your browser.
3.  Click **START FOCUS** to initialize the AudioContext.

## 📚 Tech Stack

  * **HTML5 / CSS3:** Modern Flexbox layout, CSS Variables for theming.
  * **JavaScript (ES6+):** Async/Await audio initialization.
  * **Tone.js:** Web Audio API library for synthesis and scheduling.

## 📝 License

This project is open source and available under the [MIT License](https://www.google.com/search?q=LICENSE).