---
title: "信頼できるセッション | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "Windows Communication Foundation, sessions and instances"
  - "WCF, sessions and instances"
  - "sessions and instances [WCF]"
helpviewer_keywords: 
  - "インスタンス [WCF]"
  - "セッション [WCF]"
ms.assetid: 143951b3-3aa0-4540-b4b7-d33e77e874a1
caps.latest.revision: 15
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 15
---
# 信頼できるセッション
ここでは、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] の信頼できるセッションについて、その使用目的、使用方法と使用する状況、サポートするバインディング構成、およびベスト プラクティスの参照先について説明します。このセクションの重要なポイントと関連するトピックの詳細について、次の表にまとめます。  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] によって提供される信頼できるセッションでは、SOAP またはトランスポート中継局を経由してエンドポイント間で送信されるメッセージが 1 回だけ配信され、オプションとして送信時と同じ順序で配信されることが保証されます。  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] アプリケーションで信頼できるセッションを使用するには、既定またはオプションとして、信頼できるセッションをサポートする、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] のシステム提供のバインディングの 1 つを使用するか、または信頼できるセッションをサポートする独自のカスタム バインディングを作成します。  
  
## このセクションの内容  
 [信頼できるセッションの概要](../../../../docs/framework/wcf/feature-details/reliable-sessions-overview.md)  
 信頼できるセッションの概要、信頼できるセッションを使用する状況、信頼できるセッションをサポートする各種のバインディング、および動作のしくみについて説明します。  
  
 [方法 : 信頼されたセッション内のメッセージを変換する](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-within-a-reliable-session.md)  
 構成で指定したカスタム バインディングを使用して、HTTP 上で信頼できるセッションを作成する方法を説明します。  
  
 [方法 : 信頼できるセッション内でメッセージをセキュリティで保護する](../../../../docs/framework/wcf/feature-details/how-to-secure-messages-within-reliable-sessions.md)  
 信頼できるセッションを保護する方法について説明します。  
  
 [方法 : カスタムの信頼できるセッションによる HTTPS を使用したバインディングを作成する](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-reliable-session-binding-with-https.md)  
 HTTPS 上で信頼できるセッションを作成する方法について説明します。  
  
 [信頼できるセッションのベスト プラクティス](../../../../docs/framework/wcf/feature-details/best-practices-for-reliable-sessions.md)  
 信頼できるセッションの使用に関するベスト プラクティスについて説明します。  
  
## 関連項目  
 <xref:System.ServiceModel.ReliableSession>  
  
## 参照  
 [キューと信頼できるセッション](../../../../docs/framework/wcf/feature-details/queues-and-reliable-sessions.md)   
 [セッション、インスタンス化、および同時実行](../../../../docs/framework/wcf/feature-details/sessions-instancing-and-concurrency.md)