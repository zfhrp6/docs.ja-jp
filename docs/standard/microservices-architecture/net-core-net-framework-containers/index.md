---
title: "Docker コンテナー用 .NET Core と .NET Framework の選択"
description: ".NET マイクロサービス: コンテナー化された .NET アプリケーションのアーキテクチャ | Docker コンテナー用 .NET Core と .NET Framework の選択"
keywords: "Docker, マイクロサービス, ASP.NET, コンテナー"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: f7a5fee26f4d138ae22f3551a25a674b22a2f6d1
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="choosing-between-net-core-and-net-framework-for-docker-containers"></a><span data-ttu-id="c9258-104">Docker コンテナー用 .NET Core と .NET Framework の選択</span><span class="sxs-lookup"><span data-stu-id="c9258-104">Choosing Between .NET Core and .NET Framework for Docker Containers</span></span>

<span data-ttu-id="c9258-105">.NET を使用してサーバー側のコンテナー化された Docker アプリケーションをビルドする場合に選択できるサポート対象の実装には、[.NET Framework](https://www.microsoft.com/net/download/framework) と [.NET Core](https://www.microsoft.com/net/download/core) の 2 つがあります。</span><span class="sxs-lookup"><span data-stu-id="c9258-105">There are two supported implementations for building server-side containerized Docker applications with .NET: [.NET Framework](https://www.microsoft.com/net/download/framework) and [.NET Core](https://www.microsoft.com/net/download/core).</span></span> <span data-ttu-id="c9258-106">この 2 つは多数の .NET Standard コンポーネントを共有しているため、両者でコードを共有できます。</span><span class="sxs-lookup"><span data-stu-id="c9258-106">They share many .NET Standard components, and you can share code across the two.</span></span> <span data-ttu-id="c9258-107">ただし、これらには基本的な違いがあり、どちらの実装を使用するかは実行内容によって決まります。</span><span class="sxs-lookup"><span data-stu-id="c9258-107">However, there are fundamental differences between them, and which implementation you use will depend on what you want to accomplish.</span></span> <span data-ttu-id="c9258-108">このセクションでは、それぞれの実装を選択する場合のガイダンスを提供します。</span><span class="sxs-lookup"><span data-stu-id="c9258-108">This section provides guidance on when to choose each implementation.</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="c9258-109">[前へ] (../container-docker-introduction/docker-containers-images-registries.md) [次へ] (general-guidance.md)</span><span class="sxs-lookup"><span data-stu-id="c9258-109">[Previous] (../container-docker-introduction/docker-containers-images-registries.md) [Next] (general-guidance.md)</span></span>
