---
title: インスタンス
ms.date: 03/30/2017
ms.assetid: c8cf3460-0ca1-4411-8262-e9ecaf7f0a31
ms.openlocfilehash: a95acf8e775e0802dc0ed781c562fa6373995a70
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33473043"
---
# <a name="instances"></a>インスタンス
カウンター名 : インスタンス  
  
## <a name="description"></a>説明  
 現在サービスに含まれているインスタンス コンテキストの数。  
  
 多くの場合、インスタンス コンテキストの数とインスタンスの数は同じです。 ただし、次のシナリオではこの規則は当てはまりません。  
  
-   サービス メソッドが <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%2A> メソッドを明示的に呼び出している場合。  
  
-   <xref:System.ServiceModel.ReleaseInstanceMode> が <xref:System.ServiceModel.OperationBehaviorAttribute> インスタンスに適用されている場合。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.ServiceModel.OperationBehaviorAttribute>
