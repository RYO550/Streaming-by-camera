# Raspberry Piを使ったカメラのストリーミング

このプロジェクトは、Raspberry Piに接続されたカメラからの映像をストリーミングする方法を説明しています。

## 必要なもの

- カメラ（例: PiカメラまたはUSBウェブカメラ）を接続したRaspberry Pi
- Raspberry PiにインストールされたGStreamer
- クライアントPC (UbuntuなどのLinuxディストリビューション)

### ステップ 1: Raspberry PiにGStreamerをインストールする

以下のコマンドを実行して、Raspberry PiにGStreamerをインストールします:

```bash
sudo apt update
sudo apt install gstreamer1.0-tools gstreamer1.0-plugins-base gstreamer1.0-plugins-good gstreamer1.0-plugins-bad gstreamer1.0-plugins-ugly
