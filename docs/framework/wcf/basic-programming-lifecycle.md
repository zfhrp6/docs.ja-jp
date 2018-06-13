---
title: 基本的なプログラミング ライフサイクル
ms.date: 03/30/2017
helpviewer_keywords:
- service creation [WCF]
ms.assetid: 7cf21bfe-23bd-46aa-8033-609f851dbf76
ms.openlocfilehash: b20167ad776f3524e4516b71e43ab8cdb5c2aea4
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/07/2018
ms.locfileid: "33803693"
---
# <a name="basic-programming-lifecycle"></a>基本的なプログラミング ライフサイクル
Windows Communication Foundation (WCF) では、アプリケーションにいるかどうか、同じコンピューター上または異なるアプリケーション プラットフォーム上、インターネット経由で通信を使用できます。 このトピックでは、WCF アプリケーションを構築するために必要なタスクについて説明します。 実際のサンプル アプリケーションでは、次を参照してください。[チュートリアル入門](../../../docs/framework/wcf/getting-started-tutorial.md)です。  
  
## <a name="the-basic-tasks"></a>基本的なタスク  
 基本的な作業は、次の順序で行います。  
  
1.  サービス コントラクトを定義します。 サービス コントラクトでは、サービスの署名、交換するデータ、およびコントラクトに必要なその他のデータを指定します。 詳細については、次を参照してください。[サービス コントラクトの設計](../../../docs/framework/wcf/designing-service-contracts.md)です。  
  
2.  コントラクトを実装します。 サービス コントラクトを実装するには、そのコントラクトを実装するクラスを作成し、ランタイムに必要なカスタム動作を指定します。 詳細については、次を参照してください。[サービス コントラクトを実装する](../../../docs/framework/wcf/implementing-service-contracts.md)です。  
  
3.  エンドポイントおよびその他の動作情報を指定して、サービスを構成します。 詳細については、次を参照してください。[サービスを構成する](../../../docs/framework/wcf/configuring-services.md)です。  
  
4.  サービスをホストします。 詳細については、次を参照してください。[ホスティング サービス](../../../docs/framework/wcf/hosting-services.md)です。  
  
5.  クライアント アプリケーションを構築します。 詳細については、次を参照してください。[クライアントを構築する](../../../docs/framework/wcf/building-clients.md)です。  
  
 このセクションのトピックではこの順に従って説明しますが、手順を最初から実行しないシナリオもあります。 たとえば、既存のサービスを使用するクライアントを構築する場合は、手順 5. から開始します。 また、既存のクライアント アプリケーションが使用するサービスを構築する場合は、手順 5. を省略できます。  
  
 サービス コントラクトの開発の経験が、参照することも[拡張機能の概要](../../../docs/framework/wcf/introduction-to-extensibility.md)です。 サービスに問題がある場合は確認[WCF トラブルシューティング クイック スタート](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md)同一または類似した問題を持つ他のユーザーかどうかを確認します。  
  
## <a name="see-also"></a>関連項目  
 [サービス コントラクトの実装](../../../docs/framework/wcf/implementing-service-contracts.md)
