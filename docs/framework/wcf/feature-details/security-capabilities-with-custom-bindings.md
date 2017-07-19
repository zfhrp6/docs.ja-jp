---
title: "カスタム バインディングを使用したセキュリティ機能 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a2425679-484a-4e6c-9c98-7da7304f1516
caps.latest.revision: 11
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 11
---
# カスタム バインディングを使用したセキュリティ機能
一般的なセキュリティ タスクのほとんどは、システム指定のバインディングのいずれかを使用して実行できます。ただし、より高度な制御が必要な場合は、以下のトピックで説明するように、<xref:System.ServiceModel.Channels.SecurityBindingElement> を使用してカスタム バインディングを作成できます。カスタム バインディング[!INCLUDE[crabout](../../../../includes/crabout-md.md)]、「[カスタム バインディング](../../../../docs/framework/wcf/extending/custom-bindings.md)」を参照してください。  
  
## このセクションの内容  
 [SecurityBindingElement 認証モード](../../../../docs/framework/wcf/feature-details/securitybindingelement-authentication-modes.md)  
 カスタム バインディングで使用できる認証モードについて説明します。  
  
 [方法 : SecurityBindingElement を使用してカスタム バインディングを作成する](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)  
 セキュリティ要素を使用してカスタム バインディングを作成するための基本手順について説明します。  
  
 [方法 : 指定した認証モード用の SecurityBindingElement を作成する](../../../../docs/framework/wcf/feature-details/how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md)  
 指定した認証モード用のセキュリティ要素を作成する方法について説明します。  
  
 [方法 : WSFederationHttpBinding のセキュリティで保護されたセッションを無効にする](../../../../docs/framework/wcf/feature-details/how-to-disable-secure-sessions-on-a-wsfederationhttpbinding.md)  
 フェデレーション サービスを作成する際に、セキュリティで保護されたセッションを無効にする方法について説明します。  
  
 [方法 : メッセージ リプレイ検出を有効にする](../../../../docs/framework/wcf/feature-details/how-to-enable-message-replay-detection.md)  
 リプレイ攻撃の発生を確認する方法について説明します。  
  
 [方法 : サポート資格情報を作成する](../../../../docs/framework/wcf/feature-details/how-to-create-a-supporting-credential.md)  
 必要な場合に、サービスにサポート資格情報を提供する方法について説明します。  
  
 [方法 : 署名確認を設定する](../../../../docs/framework/wcf/feature-details/how-to-set-up-a-signature-confirmation.md)  
 メッセージにデジタル署名する際に署名を確認する手順について説明します。  
  
 [方法 : 時刻のずれの最大値を設定する](../../../../docs/framework/wcf/feature-details/how-to-set-a-max-clock-skew.md)  
 サービスとクライアント間で許容される最大の時刻のずれを設定する方法について説明します。  
  
 [方法 : デジタル署名の暗号化を無効にする](../../../../docs/framework/wcf/feature-details/how-to-disable-encryption-of-digital-signatures.md)  
 デジタル署名の暗号化を無効にするとどのようなパフォーマンス上の利点があるかを説明します。  
  
## 関連項目  
 <xref:System.ServiceModel.Channels.SecurityBindingElement>  
  
 [\<security\>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)  
  
## 関連項目  
 [保護レベルの理解](../../../../docs/framework/wcf/understanding-protection-level.md)  
  
 [サービスおよびクライアントのセキュリティ保護](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
  
## 参照  
 [バインディングとセキュリティ](../../../../docs/framework/wcf/feature-details/bindings-and-security.md)   
 [セキュリティの概要](../../../../docs/framework/wcf/feature-details/security-overview.md)   
 [システム標準のバインディング](../../../../docs/framework/wcf/system-provided-bindings.md)