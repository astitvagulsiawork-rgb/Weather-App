<img width="1920" height="1200" alt="Screenshot (48)" src="https://github.com/user-attachments/assets/026cb39c-1212-4af8-b6b6-f59d8d5e30ce" />
<img width="1920" height="1200" alt="Screenshot (49)" src="https://github.com/user-attachments/assets/db211958-ed42-4dc9-95ff-29e4e3ce5940" />
# WeatherVibe 🌤️

A single-file, no-build weather app with a live animated sky that actually reflects the real weather — rain falls, lightning strikes, snow drifts, the sun glows hotter on hot days, and the moon shows real phase and rise/set times for wherever you are.

Open `weather-app.html` in a browser. That's the whole setup.

---

## Features

- **Live weather data** for any city (search) or your current location (geolocation + reverse geocoding), via [Open-Meteo](https://open-meteo.com/) — no API key required
- **Animated sky background** that matches the real condition and time of day:
  - Rain, drizzle, and thunderstorms with real falling raindrops
  - Lightning bolts that strike from the top or diagonally from a top corner, synced with real thunder audio
  - Snow that automatically appears below 0°C and turns into a fast-moving blizzard below −12°C, regardless of the reported condition
  - Drifting clouds (white normally, dark during rain/storms)
  - A sun that glows brighter on hot days and turns orange near sunset (skipped during bad weather)
  - A moon with real craters, phase, and glow at night
  - Twinkling stars (hidden during rain/snow/storms, since you wouldn't see them anyway)
- **A live mini "postcard" scene inside the current-conditions card**, mirroring the same weather/time logic as the full background
- **Detailed condition data**: feels-like temperature, humidity, pressure with trend, UV index, visibility, wind (with a compass dial), rain chance
- **Air quality** (PM2.5, PM10, SO₂, CO, overall AQI) via a live air-quality API
- **Sun & Moon card** with a real rise/set arc visualization and actual moon phase, computed astronomically for your exact coordinates
- **7-day and 24-hour forecasts**
- **"Conditions & activities" estimates** (outdoor activities, stargazing, fishing, sailing, cold risk, mosquito activity) — simple heuristics from temperature, wind, humidity, and moon brightness, clearly labeled as estimates rather than a scientific index
- **Ambient weather audio**, synthesized entirely in-browser with the Web Audio API (no audio files):
  - Rain/storm hiss that gets heavier with intensity
  - Real thunderclaps synced to each visible lightning strike
  - A soft snow/blizzard wind hush
  - A wind whistle that only kicks in above ~32 km/h (20 mph) and grows louder/higher-pitched with wind speed
  - Muted by default — tap the speaker icon to turn it on (required by browser autoplay rules)
- **Auto-refresh** every 10 minutes, plus a manual refresh button, so data never goes stale
- **°C/°F toggle**

## Tech stack

Plain HTML, CSS, and vanilla JavaScript — no framework, no build step, no `node_modules`. Weather art is drawn live with the Canvas API; UI charts (compass, AQI ring, sun arc) are inline SVG.

## APIs used

| Purpose | Service |
|---|---|
| Weather forecast | [Open-Meteo Forecast API](https://open-meteo.com/) |
| City search | Open-Meteo Geocoding API |
| Reverse geocoding (device location → place name) | BigDataCloud reverse-geocode-client |
| Air quality | Open-Meteo Air Quality API |

All are free and require no API key. Attribution to Open-Meteo is shown in the app footer.

## Running it

1. Download `weather-app.html`
2. Open it in any modern browser (Chrome, Firefox, Edge, Safari)
3. Allow location access when prompted, or use the search bar

No installation, no dependencies, no server required.

## Notes / limitations

- Requires an internet connection (it fetches live data on load and every 10 minutes)
- Browser geolocation on desktop is IP/Wi-Fi based, not GPS — if it resolves to the wrong city, use the search bar instead
- Ambient sound needs a tap on the speaker icon before it will play (standard browser autoplay restriction, not a bug)
- The "Conditions & activities" ratings are simple estimates built from available weather data, not a licensed or scientifically validated index

## License

MIT — feel free to fork, learn from, or build on this.

---

# WeatherVibe 🌤️（日本語）

天気に連動してリアルタイムに変化する、アニメーション背景付きの天気アプリです。ビルドや依存関係は一切不要で、`weather-app.html` を1ファイルだけブラウザで開けば動作します。

## 主な機能

- **リアルタイムの気象データ**：都市名検索、または現在地（位置情報＋逆ジオコーディング）に対応。データ取得元は [Open-Meteo](https://open-meteo.com/)（APIキー不要）
- **実際の天気・時間帯に連動したアニメーション背景**：
  - 雨・霧雨・雷雨（実際に降る雨粒アニメーション）
  - 落雷アニメーション（画面上部または上部の角から斜めに発生し、雷鳴の音とも同期）
  - 気温が0℃を下回ると自動的に雪が降り、−12℃を下回ると吹雪（ブリザード）に変化
  - 流れる雲（通常は白、雨・嵐の時は黒）
  - 気温が高い日はより明るく輝く太陽、日没前はオレンジ色に変化（悪天候時は無効）
  - 実際の満ち欠け・輝きを再現した月（クレーター表現あり）
  - 瞬く星（雨・雪・嵐の時は非表示）
- **現在の天気カード内にもミニ背景シーン**を表示し、全体の背景と同じロジックで連動
- **詳細な気象データ**：体感温度、湿度、気圧（傾向付き）、UV指数、視程、風向・風速（コンパス表示）、降水確率
- **大気質情報**（PM2.5、PM10、SO₂、CO、総合AQI）をリアルタイム取得
- **日の出・日の入り／月の出・月の入りカード**：実際の軌道を模したアーク表示と、現在地の座標から計算した正確な月齢
- **24時間予報・7日間予報**
- **「コンディション＆アクティビティ」の目安表示**（アウトドア活動、天体観測、釣り、セーリング、防寒対策、蚊の活動）※気温・風・湿度・月明かりなどから算出した簡易的な目安であり、科学的指標ではない旨を明記
- **環境音（アンビエントサウンド）**：外部音声ファイルを使わず、Web Audio APIですべてブラウザ内で合成
  - 雨・嵐の音（強さに応じて変化）
  - 実際の落雷と同期した雷鳴
  - 雪・吹雪時の静かな風音
  - 風速が約32km/h（20mph）を超えると鳴り始める、風速に応じて強く・高音になる「風切り音」
  - 初期状態はミュート。スピーカーアイコンをタップすると再生（ブラウザの自動再生制限のため）
- **10分ごとの自動更新**＋手動更新ボタン
- **摂氏／華氏の切り替え**

## 技術構成

素のHTML・CSS・JavaScriptのみで構成。フレームワークやビルド工程は使用していません。天気の描画はCanvas APIによるリアルタイム描画、UI（コンパス、AQIゲージ、太陽と月の軌道）はインラインSVGで実装しています。

## 使用API

| 用途 | サービス |
|---|---|
| 気象予報 | Open-Meteo Forecast API |
| 都市検索 | Open-Meteo Geocoding API |
| 逆ジオコーディング | BigDataCloud reverse-geocode-client |
| 大気質 | Open-Meteo Air Quality API |

すべて無料でAPIキー不要です。Open-Meteoへのクレジット表記はアプリのフッターに記載しています。

## 実行方法

1. `weather-app.html` をダウンロード
2. お好みのブラウザ（Chrome、Firefox、Edge、Safariなど）で開く
3. 位置情報の許可を求められたら許可、または検索バーで都市を検索

インストールや依存関係、サーバーは一切不要です。

## 注意事項

- インターネット接続が必要です（初回読み込み時および10分ごとにデータを取得します）
- デスクトップのブラウザの位置情報はGPSではなくIP／Wi-Fiベースのため、位置がずれる場合は検索バーのご利用を推奨します
- 環境音はブラウザの自動再生制限により、スピーカーアイコンのタップ操作が必要です（不具合ではありません）
- 「コンディション＆アクティビティ」の目安は取得可能な気象データから算出した簡易的な推定値であり、正式な指標やライセンスされた評価基準ではありません

## ライセンス

MITライセンス。自由にフォーク・学習・改変してご利用いただけます。
