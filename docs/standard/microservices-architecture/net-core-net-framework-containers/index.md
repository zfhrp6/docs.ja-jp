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
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 60d21de06262a14f9be6a1a5ce80edf15ddf1b59
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/23/2017
---
# <a name="choosing-between-net-core-and-net-framework-for-docker-containers"></a><span data-ttu-id="c84e3-104">Docker コンテナー用 .NET Core と .NET Framework の選択</span><span class="sxs-lookup"><span data-stu-id="c84e3-104">Choosing Between .NET Core and .NET Framework for Docker Containers</span></span>

<span data-ttu-id="c84e3-105">.NET を使用してサーバー側のコンテナー化された Docker アプリケーションをビルドする場合に選択できるサポート対象の実装には、[.NET Framework](https://www.microsoft.com/net/download/framework) と [.NET Core](https://www.microsoft.com/net/download/core) の 2 つがあります。</span><span class="sxs-lookup"><span data-stu-id="c84e3-105">There are two supported implementations for building server-side containerized Docker applications with .NET: [.NET Framework](https://www.microsoft.com/net/download/framework) and [.NET Core](https://www.microsoft.com/net/download/core).</span></span> <span data-ttu-id="c84e3-106">この 2 つは多数の .NET Standard コンポーネントを共有しているため、両者でコードを共有できます。</span><span class="sxs-lookup"><span data-stu-id="c84e3-106">They share many .NET Standard components, and you can share code across the two.</span></span> <span data-ttu-id="c84e3-107">ただし、これらには基本的な違いがあり、どちらの実装を使用するかは実行内容によって決まります。</span><span class="sxs-lookup"><span data-stu-id="c84e3-107">However, there are fundamental differences between them, and which implementation you use will depend on what you want to accomplish.</span></span> <span data-ttu-id="c84e3-108">このセクションでは、それぞれの実装を選択する場合のガイダンスを提供します。</span><span class="sxs-lookup"><span data-stu-id="c84e3-108">This section provides guidance on when to choose each implementation.</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="c84e3-109">[前へ] (../container-docker-introduction/docker-containers-images-registries.md) [次へ] (general-guidance.md)</span><span class="sxs-lookup"><span data-stu-id="c84e3-109">[Previous] (../container-docker-introduction/docker-containers-images-registries.md) [Next] (general-guidance.md)</span></span>
