---
title: "方法: WebRequest を使用してカスタム プロトコルを登録する"
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
ms.assetid: 98ddbdb9-66b1-4080-92ad-51f5c447fcf8
caps.latest.revision: "11"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 4fdb1188aeb7fd754ab21a268070830f55347441
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-register-a-custom-protocol-using-webrequest"></a><span data-ttu-id="6fd64-102">方法: WebRequest を使用してカスタム プロトコルを登録する</span><span class="sxs-lookup"><span data-stu-id="6fd64-102">How to: Register a Custom Protocol Using WebRequest</span></span>
<span data-ttu-id="6fd64-103">この例では、他の場所で定義されているプロトコル固有のクラスを登録する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="6fd64-103">This example shows how to register a protocol specific classthat is defined elsewhere.</span></span> <span data-ttu-id="6fd64-104">この例では、`CustomWebRequestCreator` は、`CustomWebRequest` オブジェクトを返す **Create** メソッドを実装するユーザー実装のオブジェクトです。</span><span class="sxs-lookup"><span data-stu-id="6fd64-104">In this example, `CustomWebRequestCreator` is the user-implemented object that implements the **Create** method that returns the `CustomWebRequest` object.</span></span> <span data-ttu-id="6fd64-105">このコード例では、カスタム プロトコルを実装する `CustomWebRequest` コードが既に作成されているものとします。</span><span class="sxs-lookup"><span data-stu-id="6fd64-105">The code example assumes that you have written the `CustomWebRequest` code that implements the custom protocol.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6fd64-106">例</span><span class="sxs-lookup"><span data-stu-id="6fd64-106">Example</span></span>  
  
```csharp  
WebRequest.RegisterPrefix("custom", new CustomWebRequestCreator());  
WebRequest req = WebRequest.Create("custom://customHost.contoso.com/");  
```  
  
```vb  
WebRequest.RegisterPrefix("custom", New CustomWebRequestCreator())  
Dim req As WebRequest = WebRequest.Create("custom://customHost.contoso.com/")  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="6fd64-107">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="6fd64-107">Compiling the Code</span></span>  
 <span data-ttu-id="6fd64-108">この例で必要な要素は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="6fd64-108">This example requires:</span></span>  
  
 <span data-ttu-id="6fd64-109"><xref:System.Net> 名前空間への参照。</span><span class="sxs-lookup"><span data-stu-id="6fd64-109">References to the <xref:System.Net> namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6fd64-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="6fd64-110">See Also</span></span>  
 [<span data-ttu-id="6fd64-111">プラグ可能なプロトコルのプログラミング</span><span class="sxs-lookup"><span data-stu-id="6fd64-111">Programming Pluggable Protocols</span></span>](../../../docs/framework/network-programming/programming-pluggable-protocols.md)
