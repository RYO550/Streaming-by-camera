# Raspberry Piを使ったカメラのストリーミング

このプロジェクトは、Raspberry Piに接続されたカメラからの映像をストリーミングする方法を説明しています。

## 本記事で使用したもの
- WEBカメラ UCAM-C520FBBK ELECOM
- Raspberry PiにインストールされたGStreamer
- クライアントPC (UbuntuなどのLinuxディストリビューション)

### ステップ 1: Raspberry PiにGStreamerをインストールする
以下のコマンドを実行して、Raspberry PiにGStreamerをインストールします:
sudo apt update
sudo apt install gstreamer1.0-tools gstreamer1.0-plugins-base gstreamer1.0-plugins-good gstreamer1.0-plugins-bad gstreamer1.0-plugins-ugly

### ステップ 2: カメラを使ってストリーミングを開始
GStreamer のインストールが完了したら、Raspberry Pi に接続したカメラの映像をストリーミングします。以下のコマンドを使用して、カメラの映像をエンコードし、同一ネットワーク内の受信側デバイスに送信します。

gst-launch-1.0 v4l2src device=/dev/video0 ! videoconvert ! x264enc tune=zerolatency ! rtph264pay ! udpsink host=<受信側のIPアドレス> port=5000
