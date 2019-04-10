# coin-recoginition

日本円硬貨の画像を認識して、バンティングボックスを表示するプログラムを実装しました。  
  
ここでは入力画像に対するバンディングボックスの付与しか行っていませんが、自分が参加したプロジェクトではリアルタイム認識まで実装しました。

## 実行環境

基本的にgoogle colabolatryで実行することを想定しています。  
   
```

# ここから先はマウントしたディレクトリで作業
SAMPLE_DIR="/content/gdrive/My Drive/coin"
%cd "{SAMPLE_DIR}"

# backupディレクトリを作っておく必要がある
! mkdir backup
```

ここで示すように  
・デフォルトのプログラムではgoogle driveのrootディレクトリにcoinという名前のディレクトリを作成する  
・"yolo_coin.ipynb", "yolov3.cfg"の2ファイルと, "data", "backup"の2フォルダをcoin以下に配置  

## 実行方法

基本的には yolo_coin.ipynbに従えばOK  
   
```
# 予測実行
DATA = f"{SAMPLE_DIR}/data/obj.data"
CONFIG = f"{SAMPLE_DIR}/yolov3.cfg"
# 一旦、900.weightsを使う
WEIGHTS = f"{SAMPLE_DIR}/backup/yolov3_final.weights"
TARGET_IMG = f"{SAMPLE_DIR}/IMG_0411_frame_1.jpg"

! /content/darknet/darknet detector test "{DATA}" "{CONFIG}"  "{WEIGHTS}" "{TARGET_IMG}"
```
TARGET_IMGが入力画像となるが、ここを適宜変更して用いてください。

また
```
from IPython.display import Image, display
display(Image(f"{SAMPLE_DIR}/predictions.jpg"))
```
を変更すれば出力画像の保存先を変更できます。
