---
title: "信頼できるサービス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WCF [WCF], reliable messaging
- Windows Communication Foundation [WCF], reliable messaging
- WCF [WCF], reliable sessions
- Windows Communication Foundation [WCF], reliable sessions
- service contracts [WCF], reliable services
ms.assetid: 07814ed0-0775-47f2-987b-d8134fdd5099
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 4872afb097d01279b24697a7b385f336d34ea4f9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="reliable-services"></a>信頼できるサービス
キューおよび信頼できるセッションは、信頼できるメッセージングを実装する [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] の機能です。 このトピックでは、[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] の信頼できるメッセージング機能について説明します。  
  
 *信頼できるメッセージング*方法、信頼できるメッセージング送信元は、(と呼ばれる、*ソース*) 信頼できるメッセージング送信先にメッセージを確実に転送 (と呼ばれる、*先*)。  
  
 信頼できるメッセージングは、次の機能を実行します。  
  
-   メッセージ転送エラーまたはトランスポート エラーに関係なく、送信元から送信先に送られるメッセージの転送が保証されること。  
  
-   送信元と送信先を互いに分離すること。 これにより、送信元または送信先が利用できない場合でも、送信元と送信先でのそれぞれ独立したエラーと回復が可能になると共に、信頼できるメッセージの転送と配信が実現されます。  
  
 信頼できるメッセージングを実現すると、待ち時間が長くなることがよくあります。 *待機時間*メッセージ ソースから宛先に到達するまでにかかる時間です。 そこで、[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] では、信頼できるメッセージングとして、次の 2 種類を提供します。  
  
-   [信頼できるセッション](../../../docs/framework/wcf/feature-details/reliable-sessions.md)コストの遅延が大きいことがなく信頼できる転送を提供します。  
  
-   [WCF のキュー](../../../docs/framework/wcf/feature-details/queues-in-wcf.md)、信頼できる転送と、ソースとターゲット間の分離の両方を提供します。  
  
## <a name="reliable-sessions"></a>信頼できるセッション  
 信頼できるセッションでは、メッセージング (送信元および送信先) エンドポイントを分離する中継局の数や種類に関係なく、WS-ReliableMessaging プロトコルを使用して、送信元から送信先へのエンドツーエンドの信頼できるメッセージ転送を実現します。 これには SOAP を使用しないトランスポート手段 (HTTP プロキシなど)、またはエンドポイント間でメッセージをやりとりする場合に必要となる SOAP を使用する手段 (SOAP ベースのルーターやブリッジなど) が含まれます。 信頼できるセッションでは、メモリ内転送ウィンドウを使用して、トランスポート エラーが発生した場合に SOAP メッセージ レベル エラーをマスクし、接続を再確立します。  
  
 信頼できるセッションは、待ち時間の短い、信頼できるメッセージ転送を実現します。 これらは、TCP が IP ブリッジ経由のパケットで実現するものと同等の転送を、プロキシや中継局経由の SOAP メッセージで実現します。 [!INCLUDE[crabout](../../../includes/crabout-md.md)]信頼できるセッションを参照してください[信頼できるセッション](../../../docs/framework/wcf/feature-details/reliable-sessions.md)です。  
  
### <a name="queues"></a>キュー  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] のキューでは、待ち時間は長くなりますが、信頼できるメッセージの転送と共に送信元および送信先の分離が実現されます。 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] のキュー通信は、Microsoft Message Queuing (MSMQ) に基づいています。  
  
 MSMQ は Windows のオプション コンポーネントとして付属します。 MSMQ サービスは Windows サービスの 1 つとして実行されます。 MSMQ サービスは、送信元の代わりに転送キューで転送用のメッセージを取得し、ターゲット キューに配信します。 ターゲット キューは、送信先の代わりにメッセージを受け取り、後で送信先がメッセージを要求したときに配信します。 MSMQ マネージャーは信頼できるメッセージ転送プロトコルを実装するため、転送中にメッセージが失われることはありません。 このプロトコルは、ネイティブまたは SOAP リライアブル メッセージ プロトコル (SRMP) と呼ばれる SOAP ベースのプロトコルです。  
  
 キュー間でのメッセージの信頼できる転送に加え、送信元と送信先の分離により、疎結合されたアプリケーションで信頼できる通信を実現できます。 信頼できるセッションとは異なり、送信元と送信先が同時に実行されている必要はありません。 このため、送信元によるメッセージの生成レートと送信先によるメッセージの消費レートが一致しないときに、キューが実質上、負荷平準化機構として使用されるというシナリオが暗黙的に可能になります。 [!INCLUDE[crabout](../../../includes/crabout-md.md)]キューを参照してください[WCF のキュー](../../../docs/framework/wcf/feature-details/queues-in-wcf.md)です。  
  
## <a name="see-also"></a>関連項目  
 [信頼できるセッションの概要](../../../docs/framework/wcf/feature-details/reliable-sessions-overview.md)  
 [WCF でのキュー](../../../docs/framework/wcf/feature-details/queuing-in-wcf.md)
