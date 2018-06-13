---
title: '&lt;バインド&gt;'
ms.date: 03/30/2017
ms.assetid: b62cd369-5409-4030-8490-9759a462dd3a
ms.openlocfilehash: 76ebd7c317bf5f0aa1ec02d4014235df232314f0
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32747822"
---
# <a name="ltbindingsgt"></a>&lt;バインド&gt;
このセクションには、標準バインディングおよびカスタム バインドのコレクションが保持されます。 各エントリは、その一意の `binding` 属性で識別できる `name` 要素です。 サービスは、`name` を使用してバインディングをリンクすることにより、バインディングを使用します。 [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)] 以降では、バインディングおよび動作に名前を付ける必要はありません。 既定の構成と無名のバインディングおよび動作の詳細については、次を参照してください。[簡略化された構成](../../../../../docs/framework/wcf/simplified-configuration.md)と[WCF サービスの構成を簡略化](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md)です。  
  
## <a name="system-provided-binding"></a>システム指定のバインディング  
 システム指定のバインディングは、WCF メッセージ スタックの複雑さを隠蔽します。 システム指定のバインディングを使用しているアプリケーションは、スタックを完全に制御する必要はありません。 システム指定の各バインディングに公開される属性は、バインディングが処理する使用シナリオに最適な属性です。  
  
 システム指定の各バインディングの構成セクションは、バインディングの構成に使用される複数の構成を定義できます。 各構成は、一意の名前によって識別されます。  
  
 要素または属性をシステム指定のバインディングに追加することはできません。 追加するには、このトピックの「カスタム バインディング」セクションで説明するように、カスタム バインディングを実装する必要があります。 システム指定のバインディングを完全に再現し、ユーザー アプリケーションで制御するいくつかの設定を追加するカスタム バインドを定義できます。  
  
 システム指定のバインディングの一覧は、次を参照してください。[システム指定のバインディング](../../../../../docs/framework/wcf/system-provided-bindings.md)です。  
  
## <a name="custom-binding"></a>カスタム バインド  
 カスタム バインディングを使用すると、WCF メッセージ スタックのフル コントロールが可能になります。 個別のバインディングは、メッセージ スタックを、スタック要素の構成要素をスタックに出現する順序で指定することにより定義します。 各要素は、スタック内の 1 つの要素を定義および構成します。 各カスタム バインディング内の `transport` 要素は 1 つだけにする必要があります。 この要素がない場合、メッセージ スタックは不完全です。  
  
 要素がスタックに出現する順序は重要です。それは、その順序で操作がメッセージに適用されるためです。 スタック要素で必要な順序を次に示します。  
  
1.  トランザクション (省略可能)  
  
2.  リライアブル メッセージ機能 (省略可能)  
  
3.  セキュリティ (省略可能)  
  
4.  エンコーダー  
  
5.  Transport  
  
 カスタム バインディングは、`name` 属性によって識別されます。 カスタム バインドの詳細については、次を参照してください。[カスタム バインド](../../../../../docs/framework/wcf/extending/custom-bindings.md)です。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.ServiceModel.Configuration.BindingsSection>  
 <xref:System.ServiceModel.Channels.Binding>  
 <xref:System.ServiceModel.Channels.BindingElement>  
 [バインディング](../../../../../docs/framework/wcf/bindings.md)  
 [カスタム バインディング](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [\<customBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)  
 [\<binding>](../../../../../docs/framework/misc/binding.md)
