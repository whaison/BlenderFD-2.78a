# BlenderFD-2.78a
# Fluid Designer
これは、必要な流体デザイナーの変更を加えたBlender 2.78aソースコードです

Fluid Designerを構築するプロセスは、Building Blenderとまったく同じです。 ここでドキュメントを見つけることができます：
https://wiki.blender.org/index.php/Dev:Doc/Building_Blender


----------------------------------------------------------------------------------------------------------------
-----------------ここからURLの内容---------- https://wiki.blender.org/index.php/Dev:Doc/Building_Blender --------------------------


# ブレンダーの構築

# Blenderビルドをゼロから作成するためのオペレーティングシステム固有の手順。

- 上のLinux

- 上のMac

- 上のWindows

- 注：これは現在古くなっています：


- 上のFreeBSD
# ビルド環境の設定の概要
- このセクションは、ソースからC、C ++ソフトウェアをコンパイルするプロセスに慣れていない人のために、すべてのプラットフォームで従わなければならない主なステップをリストしています。

- 依存関係をインストールする（git、subversion、C、C ++コンパイラ）。
- バージョン管理からBlenderのソースコードをチェックアウトします。
- CMakeを使用して、ソースコードを実行可能ファイルにコンパイルします。
- オプション：

- エディタまたはIDEをインストールして、ソースコードをナビゲートして編集します。
- CMakeのを設定し、デバッグオプションを有効にするか、時間の機能をコンパイル切り替えます。
- 正確な手順はオペレーティングシステムによって異なります（上記のリンクを参照）。

# ビルドシステム
- BlenderはCMakeビルドシステムを使用します。それに加えて、インストールするコンパイラも選択し、32ビットまたは64ビットのBlenderをビルドするかどうかを選択する必要があります。

# CMakeの概要
- カスタマイズ
- cmakeのGUIを使用して、ccmakeや編集を./../build_<platform>/CMakeCache.txt
- Using cmake GUI, ccmake or editing ./../build_<platform>/CMakeCache.txt
- 例えば、ソースディレクトリ以外のディレクトリでのビルドファイルを生成するようにしてください./../build/
- Be sure to generate the build files in a directory other than the source directory, e.g. ./../build/

- ドキュメンテーション
- オンライン（このWikiで  https://wiki.blender.org/index.php/Dev:Doc/Building_Blender ）
- Building Blender
- FreeBSD

- Linux

- Mac

- Windows

- CMakeMSVC  https://wiki.blender.org/index.php/Dev:Doc/Building_Blender/Windows/CMakeMSVC

- MinGW   https://wiki.blender.org/index.php/Dev:Doc/Building_Blender/Windows/MinGW

- MinGW  CMake   https://wiki.blender.org/index.php/Dev:Doc/Building_Blender/Windows/MinGW/CMake

- Troubleshooting        https://wiki.blender.org/index.php/Dev:Doc/Building_Blender/Windows/Troubleshooting

- Troubleshooting CMake    https://wiki.blender.org/index.php/Dev:Doc/Building_Blender/Windows/msvc/CMake

- ビルドファイル
- CMakeLists.txtソースツリー全体。
./build_files/cmake/*
出力
./../build_<platform>/bin、または指定された発電用のプロジェクトディレクトリ（CMakeの-G <ジェネレータ>）。
ビルドの失敗の解決
ほとんどのビルドの問題は、Blenderのソースコードでは実際には間違いではありませんが、その可能性を完全に排除することはできません。以下はビルドに失敗した一般的な原因です：

 # 不足している依存関係
- WindowsまたはOS Xでは依存関係を提供するので、さらにトラブルシューティングする前に、ローカルの "lib /"チェックアウトを更新してください。

- 依存関係がないと、2種類のコンパイラエラーが発生します。このようなファイルエラーは、ヘッダー（.h）ファイルが存在しないことを意味し、リンク時の未解決のシンボルエラーはライブラリが存在しないことを意味します。これは、通常、ビルドシステムで依存関係へのパスが正しく設定されていないか、依存関係がインストールされていないか、または依存関係の間違ったバージョンが使用されたためです。

- どの依存関係が壊れているかを知ることは、時には困難な場合があります。欠落しているファイル名や記号をオンラインで検索すると、しばしば簡単な答えが得られます。パッケージマネージャを持つシステムでは、ヘッダーとライブラリは通常foo-devやfoo-develと呼ばれる別個の開発パッケージに入っています。

 # ローカル変更
- 開発者がコードを変更したことを忘れることで、ビルドに失敗したBlenderの苦情のいくつかは、適用されたパッチまたは開発時に編集されたものです。

- エラービルの調査に時間を費やす前に、チェックアウトにローカルな変更がないことを確認してください。次のコマンドを使用して、それらを隠しておき（必要に応じて後で復元することもできます）

- gitの隠し場所 ではなく
------------------------------------------
git stash
-----------------------------------------
# サポートされていない環境
- Blenderは移植性がありますが、あまり一般的でないオペレーティングシステム（例えばNetBSDのような）でコンパイルすると、コンパイルのために少し編集が必要になることがあります。同じことがコンパイラにも当てはまりますが、あまり一般的でないバージョンでは、アクティブな開発者が現在それらを使用していない場合には調整が必要な場合があります。

- あまり一般的でない開発環境をサポートする時間を費やしたいのでない限り、通常はご使用のプラットフォーム用のデフォルト/標準開発ツールを使用することをお勧めします。

# ビルドの問題を報告する
- 使用バグトラッカーや#blendercoders IRCチャネルをあなたの問題を報告します。IRCを使用する場合は、使用する外部の貼り付けツールを代わりにチャネルに直接以上の5行を貼り付けます。
- ALWAYSだけで非常に有用ではないエラーを含む1-2線で「これは失敗した」と言って、完全なエラーログが含まれています。
- Blenderのオペレーティングシステム、コンパイラのバージョン、gitのリビジョンを含めてください。
- プラットフォーム管理者

このセクションは、メンテナが必要とする詳細ですが、Blenderを構築する人にとってはすぐには役に立ちません。

# コンパイラのバージョン
- コンパイラ	公式リリースバージョン	最小サポートバージョン
- Linux / Clang：	-	3.5（???）
- Linux / GCC：	4.7	4.2
- Mac-OSX / Clang：	3.5（???）	3.5（???）
- Mac OSX / GCC：	-	4.2
- MS-Windows / MSVC：	2013年	2013年

# ライブラリのバージョン
Blenderは多くの異なるライブラリを使用しています。公式のサポートされているバージョン（公式のビルド環境で使用されているもの）をすべてのプラットフォーム間で同期させようとしましょう！

# 注：ライブラリの取得に関する詳細は、各プラットフォームのビルドのドキュメントに含まれています。

# ライブラリ	バージョン
- Python	3.5.2

- NumPY（オプション）	1.10.1

- Boostブースト（オプション）	1.60

- ILMBase / OpenEXR（オプション）	2.2.0

- OCIO（オプション）	1.0.9

- OIIO（オプション）	1.7.8

- LLVM（オプション）	3.4

- OSL（オプション）	1.7.5

- OSD（オプション）	3.1.1

- OpenVDB（オプション）	3.1.0

- OpenCOLLADA（オプション）	公式リリースはない、git rev：3335ac164e68b2512a40914b14c74db260e6ff7d

- FFMpeg（オプション）	3.2.1（注意：libavのフォークではなく、実際のlibffmpegですが、これもうまくいくはずです）

- Bullet Physics 弾丸物理（オプション）	2.83


- 
-
- 

-----------------ここまでURLの内容------  - https://wiki.blender.org/index.php/Dev:Doc/Building_Blender  URLの ----------------------

----------------------------------------------------------------------------------------------------------------

# BlenderFD-2.78a
This the the Blender 2.78a Source Code with the necessary Fluid Designer Changes

The process of building Fluid Designer is exactly the same as Building Blender. You can find the documentation here:
https://wiki.blender.org/index.php/Dev:Doc/Building_Blender
