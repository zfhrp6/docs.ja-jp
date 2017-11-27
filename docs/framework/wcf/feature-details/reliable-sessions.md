---
title: "信頼できるセッション"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- Windows Communication Foundation, sessions and instances
- WCF, sessions and instances
- sessions and instances [WCF]
helpviewer_keywords:
- instances [WCF]
- sessions [WCF]
ms.assetid: 143951b3-3aa0-4540-b4b7-d33e77e874a1
caps.latest.revision: "15"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 659309ff5560480c423fc9b0adab5e93eac05ce5
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="reliable-sessions"></a>信頼できるセッション

このセクションでは、新機能について説明します、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]信頼できるセッションはの使用目的は、方法にする 1 つを使用して、どのようなバインディング構成をサポート、およびベスト プラクティスの参照先。 このセクションの重要なポイントと関連するトピックの詳細について、次の表にまとめます。

信頼できるセッション[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]エンドポイント間で送信されるメッセージは SOAP またはトランスポート中継ぎ局経由で転送されたされ、1 回だけと、必要に応じて、送信された順序と同じ順序で配信されるように featrues を提供します。

[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] アプリケーションで信頼できるセッションを使用するには、既定またはオプションとして、信頼できるセッションをサポートする、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] のシステム提供のバインディングの 1 つを使用するか、または信頼できるセッションをサポートする独自のカスタム バインディングを作成します。

## <a name="in-this-section"></a>このセクションの内容

[信頼できるセッションの概要](../../../../docs/framework/wcf/feature-details/reliable-sessions-overview.md)   
信頼できるセッションの概要、信頼できるセッションを使用する状況、信頼できるセッションをサポートする各種のバインディング、および動作のしくみについて説明します。

[方法: 信頼できるセッション内でメッセージを交換します。](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-within-a-reliable-session.md)   
構成で指定したカスタム バインドを使用して、HTTP 上で信頼できるセッションを作成する方法を説明します。

[方法: 信頼できるセッション内でメッセージをセキュリティ保護](../../../../docs/framework/wcf/feature-details/how-to-secure-messages-within-reliable-sessions.md)   
信頼できるセッションを保護する方法について説明します。

[方法: HTTPS で信頼できるセッションをカスタム バインディングを作成します。](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-reliable-session-binding-with-https.md)   
HTTPS 上で信頼できるセッションを作成する方法について説明します。

[信頼できるセッションのベスト プラクティス](../../../../docs/framework/wcf/feature-details/best-practices-for-reliable-sessions.md)   
信頼できるセッションの使用に関するベスト プラクティスについて説明します。

## <a name="reference"></a>参照

<xref:System.ServiceModel.ReliableSession>

## <a name="see-also"></a>関連項目

[キューと信頼できるセッション](../../../../docs/framework/wcf/feature-details/queues-and-reliable-sessions.md)   
[セッション、インスタンス化、および同時実行](../../../../docs/framework/wcf/feature-details/sessions-instancing-and-concurrency.md)
