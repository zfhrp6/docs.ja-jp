---
title: "WCF サービスが Web ファームでホストされている場合のリプレイ攻撃の回避 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1c2ed695-7a31-4257-92bd-9e9731b886a5
caps.latest.revision: 4
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 4
---
# WCF サービスが Web ファームでホストされている場合のリプレイ攻撃の回避
メッセージ セキュリティ WCF の使用により、受信メッセージから NONCE を作成し、生成された NONCE が内部 `InMemoryNonceCache` にあるかどうかを確認することで、リプレイ攻撃が防止される場合。そうである場合、メッセージはリプレイとして破棄されます。WCF サービスが Web ファームでホストされている場合、`InMemoryNonceCache` は Web ファームのノード間で共有されていないため、サービスはリプレイ攻撃に対して脆弱です。このシナリオの危険性を軽減するために、WCF 4.5 では抽象クラス <xref:System.ServiceModel.Security.NoneCache> からクラスを派生させることによって独自の共有 NONCE キャッシュを実装できるようにする機能拡張ポイントを提供しています。  
  
## NoneCache の実装  
 独自の共有 NONCE キャッシュを実装するには、<xref:System.ServiceModel.Security.NoneCache> からクラスを派生させ、[M:System.ServiceModel.Security.NoneCache.CheckNonce\(System.Byte\<xref:System.ServiceModel.Security.NoneCache.CheckNonce%2A> メソッドと [M:System.ServiceModel.Security.NoneCache.TryAddNonce\(System.Byte\<xref:System.ServiceModel.Security.NoneCache.TryAddNonce%2A> メソッドをオーバーライドします。[M:System.ServiceModel.Security.NoneCache.CheckNonce\(System.Byte\<xref:System.ServiceModel.Security.NoneCache.CheckNonce%2A> は、指定された NONCE がキャッシュに存在するかどうかを確認します。[M:System.ServiceModel.Security.NoneCache.TryAddNonce\(System.Byte\<xref:System.ServiceModel.Security.NoneCache.TryAddNonce%2A> は NONCE をキャッシュに追加しようとします。クラスを実装したら、インスタンスを作成して、それをクライアント側でのリプレイ検出用には <xref:System.ServiceModel.Channels.SecurityBindingElement.LocalClientSecuritySettings.NonceCache%2A>、サーバー側でのリプレイ検出用には <xref:System.ServiceModel.Channels.SecurityBindingElement.LocalServiceSecuritySettings.NonceCache%2A> に割り当てて準備します。この機能のためにすぐに使用できる構成サポートはありません。  
  
## 参照  
 [メッセージのセキュリティ](../../../../docs/framework/wcf/feature-details/message-security-in-wcf.md)   
 [SymmetricSecurityBindingElement](../../../../docs/framework/wcf/diagnostics/wmi/symmetricsecuritybindingelement.md)