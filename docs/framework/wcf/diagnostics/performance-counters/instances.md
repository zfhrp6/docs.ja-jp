---
title: "インスタンス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c8cf3460-0ca1-4411-8262-e9ecaf7f0a31
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7ed0c4a6f13ddcafdb3a9a773be9cd3f017474ec
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="instances"></a>インスタンス
カウンター名 : インスタンス  
  
## <a name="description"></a>説明  
 現在サービスに含まれているインスタンス コンテキストの数。  
  
 多くの場合、インスタンス コンテキストの数とインスタンスの数は同じです。 ただし、次のシナリオではこの規則は当てはまりません。  
  
-   サービス メソッドが <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%2A> メソッドを明示的に呼び出している場合。  
  
-   <xref:System.ServiceModel.ReleaseInstanceMode> が <xref:System.ServiceModel.OperationBehaviorAttribute> インスタンスに適用されている場合。  
  
## <a name="see-also"></a>参照  
 <xref:System.ServiceModel.OperationBehaviorAttribute>
