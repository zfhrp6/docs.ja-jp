---
title: "Visual Studio 2017 を使用した Hello World アプリケーションの発行"
description: "Visual Studio 2017 を使用した Hello World アプリケーションの発行"
keywords: ".NET、.NET Core、.NET Core コンソール アプリケーション、発行 (.NET Core)、展開 (.NET Core)"
author: BillWagner
ms.author: wiwagn
ms.date: 10/24/2016
ms.topic: article
ms.prod: .net-core
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: a19545d3-24af-4a32-9778-cfb5ae938287
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: f4a30d19e111d395088e38c4543c9dacee6105fd
ms.lasthandoff: 03/13/2017

---

# <a name="publishing-your-hello-world-application-with-visual-studio-2017"></a>Visual Studio 2017 を使用した Hello World アプリケーションの発行

「[Visual Studio 2017 での .NET Core を使用した C# Hello World アプリケーションの構築](with-visual-studio-2017.md)」では、Hello World コンソール アプリケーションを作成し、「[Debugging your C# Hello World application with Visual Studio 2017](debugging-with-visual-studio-2017.md)」 (Visual Studio 2017 での C# Hello World アプリケーションのデバッグ) では、Visual Studio デバッガーを使用してそれをテストしました。 正しく動作することが確認できたので、他のユーザーが使用できるように発行することができます。 発行では、アプリケーションを実行するために必要なファイルのセットが作成されます。これらは、対象コンピューターにコピーすることで展開できます。

アプリケーションを発行および実行するには 

1. Visual Studio がアプリケーションのリリース バージョンをビルドしているか確認します。 必要に応じて、下図のようにツールバーのビルド構成の設定を**デバッグ**から**リリース**に変更します。

   ![イメージ](media/release.jpg)

1. コンソール ウィンドウを開きます。 たとえば、Windows タスクバーの **[何でも聞いてください]** テキスト ボックスに「`Command Prompt`」と入力し、**[コマンド プロンプト]** デスクトップ アプリを選択してコンソール ウィンドウを開きます。

1. HelloWorld プロジェクト (HelloWorld ソリューションではなく) を右クリックし、メニューから **[発行]** を選択します。 Visual Studio のメイン メニューの **[ビルド]** から **[HelloWorld を発行]** を選択することもできます。

1. 下図に示す **[発行]** ダイアログ ボックスが表示されたら、**[新しいプロファイルの作成]** を選択して新しい発行プロファイルを作成します。

1. 下図に示す **[Pick a publishing target]** (発行ターゲットを選択) ダイアログで、**[OK]** をクリックし、ローカル ファイル システムにアプリケーションを発行します。 アプリケーションのプロジェクト ディレクトリの bin\release\PublishOutput サブディレクトリに発行されます。

1. これで発行プロファイルが作成されたので、下図に示すように、**[発行]** ダイアログ ボックスで **[発行]** ボタンをクリックします。

   ![イメージ](media/publish-2.jpg)

1. 次の図で示すように、発行された出力には以下の 3 つのファイルが含まれます。これらがアプリケーションを構成するものであり、ターゲット システムにコピーすることで展開ができます。

      - HelloWorld.dll
   
      - HelloWorld.deps.json

      - HelloWorld.runtimeconfig.json

   4 番目のファイル HelloWorld.pdb には、デバッグ シンボルが含まれています。 このファイルはアプリケーションと一緒に配布する必要はありませんが、発行されるバージョンのアプリケーションをデバッグする必要がある場合に保存しておく必要があります。

   ![イメージ](media/pub-files.jpg)

発行プロセスではフレームワークに依存する展開を行います。発行されるアプリケーションは、.NET Core がシステムにインストールされていれば、.NET Core がサポートする任意のプラットフォームで実行できます。 ユーザーはコンソール ウィンドウから `dotnet.exe HelloWorld.dll` コマンドを発行することによって、アプリケーションを実行できます。

.NET Core アプリケーションの発行と展開の詳細については、「[.NET Core アプリケーション展開](../../core/deploying/index.md)」を参照してください。
