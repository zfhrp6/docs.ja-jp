---
title: "サービス指向アーキテクチャ"
description: "コンテナーの .NET アプリケーションの .NET Microservices アーキテクチャ |サービス指向アーキテクチャ"
keywords: "Docker, マイクロサービス, ASP.NET, コンテナー"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 970ff86c77100077d4c7710c0a697d1745d35819
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/22/2017
---
# <a name="service-oriented-architecture"></a>サービス指向アーキテクチャ 

サービス指向アーキテクチャ (SOA) 過剰使用されている用語、別のユーザーにさまざまなものを意味していました。 共通の基盤として SOA ことを意味のサブシステムや階層のようなさまざまな種類に分類できます (最も一般的に HTTP サービス) の複数のサービスへの分解によって、アプリケーションを構成します。

これらのサービスようになりましたとして展開できます Docker コンテナー展開の問題を解決するコンテナー イメージのすべての依存関係が含まれているためです。 ただし、SOA アプリケーションを拡張する必要がある場合は、拡張性があります、可用性の課題を配置する場合は、1 つの Docker ホストに基づきます。 これは、クラスタ リング ソフトウェアまたはオーケストレーター Docker に役立つ、microservices の展開のアプローチを記述して以降のセクションで説明したようです。

Docker コンテナーに便利です (ただし、必須ではない) は、従来のサービス指向アーキテクチャより高度な microservices アーキテクチャの両方にします。

SOA から派生して Microservices が SOA は microservices アーキテクチャと異なる。 大規模なサーバーの全体のブローカーのような機能には、組織レベルでは、中央 orchestrators と[Enterprise Service Bus (ESB)](https://en.wikipedia.org/wiki/Enterprise_service_bus) SOA の典型的な。 ほとんどの場合、これらは、マイクロ サービス コミュニティでのアンチ パターン。 実際と主張する人を「マイクロ サービス アーキテクチャは SOA 適切です」

このガイドは、SOA アプローチは、要件とマイクロ サービス アーキテクチャで使用される手法よりも小さい規範となるために、microservices、について説明します。 マイクロ サービス ベースのアプリケーションを構築する方法がわかっている場合、単純なサービス指向アプリケーションをビルドする方法も知っておきます。




>[!div class="step-by-step"]
[前](docker-アプリケーションの状態-data.md) [次へ] (microservices architecture.md)
