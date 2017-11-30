---
title: "改変"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3bad93be-60bb-4f89-96ab-a1c3dc7c0fad
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: d8852c4d19c48af2beee598f4ddfae7b775a025f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="tampering"></a>改変
*改ざん*は、メッセージまたはメッセージの配信を変更しの意図された以外の目的の変更後のメッセージを使用して動作します。  
  
## <a name="do-not-disable-ws-addressing"></a>WS-Addressing を無効にしない  
 WS-Addressing の仕様では、各メッセージにアドレス ヘッダーが提供されるため、メッセージの受信者はメッセージの送信者を検証できます。 この機能を無効にするには、<xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> プロパティを <xref:System.ServiceModel.Channels.AddressingVersion.None%2A> に設定します。  
  
 セキュリティ モードが Message に設定された状態で、WS-Addressing が無効になっていると、攻撃者がクライアントから要求を取得して、これを別のサービスに送信した場合、要求を受信したサービスは、このメッセージが元のクライアントから送信されたことを検出できません。 事実上、最初のサービスは、2 番目のサービスと対話するときに、自分をクライアントと偽ることができます。  
  
 これを防ぐには、<xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> プロパティを絶対に <xref:System.ServiceModel.Channels.AddressingVersion.None%2A> に設定しないようにし、静的 <xref:System.ServiceModel.Channels.MessageVersion> プロパティのように、<xref:System.ServiceModel.Channels.MessageVersion.Soap12%2A> プロパティを <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> に設定する <xref:System.ServiceModel.Channels.AddressingVersion.None%2A> の使用を避けます。  
  
## <a name="see-also"></a>関連項目  
 [セキュリティに関する考慮事項](../../../../docs/framework/wcf/feature-details/security-considerations-in-wcf.md)  
 [情報漏えいが起こる](../../../../docs/framework/wcf/feature-details/information-disclosure.md)  
 [特権の昇格](../../../../docs/framework/wcf/feature-details/elevation-of-privilege.md)  
 [サービス拒否が起こる](../../../../docs/framework/wcf/feature-details/denial-of-service.md)  
 [サポートされていないシナリオ](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md)  
 [リプレイ攻撃](../../../../docs/framework/wcf/feature-details/replay-attacks.md)
