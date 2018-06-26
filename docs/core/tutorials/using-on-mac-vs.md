---
title: Visual Studio for Mac を使用した macOS での .NET Core の概要
description: このトピックでは、Visual Studio for Mac と .NET Core を使用して、単純なコンソール アプリケーションをビルドする手順を示します。
author: guardrex
ms.author: mairaw
ms.date: 06/12/2017
ms.openlocfilehash: dd8262a7d2fa03ab06f9f85e91c298f52e3c0849
ms.sourcegitcommit: c217b067985905cb21eafc5dd9a83568d7ff4e45
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/22/2018
ms.locfileid: "36315148"
---
# <a name="getting-started-with-net-core-on-macos-using-visual-studio-for-mac"></a>Visual Studio for Mac を使用した macOS での .NET Core の概要

Visual Studio for Mac では、.NET Core アプリケーション開発用の機能をすべて備えた統合開発環境 (IDE) が提供されます。 このトピックでは、Visual Studio for Mac と .NET Core を使用して、単純なコンソール アプリケーションをビルドする手順を示します。

> [!NOTE]
> お客様のフィードバックは非常に貴重です。 次の 2 つの方法で Visual Studio for Mac の開発チームにフィードバックを送信することができます。
> * Visual Studio for Mac で、メニューから **[ヘルプ]** > **[問題の報告]** の順に選択するか、ようこそ画面から **[問題の報告]** を選択して、バグ報告を提出するためのウィンドウを開きます。 お客様のフィードバックは、[開発者コミュニティ](https://developercommunity.visualstudio.com/spaces/8/index.html) ポータルで追跡することができます。
> * 提案するには、メニューから **[ヘルプ]** > **[提案の送信]** の順に選択するか、ようこそ画面から **[提案の送信]** を選択し、[Visual Studio for Mac の UserVoice Web ページ](https://visualstudio.uservoice.com/forums/563332-visual-studio-for-mac)に移動します。

## <a name="prerequisites"></a>必須コンポーネント

「[Mac における .NET Core の前提条件](../../core/macos-prerequisites.md)」のトピックをご覧ください。

## <a name="getting-started"></a>作業の開始

必須コンポーネントと Visual Studio for Mac を既にインストールしている場合は、このセクションをスキップして、「[プロジェクトの作成](#creating-a-project)」に進みます。 以下の手順に従って、必須コンポーネントと Visual Studio for Mac をインストールします。

[Visual Studio for Mac インストーラー](https://visualstudio.microsoft.com/vs/visual-studio-mac/)をダウンロードします。 インストーラーを実行します。 使用許諾契約書を読み、同意します。 インストール中に、Xamarin (クロスプラットフォーム モバイル アプリ開発テクノロジ) をインストールすることができます。 .NET Core の開発の場合、Xamarin とその関連コンポーネントのインストールは省略できます。 Visual Studio for Mac のインストール プロセスのチュートリアルについては、「[Introducing Visual Studio for Mac](https://developer.xamarin.com/guides/cross-platform/visual-studio-mac/)」 (Visual Studio for Mac の概要) を参照してください。 インストールが完了したら、Visual Studio for Mac IDE を起動します。

## <a name="creating-a-project"></a>プロジェクトの作成

1. ようこそ画面で **[新しいプロジェクト]** を選択します。

   ![Visual Studio for Mac のようこそ画面の [新しいプロジェクト] ボタン](./media/using-on-mac-vs/vsmac1.png)

1. **[新しいプロジェクト]** ダイアログで、**[.NET Core]** ノードの下にある **[アプリ]** を選択します。 **[コンソール アプリケーション]** テンプレートを選択してから **[次へ]** を選択します。

   ![新しいプロジェクト テンプレートのリスト](./media/using-on-mac-vs/vsmac2.png)

1. **[プロジェクト名]** には「HelloWorld」と入力します。 **[作成]** を選択します。

   ![[Configure your new Console Application (新しいコンソール アプリケーションの構成)] ダイアログ](./media/using-on-mac-vs/vsmac3.png)

1. プロジェクトの依存関係が復元されるまで待ちます。 プロジェクトには、`Main` メソッドを持つ `Program` クラスを含む *Program.cs* という C# ファイルが 1 つあります。 `Console.WriteLine` ステートメントは、アプリの実行時に コンソールに "Hello World!" と出力します。

   ![Program.cs ファイルが開かれた状態のメイン ウィンドウ](./media/using-on-mac-vs/vsmac4.png)

## <a name="run-the-application"></a>アプリケーションの実行

アプリは、<kbd>F5</kbd> キーを使用する場合はデバッグ モードで、<kbd>Ctrl</kbd> + <kbd>F5</kbd> キーを使用する場合はリリース モードで実行します。

![[アプリケーション出力] ウィンドウに Hello World! が表示された状態](./media/using-on-mac-vs/vsmac5.png)

## <a name="next-step"></a>次のステップ

「[Visual Studio for Mac を使用した macOS での完全な .NET Core ソリューションの構築](using-on-mac-vs-full-solution.md)」トピックでは、再利用可能なライブラリと単体テストを含む完全な .NET Core ソリューションを構築する方法を示します。
