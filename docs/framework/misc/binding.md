---
title: "&lt;バインド&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 666183d6-4d1f-45c7-ac64-bdf93ee8f36f
caps.latest.revision: "13"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 874a3766a64a9abb7c35efd5ac0a0f698707281e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="ltbindinggt"></a>&lt;バインド&gt;
`binding` 要素を使用して、Windows Communication Foundation (WCF) によって提供される異なる型の定義済みバインディングを構成できます。  
  
## <a name="system-provided-binding"></a>システム指定のバインディング  
 システム指定のバインディングは、WCF メッセージ スタックの複雑さを隠蔽します。 システム指定のバインディングを使用しているアプリケーションは、スタックを完全に制御する必要はありません。 システム指定の各バインディングに公開される属性は、バインディングが処理する使用シナリオに最適な属性です。  
  
 システム指定の各バインディングの構成セクションは、バインディングの構成に使用される複数の構成を定義できます。 各構成は、一意の名前によって識別されます。  
  
 要素または属性をシステム指定のバインディングに追加することはできません。 追加するには、このトピックの「カスタム バインディング」セクションで説明するように、カスタム バインディングを実装する必要があります。 システム指定のバインディングを完全に再現し、ユーザー アプリケーションで制御するいくつかの設定を追加するカスタム バインディングを定義できます。  
  
## <a name="custom-binding"></a>カスタム バインディング  
 カスタム バインディングを使用すると、WCF メッセージ スタックのフル コントロールが可能になります。 個別のバインディングは、メッセージ スタックを、スタック要素の構成要素をスタックに出現する順序で指定することにより定義します。 各要素は、スタック内の 1 つの要素を定義および構成します。 各カスタム バインディング内の `transport` 要素は 1 つだけにする必要があります。 この要素がない場合、メッセージ スタックは不完全です。  
  
 要素がスタックに出現する順序は重要です。それは、その順序で操作がメッセージに適用されるためです。 スタック要素で推奨される順序を次に示します。  
  
1.  トランザクション (省略可能)  
  
2.  リライアブル メッセージ機能 (省略可能)  
  
3.  セキュリティ (省略可能)  
  
4.  エンコーダー  
  
5.  Transport  
  
 カスタム バインディングは、`name` 属性によって識別されます。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.ServiceModel.Configuration.BindingsSection>  
 <xref:System.ServiceModel.Channels.Binding>  
 <xref:System.ServiceModel.Channels.BindingElement>  
 [バインディング](../../../docs/framework/wcf/bindings.md)  
 [カスタム バインド](../../../docs/framework/wcf/extending/custom-bindings.md)  
 [\<customBinding >](../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
