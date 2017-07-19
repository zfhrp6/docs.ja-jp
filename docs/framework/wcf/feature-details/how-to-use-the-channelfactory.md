---
title: "方法 : ChannelFactory を使用する | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
ms.assetid: d48f01b5-582b-4c8b-b547-8adddae7e371
caps.latest.revision: 14
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 14
---
# 方法 : ChannelFactory を使用する
<xref:System.ServiceModel.ChannelFactory%601> ジェネリック クラスは、複数チャネルの作成に使用できるチャネル ファクトリの作成を必要とする高度なシナリオで使用します。  
  
### ChannelFactory クラスの作成方法と使用方法  
  
1.  [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] サービスをビルドして実行します。  [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] [サービスの設計と実装](../../../../docs/framework/wcf/designing-and-implementing-services.md)、[サービスの構成](../../../../docs/framework/wcf/configuring-services.md)、および [ホスティング サービス](../../../../docs/framework/wcf/hosting-services.md)。  
  
2.  クライアントのコントラクト \(インターフェイス\) を生成するには、[ServiceModel メタデータ ユーティリティ ツール \(Svcutil.exe\)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) を使用します。  
  
3.  クライアント コード内で、<xref:System.ServiceModel.ChannelFactory%601> クラスを使用して複数のエンドポイント リスナーを作成します。  
  
## 使用例  
 [!code-csharp[c_HowToUseChannelFactory#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtousechannelfactory/cs/source.cs#1)]
 [!code-vb[c_HowToUseChannelFactory#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtousechannelfactory/vb/source.vb#1)]