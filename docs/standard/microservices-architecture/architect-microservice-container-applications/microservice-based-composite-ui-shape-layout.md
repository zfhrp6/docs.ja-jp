---
title: 複数のマイクロサービスによって生成されるビジュアル UI シェイプ、レイアウトなど、マイクロサービスを基にしている複合 UI を作成する
description: コンテナー化された .NET アプリケーションの .NET マイクロサービス アーキテクチャ | 複数のマイクロサービスによって生成されるビジュアル UI シェイプ、レイアウトなど、マイクロサービスを基にしている複合 UI を作成する
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.openlocfilehash: cbadb13109c51ba53530011a17006b585573f40a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="creating-composite-ui-based-on-microservices-including-visual-ui-shape-and-layout-generated-by-multiple-microservices"></a>複数のマイクロサービスによって生成されるビジュアル UI シェイプ、レイアウトなど、マイクロサービスを基にしている複合 UI を作成する

マイクロサービス アーキテクチャは、多くの場合、データおよびロジックを処理するサーバー側から始まります。 ただし、より高度なアプローチとして、マイクロサービスに基づいたアプリケーション UI を設計する方法もあります。 これは、サーバー上にマイクロサービスが置かれモノリシック クライアント アプリのみでマイクロサービスが利用されるというのでなく、マイクロサービスによって複合 UI が生成されることを意味します。 このアプローチの場合、ビルドするマイクロサービスは、ロジックおよび視覚的表現の両方を備えることができます。

図 4-20 に、モノリシック クライアント アプリケーションからマイクロサービスを利用するだけの簡単なアプローチを示します。 当然ながら、HTML および JavaScript の生成の間に ASP.NET MVC サービスを含めることが可能です。 図は簡単なものであり、マイクロサービスを利用している単一 (モノリシック) のクライアント UI が強調表示されています。またこれらのマイクロサービスでは、UI シェイプ (HTML および JavaScript) ではなく、ロジックとデータにのみ焦点を当てています。

![](./media/image20.png)

**図 4-20** バックエンド マイクロサービスを利用するモノリシック UI アプリケーション

これに対し、複合 UI は正確に生成され、マイクロサービス自体で構成されます。 一部のマイクロサービスでは、UI の特定の領域のビジュアル シェイプをドライブしています。 その場合の主な違いは、クライアント UI コンポーネント (TS クラスなど) がテンプレートに基づいており、それらのテンプレートのデータ シェイプ UI ViewModel が各マイクロサービスから取得されるということです。

クライアント アプリケーションの起動時、各クライアント UI コンポーネント (TypeScript クラスなど) は、特定のシナリオで ViewModels を提供できるインフラストラクチャ マイクロサービスに自らを登録します。 マイクロサービスがシェイプを変更すると、UI も変わります。

図 4-21 に、この複合 UI アプローチのバージョンを示します。 これは簡略化した図です。従来の Web アプローチ (ASP.NET MVC) または SPA (Single Page Application) をビルドする場所によっては、さまざまな手法に基づいて細分化された部分を集計するマイクロサービスが他に存在する場合もあるからです。

![](./media/image21.png)

**図 4-21** バックエンド マイクロサービスによって成形された複合 UI アプリケーションの例

これらの UI コンポジション マイクロサービスのそれぞれは、小規模な API ゲートウェイに似ています。 ただし、この場合、それぞれが小規模な UI 領域を担当します。

マイクロサービスによってドライブされる複合 UI アプローチは、使用する UI テクノロジに応じて、直面する困難の度合いが異なる可能性があります。 たとえば、SPA またはネイティブ モバイル アプリをビルドするために使用する技法 (Xamarin アプリを開発する場合などで、このアプローチの場合は困難の度合いが大きい) が従来の Web アプリケーションをビルドするために使用する技法と異なる場合があります。

[eShopOnContainers](http://aka.ms/MicroservicesArchitecture) サンプル アプリケーションでは複数の理由からモノリシック UI アプローチを使用します。 まず、マイクロサービスとコンテナーの場合です。 複合 UI は高度な技法であり、UI の設計および開発するときには複雑な処理も求められます。 次に、eShopOnContainers でも Xamarin に基づいたネイティブ モバイル アプリが実現されます。この場合は、クライアント C\# 側での処理がより複雑になります。

次の参照情報を使用してマイクロサービスに基づく複合 UI に関する知識を深めることをお勧めします。

## <a name="additional-resources"></a>その他の技術情報

-   **ASP.NET を使用した複合 UI (特定のワークショップ)**
    [*http://go.particular.net/workshop-composite-ui-demo*](http://go.particular.net/workshop-composite-ui-demo)

-   **Ruben Oostinga。マイクロサービス アーキテクチャでのモノリシック フロントエンド**
    [*http://blog.xebia.com/the-monolithic-frontend-in-the-microservices-architecture/*](http://blog.xebia.com/the-monolithic-frontend-in-the-microservices-architecture/)

-   **Mauro Servienti。優れた UI コンポジションの秘密**
    [*https://particular.net/blog/secret-of-better-ui-composition*](https://particular.net/blog/secret-of-better-ui-composition)

-   **Viktor Farcic。フロントエンド Web コンポーネントをマイクロサービスに含める**
    [*https://technologyconversations.com/2015/08/09/including-front-end-web-components-into-microservices/*](https://technologyconversations.com/2015/08/09/including-front-end-web-components-into-microservices/)

-   **マイクロサービス アーキテクチャでのフロントエンドの管理**\
    [*https://allegro.tech/2016/03/Managing-Frontend-in-the-microservices-architecture.html*](https://allegro.tech/2016/03/Managing-Frontend-in-the-microservices-architecture.html)


>[!div class="step-by-step"]
[Previous] (microservices-addressability-service-registry.md) [Next] (resilient-high-availability-microservices.md)
