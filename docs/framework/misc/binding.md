---
title: '&lt;バインド&gt;'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 666183d6-4d1f-45c7-ac64-bdf93ee8f36f
ms.openlocfilehash: d72b3a34e0696df944b2338c89f167c8bfa06400
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33392253"
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
 [カスタム バインディング](../../../docs/framework/wcf/extending/custom-bindings.md)  
 [\<customBinding>](../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
