---
title: "セキュリティ保護されたメッセージ交換とセッション | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 48cb104a-532d-40ae-aa57-769dae103fda
caps.latest.revision: 13
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 13
---
# セキュリティ保護されたメッセージ交換とセッション
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] の特徴の 1 つは、相互に認証を行い暗号化とデジタル署名のプロセスについて同意する、2 つのエンドポイント間でのセキュリティ保護されたセッションを確立する機能にあります。たとえば、サービス エンドポイントは、クライアント エンドポイントに対して認証のために X.509 証明書に基づいたセキュリティ トークンを送信するよう要求する場合があります。クライアントの認証が終わると、サービス エンドポイントはセキュリティ コンテキスト トークン \(SCT: Security Context Token\) をクライアントに返します。このセッションにおける後続のすべてのメッセージは、このセキュリティ トークンを使用してセキュリティ保護されます。セキュリティで保護されたセッションが確立されると、SCT には対称キーが含まれるため、2 つのエンドポイント間で交換される一連のメッセージの効率が向上します。X.509 証明書の基盤となる非対称キーでは、デジタル署名の生成やデータの暗号化を行う場合に、対称キーに比べて非常に大きな計算能力が必要になります。  
  
 [WS\-SecurityPolicy](http://go.microsoft.com/fwlink/?LinkId=99817) 標準の 6.2.7 節で定義されているブートストラップ ポリシーには、チャネルをセキュリティで保護し、クライアントを RST\/SCT および RSTR\/SCT 交換よりも前に認証するために使用されるメッセージ セキュリティ アサーションが含まれます。[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] の標準バインディングの中には、セキュリティで保護されたメッセージ交換を使用するかどうかを制御する `Security.Message.EstablishSecurityContext` プロパティを持つものがあります。カスタム バインディングを使用する場合、ブートストラップは、構成ファイル内の [\<secureConversationBootstrap\>](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md)、またはコードからの <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateSecureConversationBindingElement%2A>の呼び出しを介して、セキュリティ バインド要素を入れ子構造にすることによって示されます。  
  
 セッション[!INCLUDE[crabout](../../../../includes/crabout-md.md)]、「[セッションの使用](../../../../docs/framework/wcf/using-sessions.md)」を参照してください。  
  
## 参照  
 [セッション、インスタンス化、および同時実行](../../../../docs/framework/wcf/feature-details/sessions-instancing-and-concurrency.md)   
 [方法 : セッションを必要とするサービスを作成する](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-that-requires-sessions.md)