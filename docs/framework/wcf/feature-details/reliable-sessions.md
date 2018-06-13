---
title: 信頼できるセッション
ms.date: 03/30/2017
f1_keywords:
- Windows Communication Foundation, sessions and instances
- WCF, sessions and instances
- sessions and instances [WCF]
helpviewer_keywords:
- instances [WCF]
- sessions [WCF]
ms.assetid: 143951b3-3aa0-4540-b4b7-d33e77e874a1
ms.openlocfilehash: 396c76cbdb8eada881a5c87edfc2500dcdab3ad4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33497166"
---
# <a name="reliable-sessions"></a>信頼できるセッション

このセクションでは、どのような Windows Communication Foundation (WCF) は、信頼できるセッションの使用目的は、どのようにと 1 つを使用するどのようなバインディング サポート構成、およびベスト プラクティスの参照先について説明します。 このセクションの重要なポイントと関連するトピックの詳細について、次の表にまとめます。

信頼できるセッション WCF には、エンドポイント間で送信されるメッセージは SOAP またはトランスポート中継ぎ局経由で転送されたされ、1 回だけと、必要に応じて、送信された順序と同じ順序で配信されるように featrues が用意されています。

で WCF アプリケーションを信頼できるセッションを使用するには、既定またはオプションとして、信頼できるセッションをサポートして WCF でのシステムによって提供されるバインディングの 1 つを使用するかセッションをサポートする独自のカスタム バインドを作成します。

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
