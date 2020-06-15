# SDLTest

[ゲームプログラミング C++](https://www.amazon.co.jp/dp/4798157619) を読んでいたが、ライブラリの導入方法がよくわからなかったので個人的にまとめた。
適当にやったらできたのでメモ

## ファイル構成
```
C-
 |-ProgLibs
  |-SDL
  |-SOIL
  |-GLEW
  |-rapidjson
```
中身は[ここ](https://github.com/gameprogcpp/code)の External ディレクトリをまんまコピー

## Visual Studio 側の設定
環境は、Community 2019 です。ほかのやつでも行けそう。  
  
**NOTE : 設定を見比べながらやったので、抜けがあるかもしれません。また、何かあっても私はなんら責任を負いません**

> 1. プロジェクトを開いて、`プロジェクト` → `<プロジェクト名>のプロパティ`から、プロパティダイアログを開く
> 1. 左上の構成を`すべての構成`にする
> 1. 左側のリストから`構成プロパティ`→`C/C++`→`全般`を選ぶ。
> 1. `追加のインクルードディレクトリ`の項目に`C:\ProgLibs\SDL\include;C:\ProgLibs\GLEW\include;C:\ProgLibs\SOIL\include;%(AdditionalIncludeDirectories)`と入力
> 1. 左側のリストから`構成プロパティ`→`リンカー`→`全般`を選ぶ
> 1. `追加のライブラリディレクトリ`の項目に`C:\ProgLibs\SDL\lib\win\x86;C:\ProgLibs\GLEW\lib\win\x86;C:\ProgLibs\SOIL\lib\win\x86;%(AdditionalLibraryDirectories)`と入力
> 1. `リンカー`→`入力`を選ぶ
> 1. `追加の依存ファイル`の項目に`opengl32.lib;SDL2.lib;SDL2main.lib;SDL2_ttf.lib;SDL2_mixer.lib;SDL2_image.lib;glew32.lib;SOIL.lib;%(AdditionalDependencies)`と入力
> 1. 左側のリストから`構成プロパティ`→`ビルドイベント`→`ビルド後のイベント`を選ぶ
> 1. `コマンドライン`の項目に`xcopy "C:\ProgLibs\SDL\lib\win\x86\*.dll" "$(OutDir)" /i /s /y
xcopy "C:\ProgLibs\GLEW\lib\win\x86\*.dll" "$(OutDir)" /i /s /y`を入力
> 1. `OK`を押す
