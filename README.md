# android-dev-check-list 🚀

![Kotlin](https://img.shields.io/badge/Kotlin-1.9%2B-7F52FF?logo=kotlin&logoColor=white)
![Jetpack Compose](https://img.shields.io/badge/Jetpack%20Compose-May%202024-4285F4?logo=android&logoColor=white)
![Platform](https://img.shields.io/badge/Platform-Android%20%7C%20KMP-3DDC84?logo=android&logoColor=white)
![License](https://img.shields.io/badge/License-MIT-green)

A comprehensive checklist for Modern Android Development (MAD).
This list covers everything from project setup to release, focusing on **Jetpack Compose**, **Kotlin Multiplatform (KMP)** readiness, and clean architecture best practices.

## 🏗️ 1. Project Setup & Architecture
基盤設計とビルド環境の整備。プロジェクトの健全性とスケーラビリティを担保する。

- [ ] **Project Structure (Multi-module)**
    - *Desc:* 機能(Feature)、UI、Data、Coreなどでモジュールを分割し、ビルド時間の短縮と責務の分離を図る。
    - *💡 Rec:* [Guide to App Architecture](https://developer.android.com/topic/architecture)
- [ ] **Build Logic (Gradle)**
    - *Desc:* 依存関係の一元管理とConvention Pluginによるビルドロジックの再利用。
    - *💡 Rec:* Version Catalogs (`libs.versions.toml`), Convention Plugins
- [ ] **Flavor / Build Variant**
    - *Desc:* 開発(dev)、検証(stg)、本番(prod)など、環境ごとの向き先や設定を分離する。
- [ ] **Dependency Injection (DI)**
    - *Desc:* 依存性の注入により、コンポーネント間の結合度を下げテストを容易にする。
    - *💡 Rec:* **Hilt** (Android only), **Koin** (KMP ready)
- [ ] **BuildConfig / Secrets**
    - *Desc:* APIキーや環境ごとの定数を安全に管理し、コードから分離する。
    - *💡 Rec:* **Secrets Gradle Plugin**
- [ ] **Coroutines & Flow**
    - *Desc:* 非同期処理とリアクティブストリームの基盤整備。
    - *💡 Rec:* `StateFlow`, `SharedFlow`, `Dispatchers` injection
- [ ] **Network Config**
    - *Desc:* クリアテキスト通信(http)の無効化や証明書ピニングの設定。
    - *💡 Rec:* `res/xml/network_security_config.xml`
- [ ] **App Startup**
    - *Desc:* アプリ起動時の初期化処理を最適化する。
    - *💡 Rec:* Jetpack App Startup

## 🎨 2. UI/UX & Design System
Jetpack Composeを用いた宣言的UIと、ユーザー体験の最大化。

- [ ] **Theme & Style (Material 3)**
    - *Desc:* ダークモード/ライトモード、Dynamic Color対応、Typographyの一元管理。
    - *💡 Rec:* Material Theme Builder
- [ ] **Edge to Edge**
    - *Desc:* ステータスバーやナビゲーションバーの領域までコンテンツを描画し、没入感を高める。
    - *💡 Rec:* `enableEdgeToEdge()`, `WindowInsets`
- [ ] **Navigation**
    - *Desc:* 型安全な画面遷移と引数の受け渡し。
    - *💡 Rec:* **Navigation Compose** (Type-safe APIs), Voyager (KMP)
- [ ] **Responsive / Adaptive Layout**
    - *Desc:* タブレット、フォルダブル、横画面など多様な画面サイズへの対応。
    - *💡 Rec:* `WindowSizeClass`, `BoxWithConstraints`
- [ ] **Resources Management**
    - *Desc:* 文字列、画像、フォントの管理（KMPを見据えた構成）。
    - *💡 Rec:* **Compose Multiplatform Resources**
- [ ] **Splash Screen**
    - *Desc:* Android 12以降の標準仕様に準拠した起動画面。
    - *💡 Rec:* Core Splashscreen API
- [ ] **Image Loading**
    - *Desc:* 画像の非同期読み込み、キャッシュ、メモリ管理。
    - *💡 Rec:* **Coil 3** (KMP ready)
- [ ] **Animations**
    - *Desc:* 状態変化に伴うトランジションやインタラクションのフィードバック。
    - *💡 Rec:* `AnimatedVisibility`, `SharedElementTransition`
- [ ] **Dialogs, Toasts & Overlays**
    - *Desc:* ユーザーへの通知や確認ダイアログの実装。
    - *💡 Rec:* Material 3 Components (`ModalBottomSheet`, `Snackbar`)
- [ ] **Accessibility (a11y)**
    - *Desc:* TalkBack対応、タッチターゲットサイズ(48dp+)、コンテンツ説明。
    - *💡 Rec:* Accessibility Scanner
- [ ] **Localization (i18n)**
    - *Desc:* 多言語対応リソースの準備。
    - *💡 Rec:* Android Studio Translations Editor
- [ ] **Rich Input / Keyboard**
    - *Desc:* Emoji Picker、IMEアクション（検索、完了など）の適切な設定。

## 💾 3. Data & Business Logic
堅牢なデータ層とビジネスロジックの実装。

- [ ] **Networking**
    - *Desc:* API通信の実装とエラーハンドリング。
    - *💡 Rec:* **Ktor** (KMP), Retrofit
- [ ] **Serialization**
    - *Desc:* JSONデータのパース処理。
    - *💡 Rec:* **Kotlinx.serialization**
- [ ] **Local Database**
    - *Desc:* オフラインキャッシュや複雑なデータ構造の永続化。
    - *💡 Rec:* **Room** (KMP Alpha), SQLDelight
- [ ] **Key-Value Storage**
    - *Desc:* ユーザー設定などの軽量なデータの保存。
    - *💡 Rec:* **DataStore** (Preferences/Proto)
- [ ] **State Management**
    - *Desc:* UIの状態(State)とロジックの分離。
    - *💡 Rec:* **ViewModel**, `androidx.lifecycle`
- [ ] **WorkManager**
    - *Desc:* バックグラウンドでの定期実行タスクや長時間処理。
- [ ] **Permissions Handling**
    - *Desc:* ランタイムパーミッションの要求と拒否時のUX考慮。
    - *💡 Rec:* Accompanist Permissions / Activity Result API
- [ ] **Pagination**
    - *Desc:* 大量データの分割読み込みと無限スクロール。
    - *💡 Rec:* **Paging 3**

## 🛡️ 4. Quality Assurance & Testing
「動く」だけでなく「正しく動き続ける」ための仕組み。

- [ ] **Unit Testing**
    - *Desc:* ViewModel, Repository, UseCaseのロジックテスト。
    - *💡 Rec:* JUnit 5, MockK, Turbine
- [ ] **UI / Integration Testing**
    - *Desc:* 画面描画とユーザー操作のテスト。
    - *💡 Rec:* Compose UI Test, Espresso
- [ ] **Screenshot Testing (VRT)**
    - *Desc:* デザイン崩れを検知するための画像比較テスト。
    - *💡 Rec:* **Roborazzi**, Paparazzi
- [ ] **Static Analysis (Lint)**
    - *Desc:* コードスタイルの統一とバグの早期発見。
    - *💡 Rec:* **Ktlint**, **Detekt**, Android Lint
- [ ] **Compose Stability**
    - *Desc:* Recompositionのスキップ判定を確認しパフォーマンスを最適化する。
    - *💡 Rec:* Compose Stability Analyzer (Compiler Metrics)
- [ ] **Error Handling / Crash Reporting**
    - *Desc:* 未処理例外の捕捉とクラッシュログの収集。
    - *💡 Rec:* **Firebase Crashlytics**
- [ ] **Memory Leaks**
    - *Desc:* メモリリークの検知。
    - *💡 Rec:* **LeakCanary**
- [ ] **Logging Strategy**
    - *Desc:* デバッグ用ログと本番用ログの出し分け。
    - *💡 Rec:* **Timber**, Napier (KMP)

## 🚀 5. Release & CI/CD
自動化による安全かつ迅速なリリースパイプライン。

- [ ] **CI/CD Pipeline**
    - *Desc:* プルリクエスト時のテスト実行、マージ時のビルドと配布の自動化。
    - *💡 Rec:* **GitHub Actions**, Bitrise
- [ ] **App Signing**
    - *Desc:* アップロード鍵の安全な管理（リポジトリに含めない）。
    - *💡 Rec:* Play App Signing
- [ ] **Obfuscation (R8)**
    - *Desc:* コードの難読化とリソースの削除によるアプリサイズ削減。
    - *💡 Rec:* `isMinifyEnabled = true`, ProGuard Rules
- [ ] **16KB Page Size Support**
    - *Desc:* Android 15以降のメモリページサイズ変更への対応。
- [ ] **Analytics**
    - *Desc:* ユーザー行動の分析。
    - *💡 Rec:* **Firebase Analytics**
- [ ] **Attribution**
    - *Desc:* インストール経路の計測（広告効果測定）。
    - *💡 Rec:* AppsFlyer, Adjust
- [ ] **Push Notifications**
    - *Desc:* リモートプッシュ通知の実装。
    - *💡 Rec:* Firebase Cloud Messaging (FCM)
- [ ] **License Management**
    - *Desc:* 使用しているOSSのライセンス一覧画面の生成。
    - *💡 Rec:* **AboutLibraries** plugin

## 📢 6. Store Presence
Google Play Storeでのコンバージョンを高める準備。

- [ ] **Privacy Policy & Terms**
    - *Desc:* 規約類のWebページ作成とリンク。
- [ ] **Store Assets**
    - *Desc:* アイコン、Feature Graphic、スクリーンショットの作成。
- [ ] **App Description (ASO)**
    - *Desc:* キーワードを意識したタイトルと説明文。
- [ ] **Release Notes**
    - *Desc:* ユーザーに向けた更新情報。

## 🧠 7. Development Knowledge Check
開発者が意識すべきKotlin/Androidのコアコンセプト。

- [ ] **Kotlin features:** `inline`/`noinline`, `reified`, `lateinit` vs `lazy`, `data class`
- [ ] **Equality:** `==` (構造) vs `===` (参照)
- [ ] **Lifecycle:** Activity/Fragment/ComposeのライフサイクルとState復元の理解
- [ ] **Threading:** Main(UI)スレッドブロックの回避 (ANR対策)
- [ ] **Memory:** メモリリークとOOMの違い、Bitmapの扱い
- [ ] **Security:** APIキー保護、外部ストレージ利用時の注意

## 🛠️ 8. Workflow & Productivity
チーム開発を円滑に進めるためのルール。

- [ ] **Git Strategy:** Conventional Commits, Branching Model
- [ ] **AI Assistance:** Copilot, Gemini, Claude Codeの活用
- [ ] **Documentation:** README, ADR (Architecture Decision Records)
