---
title: "基本的なプログラミング ライフサイクル"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: service creation [WCF]
ms.assetid: 7cf21bfe-23bd-46aa-8033-609f851dbf76
caps.latest.revision: "36"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 78ad1159232ecfb75745dd72b7da1e3153a79574
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="basic-programming-lifecycle"></a>基本的なプログラミング ライフサイクル
[!INCLUDE[indigo1](../../../includes/indigo1-md.md)] では、アプリケーションは、同一のコンピューター上、インターネット上、異なるアプリケーション プラットフォーム上のいずれに存在しても、通信できます。 ここでは、[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] アプリケーションを構築するために必要な作業について説明します。 実際のサンプル アプリケーションでは、次を参照してください。[チュートリアル入門](../../../docs/framework/wcf/getting-started-tutorial.md)です。  
  
## <a name="the-basic-tasks"></a>基本的なタスク  
 基本的な作業は、次の順序で行います。  
  
1.  サービス コントラクトを定義します。 サービス コントラクトでは、サービスの署名、交換するデータ、およびコントラクトに必要なその他のデータを指定します。 [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][サービス コントラクトの設計](../../../docs/framework/wcf/designing-service-contracts.md)です。  
  
2.  コントラクトを実装します。 サービス コントラクトを実装するには、そのコントラクトを実装するクラスを作成し、ランタイムに必要なカスタム動作を指定します。 [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][サービス コントラクトを実装する](../../../docs/framework/wcf/implementing-service-contracts.md)です。  
  
3.  エンドポイントおよびその他の動作情報を指定して、サービスを構成します。 [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][Services の構成](../../../docs/framework/wcf/configuring-services.md)です。  
  
4.  サービスをホストします。 [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][Services をホストしている](../../../docs/framework/wcf/hosting-services.md)です。  
  
5.  クライアント アプリケーションを構築します。 [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][クライアントを構築](../../../docs/framework/wcf/building-clients.md)です。  
  
 このセクションのトピックではこの順に従って説明しますが、手順を最初から実行しないシナリオもあります。 たとえば、既存のサービスを使用するクライアントを構築する場合は、手順 5. から開始します。 また、既存のクライアント アプリケーションが使用するサービスを構築する場合は、手順 5. を省略できます。  
  
 サービス コントラクトの開発の経験が、参照することも[拡張機能の概要](../../../docs/framework/wcf/introduction-to-extensibility.md)です。 サービスに問題がある場合は確認[WCF トラブルシューティング クイック スタート](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md)同一または類似した問題を持つ他のユーザーかどうかを確認します。  
  
## <a name="see-also"></a>関連項目  
 [サービス コントラクトの実装](../../../docs/framework/wcf/implementing-service-contracts.md)
