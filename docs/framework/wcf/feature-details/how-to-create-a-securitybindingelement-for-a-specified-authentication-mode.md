---
title: "方法 : 指定した認証モード用の SecurityBindingElement を作成する"
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
ms.assetid: a7c7747a-5b8c-463f-8493-7266dac75066
caps.latest.revision: "9"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 658eaf3469e0be179c78d9963687e6de9cb7fc00
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-securitybindingelement-for-a-specified-authentication-mode"></a>方法 : 指定した認証モード用の SecurityBindingElement を作成する
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] には、クライアントとサービスが互いに認証するためのモードが複数あります。 これらの認証モード用のセキュリティ バインド要素は、次の例のように、<xref:System.ServiceModel.Channels.SecurityBindingElement> クラスの静的メソッドまたは構成を使用して作成できます。  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]18 の認証モードを参照してください[SecurityBindingElement 認証モード](../../../../docs/framework/wcf/feature-details/securitybindingelement-authentication-modes.md)です。  
  
## <a name="example"></a>例  
 次のコード例では、複数の認証モードのバインディングを作成するメソッドを示します。  
  
> [!NOTE]
>  <xref:System.ServiceModel.Channels.SecurityBindingElement> オブジェクトのインスタンスが一度作成されると、<xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters.KeyType%2A> や <xref:System.ServiceModel.Channels.SecurityBindingElement.MessageSecurityVersion%2A> などの多数のプロパティは変更できなくなります。 これらのプロパティで `set` を呼び出しても変更されません。  
  
 [!code-csharp[c_CustomBindingsAuthMode#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombindingsauthmode/cs/source.cs#2)]
 [!code-vb[c_CustomBindingsAuthMode#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_custombindingsauthmode/vb/source.vb#2)]  
  
## <a name="see-also"></a>関連項目  
 [SecurityBindingElement 認証モード](../../../../docs/framework/wcf/feature-details/securitybindingelement-authentication-modes.md)  
 [方法: SecurityBindingElement を使用してカスタム バインディングを作成します。](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
