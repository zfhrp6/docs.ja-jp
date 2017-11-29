---
title: "方法: WebRequest に一致するプロトコル固有の WebResponse を取得する"
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
ms.assetid: d8c90785-f16b-42a5-8439-ed2f731b2ba8
caps.latest.revision: "8"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: cbf6b6eab3502f8f04f33f6f11d5d071e3406a7a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-retrieve-a-protocol-specific-webresponse-that-matches-a-webrequest"></a><span data-ttu-id="d44ed-102">方法: WebRequest に一致するプロトコル固有の WebResponse を取得する</span><span class="sxs-lookup"><span data-stu-id="d44ed-102">How to: Retrieve a Protocol-Specific WebResponse that Matches a WebRequest</span></span>
<span data-ttu-id="d44ed-103">この例では、WebRequest に一致するプロトコル固有の WebResponse を取得する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="d44ed-103">This example shows how to retrieve a protocol-specific WebResponse that matches a WebRequest.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d44ed-104">例</span><span class="sxs-lookup"><span data-stu-id="d44ed-104">Example</span></span>  
  
```csharp  
WebRequest req = WebRequest.Create("http://www.contoso.com/");  
WebResponse resp = req.GetResponse();  
```  
  
```vb  
Dim req As WebRequest = WebRequest.Create("http://www.contoso.com")  
Dim resp As WebResponse = req.GetResponse()  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="d44ed-105">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="d44ed-105">Compiling the Code</span></span>  
 <span data-ttu-id="d44ed-106">この例で必要な要素は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="d44ed-106">This example requires:</span></span>  
  
-   <span data-ttu-id="d44ed-107">**System.Net** 名前空間の参照。</span><span class="sxs-lookup"><span data-stu-id="d44ed-107">References to the **System.Net** namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d44ed-108">関連項目</span><span class="sxs-lookup"><span data-stu-id="d44ed-108">See Also</span></span>  
 [<span data-ttu-id="d44ed-109">データの要求</span><span class="sxs-lookup"><span data-stu-id="d44ed-109">Requesting Data</span></span>](../../../docs/framework/network-programming/requesting-data.md)
