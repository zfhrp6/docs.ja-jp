---
title: ".NET のコンテナーでのターゲットにどのような OS"
description: "コンテナーの .NET アプリケーションの .NET Microservices アーキテクチャ |.NET のコンテナーでのターゲットにどのような OS"
keywords: "Docker, マイクロサービス, ASP.NET, コンテナー"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/18/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 828ccb5e7a76f9419e80793b6cb3a6ba24f358cf
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/22/2017
---
# <a name="what-os-to-target-with-net-containers"></a>.NET のコンテナーでのターゲットにどのような OS

Docker と .NET Framework と .NET Core の違いによってサポートされるオペレーティング システムの多様性を指定するには、特定の OS とを使用するために、フレームワークによって特定のバージョンをターゲットする必要があります。 

Windows の場合は、Windows Server Core または Nano Server の Windows を使用できます。 これらのバージョンの Windows では、必要となる .NET Framework または .NET Core でそれぞれ異なる特性 (Windows Server Core と Nano Server で Kestrel のように自己ホスト型の web サーバーで IIS) を提供します。 

For Linux ディストリビューションの場合は複数、使用可能な (Debian) などの公式の .NET Docker イメージでサポートされているです。

図 3-1 によっては、.NET framework を使用可能な OS バージョンを確認できます。

![](./media/image1.png)

**図 3-1。** .NET framework のバージョンによって対象とするオペレーティング システム

さまざまな Linux ディストリビューションを使用するか、Microsoft では提供されないバージョンのイメージが必要な場合は、独自の Docker イメージを作成できます。 たとえば、従来の .NET Framework および Windows Server Core では、Docker のないのため、一般的なシナリオで実行されている ASP.NET Core と、イメージを作成する可能性があります。

Dockerfile は、ファイルをイメージ名を追加する場合は、オペレーティング システムおよび使用すると、次の例のように、タグによってバージョンを選択できます。

-   microsoft/**dotnet:2.0.0-ランタイム-jessie**

        .NET Core 2.0 runtime-only on Linux

-   microsoft/**dotnet:2.0.0-ランタイム-nanoserver-1709** 

        .NET Core 2.0 runtime-only on Windows Nano Server (Windows Server 2016 Fall Creators Update version 1709)

-   microsoft/**aspnetcore:2.0**
    
        .NET Core 2.0 multi-architecture: Supports Linux and Windows Nano Server depending on the Docker host.
        The aspnetcore image has a few optimizations for ASP.NET Core. 





>[!div class="step-by-step"]
[前](コンテナーのフレームワークの選択-factors.md) [次へ] (公式の net-docker-images.md)
