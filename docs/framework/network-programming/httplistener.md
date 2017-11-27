---
title: HttpListener
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: HTTP
ms.assetid: 5b89d3fb-3c9a-49e2-af1f-c34c020c68ac
caps.latest.revision: "9"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: ca0a22ff1d06485658da75a46bd408a12a3a964c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="httplistener"></a><span data-ttu-id="7376c-102">HttpListener</span><span class="sxs-lookup"><span data-stu-id="7376c-102">HttpListener</span></span>
<span data-ttu-id="7376c-103"><xref:System.Net.HttpListener> クラスは、プログラムによって制御できる HTTP プロトコル リスナーを提供します。</span><span class="sxs-lookup"><span data-stu-id="7376c-103">The <xref:System.Net.HttpListener> class provides a programmatically controlled HTTP protocol listener.</span></span> <span data-ttu-id="7376c-104">リスナーは、<xref:System.Net.HttpListener> オブジェクトの有効期間にわたってアクティブで、アプリケーション内で実行されます。</span><span class="sxs-lookup"><span data-stu-id="7376c-104">The listener is active for the lifetime of the <xref:System.Net.HttpListener> object and runs within your application.</span></span>  
  
## <a name="httpsys"></a><span data-ttu-id="7376c-105">HTTP.SYS</span><span class="sxs-lookup"><span data-stu-id="7376c-105">HTTP.SYS</span></span>  
 <span data-ttu-id="7376c-106"><xref:System.Net.HttpListener> クラスは、Windows のすべての HTTP トラフィックを処理するカーネル モード リスナーである HTTP.sys の上に構築されています。</span><span class="sxs-lookup"><span data-stu-id="7376c-106">The <xref:System.Net.HttpListener> class is built on top of HTTP.sys, which is the kernel mode listener that handles all HTTP traffic for Windows.</span></span> <span data-ttu-id="7376c-107">HTTP.sys は、接続管理、帯域幅の調整、および Web サーバーのログ記録を提供します。</span><span class="sxs-lookup"><span data-stu-id="7376c-107">HTTP.sys provides connection management, bandwidth throttling, and Web server logging.</span></span> <span data-ttu-id="7376c-108">SSL 証明書の追加には `HttpCfg.exe` ツールを使用します。</span><span class="sxs-lookup"><span data-stu-id="7376c-108">Use the `HttpCfg.exe` tool to add SSL certificates.</span></span> <span data-ttu-id="7376c-109">詳細については、[サーバー](http://go.microsoft.com/fwlink/?LinkID=178285) ドキュメントで、[HttpCfg.exe](http://go.microsoft.com/fwlink/?LinkID=178284) ツールのドキュメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="7376c-109">For more information, see the documentation on the [HttpCfg.exe](http://go.microsoft.com/fwlink/?LinkID=178284) tool in the [Server](http://go.microsoft.com/fwlink/?LinkID=178285) documentation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7376c-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="7376c-110">See Also</span></span>  
 <xref:System.Net.HttpListener>  
 <xref:System.Net.HttpWebRequest>  
 <xref:System.Net.HttpWebResponse>  
 [<span data-ttu-id="7376c-111">HTTP サーバー</span><span class="sxs-lookup"><span data-stu-id="7376c-111">HTTP Server</span></span>](http://go.microsoft.com/fwlink/?LinkID=178285)  
 [<span data-ttu-id="7376c-112">インターネット インフォメーションにおけるセキュリティ強化</span><span class="sxs-lookup"><span data-stu-id="7376c-112">Security Enhancements in Internet Information</span></span>](http://go.microsoft.com/fwlink/?LinkID=178286)  
 [<span data-ttu-id="7376c-113">HttpListener ASPX ホスト アプリケーションのサンプル</span><span class="sxs-lookup"><span data-stu-id="7376c-113">HttpListener ASPX Host Application Sample</span></span>](http://go.microsoft.com/fwlink/?LinkID=179560)  
 [<span data-ttu-id="7376c-114">HttpListener テクノロジのサンプル</span><span class="sxs-lookup"><span data-stu-id="7376c-114">HttpListener Technology Sample</span></span>](http://go.microsoft.com/fwlink/?LinkID=179558)  
 [<span data-ttu-id="7376c-115">ネットワーク プログラミングのサンプル</span><span class="sxs-lookup"><span data-stu-id="7376c-115">Network Programming Samples</span></span>](../../../docs/framework/network-programming/network-programming-samples.md)
