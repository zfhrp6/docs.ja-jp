---
title: 上位互換性のあるデータ コントラクト
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data contracts [WCF], forward compatibility
ms.assetid: 413c9044-26f8-4ecb-968c-18495ea52cd9
caps.latest.revision: 21
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 554176d2b6ac0c1d5cbe817721c55d06f88457cc
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2018
---
# <a name="forward-compatible-data-contracts"></a>上位互換性のあるデータ コントラクト
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] のデータ コントラクト システムの特徴の 1 つは、コントラクトが互換性に影響のない形で時間の経過に応じて変化できる点にあります。 つまり、古いバージョンのデータ コントラクトを使用するクライアントが同じデータ コントラクトの新しいバージョンのサービスと通信したり、新しいバージョンのデータ コントラクトを使用するクライアントが同じデータ コントラクトの古いバージョンと通信したりできます。 詳細については、次を参照してください。[ベスト プラクティス: データ コントラクトのバージョン管理](../../../../docs/framework/wcf/best-practices-data-contract-versioning.md)です。  
  
 バージョン管理機能の大半は、既存のデータ コントラクトの新しいバージョンが作成されたときに、必要に応じて適用できます。 ただし、1 つのバージョン管理機能*ラウンド トリップ*、正常に動作するために最初のバージョンからの型に組み込む必要があります。  
  
## <a name="round-tripping"></a>ラウンド トリップ  
 ラウンド トリップは、データ コントラクトの新しいバージョンから古いバージョンにデータが渡され、新しいバージョンに戻されるときに発生します。 ラウンド トリップでは、データの損失がないことが保証されます。 ラウンド トリップを有効にすると、データ コントラクト バージョン管理モデルによってサポートされる将来の変更に関して、型の上位互換性が保たれます。  
  
 特定の型のラウンド トリップを有効にするには、この型に <xref:System.Runtime.Serialization.IExtensibleDataObject> インターフェイスを実装する必要があります。 このインターフェイスには、(<xref:System.Runtime.Serialization.IExtensibleDataObject.ExtensionData%2A> 型を返す) <xref:System.Runtime.Serialization.ExtensionDataObject> プロパティが含まれます。 このプロパティにより、現在のバージョンでは未知の、今後使用されるデータ コントラクトの任意のデータが格納されます。  
  
### <a name="example"></a>例  
 次のデータ コントラクトは、将来の変更に対して上位互換性がありません。  
  
 [!code-csharp[C_DataContract#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontract/cs/source.cs#7)]
 [!code-vb[C_DataContract#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontract/vb/source.vb#7)]  
  
 将来の変更 (たとえば、"phoneNumber" という名前の新しいデータ メンバーを追加する) に対して互換性を確保するには、<xref:System.Runtime.Serialization.IExtensibleDataObject> インターフェイスを次のように実装します。  
  
 [!code-csharp[C_DataContract#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontract/cs/source.cs#8)]
 [!code-vb[C_DataContract#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontract/vb/source.vb#8)]  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] インフラストラクチャが、元のデータ コントラクトに含まれないデータを検出すると、このデータはプロパティに格納されて維持されます。 データは一時的に格納されるだけで、処理されることはありません。 オブジェクトを発生元に返すと、元の (未知の) データも返されます。 したがって、データが失われることなく、元のエンドポイントとの間でラウンド トリップ (往復) が行われます。 ただし、発生元のエンドポイントでデータを処理する必要がある場合、この要求は満たされないため、このエンドポイントでは何らかの方法で変更を検出して対応する必要があることに注意してください。  
  
 <xref:System.Runtime.Serialization.ExtensionDataObject> 型にはパブリックなメソッドやプロパティはありません。 そのため、<xref:System.Runtime.Serialization.IExtensibleDataObject.ExtensionData%2A> プロパティ内に格納されているデータに直接アクセスすることはできません。  
  
 ラウンド トリップ機能は、`ignoreExtensionDataObject` コンストラクターで `true` を <xref:System.Runtime.Serialization.DataContractSerializer> に設定する、または <xref:System.ServiceModel.ServiceBehaviorAttribute.IgnoreExtensionDataObject%2A> で `true` プロパティを <xref:System.ServiceModel.ServiceBehaviorAttribute> に設定することで無効にできます。 この機能を無効にすると、デシリアライザーが <xref:System.Runtime.Serialization.IExtensibleDataObject.ExtensionData%2A> プロパティを設定しないため、シリアライザーはプロパティの内容を出力しません。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Runtime.Serialization.IExtensibleDataObject>  
 <xref:System.Runtime.Serialization.ExtensionDataObject>  
 [データ コントラクトのバージョン管理](../../../../docs/framework/wcf/feature-details/data-contract-versioning.md)  
 [ベスト プラクティス: データ コントラクトのバージョン管理](../../../../docs/framework/wcf/best-practices-data-contract-versioning.md)
