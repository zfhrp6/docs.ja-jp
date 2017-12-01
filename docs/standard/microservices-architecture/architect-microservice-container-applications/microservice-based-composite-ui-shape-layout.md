---
title: "Visual UI 図形および複数 microservices によって生成されたレイアウトを含む microservices に基づく複合 UI の作成"
description: "コンテナーの .NET アプリケーションの .NET Microservices アーキテクチャ |Visual UI 図形および複数 microservices によって生成されたレイアウトを含む microservices に基づく複合 UI の作成"
keywords: "Docker, マイクロサービス, ASP.NET, コンテナー"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 4b32fed5eb0de02b01665efa4368eb83e3fda08d
ms.sourcegitcommit: e99dfadbca1992c187179b6a3b42bef44534ebb6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/01/2017
---
# <a name="creating-composite-ui-based-on-microservices-including-visual-ui-shape-and-layout-generated-by-multiple-microservices"></a>Visual UI 図形および複数 microservices によって生成されたレイアウトを含む microservices に基づく複合 UI の作成

Microservices アーキテクチャは、多くの場合、サーバー側のデータおよびロジックの処理を開始します。 ただしより高度な手法は、UI が microservices もに基づいてアプリケーションを設計します。 Microservices、サーバーと使用、microservices モノリシック クライアント アプリではなく、microservices によって生成される複合 UI を持つためです。 この方法でビルドする microservices はロジックおよび視覚的表現の両方を備えたすることはできます。

図 4-20 モノリシックなクライアント アプリケーションから microservices を消費だけの簡単な方法を示しています。 もちろん、JavaScript と HTML を生成する間、ASP.NET MVC サービスことができます。 図は、1 つの (モノリシック) クライアントだけ専念ロジックとデータ (HTML および JavaScript) の UI 図形ではなくなると、microservices を使用する UI があることを強調表示するための簡略化します。

![](./media/image20.png)

**図 4-20**です。 バック エンド microservices を消費するモノリシック UI アプリケーション

これに対し、複合 UI は正確に生成され microservices 自体で構成します。 UI の特定の領域のビジュアルの図形のドライブ、microservices の一部です。 主な違いは、テンプレートに基づいてクライアントの UI コンポーネント (たとえば TS クラス) があり、そのデータの整形 UI ViewModel、それらのテンプレートは各マイクロ サービスから取得します。

クライアント アプリケーションのスタートアップ時に各クライアントの UI コンポーネント (TypeScript のクラスの例) は自身に登録、特定のシナリオ ViewModels を提供できるインフラストラクチャ マイクロ サービス。 マイクロ サービスは、図形を変更する場合、UI も変更します。

図 4-21 は、この複合 UI アプローチのバージョンを示しています。 これは、簡体字、その他の microservices 細分化された部分がさまざまな手法に基づいて集計をする必要がありますので、従来の web 手法 (ASP.NET MVC) など、SPA (Single Page Application) を作成するかどうかによって異なります。

![](./media/image21.png)

**図 4-21**です。 バック エンド microservices によって形作ら複合 UI アプリケーションの例

これらの UI コンポジション microservices の各するようになります小さな API ゲートウェイ。 ここでは各小さな UI 領域を担当します。

小さいため、どのような UI テクノロジに応じて使用しているまたは microservices によって駆動される複合 UI アプローチがより困難できます。 インスタンスは使用しませんのと同じ手法、SPA を構築するため、またはネイティブ モバイル アプリを使用する従来の web アプリケーションを構築するため (このアプローチのより困難になることができます、Xamarin アプリを開発する際に同様)。

[EShopOnContainers](http://aka.ms/MicroservicesArchitecture)サンプル アプリケーションでは、複数の理由によりモノリシック UI アプローチを使用します。 まず、microservices とコンテナーの概要です。 複合 UI より高度なさらに複雑なデザインおよび UI を開発するときにもが必要です。 次に、eShopOnContainers でもありより複雑な C クライアントで Xamarin に基づいてネイティブ モバイル アプリが提供\#側です。

ただし、複合 microservices に基づいて、UI に関する詳細については、次の参照を使用することをお勧めします。

## <a name="additional-resources"></a>その他の技術情報

-   **ASP.NET (特定のワーク ショップ) を使用して複合 UI**
    [*http://go.particular.net/workshop-composite-ui-demo*](http://go.particular.net/workshop-composite-ui-demo)

-   **Ruben Oostinga です。Microservices アーキテクチャでモノリシック フロント エンド**
    [*http://blog.xebia.com/the-monolithic-frontend-in-the-microservices-architecture/*](http://blog.xebia.com/the-monolithic-frontend-in-the-microservices-architecture/)

-   **Mauro Servienti です。優れた UI コンポジションのシークレット**
    [*https://particular.net/blog/secret-of-better-ui-composition*](https://particular.net/blog/secret-of-better-ui-composition)

-   **Viktor Farcic です。Microservices にフロント エンド Web コンポーネントを含む**
    [*https://technologyconversations.com/2015/08/09/including-front-end-web-components-into-microservices/*](https://technologyconversations.com/2015/08/09/including-front-end-web-components-into-microservices/)

-   **Microservices アーキテクチャでは、フロント エンドを管理します。**\
    [*http://allegro.tech/2016/03/Managing-Frontend-in-the-microservices-architecture.html*](http://allegro.tech/2016/03/Managing-Frontend-in-the-microservices-architecture.html)


>[!div class="step-by-step"]
[前](microservices-addressability-サービス-registry.md) [次へ] (回復力の高い-可用性-microservices.md)
