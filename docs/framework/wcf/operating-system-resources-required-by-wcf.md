---
title: "WCF に必要なオペレーティング システム リソース"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cdd9a331-53fe-4e0d-bdfe-782264aec5c9
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 6cfe114e5e044a6aaa1e356194a46b4a46011aa0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="operating-system-resources-required-by-wcf"></a><span data-ttu-id="04479-102">WCF に必要なオペレーティング システム リソース</span><span class="sxs-lookup"><span data-stu-id="04479-102">Operating System Resources Required by WCF</span></span>
[!INCLUDE[indigo1](../../../includes/indigo1-md.md)]<span data-ttu-id="04479-103"> は、オペレーティング システムで提供される複数のリソースに基づいて機能します。</span><span class="sxs-lookup"><span data-stu-id="04479-103"> depends on several resources that are provided by the operating system to function.</span></span> <span data-ttu-id="04479-104">このリソースを次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="04479-104">The following table lists those resources.</span></span>  
  
|<span data-ttu-id="04479-105">リソース</span><span class="sxs-lookup"><span data-stu-id="04479-105">Resource</span></span>|<span data-ttu-id="04479-106">説明</span><span class="sxs-lookup"><span data-stu-id="04479-106">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="04479-107">Microsoft 分散トランザクション コーディネーター (MSDTC)</span><span class="sxs-lookup"><span data-stu-id="04479-107">Microsoft Distributed Transaction Coordinator (MSDTC)</span></span>|<span data-ttu-id="04479-108">OleTx トランザクションをサポートするために必要です。</span><span class="sxs-lookup"><span data-stu-id="04479-108">Required to support OleTx transactions.</span></span>|  
|<span data-ttu-id="04479-109">インターネット インフォメーション サービス (IIS)</span><span class="sxs-lookup"><span data-stu-id="04479-109">Internet Information Services (IIS)</span></span>|<span data-ttu-id="04479-110">IIS を使用してアプリケーションをホストする場合に必要です。</span><span class="sxs-lookup"><span data-stu-id="04479-110">Required if you want to use IIS to host your application.</span></span>|  
|<span data-ttu-id="04479-111">Windows プロセス アクティブ化サービス (WAS)</span><span class="sxs-lookup"><span data-stu-id="04479-111">Windows Process Activation Service (WAS)</span></span>|<span data-ttu-id="04479-112">WAS を使用してアプリケーションをホストする場合に必要です。</span><span class="sxs-lookup"><span data-stu-id="04479-112">Required if you want to use WAS to host your application.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="04479-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="04479-113">See Also</span></span>  
 [<span data-ttu-id="04479-114">システム要件</span><span class="sxs-lookup"><span data-stu-id="04479-114">System Requirements</span></span>](../../../docs/framework/wcf/wcf-system-requirements.md)
