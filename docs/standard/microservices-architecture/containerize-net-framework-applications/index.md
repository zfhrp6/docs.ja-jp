---
title: レガシ モノリシック .NET Framework アプリケーションを Windows コンテナーに移行する
description: '.NET マイクロサービス: コンテナー化された .NET アプリケーションのアーキテクチャ | レガシ モノリシック .NET Framework アプリケーションを Windows コンテナーに移行する'
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.openlocfilehash: 01b84d29a559bde02ebd30535488c272d5208167
ms.sourcegitcommit: 979597cd8055534b63d2c6ee8322938a27d0c87b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/29/2018
ms.locfileid: "37106516"
---
# <a name="migrating-legacy-monolithic-net-framework-applications-to-windows-containers"></a>レガシ モノリシック .NET Framework アプリケーションを Windows コンテナーに移行する

*Windows コンテナーは、開発環境とテスト環境を強化し、Web* *Forms などのレガシ .NET Framework テクノロジをベースにするアプリケーションを展開する方法として使用できます。この方法でレガシ アプリケーションのコンテナーを使用することを、"リフトアンドシフト" シナリオと呼びます。*

このガイドの前のセクションでは、小規模のフォーカスされているサービスを実行するごとに、ビジネス アプリケーションがさまざまなコンテナーに配布される、マイクロサービス アーキテクチャを支持していました。 このゴールには、多くの利点があります。 新しい開発では、この手法を強くお勧めします。 また、エンタープライズに必要なアプリケーションは、アーキテクチャと実装の見直しにかかるコストの正当性を保証できるだけの利益を得ることもできます。

ただし、すべてのアプリケーションが、そのコストの正当性を証明できるだけの利益を得るわけではありません。 これは、これらのアプリケーションがコンテナーのシナリオで使用できないということではありません。

このセクションでは、図 7-1 に示すように、eShopOnContainers のアプリケーションの詳細を確認します。 このアプリケーションは、製品カタログを表示および編集するために、eShopOnContainers エンタープライズ チームのメンバーによって使用されます。

![](./media/image1.png)

**図 7-1**。 Windows コンテナー上の ASP.NET Web フォーム アプリケーション (レガシ テクノロジ)

これは、カタログ エントリを参照および変更するために使用する、Web フォーム アプリケーションです。 Web フォームの依存関係は、このアプリケーションが Web フォームではなく、ASP.NET Core MVC を使用して書き換えない限り、.NET Core 上で実行されないことを意味します。 変更を行くことなく、コンテナーのアプリケーションのように、アプリケーションを実行できることがわかります。 また、一部の機能が個別のマイクロサービスに移動されているハイブリッド モードで機能するように、最小限の変更を加える方法についても確認できますが、ほとんどの機能はモノリシック アプリケーション内に保持されます。

## <a name="benefits-of-containerizing-a-monolithic-application"></a>コンテナー化されたモノリシック アプリケーションの利点

Catalog.WebForms アプリケーションは、eShopOnContainers GitHub リポジトリ (<https://github.com/dotnet/eShopOnContainers>) で入手できます。 このアプリケーションは、可用性の高いデータ ストアにアクセスする、スタンドアロンの Web アプリケーションです。 そうであっても、コンテナー内でアプリケーションを実行する利点があります。 アプリケーションのイメージを作成します。 この時点から、すべての展開は同じ環境で実行されます。 すべてのコンテナーは、同じ OS バージョンを使用し、同じバージョンの依存関係がインストールされており、同じフレームワークを使用し、同じプロセスを使用してビルドされます。 図 7-2 では、Visual Studio 2017 に読み込まれたアプリケーションを確認できます。

![](./media/image2.png)

**図 7-2**。 Visual Studio 2017 のカタログ管理の Web フォーム アプリケーション

さらに、すべての開発者が、この一貫した環境でアプリケーションを実行できます。 特定のバージョンでのみ表れる問題は、ステージング環境や運用環境に提示されるのではなく、開発者にすぐに表示されます。 開発チーム間での開発環境の違いは、アプリケーションをコンテナーで実行すると、さほど問題ではありません。

最後に、コンテナー化されたアプリケーションは、時間をかけてスケールアウトできます。 コンテナー化されたアプリを使って、VM で多くのコンテナーまたは物理マシンで多くのコンテナーを有効にする方法について学習しました。 この操作を行うと、平均密度が高くなり、必要なリソースが少なくなります。

これらすべての理由から、"リフトアンドシフト" 操作を使用して、Docker コンテナーでレガシ モノリシック アプリを実行することを検討してください。 "リフトアンドシフト" という語句は、タスクのスコープについて示しています。物理マシンまたは仮想マシンからアプリケーション全体を*リフト*して、コンテナーに*シフト*します。 理想的な状況では、コンテナーで実行するために、アプリケーション コードに変更を加える必要はありません。

## <a name="possible-migration-paths"></a>使用可能な移行パス

モノリシック アプリケーションとして、Catalog.Webforms アプリケーションは、データ アクセス ライブラリなど、すべてのコードを含む 1 つの Web アプリケーションです。 そのデータベースは、個別の可用性の高いマシンで実行されています。 この構成は、モック カタログ サービスを使用して、サンプル コードでシミュレートされます。純粋なリフトアンドシフトするシナリオをシミュレートする仮のデータに対して、Catalog.WebForms アプリケーションを実行できます。 これにより、コードに変更を加えることなく、コンテナーで実行するために、既存のアセットを移動する最も簡単な移行パスが示されます。 このパスは、完全なアプリケーション、およびマイクロサービスに移動する機能と最小限の相互作用があるアプリケーションに適しています。

ただし、eShopOnContainers Web サイトは、既にさまざまなシナリオのマイクロサービスを使用して、データ ストレージにアクセスしています。 カタログ データ ストレージに直接アクセスするのではなく、カタログ マイクロサービスを活用するために、いくつかの小さな追加の変更がカタログ エディターに加えられる可能性があります。

これらの変更は、独自のアプリケーションの Continuum をデモンストレーションします。 既存のアプリケーションがいくつかの新しいマイクロサービスにアクセスできるように小さな変更を加えるため、新しいマイクロサービス ベースのアーキテクチャに完全に参加するためにアプリケーションを完全に書き換えるために、コンテナーに変更を加えることなく、既存のアプリケーションを移動することで、すべての操作を実行できます。 この適切なパスは、移行のコストと移行からの利点の両方に依存します。

## <a name="application-tour"></a>アプリケーション ツアー

Catalog.WebForms ソリューションを読み込み、スタンドアロン アプリケーションとしてアプリケーションを実行することができます。 この構成では、永続ストレージ データベースの代わりに、アプリケーションはデータを返すために仮のサービスを使用します。 アプリケーションでは、制御の反転 (IOC) コンテナーとして Autofac (<https://autofac.org/>) を使用します。 依存関係の挿入 (DI) を使用して、仮のデータやライブ カタログ データ サービスを使用するように、アプリケーションを構成できます。 (DI の詳細については、この後ですぐに説明します)。スタートアップ コードは、web.config ファイルから useFake 設定を読み込んで、仮のデータ サービスまたはライブ カタログ サービスのいずれかを挿入するように、Autofac コンテナーを構成します。 web.config ファイルの useFake を false に設定してアプリケーションを実行した場合、カタログ データを示している Web フォーム アプリケーションが表示されます。

このアプリケーションで使用される技術のほとんどを、Web フォームを使用しているすべてのユーザーがよく理解している必要があります。 ただし、カタログ マイクロサービスでは、慣れていない可能性がある 2 つの技術を導入しています。それは、前述の依存関係の挿入 (DI) で、Web フォームで保存される非同期データを使って動作します。

DI は、必要なすべてのリソースを割り当てるクラスを作成する、一般的なオブジェクト指向の戦略を逆転させたものです。 代わりに、クラスがサービス コンテナーに依存関係を要求します。 DI の利点は、テスト環境やその他の環境をサポートするために、外部サービスを仮 (モック) に置き換えることができることです。

DI コンテナーでは、web.config appSettings 構成を使用して、仮のカタログ データを使用するか、実行中のサービスからのライブ データを使用するかをコントロールします。 アプリケーションは、コンテナーを構築する HttpModule オブジェクトを登録し、依存関係を挿入するために、事前に要求されたハンドラーを登録します。 次の例のように、コードを Modules/AutoFacHttpModule.cs ファイルで確認することができます。

```cs
private static IContainer CreateContainer()
{
  // Configure AutoFac:
  // Register Containers:

  var settings = WebConfigurationManager.AppSettings;
  var useFake = settings["usefake"];
  bool fake = useFake == "true";
  var builder = new ContainerBuilder();

  if (fake)
  {
    builder.RegisterType<CatalogMockService>()
    .As<ICatalogService>();
  }
  else
  {
    builder.RegisterType<CatalogService>()
    .As<ICatalogService>();
    builder.RegisterType<RequestProvider>()
    .As<IRequestProvider>();
  }

  var container = builder.Build();
  return container;
}

private void InjectDependencies()
{
  if (HttpContext.Current.CurrentHandler is Page page)
  {
    // Get the code-behind class that we may have written
    var pageType = page.GetType().BaseType;

    // Determine if there is a constructor to inject, and grab it
    var ctor = (from c in pageType.GetConstructors()
                where c.GetParameters().Length > 0
                select c).FirstOrDefault();

    if (ctor != null)
    {
      // Resolve the parameters for the constructor
      var args = (from parm in ctor.GetParameters()
                  select Container.Resolve(parm.ParameterType))
                  .ToArray();

      // Execute the constructor method with the arguments resolved
      ctor.Invoke(page, args);
    }

    // Use the Autofac method to inject any
    // properties that can be filled by Autofac
    Container.InjectProperties(page);
  }
}
```

アプリケーションのページ (Default.aspx.cs と EditPage.aspx.cs) は、これらの依存関係を取得するコンストラクターを定義します。 既定のコンストラクターが引き続き存在し、アクセスできることに注意してください。 インフラストラクチャには、次のコードが必要です。

```cs
protected _Default() { }

public _Default(ICatalogService catalog) => this.catalog = catalog;
```

カタログ API はすべて、非同期メソッドです。 Web フォームでは、すべてのデータ コントロールに対してこれらをサポートするようになりました。 Catalog.WebForms アプリケーションでは、リストと編集ページにモデル バインドを使用します。これは、タスクを返す非同期操作を指定する、SelectMethod、UpdateMethod、InsertMethod、DeleteMethod プロパティを定義するページをコントロールします。 Web フォーム コントロールは、メソッドが非同期のコントロールにバインドされるタイミングを理解します。 非同期の選択メソッドを使用するときに直面する唯一の制限は、ページングをサポートできないことです。 ページング署名には out パラメーターが必要で、非同期メソッドが out パラメーターを持つことはできません。 この同じ技術が、カタログ サービスからのデータを必要とするその他のページで使用されます。

カタログ Web フォーム アプリケーションの既定の構成は、catalog.api サービスのモック実装を使用します。 このモックは、開発環境の catalog.api サービスの依存関係を削除して、一部のタスクを簡略化する、データがハードコーディングされたデータセットを使用します。

## <a name="lifting-and-shifting"></a>リフトアンドシフト

Visual Studio では、アプリケーションをコンテナー化するために最適なサポートを提供します。 プロジェクト ノードを右クリックし、**[追加]**、**[Docker サポート]** の順に選択します。 Docker プロジェクト テンプレートは、新しいプロジェクトを **docker-compose** と呼ばれるソリューションに追加します。 プロジェクトには、図 7-3 に示すように、必要なイメージを作成 (またはビルド) する Docker アセットが含まれ、必要なコンテナーの実行を開始します。

最も簡単なリフトアンドシフトのシナリオでは、アプリケーションは、Web フォーム アプリケーションに使用する単一のサービスになります。 また、テンプレートは、**docker-compose** プロジェクトをポイントするスタートアップ プロジェクトも変更します。 Ctrl キーを押しながら F5 キーを押すか、F5 キーを押して、Docker イメージを作成し、Docker コンテナーを開始できます。

![](./media/image3.png)

**図 7-3**。 Web フォーム ソリューションの **docker-compose** プロジェクト

ソリューションを実行する前に、Windows コンテナーを使用するように、Docker を構成する必要があります。 この操作を行うには、図 7-4 に示すように、Windows の Docker タスク バー アイコンを右クリックして、**[Switch to Windows Containers]\(Windows コンテナーに切り替える\)** を選択します。

![](./media/image4.png)

**図 7-4**。 Windows で Docker タスク バーから Windows コンテナーに切り替える

メニュー項目に **[Switch to Linux Containers]\(Linux コンテナーに切り替える\)** と表示される場合は、既に Windows コンテナーで Docker を実行しています。

ソリューションを実行すると、Docker ホストが再起動されます。 構築するときに、Web フォーム プロジェクトのアプリケーションと Docker イメージを作成します。 初めてこの操作を行う場合は、時間がかかります。 ビルド プロセスでは、Windows Server の基本イメージと ASP.NET の追加イメージをプルダウンするためです。 後のビルドおよび実行サイクルは、はるかに速くなります。

Docker プロジェクト テンプレートによって追加されるファイルを詳しく見ていきましょう。 いくつかのファイルが作成されています。 Visual Studio では、これらのファイルを使用して、Docker イメージを作成し、コンテナーを開始します。 CLI から同じファイルを使用して、手動で Docker コマンドを実行することができます。

次の Dockerfile の例は、ASP.NET サイトを実行する Windows ASP.NET イメージに基づいて、Docker イメージをビルドするための基本的な設定を示しています。

```
FROM microsoft/aspnet

ARG source

WORKDIR /inetpub/wwwroot

COPY ${source:-obj/Docker/publish} .
```

この Dockerfile は、Linux コンテナーで ASP.NET Core アプリケーションを実行するために作成されたものとよく似ています。 ただし、重要な違いがいくつかあります。 最も重要な違いは、基本イメージが microsoft/aspnet であることです。これは、.NET Framework を含む、現在の Windows Server イメージです。 他の違いは、ソース ディレクトリからコピーされたディレクトリが異なるということです。

**docker-compose** プロジェクトのその他のファイルは、コンテナーをビルドおよび構成するために必要な Docker アセットです。 Visual Studio では、ファイルの使用方法を強調するために、1 つのノードにさまざまな docker-compose.yml ファイルを配置しています。 基本の docker-compose ファイルには、すべての構成に共通のディレクティブが含まれています。 docker-compose.override.yml ファイルには、環境変数および開発者用の構成に関連するオーバーライドが含まれています。 .vs.debug と .vs.release を含むバリアントは、Visual Studio が実行中のコンテナーに対してアタッチし、管理できるようにする環境設定を指定します。

Visual Studio の統合は、ソリューションへの Docker サポートの追加の一部ですが、前のセクションで示したように、docker-compose up コマンドを使用して、コマンド ラインからビルドおよび実行することもできます。

## <a name="getting-data-from-the-existing-catalog-net-core-microservice"></a>既存のカタログ .NET Core マイクロサービスからデータを取得する

仮のデータを使用する代わりに、データを取得する eShopOnContainers カタログ マイクロサービスを使用するように、Web フォーム アプリケーションを構成できます。 この操作を行うには、web.config ファイルを編集して、useFake キーの値を false に設定します。 DI コンテナーでは、ハード コーディングされたデータを返すクラスの代わりに、ライブ カタログ マイクロサービスにアクセスするクラスを使用します。 他のコードの変更は必要ありません。

ライブ カタログ サービスにアクセスするということは、カタログ サービス イメージをビルドして、カタログ サービス コンテナーを開始するように、**docker-compose** プロジェクトを更新する必要があるということです。 Docker CE for Windows は、Linux コンテナーと Windows コンテナーの両方をサポートしますが、同時に使用することはできません。 カタログ マイクロサービスを実行するには、Windows ベースのコンテナーの上にカタログ マイクロサービスを実行するイメージをビルドする必要があります。 この手法では、前のセクションで使用したものではなく、マイクロサービス プロジェクト用に別の Dockerfile が必要です。 Dockerfile.windows ファイルには、カタログ API コンテナー イメージをビルドするために、構成設定が含まれるため、(たとえば、Windows Nano Docker イメージを使用するために) Windows コンテナー上で実行されます。

カタログ マイクロサービスは、SQL Server データベースに依存します。 そのため、Windows ベースの SQL Server の Docker イメージも使用する必要があります。

これらの変更後、docker-compose プロジェクトは、アプリケーションを開始するために、さらに多くのことを行います。 そして、プロジェクトは、Windows ベースの SQL Server イメージを使用して、SQL Server を開始します。 これにより、Windows コンテナーでカタログ マイクロサービスが開始されます。 また、Windows コンテナーで Web フォーム カタログ エディター コンテナーも開始されます。 いずれかのイメージでビルドが必要な場合、そのイメージが最初に作成されます。

## <a name="development-and-production-environments"></a>開発環境と運用環境

開発環境の構成と運用環境の構成には、いくつかの違いがあります。 開発環境では、同じ Docker ホストの一部として、Windows コンテナー内で Web フォーム アプリケーション、カタログ マイクロサービス、および SQL Server を実行します。 前のセクションで、SQL Server イメージは、Linux ベースの Docker ホスト上の他の .NET Core ベースのサービスとして、同じ Docker ホストに展開されると説明しました。 同じ Docker ホスト (またはクラスター) で実行している複数のマイクロサービスの利点は、ネットワーク通信を減らし、コンテナー間の通信の待ち時間の短くできることです。

開発環境では、同じ OS のすべてのコンテナーを実行する必要があります。 Docker CE for Windows では、Windows ベースのコンテナーと Linux ベースのコンテナーの同時実行はサポートしていません。 運用環境で、単一の Docker ホスト (またはクラスター) の Windows コンテナーでカタログ マイクロサービスを実行するか、Web フォーム アプリケーションを別の Docker ホストの Linux コンテナーで実行しているカタログ マイクロサービスのインスタンスと通信させるかを決定することができます。 これは、ネットワーク待ち時間を最適化する方法によって異なります。 ほとんどの場合、展開を簡単にして通信の待ち時間を短くするために、アプリケーションが同じ Docker ホスト (または Swarm) で実行されていることに依存するマイクロサービスを必要とします。 これらの構成で、コストがかかる通信は、マイクロサービス インスタンスと永続データ ストレージの可用性が高いサーバー間のみです。

>[!div class="step-by-step"]
[前へ](../net-core-single-containers-linux-windows-server-hosts/index.md)
[次へ](../multi-container-microservice-net-applications/index.md)
