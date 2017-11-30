---
title: "方法 : 承認中にメタデータ要求を許可する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: allowing metadata requests while authorizing [WCF]
ms.assetid: 90cec34f-b619-452b-a056-8b1c0de49d05
caps.latest.revision: "9"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 103aba5118810064c1cafb7c82634ef000ced667
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-allow-metadata-requests-while-authorizing"></a>方法 : 承認中にメタデータ要求を許可する
カスタム承認中に、メタデータの処理要求を許可することがあります。 ここでは、このような要求を検証する手順を示します。  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)][!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]承認を参照してください[承認](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md)です。  
  
### <a name="to-allow-metadata-requests-during-authorization"></a>承認中にメタデータ要求を許可するには  
  
1.  <xref:System.ServiceModel.ServiceAuthorizationManager> クラスの拡張を作成します。  
  
2.  <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> メソッドをオーバーライドします。 このメソッドは、承認が許可されるかどうかによって、`true` または `false` を返します。 現在のプロシージャに関する情報は、メソッドへのパラメーターとして渡される <xref:System.ServiceModel.OperationContext> にあります。  
  
3.  オーバーライドで、コントラクト名、名前空間、およびアクションを確認します。次の例を参照してください。 条件が有効な場合は、`true.` を返します。  
  
4.  クラスを使用するための拡張ポイントを使用します。 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][する方法: サービスのカスタム承認マネージャーを作成する](../../../../docs/framework/wcf/extending/how-to-create-a-custom-authorization-manager-for-a-service.md)です。  
  
## <a name="example"></a>例  
 <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> メソッドのオーバーライドを次の例に示します。  
  
 [!code-csharp[C_HowtoCheckForMexRequestsInAuthorization#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtocheckformexrequestsinauthorization/cs/source.cs#1)]
 [!code-vb[C_HowtoCheckForMexRequestsInAuthorization#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtocheckformexrequestsinauthorization/vb/source.vb#1)]  
  
## <a name="see-also"></a>関連項目  
 <xref:System.ServiceModel.ServiceAuthorizationManager>  
 [承認](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md)  
 [クレームと Id モデルによる承認の管理](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)
