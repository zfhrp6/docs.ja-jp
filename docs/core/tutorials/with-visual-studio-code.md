---
title: "C# および Visual Studio Code の使用を開始する - C# ガイド"
description: "Visual Studio Code を使用した、C# で初めての .NET Core アプリケーションを作成してデバッグする方法について説明します。"
keywords: "C#、概要、取得、インストール、Visual Studio Code、クロス プラットフォーム"
author: kendrahavens
ms.author: mairaw
ms.date: 09/27/2017
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 76c23597-4cf9-467e-8a47-0c3703ce37e7
ms.workload: dotnetcore
ms.openlocfilehash: 95052da1688ec1026f11ff679dda6aad50a340fa
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/23/2017
---
# <a name="get-started-with-c-and-visual-studio-code"></a>C# および Visual Studio Code の使用を開始する

.NET Core は、Windows、Linux および macOS で実行されるアプリケーションを作成するための、高速でモジュール型のプラットフォームを提供します。 Visual Studio Code を C# 拡張機能とともに使用して、C# IntelliSense の完全サポート (スマート コード補完) とデバッグによる強力な編集機能をご活用ください。

## <a name="prerequisites"></a>必須コンポーネント

1. [Visual Studio Code](https://code.visualstudio.com/) のインストール。
2. [.NET Core SDK](https://www.microsoft.com/net/download/core) のインストール。
3. Visual Studio Code Marketplace からの [C# 拡張機能](https://marketplace.visualstudio.com/items?itemName=ms-vscode.csharp)のインストール。

## <a name="hello-world"></a>Hello World

.NET Core でシンプルな "Hello World" プログラムを作成してみましょう。

1. プロジェクトを開く

    * Visual Studio Code を開きます。
    * 左側のメニューで [エクスプローラー] アイコンをクリックし、**[フォルダーを開く]** をクリックします。
    * メイン メニューから **[ファイル]**、**[フォルダーを開く]** の順に選択し、C# プロジェクトを保存するフォルダーを開き、**[フォルダーの選択]** をクリックします。 ここで、*Hello World* という名前のプロジェクトのフォルダーを作成します。

      ![VSCodeOpenFolder](media/with-visual-studio-code/vscodeopenfolder.png)

2. C# プロジェクトを初期化する
    * Visual Studio Code から統合ターミナルを開きます。メイン メニューで **[表示]**、**[統合端末]** の順に選択してください。
    * ターミナル ウィンドウで、`dotnet new console` と入力します。
    * このコマンドで、フォルダーに `HelloWorld.csproj` という名前の C# プロジェクト ファイルとともに、単純な "Hello World" プログラムが既に書き込まれた `Program.cs` ファイルが作成されます。

      ![dotnet new コマンド](media/with-visual-studio-code/dotnetnew.png)

3. ビルド資産を解決する

    * **.NET Core 1.x** の場合、「`dotnet restore`」と入力します。 `dotnet restore` を実行すると、プロジェクトのビルドに必要な .NET Core パッケージにアクセスします。

      ![dotnet restore コマンド](media/with-visual-studio-code/dotnetrestore.png)

      [!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

4. "Hello World" プログラムを実行する

    * 「`dotnet run`」と入力します。 

      ![dotnet run コマンド](media/with-visual-studio-code/dotnetrun.png)

[Windows](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core)、[macOS](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core-on-MacOS)、または [Linux](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-Csharp-dotnet-Core-Ubuntu) での詳細設定については、簡単なビデオ チュートリアルを見ることができます。

## <a name="debug"></a>デバッグ

1. *Program.cs* をクリックして開きます。 Visual Studio Code で初めて C# ファイルを開くと、[OmniSharp](http://www.omnisharp.net/) がエディターに読み込まれます。

    ![Program.cs ファイルを開く](media/with-visual-studio-code/opencs.png)

2. Visual Studio Code で、アプリのビルドとデバッグに必要なアセットの追加を求められます。 **[はい]** を選択します。 

    ![足りない資産の入力を求める](media/with-visual-studio-code/missing-assets.png)

3. デバッグ ビューを開くには、左側のメニューにある [デバッグ] アイコンをクリックします。

    ![[デバッグ] タブを開く](media/with-visual-studio-code/opendebug.png)

4. ウィンドウの上部で緑色の矢印を探します。 その横にあるドロップダウン リストで `.NET Core Launch (console)` が選択されていることを確認します。

    ![.NET Core を選択する](media/with-visual-studio-code/selectcore.png)

5. 9 行目の横にある**エディター余白** (エディター内の行番号の左側の領域) をクリックして、プロジェクトにブレークポイントを追加します。

    ![ブレークポイントの設定](media/with-visual-studio-code/setbreakpoint.png)

6. デバッグを開始するには、<kbd>F5 キー</kbd>または緑色の矢印を選択します。 デバッガーは、前述の手順で設定したブレークポイントに達すると、プログラムの実行を停止します。
    * デバッグ中は左上のペインにローカル変数が表示され、デバッグ コンソールを使用できます。

    ![実行およびデバッグ](media/with-visual-studio-code/rundebug.png)

7. 上部にある緑色の矢印を選択してデバッグを継続するか、上部にある赤色の四角形を選択して停止します。

> [!TIP] 
> Visual Studio Code で OmniSharp を使用した .NET Core のデバッグの詳細とトラブルシューティングのヒントについては、「[Instructions for setting up the .NET Core debugger](https://github.com/OmniSharp/omnisharp-vscode/blob/master/debugger.md)」 (.NET Core デバッガーの設定に関する指示) を参照してください。

## <a name="see-also"></a>関連項目
[Visual Studio Code の設定](https://code.visualstudio.com/docs/setup/setup-overview)   
[Visual Studio Code でのデバッグ](https://code.visualstudio.com/Docs/editor/debugging)
