---
title: ASP.NET Core および Azure での最新の Web アプリケーションの設計
description: ASP.NET Core および Azure での最新の Web アプリケーションの設計 | 概要
author: ardalis
ms.author: wiwagn
ms.date: 10/06/2017
ms.openlocfilehash: 57c2a598e48f855dd540b96c7ebdb522b4197b91
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="architect-modern-web-applications-with-aspnet-core-and-azure"></a>ASP.NET Core および Azure での最新の Web アプリケーションの設計

![カバーの画像](./media/cover.jpg)


.NET Core と ASP.NET Core は、従来の .NET 開発よりも優れたいくつかの利点を提供します。 次の一部またはすべてがアプリケーションの成功に重要な場合は、サーバー アプリケーションに .NET Core を使用してください。

-   クロス プラットフォーム サポート

-   マイクロサービスの使用

-   Docker コンテナーの使用

-   高パフォーマンスとスケーラビリティの要件

-   同じサーバー上のアプリケーション別の .NET バージョンのサイド バイ サイドのバージョン管理

従来の .NET アプリケーションはこれらの要件をサポートできますが、ASP.NET Core と .NET Core は、上記のシナリオに対する改善されたサポートを提供するように最適化されています。

ますます多くの組織が、Microsoft Azure などのサービスを使用してクラウドで Web アプリケーションをホストすることを選択しています。 アプリケーションまたは組織にとって次のことが重要な場合は、クラウドでのアプリケーションのホストを検討してください。

-   データ センターのコスト (ハードウェア、ソフトウェア、スペース、ユーティリティなど) の投資の削減

-   柔軟な料金 (アイドル状態の容量ではなく、使用量に基づく支払い)

-   極端な信頼性

-   強化されたアプリのモビリティ。アプリが展開されている場所と方法を簡単に変更できること。

-   柔軟な容量。実際のニーズに基づいたスケール アップまたはスケール ダウン。

Microsoft Azure でホストされる ASP.NET Core での Web アプリケーションを構築すると、従来型の代替手段よりも優れた多くの競争上の優位性が得られます。 ASP.NET Core は、最新の Web アプリケーションの開発作業とクラウド ホスティングのシナリオ用に最適化されています。 このガイドでは、これらの機能を最適に活用するために ASP.NET Core アプリケーションを設計する方法を学習します。

## <a name="purpose"></a>目的

このガイドでは、ASP.NET Core と Azure を使用したモノリシックな Web アプリケーションの構築に関するエンド ツー エンドのガイダンスを提供します。

このガイドは、エンタープライズ アプリケーションをホストするための Docker、マイクロサービス、およびコンテナーの展開を中心に説明している「*Architecting and Developing Containerized and Microservice-based Applications with .NET*」(.NET を使用したコンテナー化およびマイクロサービス ベースのアプリケーションの設計と開発) を補完します。

> ### <a name="architecting-and-developing-containerized-microservice-based-apps-in-net"></a>.NET でのコンテナー化されたマイクロサービス ベースのアプリの設計および開発
> - **電子ブック**  
> <http://aka.ms/MicroservicesEbook>
> - **サンプル アプリケーション**  
> <http://aka.ms/microservicesarchitecture>

## <a name="who-should-use-this-guide"></a>対象読者

このガイドの対象ユーザーは、主にクラウドでの Microsoft テクノロジとサービスを使用した最新の Web アプリケーションの構築に関心がある開発者、開発担当者、およびアーキテクトです。

2 番目の対象ユーザーは、ASP.NET や Azure を既に使い慣れていて、新規または既存のプロジェクトに対して ASP.NET Core にアップグレードすることに意味があるかどうかに関する情報を探している技術的な意思決定者です。

## <a name="how-you-can-use-this-guide"></a>このガイドを使用する方法

このガイドは、最新の .NET テクノロジと Windows Azure を使用した Web アプリケーションの構築に焦点を当てた比較的小さなドキュメントに凝縮されています。 そのため、このようなアプリケーションと、技術的な考慮事項を理解するための基盤を提供するものとして、全体を読むことができます。 ガイドは、サンプル アプリケーションと共に、最初に参照するものとして使用できます。 関連するサンプル アプリケーションをテンプレートとして使用するか、アプリケーションのコンポーネント部分を整理する方法を参照してください。 独自のアプリケーションでこれらの選択肢を比較検討する場合、ガイドの基本原則とアーキテクチャのカバレッジ、テクノロジのオプション、および決定時の考慮事項を参照してください。

これらの考慮事項と営業案件の共通理解を確保するために、チームにこのガイドを自由に転送してください。 用語の共通セットと基本原則を理解して全員が作業すると、一貫性のあるアプリケーションのアーキテクチャのパターンと実践方法を確保するために役立ちます。

## <a name="references"></a>参照
- **サーバー アプリ用 .NET Core と .NET Framework の選択**  
<https://docs.microsoft.com/dotnet/standard/choosing-core-framework-server>

>[!div class="step-by-step"]
[Next] (modern-web-applications-characteristics.md)
