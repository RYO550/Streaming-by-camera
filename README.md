# Raspberry Piを使ったカメラのストリーミング
このプロジェクトは、Raspberry Piに接続されたカメラからの映像をストリーミングし、同一ネットワーク内の他のデバイスから映像を閲覧する方法を説明しています。

## 本記事で使用したもの
- WEBカメラ UCAM-C520FBBK ELECOM
- 送信側Raspberry Pi 4 OS:Ubuntu 24.04.1 LTS
- 受信側PC ハードウェアモデル:Sony Corporation SVE15127CJB
     プロセッサ:Intel® Core™ i7-3632QM × 8
     OS:Ubuntu 24.04.1 LTS
  
### ステップ 1: 送信側Raspberry Piと受信側PCにGStreamerをインストールする
以下のコマンドを実行して、Raspberry PiにGStreamerをインストールします:
sudo apt update
sudo apt install gstreamer1.0-tools gstreamer1.0-plugins-base gstreamer1.0-plugins-good gstreamer1.0-plugins-bad gstreamer1.0-plugins-ugly


### ステップ 2: カメラを使ってストリーミングを開始(送信側Raspberry Pi側の設定)
以下のコマンドを使用して、カメラの映像をエンコードし、同一ネットワーク内の受信側PCに送信します。
「<受信側のIPアドレス>」には「192.168〜」のような受信側PCのIPアドレスを記載してください。（<>を残さないように注意）
port(ポート番号)は適当にきめてください。

gst-launch-1.0 v4l2src device=/dev/video0 ! videoconvert ! x264enc tune=zerolatency ! rtph264pay ! udpsink host=<受信側のIPアドレス> port=5000


### ステップ 3: 映像を閲覧(受信側PCの設定)
以下のコマンドを使用して、映像を閲覧します。送信側の port(ポート番号)と一致させてください。

gst-launch-1.0 udpsrc port=5000 caps="application/x-rtp, media=(string)video, clock-rate=(int)90000, encoding-name=(string)H264" ! rtph264depay ! avdec_h264 ! videoconvert ! autovideosink

以上で完了です。
途切れずに安定したなめらかな映像がストリーミングできます。
