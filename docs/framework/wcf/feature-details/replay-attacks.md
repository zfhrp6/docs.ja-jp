---
title: "リプレイ攻撃"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7a17e040-93cd-4432-81b9-9f62fec78c8f
caps.latest.revision: "10"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 81bca4572b6c4845674c63284f93c86fe5925bdf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="replay-attacks"></a>リプレイ攻撃
A*リプレイ攻撃*攻撃者は、2 つのパーティ間でメッセージのストリームをコピーし、1 つまたは複数のパーティのストリームをリプレイするときに発生します。 攻撃が和らげられていない場合、攻撃対象になったコンピューターはストリームを正当なメッセージとして処理するため、項目の順序が重複するなど、望ましくない状況に陥ります。  
  
## <a name="bindings-may-be-subject-to-reflection-attacks"></a>バインディングはリフレクション攻撃にさらされる可能性がある  
 *リフレクション攻撃*からの応答として受信機と送信者に返信されるメッセージのリプレイです。 標準*リプレイ検出*で、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]メカニズムが自動的に処理しないこれです。  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] のサービス モデルは、署名されたメッセージ ID を要求メッセージに追加し、署名された `relates-to` ヘッダーを応答メッセージに要求するため、既定でリフレクション攻撃が軽減されます。 その結果、要求メッセージを応答としてリプレイできません。 セキュリティで保護された信頼できるメッセージ (RM) シナリオでは、リフレクション攻撃は次の理由で軽減されます。  
  
-   シーケンス メッセージの作成スキーマとシーケンス応答メッセージの作成スキーマが異なります。  
  
-   一方向シーケンスの場合、クライアントから送信されたシーケンス メッセージをクライアントに対してリプレイすることはできません。これは、クライアントがこのようなメッセージを認識できないためです。  
  
-   双方向シーケンスの場合、2 つのシーケンス ID が一意である必要があります。 このため、送信シーケンス メッセージを受信シーケンス メッセージとしてリプレイできません (すべてのシーケンス ヘッダーと本文も署名されています)。  
  
 リフレクション攻撃の影響を受けやすい唯一のバインディングは WS-Addressing を使用しないバインディング (WS-Addressing を無効にして、対称キー ベースのセキュリティを使用するカスタム バインディング) です。 <xref:System.ServiceModel.BasicHttpBinding> は、既定では WS-Addressing を使用しませんが、この攻撃を受けやすい方法で対称キー ベースのセキュリティを使用することはありません。  
  
 カスタム バインディングに対する攻撃を軽減するには、セキュリティ コンテキストを確立しないか、WS-Addressing ヘッダーを要求します。  
  
## <a name="web-farm-attacker-replays-request-to-multiple-nodes"></a>Web ファーム : 攻撃者が複数のノードに対して要求をリプレイする  
 クライアントは、Web ファームに実装されているサービスを使用します。 攻撃者は、ファーム内の特定のノードに送信された要求を同じファーム内の別のノードに対してリプレイします。 また、サービスが再開されると、リプレイ キャッシュがフラッシュされ、攻撃者が要求をリプレイできるようになります  (このキャッシュには、以前使用されたメッセージ署名の値が格納されています。これにより、メッセージ署名は一度しか使用できないため、リプレイを防止できます。 リプレイ キャッシュは Web ファーム内で共有されません)。  
  
 回避事項を次に示します。  
  
-   ステートフルなセキュリティ コンテキスト トークンと共にメッセージ モード セキュリティを使用します (セキュリティで保護されたメッセージ交換を有効にするかどうかは任意)。 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][する方法: セキュリティ コンテキストを作成、セキュリティで保護されたセッションのトークン](../../../../docs/framework/wcf/feature-details/how-to-create-a-security-context-token-for-a-secure-session.md)です。  
  
-   トランスポート レベルのセキュリティを使用するようにサービスを構成します。  
  
## <a name="see-also"></a>関連項目  
 [セキュリティに関する考慮事項](../../../../docs/framework/wcf/feature-details/security-considerations-in-wcf.md)  
 [情報漏えいが起こる](../../../../docs/framework/wcf/feature-details/information-disclosure.md)  
 [特権の昇格](../../../../docs/framework/wcf/feature-details/elevation-of-privilege.md)  
 [サービス拒否が起こる](../../../../docs/framework/wcf/feature-details/denial-of-service.md)  
 [改ざん](../../../../docs/framework/wcf/feature-details/tampering.md)  
 [サポートされていないシナリオ](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md)
