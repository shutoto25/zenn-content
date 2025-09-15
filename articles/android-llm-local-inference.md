---
title: "android端末でLLMを動かしてみよう"
emoji: "🤖"
type: "tech"
topics: ["android", "llm", "ai", "mediapipe"]
published: false
---

# 基本知識

#### LLM（Large Language Model）

#### 推論（Inference）

# 実際に動かしてみよう

### Google AI Studio

https://aistudio.google.com/prompts/new_chat

### MediaPipe Studio

https://mediapipe-studio.webapps.google.com/home

### Google AI Edge Gallery

https://github.com/google-ai-edge/gallery

最先端の生成AIモデルのパワーを直接体験できる実験的なアプリです。現在はAndroidのみ提供中で[Google Play](https://play.google.com/store/apps/details?id=com.google.ai.edge.gallery)からインストール可能です。アプリからモデルをダウンロードすれば、インターネット接続なしでローカルで実行が試せます。様々なモデルを試したり、チャットしたり、画像や音声クリップで質問したり、プロンプトを確認したり、色々利用可能です。

## アプリに組み込む

### 必要なもの ￼
- Android Studio（Hedgehogバージョンで動作確認済み）
- 物理Androidデバイス（Android 7.0／SDK 24以上、開発者モード有効）


### モデルのダウンロード

[Hugging Face](https://huggingface.co/litert-community)から使用したいモデルをダウンロードします。今回わたしは[Gemma3-1B-IT](https://huggingface.co/litert-community/Gemma3-1B-IT)を使いました。「Files and versions」タブからダウンロード。


ファイル名の構成
| 項目 | 内容例 | 意味・用途 |
| ---- | ---- | ---- |
| 精度・量子化 | f32, q4, q8, int4, int8 | f32は高精度（大きいサイズ）、q4/q8/int4/int8は圧縮（小さいサイズ・高速） |
| シーケンス長 | seq128, multi-prefill-seq | 入力できるトークン数やバッチ処理の違い |
| ハードウェア最適化 | sm8550, mt6989, ekv1280 | 特定のチップやデバイス向けに最適化 |
| 拡張子 | .task, .litertlm | モデルの保存形式や読み込み方法の違い |


モデル比較
| Head | Head | Head |
| ---- | ---- | ---- |
| Text | Text | Text |
| Text | Text | Text |
②adbコマンドでモデルを端末にPushする
```
$ adb shell rm -r /data/local/tmp/llm/ # 以前のモデルを削除
$ adb shell mkdir -p /data/local/tmp/llm/
$ adb push output_path /data/local/tmp/llm/model_version.task
```

#### 依存関係を追加
```
dependencies {
    implementation 'com.google.mediapipe:tasks-genai:0.10.27'
}
```

### Taskを初期化
```
// Set the configuration options for the LLM Inference task
val taskOptions = LlmInferenceOptions.builder()
        .setModelPath('/data/local/tmp/llm/model_version.task')
        .setMaxTopK(64)
        .build()

// Create an instance of the LLM Inference task
llmInference = LlmInference.createFromOptions(context, taskOptions)
```

#### Taskを実行
```
val result = llmInference.generateResponse(inputPrompt)
```

#### 動作確認
チャット風のUIを作成して、プロンプトを実行。