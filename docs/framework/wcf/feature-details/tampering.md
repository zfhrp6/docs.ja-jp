---
title: "改変 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3bad93be-60bb-4f89-96ab-a1c3dc7c0fad
caps.latest.revision: 6
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# 改変
*改変*は、メッセージまたはメッセージの配信を変更し、意図された以外の目的のために、変更したメッセージを使用する行為です。  
  
## WS\-Addressing を無効にしない  
 WS\-Addressing の仕様では、各メッセージにアドレス ヘッダーが提供されるため、メッセージの受信者はメッセージの送信者を検証できます。この機能を無効にするには、<xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> プロパティを <xref:System.ServiceModel.Channels.AddressingVersion.None%2A> に設定します。  
  
 セキュリティ モードが Message に設定された状態で、WS\-Addressing が無効になっていると、攻撃者がクライアントから要求を取得して、これを別のサービスに送信した場合、要求を受信したサービスは、このメッセージが元のクライアントから送信されたことを検出できません。事実上、最初のサービスは、2 番目のサービスと対話するときに、自分をクライアントと偽ることができます。  
  
 これを防ぐには、<xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> プロパティを絶対に <xref:System.ServiceModel.Channels.AddressingVersion.None%2A> に設定しないようにし、静的 <xref:System.ServiceModel.Channels.MessageVersion.Soap12%2A> プロパティのように、<xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> プロパティを <xref:System.ServiceModel.Channels.AddressingVersion.None%2A> に設定する <xref:System.ServiceModel.Channels.MessageVersion> の使用を避けます。  
  
## 参照  
 [セキュリティの考慮事項](../../../../docs/framework/wcf/feature-details/security-considerations-in-wcf.md)   
 [情報の漏えい](../../../../docs/framework/wcf/feature-details/information-disclosure.md)   
 [権限の昇格](../../../../docs/framework/wcf/feature-details/elevation-of-privilege.md)   
 [サービス拒否](../../../../docs/framework/wcf/feature-details/denial-of-service.md)   
 [サポートされていないシナリオ](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md)   
 [リプレイ攻撃](../../../../docs/framework/wcf/feature-details/replay-attacks.md)