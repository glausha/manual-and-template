# ADS System Architecture Diagram

自動運転システム（ADS）の全体アーキテクチャを示すMermaid図。

## 使用方法

このMermaid図をREADME.mdやドキュメントに埋め込む場合は、以下のコードブロックをコピーして使用すること。

---

## アーキテクチャ図

```mermaid
%%{init: {'theme': 'base', 'themeVariables': { 'primaryColor': '#FFFFFF', 'primaryBorderColor': '#4A90E2', 'lineColor': '#555555', 'secondaryColor': '#E8F1FF', 'tertiaryColor': '#E9F7EC', 'background': '#F7F7F7'}}}%%
flowchart TB
    subgraph ADS["🚗 ADS System Architecture"]
        direction TB
        
        subgraph Sensors["📡 センサー入力層"]
            CAM["📷 Camera\nカメラ"]
            LIDAR["🔦 LiDAR\nレーザー"]
            RADAR["📶 Radar\nレーダー"]
            GPS["🛰️ GPS/IMU\n位置情報"]
        end
        
        subgraph Perception["🧠 01_Perception - 認知モジュール"]
            OD["🎯 物体検出\nObject Detection"]
            LD["🛣️ 車線検出\nLane Detection"]
            SF["🔄 センサー統合\nSensor Fusion"]
            LOC["📍 自己位置推定\nLocalization"]
        end
        
        subgraph Planning["🗺️ 02_Planning - 計画モジュール"]
            GP["🌐 グローバル経路計画\nGlobal Path Planning"]
            LP["📐 ローカル経路計画\nLocal Path Planning"]
            BP["🚦 行動計画\nBehavior Planning"]
            PP["📈 軌道生成\nTrajectory Planning"]
        end
        
        subgraph Control["⚙️ 03_Embedded - 制御モジュール"]
            VC["🚘 車両制御\nVehicle Control"]
            ST["🔧 ステアリング制御\nSteering"]
            TH["⚡ スロットル制御\nThrottle"]
            BR["🛑 ブレーキ制御\nBrake"]
        end
        
        subgraph QA["🔍 04_QA - 品質保証"]
            SIM["🖥️ シミュレーション\nSimulation"]
            VV["✅ 検証・妥当性確認\nV&V"]
            MON["📊 監視・ログ\nMonitoring"]
        end
    end
    
    %% センサーから認知への接続
    CAM --> OD
    CAM --> LD
    LIDAR --> SF
    LIDAR --> OD
    RADAR --> SF
    GPS --> LOC
    
    %% 認知内部の接続
    OD --> SF
    LD --> SF
    SF --> LOC
    
    %% 認知から計画への接続
    LOC --> GP
    SF --> BP
    LOC --> LP
    
    %% 計画内部の接続
    GP --> LP
    BP --> LP
    LP --> PP
    
    %% 計画から制御への接続
    PP --> VC
    
    %% 制御内部の接続
    VC --> ST
    VC --> TH
    VC --> BR
    
    %% QAとの接続（点線で監視を表現）
    SF -.-> MON
    PP -.-> MON
    VC -.-> MON
    MON -.-> SIM
    SIM -.-> VV

    %% スタイル定義
    classDef sensorStyle fill:#E9F7EC,stroke:#4A90E2,stroke-width:2px,color:#333
    classDef perceptionStyle fill:#E8F1FF,stroke:#4A90E2,stroke-width:2px,color:#333
    classDef planningStyle fill:#FFF3E0,stroke:#4A90E2,stroke-width:2px,color:#333
    classDef controlStyle fill:#FCE4EC,stroke:#4A90E2,stroke-width:2px,color:#333
    classDef qaStyle fill:#F3E5F5,stroke:#7B61FF,stroke-width:2px,color:#333
    
    class CAM,LIDAR,RADAR,GPS sensorStyle
    class OD,LD,SF,LOC perceptionStyle
    class GP,LP,BP,PP planningStyle
    class VC,ST,TH,BR controlStyle
    class SIM,VV,MON qaStyle
```

---

## 簡易版（README埋め込み用）

リポジトリのREADME.mdに埋め込む場合は、以下の簡易版を使用すること。

```mermaid
%%{init: {'theme': 'base', 'themeVariables': { 'primaryColor': '#FFFFFF', 'primaryBorderColor': '#4A90E2', 'lineColor': '#555555'}}}%%
flowchart LR
    subgraph ADS["🚗 ADS System Architecture"]
        P1["📡 Sensors\nセンサー"]
        P2["🧠 Perception\n認知"]
        P3["🗺️ Planning\n計画"]
        P4["⚙️ Control\n制御"]
        
        P1 --> P2 --> P3 --> P4
    end
    
    style P1 fill:#E9F7EC,stroke:#4A90E2,stroke-width:2px
    style P2 fill:#E8F1FF,stroke:#4A90E2,stroke-width:2px
    style P3 fill:#FFF3E0,stroke:#4A90E2,stroke-width:2px
    style P4 fill:#FCE4EC,stroke:#4A90E2,stroke-width:2px
```

---

## モジュール別詳細図

### Perceptionモジュール詳細

```mermaid
%%{init: {'theme': 'base', 'themeVariables': { 'primaryColor': '#FFFFFF', 'primaryBorderColor': '#4A90E2', 'lineColor': '#555555'}}}%%
flowchart TB
    subgraph Perception["🧠 01_Perception Module"]
        direction TB
        
        subgraph Input["📥 入力"]
            I1["📷 Camera Images"]
            I2["🔦 LiDAR Point Cloud"]
            I3["📶 Radar Data"]
        end
        
        subgraph Processing["⚡ 処理"]
            P1["🎯 Object Detection\nYOLO/Transformer"]
            P2["🛣️ Lane Detection\nCNN"]
            P3["🔄 Sensor Fusion\nKalman Filter"]
        end
        
        subgraph Output["📤 出力"]
            O1["📍 Detected Objects"]
            O2["🛤️ Lane Information"]
            O3["🗺️ Fused Environment Model"]
        end
        
        I1 --> P1
        I1 --> P2
        I2 --> P1
        I2 --> P3
        I3 --> P3
        
        P1 --> O1
        P2 --> O2
        P1 --> P3
        P2 --> P3
        P3 --> O3
    end
    
    classDef inputStyle fill:#E9F7EC,stroke:#4A90E2,stroke-width:2px
    classDef processStyle fill:#E8F1FF,stroke:#4A90E2,stroke-width:2px
    classDef outputStyle fill:#FFF3E0,stroke:#4A90E2,stroke-width:2px
    
    class I1,I2,I3 inputStyle
    class P1,P2,P3 processStyle
    class O1,O2,O3 outputStyle
```

---

## 使用上の注意

1. **GitLabでの表示**: GitLab 15.0以降でMermaid図がネイティブサポートされている
2. **プレースホルダー**: `[本リポ]`の部分は、該当するリポジトリに合わせて強調表示を変更すること
3. **カスタマイズ**: 各モジュールの色は`classDef`で定義されているため、必要に応じて変更可能
