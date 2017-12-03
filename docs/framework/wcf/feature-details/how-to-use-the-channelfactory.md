---
title: "方法 : ChannelFactory を使用する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: d48f01b5-582b-4c8b-b547-8adddae7e371
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 37ad5181ad140c3ef3ea8ba5b3774fd44310dca7
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-use-the-channelfactory"></a>方法 : ChannelFactory を使用する
<xref:System.ServiceModel.ChannelFactory%601> ジェネリック クラスは、複数チャネルの作成に使用できるチャネル ファクトリの作成を必要とする高度なシナリオで使用します。  
  
### <a name="to-create-and-use-the-channelfactory-class"></a>ChannelFactory クラスの作成方法と使用方法  
  
1.  [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] サービスをビルドして実行します。 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][設計と実装のサービス](../../../../docs/framework/wcf/designing-and-implementing-services.md)、[サービスを構成する](../../../../docs/framework/wcf/configuring-services.md)、および[Services をホストしている](../../../../docs/framework/wcf/hosting-services.md)です。  
  
2.  使用して、 [ServiceModel メタデータ ユーティリティ ツール (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)をクライアントのコントラクト (インターフェイス) を生成します。  
  
3.  クライアント コード内で、<xref:System.ServiceModel.ChannelFactory%601> クラスを使用して複数のエンドポイント リスナーを作成します。  
  
## <a name="example"></a>例  
 [!code-csharp[c_HowToUseChannelFactory#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtousechannelfactory/cs/source.cs#1)]
 [!code-vb[c_HowToUseChannelFactory#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtousechannelfactory/vb/source.vb#1)]
