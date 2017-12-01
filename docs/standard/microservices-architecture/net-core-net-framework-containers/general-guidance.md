---
title: "一般的なガイダンス"
description: "コンテナーの .NET アプリケーションの .NET Microservices アーキテクチャ |一般的なガイダンス"
keywords: "Docker, マイクロサービス, ASP.NET, コンテナー"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/18/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 22dea926e77079e4f543934613ced13a28b2dae6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="general-guidance"></a>一般的なガイダンス

このセクションでは、.NET Core または .NET Framework を選択するための概要を示します。 次のセクションでこれらのオプションの詳細についてを説明します。

Linux または Windows のコンテナーでコンテナー Docker サーバー アプリケーションの .NET Core を使用する必要があるとき。

-   クロスプラット フォームが必要である。 たとえば、Linux と Windows コンテナーの両方を使用します。

-   アプリケーションのアーキテクチャは、microservices に基づいています。

-   高速コンテナーを起動し、コストを削減するために、高密度を実現するためにコンテナーまたはハードウェア ユニットあたり複数のコンテナーにつき、小さなフット プリントを対象にする必要があります。

つまり、新しいコンテナー化 .NET アプリケーションを作成するときに、既定の選択肢として .NET Core を検討してください。 数多くの利点し、最適なコンテナーの考え方と作業のスタイルを使用します。

.NET Core を使用するその他の利点は、同じコンピューター内のアプリケーションの .NET バージョンをサイド バイ サイドを実行することができます。 この利点は、コンテナー、アプリが必要な .NET のバージョンを特定するためにサーバーまたは Vm をコンテナーを使用しない方が重要です。 ある限りは、基になる OS との互換性。)

Windows コンテナーでコンテナー Docker サーバー アプリケーションの .NET Framework を使用する必要があるとき。

-   アプリケーションは現在 .NET Framework を使用して、Windows で強力な依存関係があります。

-   .NET Core でサポートされていない Windows Api を使用する必要があります。

-   サード パーティ製の .NET ライブラリまたは .NET core はない NuGet パッケージを使用する必要があります。

.NET Framework を使用して、Docker での展開に関する問題を最小限に抑えることで、配置操作を向上できます。 これは、 [*リフト アンド シフト"シナリオ*](https://aka.ms/liftandshiftwithcontainersebook)は、最初に開発された従来の .NET Framework と ASP.NET WebForms、MVC web アプリケーションまたは WCF (と同じようにレガシ アプリケーションを containerizing にとって重要Windows Communication Foundation) サービス。

### <a name="additional-resources"></a>その他の技術情報

-   **電子書籍: Azure と Windows コンテナーの既存の .NET Framework アプリケーションを最新化**
    [*https://aka.ms/liftandshiftwithcontainersebook*](https://aka.ms/liftandshiftwithcontainersebook)

-   **アプリのサンプル: Windows コンテナーを使用する従来の ASP.NET web アプリの近代化**
    [*https://aka.ms/eshopmodernizing*](https://aka.ms/eshopmodernizing)


>[!div class="step-by-step"]
[前](index.md) [次へ] (net-コア ・ コンテナー ・ scenarios.md)
