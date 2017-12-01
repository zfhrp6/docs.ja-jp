---
title: "最新の web アプリケーションの特性"
description: "ASP.NET Core と Azure での最新の Web アプリケーションを設計 |最新の web アプリケーションの特性"
author: ardalis
ms.author: wiwagn
ms.date: 10/06/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.openlocfilehash: 9ff9380b318457a842dec4e41b9b74dcddcda3d3
ms.sourcegitcommit: 882e02b086d7cb9c75f748494cf7a8d3377c5874
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="characteristics-of-modern-web-applications"></a>最新の Web アプリケーションの特性

> "… 適切な設計は、機能には、安価です。 このアプローチは骨の折れるを成功させるのには続行されます。"  
> _\-Dennis Ritchie_

## <a name="summary"></a>概要

最新の web アプリケーションは、上位のユーザーの期待とこれまでよりも大きい要求があります。 現在の web アプリケーションが使用可能な 24/7 からほぼすべてのデバイスから使用できるようにし、どこにあっても、または画面のサイズが必要です。 Web アプリケーションは、セキュリティで保護された、柔軟性が高く、およびオンデマンドの急激な増加に対応できる拡張性にする必要があります。 ますます、複雑なシナリオは、JavaScript を使用して、web Api 経由で効率的に通信するクライアント上に構築された豊富なユーザー エクスペリエンスで処理される必要があります。

ASP.NET Core は、最新の web アプリケーションとクラウド ベースのホスティング シナリオに最適です。 そのモジュール形式デザインは、実際に使用される、アプリケーションのセキュリティとホストのリソース要件を削減しながらパフォーマンスを向上させる機能のみに依存するアプリケーションを使用できます。

## <a name="reference-application-eshoponweb"></a>アプリケーションを参照: eShopOnWeb

このガイドには、参照アプリケーションが含まれています。 *eShopOnWeb*、いくつかの原則と推奨事項を示しています。 アプリケーションは、シャツ、コーヒーマグ、およびその他のマーケティングの項目のカタログからの参照をサポートする単純なオンライン ストアです。 参照アプリケーションは理解しやすくために意図的に単純です。

**図 2-1。** eShopOnWeb

![](./media/image2-1.png)

> ### <a name="reference-application"></a>アプリケーションの参照
> - **eShopOnWeb**  
> <https://github.com/dotnet/eShopOnWeb>

## <a name="cloud-hosted-and-scalable"></a>クラウドでホストされると拡張性

ASP.NET Core は、メモリ不足と高いスループットになっているため、クラウド (パブリック クラウド、プライベート クラウド、クラウド) に最適です。 ASP.NET Core アプリケーションのより小さなフット プリントは、複数の同一のハードウェア上でそれらをホストすることができ、支払-として-するを使用して、クラウド サービスのホスティングを移動するときにより少ないリソースの支払いを意味します。 高いスループットでは、さらにサーバーとホスティング インフラストラクチャに投資する必要性が低く、同じハードウェアを指定したアプリケーションからより多くの顧客を提供することができますを意味します。

## <a name="cross-platform"></a>クロス プラットフォーム

ASP.NET Core は、プラットフォーム間で Linux MacOS と Windows 上で実行できます。 これは、開発と ASP.NET Core でビルドされたアプリの展開の両方の多くの新しいオプションが表示されます。 Docker コンテナーは、通常 Linux を現在実行して、ASP.NET Core アプリケーションの利点を活用することをホストできる[コンテナーおよび microservices](../microservices-architecture)です。

## <a name="modular-and-loosely-coupled"></a>モジュール化し、疎結合

NuGet パッケージは、.NET Core で捉えるおよび ASP.NET Core アプリケーションは NuGet で多くのライブラリで構成されます。 この細分性の機能により、アプリはのみに依存し、実際には、必要な領域の低減、フット プリントとセキュリティの脆弱性の機能を展開します。

ASP.NET Core は、内部的とアプリケーション レベルの両方も完全に依存関係の挿入をサポートします。 インターフェイスは、スワップ アウトでき、必要に応じて、複数の実装であることができます。 依存関係の挿入は、やすく拡張、保守、およびテストするために、これらのインターフェイスに疎結合にアプリがします。

## <a name="easily-tested-with-automated-tests"></a>自動テストを簡単にテスト

ASP.NET Core アプリケーションが単体テストをサポートし、疎結合との依存関係挿入できるサポート簡単にテスト目的での偽の実装とインフラストラクチャ上の問題をスワップします。 ASP.NET Core では、メモリ内のホストのアプリに使用できる TestServer も同梱されています。 機能テスト (ミドルウェア、ルーティング、モデルのバインド、フィルターなどを含む) 完全なアプリケーション スタックを使用すること、このメモリ内のサーバーに要求を作成でき、時間の割合ですべての応答を受け取るためにかかる実際のサーバー上でのアプリをホストネットワーク レイヤーを通じて要求を作成したりします。 これらのテストが記述するには特に容易、貴重な api、か最新の web アプリケーションでますます重要にします。

## <a name="traditional-and-spa-behaviors-supported"></a>従来と SPA 動作のサポート

従来の web アプリケーションでは、ほとんどのクライアント側の動作が関係しているが、代わりに依存して、サーバーのすべてのナビゲーション、クエリ、および更新プログラム、アプリが行う必要があります。 エンドユーザーのブラウザーでページ全体の再読み込みされている結果を使用して新しい web 要求に変換されるユーザーが行った各新しい操作。 従来のモデル ビュー コント ローラー (MVC) フレームワークには、さらに、モデルで作業とビューを返す別のコント ローラーのアクションに対応する新しい要求のたびにこの方法は、通常に従います。 AJAX (Asynchronous JavaScript and XML) 機能により、特定のページにある個々 の操作を拡張することがありますが、多くのさまざまな MVC ビューと URL エンドポイントを使用するアプリの全体的なアーキテクチャ。

これに対し、単一ページ アプリケーション (SPAs) は、(存在する場合) はほとんどの動的に生成されたサーバー側ページ読み込みが含まれません。 多くの SPAs を起動し、アプリを実行するために必要な JavaScript ライブラリを読み込むための静的 HTML ファイル内で初期化されます。 これらのアプリ、データ ニーズを満たす web Api の使用率が高いを行い程度豊富なユーザー エクスペリエンスを提供できます。

多くの web アプリケーションには、従来の web アプリケーションの動作 (通常はコンテンツ) との対話機能) SPAs の組み合わせが含まれます。 ASP.NET Core は、MVC および web ツールの同じセットを使用して、フレームワーク ライブラリを基になる、同じアプリケーション内の Api の両方をサポートします。

## <a name="simple-development-and-deployment"></a>単純な開発と配置

ASP.NET Core アプリケーションを作成するには、単純なテキスト エディターとコマンド ライン インターフェイス、または Visual Studio と同様に、フル機能の開発環境を使用します。 モノリシックなアプリケーションは通常、単一のエンドポイントを展開します。 展開は、継続的インテグレーション (CI) と継続的な配信 (CD) パイプラインの一部として発生する可能性を簡単に自動化できます。 従来 CI/CD のツールに加えて、Windows Azure は git リポジトリ用のサポートが統合されてし、指定された git ブランチまたはタグに行われるように自動的に、更新プログラムを展開できます。

## <a name="traditional-aspnet-and-web-forms"></a>従来の ASP.NET および Web フォーム

ASP.NET Core、従来の ASP.NET だけでなく 4.x は引き続き web アプリケーションを構築するための堅牢性と信頼性の高いプラットフォームです。 ASP.NET は、MVC、Web API の開発モデルだけでなく、豊富なページ ベースのアプリケーションの開発に適してと機能の豊富なサード パーティ コンポーネント エコシステム Web フォームをサポートします。 Windows Azure は、ASP.NET 4.x アプリケーションの優れた従来からサポートを持ち、多くの開発者はこのプラットフォームに精通します。

> ### <a name="references--modern-web-applications"></a>参照: 最新の Web アプリケーション
> - **ASP.NET Core の概要**  
> <https://docs.microsoft.com/aspnet/core/>
> - **6 キー メリットの ASP.NET Core を使用する異なると向上します。**  
> <https://blog.trigent.com/six-key-benefits-of-asp-net-core-1-0-which-make-it-different-better/>
> - **ASP.NET Core でのテスト**  
> <https://docs.microsoft.com/aspnet/core/testing/>

>[!div class="step-by-step"]
[前](index.md) [次へ] (choose-between-traditional-web-and-single-page-apps.md)
