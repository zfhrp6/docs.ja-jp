---
title: "Visual Studio Code の使用を開始する - C# のガイド"
description: "Visual Studio Code を使用した、C# で初めての .NET Core アプリケーションを作成してデバッグする方法について説明します。"
keywords: "C#、概要、取得、インストール、Visual Studio Code、クロス プラットフォーム"
author: kendrahavens
ms.author: mairaw
ms.date: 5/02/2017
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 76c23597-4cf9-467e-8a47-0c3703ce37e7
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 2e1e9ce39b2de05478a2bf010584e2e7fd8eb02f
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---

# <a name="get-started-with-visual-studio-code"></a>Visual Studio Code の使用を開始する

.NET core は、Windows、Linux および macOS で実行されるサーバー アプリケーションを作成するための、高速でモジュール型のプラットフォームを提供します。 Visual Studio Code を C# 拡張機能とともに使用して、C# IntelliSense の完全サポート (スマート コード補完) とデバッグによる強力な編集機能をご活用ください。

## <a name="prerequisites"></a>必須コンポーネント

1. [Visual Studio Code](https://code.visualstudio.com/) のインストール。
2. [.NET Core SDK](https://www.microsoft.com/net/download/core) のインストール。
3. Visual Studio Code Marketplace からの [C# 拡張機能](https://marketplace.visualstudio.com/items?itemName=ms-vscode.csharp)のインストール。

## <a name="hello-world"></a>Hello World

.NET Core でシンプルな "Hello World" プログラムを作成してみましょう。

1. プロジェクトを開く

    * Visual Studio Code を開きます。
    * 左側のメニューで [エクスプローラー] アイコンをクリックし、**[フォルダーを開く]** をクリックします。
    * C# プロジェクトを保存するフォルダーを選択し、**[フォルダーの選択]** をクリックします。 ここで、"Hello World" という名前のプロジェクトのフォルダーを作成します。 

  ![VSCodeOpenFolder](media/with-visual-studio-code/vscodeopenfolder.png)

    * あるいは、メイン メニューから **[ファイル]** > **[フォルダーを開く]** と選択してプロジェクト フォルダーを開くこともできます。

2. C# プロジェクトを初期化する
    * <kbd>CTRL</kbd>+<kbd>\`</kbd> (バッククォート) と入力して、Visual Studio Code から統合ターミナルを開きます。
    * ターミナル ウィンドウで、`dotnet new console` と入力します。
    * これで、フォルダーに `HelloWorld.csproj` という名前の C# プロジェクト ファイルとともに、単純な "Hello World" プログラムが既に書き込まれた `Program.cs` ファイルが作成されます。

  ![dotnet new コマンド](media/with-visual-studio-code/dotnetnew.png)

3. ビルド資産を解決する

    * 「`dotnet restore`」と入力します。 `dotnet restore` を実行すると、プロジェクトのビルドに必要な .NET Core パッケージにアクセスします。

  ![dotnet restore コマンド](media/with-visual-studio-code/dotnetrestore.png)

4. "Hello World" プログラムを実行する

    * 「`dotnet run`」と入力します。 

  ![dotnet run コマンド](media/with-visual-studio-code/dotnetrun.png)

[Windows](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core)、[macOS](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core-on-MacOS)、または [Linux](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-Csharp-dotnet-Core-Ubuntu) での詳細設定については、簡単なビデオ チュートリアルを見ることができます。

## <a name="debug"></a>デバッグ
1. *Program.cs* をクリックして開きます。 Visual Studio Code で初めて C# ファイルを開くと、[OmniSharp](http://www.omnisharp.net/) がエディタに読み込まれます。

  ![Program.cs ファイルを開く](media/with-visual-studio-code/opencs.png)

2. Visual Studio Code で、アプリのビルドとデバッグに必要なアセットの追加を求められます。 **[はい]** を選択します。 

  ![足りない資産の入力を求める](media/with-visual-studio-code/missing-assets.png)

3. デバッグ ビューを開くには、左側のメニューにある [デバッグ] アイコンをクリックします。

  ![[デバッグ] タブを開く](media/with-visual-studio-code/opendebug.png)

4. ウィンドウの上部で緑色の矢印を探します。 その横にあるドロップダウン リストで `.NET Core Launch (console)` が選択されていることを確認します。

  ![.NET Core を選択する](media/with-visual-studio-code/selectcore.png)

5. 9 行目の横にある**エディター余白** (エディター内の行番号の左側の領域) をクリックして、プロジェクトにブレークポイントを追加します。

  ![ブレークポイントの設定](media/with-visual-studio-code/setbreakpoint.png)

6. <kbd>F5 キー</kbd>または緑色の矢印を選択して、デバッグを開始します。 デバッガーは、前述の手順で設定したブレークポイントに達すると、プログラムの実行を停止します。
    * デバッグ中は左上のペインにローカル変数が表示され、デバッグ コンソールを使用できます。

  ![実行およびデバッグ](media/with-visual-studio-code/rundebug.png)

7. 上部にある緑色の矢印を選択してデバッグを継続するか、赤色の四角形を押して停止します。

> [!TIP] 
> Visual Studio Code で OmniSharp を使用した .NET Core のデバッグの詳細とトラブルシューティングのヒントについては、「[Instructions for setting up the .NET Core debugger](https://github.com/OmniSharp/omnisharp-vscode/blob/master/debugger.md)」 (.NET Core デバッガーの設定に関する指示) を参照してください。

## <a name="see-also"></a>関連項目
[Visual Studio Code の設定](https://code.visualstudio.com/docs/setup/setup-overview)   
[Visual Studio Code でのデバッグ](https://code.visualstudio.com/Docs/editor/debugging)

