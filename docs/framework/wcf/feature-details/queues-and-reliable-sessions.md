---
title: "キューと信頼できるセッション | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7e794d03-141c-45ed-b6b1-6c0e104c1464
caps.latest.revision: 10
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 10
---
# キューと信頼できるセッション
キューおよび信頼できるセッションは、信頼できるメッセージングを実装する [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] の機能です。このセクションの各トピックでは、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] の信頼できるメッセージング機能について説明します。  
  
 信頼できるメッセージングとは、信頼できるメッセージング送信元 \(送信元と呼ぶ\) から信頼できるメッセージング送信先 \(送信先と呼ぶ\) にメッセージを確実に転送することを指します。  
  
 信頼できるメッセージングの主要な側面は、次のとおりです。  
  
-   メッセージ転送エラーまたはトランスポート エラーに関係なく、送信元から送信先に送られるメッセージの転送が保証されること。  
  
-   送信元と送信先を互いに分離することにより、送信元または送信先が利用できない場合でも、送信元と送信先でのそれぞれ独立したエラーと回復が可能になると共に、信頼できるメッセージの転送と配信が実現されること。  
  
 信頼できるメッセージングを実現すると、待ち時間が長くなることがよくあります。待ち時間とは、メッセージが送信元から送信先に到達するまでにかかる時間です。そこで、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] では、信頼できるメッセージングとして、次の 2 種類を提供します。  
  
-   [信頼できるセッション](../../../../docs/framework/wcf/feature-details/reliable-sessions.md) : 長い待ち時間という代償を伴わずに、信頼できる転送を実現します。  
  
-   [WCF のキュー](../../../../docs/framework/wcf/feature-details/queues-in-wcf.md) : 信頼できる転送、および送信元と送信先の分離を共に実現します。  
  
## 信頼できるセッション  
 信頼できるセッションでは、メッセージング \(送信元および送信先\) エンドポイントを分離する中継局の数や種類に関係なく、WS\-ReliableMessaging プロトコルを使用して、送信元から送信先へのエンドツーエンドの信頼できるメッセージ転送を実現します。これには SOAP を使用しないトランスポート手段 \(HTTP プロキシなど\)、またはエンドポイント間でメッセージをやりとりする場合に必要となる SOAP を使用する手段 \(SOAP ベースのルーターやブリッジなど\) が含まれます。信頼できるセッションでは、メモリ内転送ウィンドウを使用して、トランスポート エラーが発生した場合に SOAP メッセージ レベル エラーをマスクし、接続を再確立します。  
  
 信頼できるセッションは、待ち時間の短い、信頼できるメッセージ転送を実現します。これらは、TCP が IP ブリッジ経由のパケットで実現するものと同等の転送を、プロキシや中継局経由の SOAP メッセージで実現します。信頼できるセッション[!INCLUDE[crabout](../../../../includes/crabout-md.md)]、「[信頼できるセッション](../../../../docs/framework/wcf/feature-details/reliable-sessions.md)」を参照してください。  
  
### キュー  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] のキューでは、待ち時間は長くなりますが、信頼できるメッセージの転送と共に送信元および送信先の分離が実現されます。[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] のキュー通信は、Microsoft Message Queuing \(MSMQ\) に基づいています。  
  
 MSMQ は Windows にオプションとして付属し、NT サービスの 1 つとして実行されます。MSMQ サービスは、送信元の代わりに転送キューで転送用のメッセージを取得し、ターゲット キューに配信します。ターゲット キューは、送信先の代わりにメッセージを受け取り、後で送信先がメッセージを要求したときに配信します。MSMQ キュー マネージャーは信頼できるメッセージ転送プロトコルを実装して、送信中にメッセージが失われないようにします。このプロトコルは、ネイティブまたは SOAP リライアブル メッセージ プロトコル \(SRMP\) などの SOAP ベースのプロトコルです。  
  
 キュー間でのメッセージの信頼できる転送に加え、送信元と送信先の分離により、疎結合されたアプリケーションで信頼できる通信を実現できます。信頼できるセッションとは異なり、送信元と送信先が同時に実行されている必要はありません。このため、送信元によるメッセージの生成レートと送信先によるメッセージの消費レートが一致しないときに、キューを実質的に負荷平準化機構として使用できるようになります。キュー[!INCLUDE[crabout](../../../../includes/crabout-md.md)]、「[WCF のキュー](../../../../docs/framework/wcf/feature-details/queues-in-wcf.md)」を参照してください。  
  
## 参照  
 [WCF のキュー](../../../../docs/framework/wcf/feature-details/queues-in-wcf.md)   
 [WCF でのキュー](../../../../docs/framework/wcf/feature-details/queuing-in-wcf.md)   
 [信頼できるセッション](../../../../docs/framework/wcf/feature-details/reliable-sessions.md)   
 [信頼できるセッションの概要](../../../../docs/framework/wcf/feature-details/reliable-sessions-overview.md)