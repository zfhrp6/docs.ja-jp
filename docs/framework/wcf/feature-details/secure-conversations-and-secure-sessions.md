---
title: セキュリティ保護されたメッセージ交換とセッション
ms.date: 03/30/2017
ms.assetid: 48cb104a-532d-40ae-aa57-769dae103fda
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: c87f53bcaa167dd7b3b039c70129efca43742c1c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33497608"
---
# <a name="secure-conversations-and-secure-sessions"></a>セキュリティ保護されたメッセージ交換とセッション
Windows Communication Foundation (WCF) の機能は、相互に認証し、暗号化とデジタル署名のプロセスについて同意する 2 つのエンドポイント間でセキュリティで保護されたセッションを確立する機能です。 たとえば、サービス エンドポイントは、クライアント エンドポイントに対して認証のために X.509 証明書に基づいたセキュリティ トークンを送信するよう要求する場合があります。 クライアントの認証が終わると、サービス エンドポイントはセキュリティ コンテキスト トークン (SCT: Security Context Token) をクライアントに返します。このセッションにおける後続のすべてのメッセージは、このセキュリティ トークンを使用してセキュリティ保護されます。 セキュリティで保護されたセッションが確立されると、SCT には対称キーが含まれるため、2 つのエンドポイント間で交換される一連のメッセージの効率が向上します。 X.509 証明書の基盤となる非対称キーでは、デジタル署名の生成やデータの暗号化を行う場合に、対称キーに比べて非常に大きな計算能力が必要になります。  
  
 ブートス トラップのポリシー (の 6.2.7 セクションで定義されている、 [Ws-securitypolicy](http://go.microsoft.com/fwlink/?LinkId=99817)標準)、チャネルをセキュリティで保護し、/SCT RST および RSTR/SCT 交換する前にクライアントを認証するために使用するメッセージのセキュリティ アサーションを格納します。 特定の WCF は、標準バインディングが、`Security.Message.EstablishSecurityContext`プロパティを制御するかどうかメッセージ交換をセキュリティで保護を使用します。 カスタム バインドを使用してブートス トラップが使用するか、入れ子になったのセキュリティ バインド要素で示されます。 [ \<secureConversationBootstrap >](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md)または呼び出すことによって、構成ファイルで<xref:System.ServiceModel.Channels.SecurityBindingElement.CreateSecureConversationBindingElement%2A>のコードにします。  
  
 セッションの詳細については、次を参照してください。[セッションを使用した](../../../../docs/framework/wcf/using-sessions.md)です。  
  
## <a name="see-also"></a>関連項目  
 [セッション、インスタンス化、および同時実行](../../../../docs/framework/wcf/feature-details/sessions-instancing-and-concurrency.md)  
 [方法 : セッションを必要とするサービスを作成する](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-that-requires-sessions.md)
