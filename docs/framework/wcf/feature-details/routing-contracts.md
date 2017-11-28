---
title: "ルーティング コントラクト"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9ceea7ae-ea19-4cf9-ba4f-d071e236546d
caps.latest.revision: "7"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.openlocfilehash: daebd84c9cef5e64ea7ed55c27b671ba01d14df0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="routing-contracts"></a>ルーティング コントラクト
ルーティング コントラクトは、ルーティング サービスが処理できるメッセージ パターンを定義します。  各コントラクトは型指定されておらず、サービスは、メッセージ スキーマやアクションを認識していない場合でもメッセージを受信できます。 このため、ルーティング サービスは、ルーティングされる基盤のメッセージの詳細構成を追加することなく、メッセージをジェネリックにルーティングできます。  
  
## <a name="routing-contracts"></a>ルーティング コントラクト  
 ルーティング サービスには汎用 WCF メッセージ オブジェクトを使用できるため、コントラクトを選ぶ場合の最大の検討事項は、クライアントとサービスとの通信時に使用されるチャネルの形状です。 ルーティング サービスは、メッセージを処理するときに対象型メッセージ ポンプを使用するため、通常、受信コントラクトの形状は、送信コントラクトの形状と一致します。 ただし、サービス モデルのディスパッチャーがディスパッチャーが要求/応答チャネルでは、双方向チャネルに変換または不要であり、(使用されていない場合に、チャネルからセッションのサポートを削除などの図形を変更できる場合があります。、ときに**SessionMode.Allowed**、変換、 **IInputSessionChannel**に、 **IInputChannel**)。  
  
 これらのメッセージ ポンプをサポートするために、ルーティング サービスでは、<xref:System.ServiceModel.Routing> 名前空間にコントラクトを用意しています。これらのコントラクトは、ルーティング サービスが使用するサービス エンドポイントを定義するときに、使用される必要があります。 これらのコントラクトは型指定されていないため、どのようなメッセージの種類やアクションでも受信でき、ルーティング サービスは、特定のメッセージ スキーマを認識しない場合でもメッセージを処理できます。 ルーティング サービスで使用されるコントラクトの詳細については、次を参照してください。[ルーティング コントラクト](../../../../docs/framework/wcf/feature-details/routing-contracts.md)です。  
  
 ルーティング サービスによって提供されるコントラクトは、<xref:System.ServiceModel.Routing> 名前空間に含まれています。これらのコントラクトは、次の表のとおりです。  
  
|コントラクト|形式|チャネル形状|  
|--------------|-----------|-------------------|  
|<xref:System.ServiceModel.Routing.ISimplexDatagramRouter>|SessionMode = SessionMode.Allowed<br /><br /> AsyncPattern = true<br /><br /> IsOneWay = true|IInputChannel -> IOutputChannel|  
|<xref:System.ServiceModel.Routing.ISimplexSessionRouter>|SessionMode = SessionMode.Required<br /><br /> AsyncPattern = true<br /><br /> IsOneWay = true|IInputSessionChannel -> IOutputSessionChannel|  
|<xref:System.ServiceModel.Routing.IRequestReplyRouter>|SessionMode = SessionMode.Allowed<br /><br /> AsyncPattern = true|IReplyChannel -> IRequestChannel|  
|<xref:System.ServiceModel.Routing.IDuplexSessionRouter>|SessionMode=SessionMode.Required<br /><br /> CallbackContract=typeof(ISimplexSession)<br /><br /> AsyncPattern = true<br /><br /> IsOneWay = true<br /><br /> TransactionFlow(TransactionFlowOption.Allowed)|IDuplexSessionChannel -> IDuplexSessionChannel|  
  
## <a name="see-also"></a>関連項目  
 [ルーティング サービス](http://msdn.microsoft.com/en-us/5ac8718c-bcef-456f-bfd5-1e60a30d6eaa)  
 [ルーティングの概要](../../../../docs/framework/wcf/feature-details/routing-introduction.md)
