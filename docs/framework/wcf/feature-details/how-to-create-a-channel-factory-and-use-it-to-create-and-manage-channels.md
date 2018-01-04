---
title: "方法 : チャネル ファクトリを作成および使用して、チャネルを作成および管理する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 018dcc30-9f61-419e-af8e-412a85e8d282
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d41dfc85df1b706028fd95465596a980c040d512
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-channel-factory-and-use-it-to-create-and-manage-channels"></a><span data-ttu-id="07d96-102">方法 : チャネル ファクトリを作成および使用して、チャネルを作成および管理する</span><span class="sxs-lookup"><span data-stu-id="07d96-102">How to: Create a Channel Factory and Use it to Create and Manage Channels</span></span>
<span data-ttu-id="07d96-103"><xref:System.ServiceModel.DuplexChannelFactory%601> クラスは、クライアントがサービス エンドポイントとの間でメッセージを送受信するために使用する、さまざまな種類の双方向チャネルを作成したり、管理したりする手段を提供します。</span><span class="sxs-lookup"><span data-stu-id="07d96-103">The <xref:System.ServiceModel.DuplexChannelFactory%601> class provides the means to create and manage duplex channels of different types that clients use to send and receive messages to and from service endpoints.</span></span>  
  
## <a name="example"></a><span data-ttu-id="07d96-104">例</span><span class="sxs-lookup"><span data-stu-id="07d96-104">Example</span></span>  
 <span data-ttu-id="07d96-105">次のコードは、チャネル ファクトリを作成および使用して、チャネルを作成および管理する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="07d96-105">The following code shows how to create a channel factory and use it to create and manage channels.</span></span>  
  
 [!code-csharp[S_CustomAuthentication#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_customauthentication/cs/instance.cs#1)]  
  
## <a name="see-also"></a><span data-ttu-id="07d96-106">参照</span><span class="sxs-lookup"><span data-stu-id="07d96-106">See Also</span></span>  
 <xref:System.ServiceModel.DuplexChannelFactory%601>
