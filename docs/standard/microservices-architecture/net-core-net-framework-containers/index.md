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
# <a name="choosing-between-net-core-and-net-framework-for-docker-containers"></a>Docker コンテナー用 .NET Core と .NET Framework の選択

.NET を使用してサーバー側のコンテナー化された Docker アプリケーションをビルドする場合に選択できるサポート対象の実装には、[.NET Framework](https://www.microsoft.com/net/download/framework) と [.NET Core](https://www.microsoft.com/net/download/core) の 2 つがあります。 この 2 つは多数の .NET Standard コンポーネントを共有しているため、両者でコードを共有できます。 ただし、これらには基本的な違いがあり、どちらの実装を使用するかは実行内容によって決まります。 このセクションでは、それぞれの実装を選択する場合のガイダンスを提供します。


>[!div class="step-by-step"]
[前へ] (../container-docker-introduction/docker-containers-images-registries.md) [次へ] (general-guidance.md)
