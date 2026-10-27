# Multi Quest Viewer

Meta Questの映像をWindows PCで一覧・拡大・投影するアプリです。Windows 11 x64向けのプレビュー版です。

**基本セットはMulti Quest Viewer＋Multi Quest Connectです。QuestBladeは必要ありません。**

## Connectから始める

1. [Connectの公開Releases](https://github.com/noriki-mochizuki/multi-quest-connect/releases/latest)から `MultiQuestConnect-Setup.zip` を取得し、全ファイルを展開して `Multi Quest Connect Setup.exe` を開きます。ViewerやQuestBladeが未導入でも実行できます。
2. Questを同じLANへつなぎ、USB接続します。信頼するPCでは、Quest内のUSBデバッグ許可で「このパソコンから常に許可」を本人が選びます。WindowsのSetupで対象Questを選び、導入・設定を実行します。
3. 完了後USBを外し、下記Viewerを同じWindowsユーザーへインストールして起動します。登録済みQuestへ接続し、利用者がQuest上で起動したVRアプリを表示します。

PCごとにADBの信頼が必要です。別PCで初めて使う場合は、そのPCでConnectのUSBセットアップ・標準の信頼確認を行ってください。認証済みPCでの普段の利用とは異なります。キーは作り直しません。初回許可を自動で押す機能はありません。

ConnectはQuest内で開いて単独更新できます。ViewerやQuestBladeを更新のために起動する必要はありません。更新確認の通信失敗はLAN接続を妨げません。

## インストール

[最新のReleases](https://github.com/noriki-mochizuki/multi-quest-viewer/releases/latest)から **Multi-Quest-Viewer-Setup.exe** を取得して実行してください。GitHubの認証キーは不要です。インストール後はスタートメニューから起動します。.NETと転送用ツールを同梱し、ゲーム配信にはMicrosoft WebView2 Runtimeを使用します。

旧ポータブル版の設定を引き継ぐ場合は、旧`Multi Quest Viewer.exe`があるフォルダーにインストーラーを置いて実行してください。設定・A〜F・接続情報はユーザーのローカル領域へ保存し、上書き更新で保持します。設定内「更新を確認する」から、整合性検査後のインストーラーを起動できます。

Windowsコード署名は未導入です。SmartScreen等で発行元確認が表示される場合があります。添付のSHA256SUMS.txtで取得ファイルを照合できます。

## 使い方

- 通常のQuest表示：最初にUSBでセットアップし、信頼するPCではQuest内で「このパソコンから常に許可」を選びます。その後は同一LANへ接続します。標準の許可画面は自動操作しません。
- QuestBladeのゲーム配信：対応するゲーム側で配信をONにします。USB/ADB不要です。ゲーム本体はこの公開リポジトリに含みません。
- 個体ラベル：設定で同じ実機の通常表示とゲーム配信をA〜Fへ手動で対応付けます。接続順・IPが変わっても維持し、未接続枠も固定です。
- 音声：各画面の「音声」を選ぶと、その1台だけPCで再生します。起動時はミュート。別の台を選ぶと前の音声は停止します。ゲーム配信の音声にはQuestBlade0.1.19以降が必要です。OSや対象アプリが音声取得を制限する場合は取得できません。
- Fキーで投影のON/OFF、Escで解除。映像をクリックして拡大できます。

ADBは、自分で起動したサーバーだけを管理し、既存の共有サーバーを終了しません。初回のQuest許可、Developer Mode、WindowsのLAN通信許可は利用者が行います。保護されたコンテンツの取得制限を回避する機能はありません。

## 検証段階

PCでの自動テスト、CPU/D3D11の実H.264復号、切断分離、Windows上のUnityからWebView2へのOpus受信、インストール・更新・アンインストールを確認しています。

物理Quest2台のUSBなし同一LAN、別途オフラインLAN、Quest実音声、4→6台・30分連続、Surface Laptop Studioでの性能は未確認です。**実機同時上限は2台**を維持しています。合成6画面の成功は、実機6台の受入を意味しません。まず軽量画質を使用してください。

## 配布物・ライセンス

このリポジトリはバイナリ配布用です。Viewerのソース、端末設定・ログ、認証キー、ゲームのAPK・素材は公開していません。Viewerバイナリの利用・再配布条件は添付LICENSE.txtを参照してください。

公式scrcpy4.1、公式ADB37.0.0、.NET/WPF/ASP.NET Core、WebView2等のライセンスとNOTICEをインストーラーへ同梱しています。FFmpeg9.0.1は公式ソースから外部コーデック依存なしでビルドし、完全な対応ソース・実構成・再ビルド手順を **ffmpeg-corresponding-source.zip** として同梱・添付しています。各OSSの権利は各ライセンスに従います。
