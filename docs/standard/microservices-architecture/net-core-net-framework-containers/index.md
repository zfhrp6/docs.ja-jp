---
title: Docker コンテナー用 .NET Core と .NET Framework の選択
description: '.NET マイクロサービス: コンテナー化された .NET アプリケーションのアーキテクチャ | Docker コンテナー用 .NET Core と .NET Framework の選択'
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.openlocfilehash: b483214e7bd039a71ae642aa26e69d63222af8ab
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33580128"
---
# <a name="choosing-between-net-core-and-net-framework-for-docker-containers"></a><span data-ttu-id="5bfa2-103">Docker コンテナー用 .NET Core と .NET Framework の選択</span><span class="sxs-lookup"><span data-stu-id="5bfa2-103">Choosing Between .NET Core and .NET Framework for Docker Containers</span></span>

<span data-ttu-id="5bfa2-104">.NET を使用してサーバー側のコンテナー化された Docker アプリケーションをビルドする場合に選択できるサポート対象の実装には、[.NET Framework](https://www.microsoft.com/net/download/framework) と [.NET Core](https://www.microsoft.com/net/download/core) の 2 つがあります。</span><span class="sxs-lookup"><span data-stu-id="5bfa2-104">There are two supported implementations for building server-side containerized Docker applications with .NET: [.NET Framework](https://www.microsoft.com/net/download/framework) and [.NET Core](https://www.microsoft.com/net/download/core).</span></span> <span data-ttu-id="5bfa2-105">この 2 つは多数の .NET Standard コンポーネントを共有しているため、両者でコードを共有できます。</span><span class="sxs-lookup"><span data-stu-id="5bfa2-105">They share many .NET Standard components, and you can share code across the two.</span></span> <span data-ttu-id="5bfa2-106">ただし、これらには基本的な違いがあり、どちらの実装を使用するかは実行内容によって決まります。</span><span class="sxs-lookup"><span data-stu-id="5bfa2-106">However, there are fundamental differences between them, and which implementation you use will depend on what you want to accomplish.</span></span> <span data-ttu-id="5bfa2-107">このセクションでは、それぞれの実装を選択する場合のガイダンスを提供します。</span><span class="sxs-lookup"><span data-stu-id="5bfa2-107">This section provides guidance on when to choose each implementation.</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="5bfa2-108">[前へ] (../container-docker-introduction/docker-containers-images-registries.md) [次へ] (general-guidance.md)</span><span class="sxs-lookup"><span data-stu-id="5bfa2-108">[Previous] (../container-docker-introduction/docker-containers-images-registries.md) [Next] (general-guidance.md)</span></span>
