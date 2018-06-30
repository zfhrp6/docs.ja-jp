---
title: 複数のコンテナーとマイクロサービス ベースの NET アプリケーションのデザインと開発
description: '.NET マイクロサービス: コンテナー化された .NET アプリケーションのアーキテクチャ | 複数のコンテナーとマイクロサービス ベースの NET アプリケーションのデザインと開発'
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.openlocfilehash: 13abff090d42c5d59476612942560c126836dbb0
ms.sourcegitcommit: 979597cd8055534b63d2c6ee8322938a27d0c87b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/29/2018
ms.locfileid: "37104479"
---
# <a name="designing-and-developing-multi-container-and-microservice-based-net-applications"></a><span data-ttu-id="0ff97-103">複数のコンテナーとマイクロサービス ベースの NET アプリケーションのデザインと開発</span><span class="sxs-lookup"><span data-stu-id="0ff97-103">Designing and Developing Multi-Container and Microservice-Based .NET Applications</span></span>

<span data-ttu-id="0ff97-104">*コンテナー化されたマイクロサービス アプリケーションを開発しているということは、複数コンテナーのアプリケーションを構築しているということです。ただし、複数コンテナーのアプリケーションは、単純である可能性があり (3 層アプリケーションなど)、マイクロサービス アーキテクチャを使って構築されない場合があります。*</span><span class="sxs-lookup"><span data-stu-id="0ff97-104">*Developing containerized microservice applications means you are building multi-container applications. However, a multi-container application could also be simpler—for example, a three-tier application—and might not be built using a microservice architecture.*</span></span>

<span data-ttu-id="0ff97-105">以前に "マイクロサービス アーキテクチャを構築するときに Docker は必要か?" という疑問を提起しました。</span><span class="sxs-lookup"><span data-stu-id="0ff97-105">Earlier we raised the question “Is Docker necessary when building a microservice architecture?”</span></span> <span data-ttu-id="0ff97-106">その答えは、明らかに "いいえ" です。</span><span class="sxs-lookup"><span data-stu-id="0ff97-106">The answer is a clear no.</span></span> <span data-ttu-id="0ff97-107">Docker は拡張機能であり、大きな利点を提供できますが、コンテナーおよび Docker はマイクロサービスのハード要件ではありません。</span><span class="sxs-lookup"><span data-stu-id="0ff97-107">Docker is an enabler and can provide significant benefits, but containers and Docker are not a hard requirement for microservices.</span></span> <span data-ttu-id="0ff97-108">たとえば、簡単なプロセスまたは Docker コンテナーとして実行されているマイクロサービスをサポートする、Azure Service Fabric を使用している場合、Docker の有無にかかわらず、マイクロサービス ベースのアプリケーションを作成できます。</span><span class="sxs-lookup"><span data-stu-id="0ff97-108">As an example, you could create a microservices-based application with or without Docker when using Azure Service Fabric, which supports microservices running as simple processes or as Docker containers.</span></span>

<span data-ttu-id="0ff97-109">ただし、Docker コンテナーにも基づくマイクロサービス ベースのアプリケーションをデザインおよび開発する方法を知っている場合、その他の単純なアプリケーション モデルをデザインおよび開発することができます。</span><span class="sxs-lookup"><span data-stu-id="0ff97-109">However, if you know how to design and develop a microservices-based application that is also based on Docker containers, you will be able to design and develop any other, simpler application model.</span></span> <span data-ttu-id="0ff97-110">たとえば、複数コンテナーの手法も必要とする、3 層のアプリケーションをデザインする可能性があります。</span><span class="sxs-lookup"><span data-stu-id="0ff97-110">For example, you might design a three-tier application that also requires a multi-container approach.</span></span> <span data-ttu-id="0ff97-111">そのために、また、マイクロサービス アーキテクチャはコンテナーの世界で重要なトレンドであるため、このセクションでは、Docker コンテナーを使用するマイクロサービス アーキテクチャの実装に注目します。</span><span class="sxs-lookup"><span data-stu-id="0ff97-111">Because of that, and because microservice architectures are an important trend within the container world, this section focuses on a microservice architecture implementation using Docker containers.</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="0ff97-112">[前へ](../containerize-net-framework-applications/index.md)
[次へ](microservice-application-design.md)</span><span class="sxs-lookup"><span data-stu-id="0ff97-112">[Previous](../containerize-net-framework-applications/index.md)
[Next](microservice-application-design.md)</span></span>
