---
title: WCF に必要なオペレーティング システム リソース
ms.date: 03/30/2017
ms.assetid: cdd9a331-53fe-4e0d-bdfe-782264aec5c9
ms.openlocfilehash: 4522f1c59c8f74281a0e197338c6206ab29c229b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33498645"
---
# <a name="operating-system-resources-required-by-wcf"></a><span data-ttu-id="f6e4f-102">WCF に必要なオペレーティング システム リソース</span><span class="sxs-lookup"><span data-stu-id="f6e4f-102">Operating System Resources Required by WCF</span></span>
<span data-ttu-id="f6e4f-103">Windows Communication Foundation (WCF) は、関数に、オペレーティング システムによって提供されているいくつかのリソースに依存します。</span><span class="sxs-lookup"><span data-stu-id="f6e4f-103">Windows Communication Foundation (WCF) depends on several resources that are provided by the operating system to function.</span></span> <span data-ttu-id="f6e4f-104">このリソースを次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="f6e4f-104">The following table lists those resources.</span></span>  
  
|<span data-ttu-id="f6e4f-105">リソース</span><span class="sxs-lookup"><span data-stu-id="f6e4f-105">Resource</span></span>|<span data-ttu-id="f6e4f-106">説明</span><span class="sxs-lookup"><span data-stu-id="f6e4f-106">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="f6e4f-107">Microsoft 分散トランザクション コーディネーター (MSDTC)</span><span class="sxs-lookup"><span data-stu-id="f6e4f-107">Microsoft Distributed Transaction Coordinator (MSDTC)</span></span>|<span data-ttu-id="f6e4f-108">OleTx トランザクションをサポートするために必要です。</span><span class="sxs-lookup"><span data-stu-id="f6e4f-108">Required to support OleTx transactions.</span></span>|  
|<span data-ttu-id="f6e4f-109">インターネット インフォメーション サービス (IIS)</span><span class="sxs-lookup"><span data-stu-id="f6e4f-109">Internet Information Services (IIS)</span></span>|<span data-ttu-id="f6e4f-110">IIS を使用してアプリケーションをホストする場合に必要です。</span><span class="sxs-lookup"><span data-stu-id="f6e4f-110">Required if you want to use IIS to host your application.</span></span>|  
|<span data-ttu-id="f6e4f-111">Windows プロセス アクティブ化サービス (WAS)</span><span class="sxs-lookup"><span data-stu-id="f6e4f-111">Windows Process Activation Service (WAS)</span></span>|<span data-ttu-id="f6e4f-112">WAS を使用してアプリケーションをホストする場合に必要です。</span><span class="sxs-lookup"><span data-stu-id="f6e4f-112">Required if you want to use WAS to host your application.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f6e4f-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="f6e4f-113">See Also</span></span>  
 [<span data-ttu-id="f6e4f-114">システム要件</span><span class="sxs-lookup"><span data-stu-id="f6e4f-114">System Requirements</span></span>](../../../docs/framework/wcf/wcf-system-requirements.md)
