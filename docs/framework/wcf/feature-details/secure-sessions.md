---
title: "セキュリティで保護されたセッション"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7b50602f-d7b5-42e9-8e92-1f0413df0d8b
caps.latest.revision: "14"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 724ea72c52296c448ead80a8f357235d625f5842
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="secure-sessions"></a>セキュリティで保護されたセッション
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] の機能の 1 つに、送信された順序でメッセージが受信されることを保証する "信頼できるセッション" があります。 このセクションの各トピックでは、信頼できるセッションを作成する際に考慮する必要のあるセキュリティへの影響について説明します。 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]信頼できるセッションを参照してください[セッションを使用した](../../../../docs/framework/wcf/using-sessions.md)です。  
  
> [!NOTE]
>  Windows XP で偽装が必要な場合は、ステートフルなセキュリティ コンテキスト トークン (SCT: Security Context Token) を使用しない、セキュリティで保護されたセッションを使用します。 ステートフル SCT が偽装と共に使用されると、<xref:System.InvalidOperationException> がスローされます。 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][サポートされていないシナリオ](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md)です。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
|||  
|-|-|  
|[メッセージ交換とセッションをセキュリティで保護](../../../../docs/framework/wcf/feature-details/secure-conversations-and-secure-sessions.md)|セキュリティで保護されたメッセージ交換とセキュリティで保護されたセッションは、同じ意味で使用されます。 ここでは、セキュリティで保護されたメッセージ交換のしくみ、およびこのパターンを使用する状況と理由について説明します。|  
|[方法: セキュリティで保護されたセッションを作成します。](../../../../docs/framework/wcf/feature-details/how-to-create-a-secure-session.md)|セキュリティで保護されたセッションの基本的な作成手順を説明するチュートリアルです。|  
|[方法: セキュリティ コンテキストを作成、セキュリティで保護されたセッションのトークン](../../../../docs/framework/wcf/feature-details/how-to-create-a-security-context-token-for-a-secure-session.md)|クライアントの状態とセッションを保持する Web ファームを作成する手順について説明します。|  
|[セキュリティで保護されたセッションに関する考慮事項](../../../../docs/framework/wcf/feature-details/security-considerations-for-secure-sessions.md)|セキュリティで保護されたセッションに関する特別な考慮事項について説明します。|  
  
## <a name="reference"></a>参照  
 <xref:System.ServiceModel>  
  
 <xref:System.ServiceModel.Channels>  
  
## <a name="related-sections"></a>関連項目  
 [セッション、インスタンス化、および同時実行](../../../../docs/framework/wcf/feature-details/sessions-instancing-and-concurrency.md)  
  
 [サービスの設計と実装](../../../../docs/framework/wcf/designing-and-implementing-services.md)  
  
## <a name="see-also"></a>関連項目  
 [方法: メッセージ リプレイ検出を有効にします。](../../../../docs/framework/wcf/feature-details/how-to-enable-message-replay-detection.md)  
 [リプレイ攻撃](../../../../docs/framework/wcf/feature-details/replay-attacks.md)  
 [方法: セッションを必要とするサービスを作成します。](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-that-requires-sessions.md)
