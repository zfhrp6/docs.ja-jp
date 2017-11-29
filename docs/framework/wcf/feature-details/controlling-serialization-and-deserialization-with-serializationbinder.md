---
title: "SerializationBinder を使用したシリアル化および逆シリアル化の制御"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ba8dcecf-acc7-467c-939d-021bbac797d4
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 1c3180d62824f94e27e02c80e09fdf32252f0a23
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="controlling-serialization-and-deserialization-with-serializationbinder"></a>SerializationBinder を使用したシリアル化および逆シリアル化の制御
シリアル化中に、フォーマッタは、正しい型およびバージョンのオブジェクトのインスタンスを作成するために必要な情報を送信します。 通常、この情報には、オブジェクトの完全な型名および完全なアセンブリ名が含まれます。 既定では、逆シリアル化でこの情報を使用して、同一のオブジェクトのインスタンスを作成します。 場合によっては、シリアル化するクラスと逆シリアル化するクラスの制御が必要となります。これは、元のクラスが逆シリアル化を実行するコンピューター上に存在していない可能性がある場合、元のクラスがアセンブリ間で移動されている場合、または、サーバー上とクライアント上では異なるバージョンのクラスが必要である場合です。 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][シリアル化バインダーの使用法](../../../../docs/framework/wcf/samples/usage-of-serialization-binder.md)です。  
  
> [!WARNING]
>  この機能は、<xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> または <xref:System.Runtime.Serialization.NetDataContractSerializer> を使用してのみ、使用可能です。  
  
## <a name="using-serializationbinder"></a>SerializationBinder の使用  
 <xref:System.Runtime.Serialization.SerializationBinder> は、シリアル化中および逆シリアル化中に使用される実際の型を制御するために使用される抽象クラスです。 シリアル化および逆シリアル化中に使用される型を制御するには、派生クラスを<xref:System.Runtime.Serialization.SerializationBinder>をオーバーライドし、 <xref:System.Runtime.Serialization.SerializationBinder.BindToName%2A> System.String、System.String)?qualifyHint=False & autoUpgrade = True と<xref:System.Runtime.Serialization.SerializationBinder.BindToType%2A>System.String)?qualifyHint = False & autoUpgrade = True メソッドです。 <xref:System.Runtime.Serialization.SerializationBinder.BindToName%2A> System.String、System.String)?qualifyHint=False & autoUpgrade = True メソッドは、<xref:System.Type>し、アセンブリと型名を返します。 <xref:System.Runtime.Serialization.SerializationBinder.BindToType%2A> System.String)?qualifyHint=False & autoUpgrade = True メソッドはアセンブリと型名を返します、<xref:System.Type>です。  
  
## <a name="see-also"></a>関連項目  
 [シリアル化および逆シリアル化](../../../../docs/framework/wcf/feature-details/serialization-and-deserialization.md)  
 [シリアル化バインダーの使用法](../../../../docs/framework/wcf/samples/usage-of-serialization-binder.md)
