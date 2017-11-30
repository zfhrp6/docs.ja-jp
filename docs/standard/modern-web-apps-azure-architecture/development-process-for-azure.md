---
title: "Azure の開発プロセス"
description: "ASP.NET Core と Azure での最新の Web アプリケーションを設計 |Azure の開発プロセス"
author: ardalis
ms.author: wiwagn
ms.date: 10/08/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.openlocfilehash: e676c1225f7d11381808040cf101e897e0726ad4
ms.sourcegitcommit: bbde43da655ae7bea1977f7af7345eb87bd7fd5f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/21/2017
---
# <a name="development-process-for-azure"></a>Azure の開発プロセス

> _「、クラウドに個人ユーザーおよび小規模企業、指をスナップできエンタープライズ クラスのサービスをすばやくセットアップできます。」_  
> _-者を務める Roy ので、セントラル_

 ## <a name="vision"></a>ビジョン

> *ASP .NET Core アプリケーションが適切に設計された必要な場合、Visual Studio または dotnet CLI と Visual Studio Code または任意のエディターを使用する方法を開発します。*

## <a name="development-environment-for-aspnet-core-apps"></a>ASP.NET Core アプリケーションの開発環境

### <a name="development-tools-choices-ide-or-editor"></a>開発ツールの選択: IDE やエディター

かどうか完全かつ強力な IDE または軽量とアジャイル エディターについて、必要に応じて、Microsoft ASP.NET Core アプリケーションの開発時に対応します。

**Visual Studio 2017 です。** 使用する場合*Visual Studio 2017* ASP.NET Core アプリケーションを構築できますがある限り、 *.NET Core クロスプラット フォーム開発*ワークロードがインストールされています。 図 10-1 では、Visual Studio 2017 の [設定] ダイアログ ボックスで、必要なワークロードを示しています。

![](./media/image10-1.png)

**図 10-1。** Visual Studio 2017 で .NET Core ワークロードをインストールしています。

[Visual Studio 2017 をダウンロードする](https://www.visualstudio.com/downloads/)

**Visual Studio Code と dotnet CLI** (Mac、Linux および Windows 用のクロスプラット フォーム ツール)。 任意の開発言語をサポートする、軽量でクロスプラット フォーム エディターを使用する場合は、Microsoft Visual Studio Code と dotnet CLI を使用できます。 これらの製品では、開発者のワークフローを利用すれば、簡単かつ堅牢なエクスペリエンスを提供します。 さらに、Visual Studio のコードは C の拡張機能をサポートしている\#および web 開発、intellisense と、エディター内のショートカット タスクを提供します。

[.NET Core SDK をダウンロードします。](https://www.microsoft.com/net/download/core)

[Visual Studio のコードをダウンロードします。](https://code.visualstudio.com/download)



## <a name="development-workflow-for-azure-hosted-aspnet-core-apps"></a>Azure でホストされる ASP.NET Core アプリケーションの開発のワークフロー

アプリケーションの開発ライフ サイクルは、アプリケーションが希望する言語を使用し、ローカルでテストをコーディング、各開発者のコンピューターから開始します。 開発者は、優先されるソース管理システムを選択することがあります継続的な統合 (CI) や継続的な配信/デプロイ (CD) ビルド サーバーを使用して構成できますや、Azure 組み込みの機能に基づいたしてください。

Visual Studio Team Services や、組織を使用する、CI/CD を使用して ASP.NET Core アプリケーションの開発作業を開始する Team Foundation Server (TFS) を所有します。

### <a name="initial-setup"></a>初期のセットアップ

アプリのリリース パイプラインを作成するには、ソース管理に、アプリケーション コードがある必要があります。 ローカル リポジトリを設定し、チーム プロジェクト内のリモート リポジトリに接続します。 これらの手順に従います。

-   [Git と Visual Studio でコードを共有](https://www.visualstudio.com/docs/git/share-your-code-in-git-vs)または

-   [TFVC および Visual Studio とコードを共有します。](https://www.visualstudio.com/docs/tfvc/share-your-code-in-tfvc-vs)

アプリケーションを展開する場合、Azure App Service を作成します。 Azure ポータルの アプリ サービスのブレードに移動して、Web アプリを作成します。 追加 を押しながらクリック、Web アプリケーション テンプレートを選択を作成する、名前とその他の詳細を提供します。 Web アプリは {name} からアクセス可能になります。 azurewebsites.net です。

![AzureWebApp](./media/image10-2.png)

**図 10-2 です。** Azure ポータルで新しい Azure App Service Web アプリを作成しています。

CI ビルド プロセスは新しいコードは、プロジェクトのソース管理リポジトリにコミットされるたびに自動ビルドを実行します。 これにより、コードはビルドをすぐにフィードバック (および、理想的には、自動のテストに合格した) し、配置可能性があることができます。 この CI ビルド web が生成されますパッケージ成果物を展開し、CD プロセスによって消費を発行します。

[CI ビルド プロセスを定義します。](https://www.visualstudio.com/docs/build/apps/aspnet/aspnetcore-to-azure#ci)

新しいコードをチームの誰かがコミットされるたびに、システムは、ビルドをキューは、継続的な統合を有効にすることを確認します。 ビルドをテストし、生成されているなど、web を確認、成果物のいずれかとしてパッケージを展開します。

ビルドが成功した場合、CD プロセスは、Azure web アプリに対する CI ビルドの結果を展開します。 これを構成する、作成し、構成、*リリース*、Azure App Service に配置します。

[CD リリース プロセスを定義します。](https://www.visualstudio.com/docs/build/apps/aspnet/aspnetcore-to-azure#cd)

CI/CD パイプラインを構成した後は、web アプリの更新を行うし、ソース コントロールに展開されていることにコミットします。

### <a name="workflow-for-developing-azure-hosted-aspnet-core-applications"></a>Azure でホストされる ASP.NET Core アプリケーションの開発のワークフロー

Azure アカウントと、CI/CD プロセスを構成した後、Azure でホストされる ASP.NET Core アプリケーションを開発するは簡単です。 図 10-3 に示すように、Web アプリと Azure App Service でホストされている、ASP.NET Core アプリケーションのビルド時に実行する通常の基本的な手順を次に示します。

![EndToEndDevDeployWorkflow](./media/image10-3.png)

**図 10-3。** ASP.NET Core アプリケーションの構築し、Azure でホストするそれらのステップ バイ ステップのワークフロー

#### <a name="step-1-local-dev-environment-inner-loop"></a>手順 1. ローカル開発環境の内側のループ

Azure への展開用 ASP.NET Core アプリケーションの開発は、それ以外の場合、アプリケーションの開発と同じです。 ローカル開発環境に満足する、Visual Studio 2017 または dotnet CLI と Visual Studio Code または好みのエディターであるかどうかを使用します。 コードを記述、実行し変更内容をデバッグ、自動のテストを実行でき、変更内容を共有されているソース管理リポジトリにプッシュする準備ができたらまで、ローカルのコミットをソース管理に加えることできます。

#### <a name="step-2-application-code-repository"></a>手順 2. アプリケーション コード リポジトリ

チームでコードを共有する準備ができたら、されるたびにする必要があります、変更内容をローカル ソース リポジトリからをリポジトリにプッシュ チームの共有ソース。 場合は、カスタムの分岐で作業してきた、この手順通常では、共有の分岐にコードをマージする (おそらくの[プル要求](https://www.visualstudio.com/docs/git/pull-requests))。

#### <a name="step-3-build-server-continuous-integration-build-test-package"></a>手順 3. ビルド サーバー: 継続的な統合。 ビルド、テストでは、パッケージ

共有アプリケーションのコード リポジトリに新しいコミットが行われたときに、ビルド サーバー上に新しいビルドがトリガーされます。 CI のプロセスの一環として、このビルドが完全にアプリケーションをコンパイルし、どおりすべてが動作を確認する自動テストを実行する必要があります。 CI のプロセスの最終結果には、パッケージのバージョンの web アプリ、展開用に準備をする必要があります。

#### <a name="step-4-build-server-continuous-delivery"></a>手順 4. 継続的配信のビルド サーバー:

1 回、ビルドが成功したように、CD 処理を引き継ぎますビルド成果物を生成します。 Web は、このパッケージを展開します。 Azure App Service、既存のサービスを新しく作成されたものに置き換えるには、ビルド サーバーはこのパッケージを展開します。 通常この手順は、ステージング環境を対象が、一部のアプリケーションが直接 CD プロセスには、実稼働環境に展開します。

#### <a name="step-5-azure-app-service-web-app"></a>手順 5. Azure App Service。 Web アプリです。

展開した後は、Azure App Service Web アプリのコンテキスト内で ASP.NET Core アプリケーションが実行されます。 この Web アプリは、監視することができ、さらに、Azure ポータルを使用するように構成します。

#### <a name="step-6-production-monitoring-and-diagnostics"></a>手順 6. 運用環境の監視と診断

Web アプリの実行中には、アプリケーションのヘルスを監視および診断とユーザー動作のデータを収集できます。 Application Insights は、Visual Studio に含まれ、ASP.NET アプリ用の自動実装を提供します。 使用状況、例外、要求、パフォーマンス、およびログに関する情報を提供します。

## <a name="references"></a>参照

**ビルドし、ASP.NET Core アプリを Azure に配置**  
<https://www.visualstudio.com/docs/build/apps/aspnet/aspnetcore-to-azure>


>[!div class="step-by-step"]
[前](test-asp-net-core-mvc-apps.md) [次へ] (azure-hosting-recommendations-for-asp-net-web-apps.md)
