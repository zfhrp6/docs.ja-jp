---
title: "電子署名の暗号化"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- encryption of digital signatures [WCF]
- digital signatures [WCF], encryption
- digital signatures [WCF]
ms.assetid: 0868866d-40b4-4341-8e42-eee3b7f15b69
caps.latest.revision: "9"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 147f62a895983557267d0a18fdd1ea261ae6c855
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="encryption-of-digital-signatures"></a>電子署名の暗号化
既定では、メッセージは署名および暗号化され、署名はデジタル暗号化されます。 これは、<xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement> または <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> のインスタンスを使用してカスタム バインディングを作成し、いずれかのクラスの `MessageProtectionOrder` プロパティを <xref:System.ServiceModel.Security.MessageProtectionOrder> 列挙値に設定することによって制御できます。 既定値は、<xref:System.ServiceModel.Security.MessageProtectionOrder.SignBeforeEncryptAndEncryptSignature> です。 このプロセスは、単に署名して暗号化する場合よりも時間が 10 ～ 40 % 長くかかります。 ただし、署名の暗号化を無効にすると、攻撃者がメッセージの内容を予想できるようになる恐れがあります。 その理由は、メッセージ内のすべての署名部分のプレーン テキストのハッシュ コードが署名要素に含まれるからです。 たとえば、メッセージ本体は既定で暗号化されますが、暗号化されていない署名には、メッセージ本体のハッシュ コードが含まれます。 メッセージが短い場合は、攻撃者に内容を推測されてしまうおそれがあります。 署名を暗号化すると、このような危険性が低減または解消されます。  
  
 そのため、署名の暗号化を無効にするのは、セキュリティに影響しない大型のバイナリ ファイルを送信する場合などの、内容の重要性が低く、パフォーマンスの向上が重要な場合に限定してください。  
  
### <a name="to-disable-digital-signing"></a>デジタル署名を無効にするには  
  
1.  <xref:System.ServiceModel.Channels.CustomBinding> を作成します。 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][する方法: SecurityBindingElement を使用してカスタム バインディングを作成する](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)です。  
  
2.  <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement> または <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> をバインディング コレクションに追加します。  
  
3.  <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement.MessageProtectionOrder%2A?displayProperty=nameWithType> プロパティを <xref:System.ServiceModel.Security.MessageProtectionOrder.SignBeforeEncrypt> に設定するか、または <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement.MessageProtectionOrder%2A?displayProperty=nameWithType> プロパティを <xref:System.ServiceModel.Security.MessageProtectionOrder.SignBeforeEncrypt> に設定します。  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]カスタム バインディングを作成するを参照してください[ユーザー定義バインディング](../../../../docs/framework/wcf/extending/creating-user-defined-bindings.md)です。 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]特定の認証モード用のカスタム バインドを作成するを参照してください[する方法: 指定された認証モードでは、SecurityBindingElement を作成する](../../../../docs/framework/wcf/feature-details/how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md)です。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.ServiceModel.Security.MessageProtectionOrder>  
 <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>  
 <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>  
 [方法: SecurityBindingElement を使用してカスタム バインディングを作成します。](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)  
 [ユーザー定義のバインディングを作成します。](../../../../docs/framework/wcf/extending/creating-user-defined-bindings.md)  
 [方法: 指定された認証モード用の SecurityBindingElement を作成](../../../../docs/framework/wcf/feature-details/how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md)
