---
title: "方法: WebRequest でインターネットとの通信にプロキシを使用できるようにする"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 63c0ef2c-44b5-4c54-9804-ba0b9b001ac7
caps.latest.revision: "9"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 68871505e735485dd73d219b4144d56eabe21e43
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-enable-a-webrequest-to-use-a-proxy-to-communicate-with-the-internet"></a><span data-ttu-id="5fb45-102">方法: WebRequest でインターネットとの通信にプロキシを使用できるようにする</span><span class="sxs-lookup"><span data-stu-id="5fb45-102">How to: Enable a WebRequest to Use a Proxy to Communicate With the Internet</span></span>
<span data-ttu-id="5fb45-103">この例では、<xref:System.Net.WebRequest> でインターネットとの通信にプロキシを使用できるようにするグローバル プロキシ インスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="5fb45-103">This example creates a global proxy instance that will enable any <xref:System.Net.WebRequest> to use a proxy to communicate with the Internet.</span></span> <span data-ttu-id="5fb45-104">ここでは、プロキシ サーバーが `webproxy` という名前で、ポート 80 (標準 HTTP ポート) で通信を行うことを想定します。</span><span class="sxs-lookup"><span data-stu-id="5fb45-104">The example assumes that the proxy server is named `webproxy` and that it communicates on port 80, the standard HTTP port.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5fb45-105">例</span><span class="sxs-lookup"><span data-stu-id="5fb45-105">Example</span></span>  
  
```csharp  
WebProxy proxyObject = new WebProxy("http://webproxy:80/");  
GlobalProxySelection.Select = proxyObject;  
```  
  
```vb  
Dim proxyObject As WebProxy = New WebProxy("http://webproxy:80/")  
GlobalProxySelection.Select = proxyObject  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="5fb45-106">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="5fb45-106">Compiling the Code</span></span>  
 <span data-ttu-id="5fb45-107">この例で必要な要素は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="5fb45-107">This example requires:</span></span>  
  
-   <span data-ttu-id="5fb45-108">**System.Net** 名前空間への参照。</span><span class="sxs-lookup"><span data-stu-id="5fb45-108">References to the **System.Net** namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5fb45-109">参照</span><span class="sxs-lookup"><span data-stu-id="5fb45-109">See Also</span></span>  
 [<span data-ttu-id="5fb45-110">アプリケーション プロトコルの使用</span><span class="sxs-lookup"><span data-stu-id="5fb45-110">Using Application Protocols</span></span>](../../../docs/framework/network-programming/using-application-protocols.md)  
 [<span data-ttu-id="5fb45-111">プロキシを介したインターネットへのアクセス</span><span class="sxs-lookup"><span data-stu-id="5fb45-111">Accessing the Internet Through a Proxy</span></span>](../../../docs/framework/network-programming/accessing-the-internet-through-a-proxy.md)
