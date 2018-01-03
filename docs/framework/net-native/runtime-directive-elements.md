---
title: "ランタイム ディレクティブ要素"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3fe5848c-ecd7-4136-970b-8e48d250bde6
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e2566c5ebe8c94610c8f7e258da7c77adb86a49f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="runtime-directive-elements"></a>ランタイム ディレクティブ要素
ランタイム ディレクティブ (rd.xml) ファイル形式は、次のランタイム ディレクティブ要素をサポートします。 階層表現については、「[ランタイム ディレクティブ (rd.xml) 構成ファイル リファレンス](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)」を参照してください。  
  
 [\<Application>](../../../docs/framework/net-native/application-element-net-native.md)  
 アプリで使用されるすべての型にランタイム リフレクション ポリシーを適用し、実行時にリフレクションに使用できるメタデータを持つアプリケーション全体の型と型のメンバーのコンテナーとして機能します。 これは、[\<Directives>](../../../docs/framework/net-native/directives-element-net-native.md) 要素の子です。  
  
 [\<Assembly>](../../../docs/framework/net-native/assembly-element-net-native.md)  
 アセンブリ内のすべての型に実行時ポリシーを適用します。 これは、[\<Application>](../../../docs/framework/net-native/application-element-net-native.md) 要素と [\<Library>](../../../docs/framework/net-native/library-element-net-native.md) 要素の子です。  
  
 [\<AttributeImplies>](../../../docs/framework/net-native/attributeimplies-element-net-native.md)  
 それを含んでいる [\<Type>](../../../docs/framework/net-native/type-element-net-native.md) ディレクティブが属性の場合、その属性が適用されるコード要素に実行時ポリシーを適用します。  
  
 [\<Directives>](../../../docs/framework/net-native/directives-element-net-native.md)  
 [!INCLUDE[net_native](../../../includes/net-native-md.md)]のすべてのランタイム ディレクティブ ファイルのルート要素です。 その子要素は、[\<Application>](../../../docs/framework/net-native/application-element-net-native.md) と [\<Library>](../../../docs/framework/net-native/library-element-net-native.md) です。  
  
 [\<Event>](../../../docs/framework/net-native/event-element-net-native.md)  
 イベントに実行時ポリシーを適用します。 これは、[\<Type>](../../../docs/framework/net-native/type-element-net-native.md) 要素と [\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) 要素の子です。  
  
 [\<Field>](../../../docs/framework/net-native/field-element-net-native.md)  
 フィールドに実行時ポリシーを適用します。 これは、[\<Type>](../../../docs/framework/net-native/type-element-net-native.md) 要素と [\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) 要素の子です。  
  
 [\<GenericParameter>](../../../docs/framework/net-native/genericparameter-element-net-native.md)  
 ジェネリック型またはメソッドのパラメーター型に実行時ポリシーを適用します。  
  
 [\<ImpliesType>](../../../docs/framework/net-native/impliestype-element-net-native.md)  
 型に実行時ポリシーを適用します (それを含んでいる型またはメソッドにそのポリシーが適用されている場合)。  
  
 [\<Library>](../../../docs/framework/net-native/library-element-net-native.md)  
 アセンブリ内のすべての型に実行時ポリシーを適用します。 これは、[\<Application>](../../../docs/framework/net-native/application-element-net-native.md) 要素と [\<Library>](../../../docs/framework/net-native/library-element-net-native.md) 要素の子です。  
  
 [\<Method>](../../../docs/framework/net-native/method-element-net-native.md)  
 メソッドに実行時ポリシーを適用します。 これは、[\<Type>](../../../docs/framework/net-native/type-element-net-native.md) 要素と [\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) 要素の子です。  
  
 [\<MethodInstantiation>](../../../docs/framework/net-native/methodinstantiation-element-net-native.md)  
 構築されたジェネリック メソッドに実行時ポリシーを適用します。 これは、[\<Type>](../../../docs/framework/net-native/type-element-net-native.md) 要素と [\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) 要素の子です。  
  
 [\<Namespace>](../../../docs/framework/net-native/namespace-element-net-native.md)  
 名前空間内のすべての型に実行時ポリシーを適用します。  
  
 [\<Parameter>](../../../docs/framework/net-native/parameter-element-net-native.md)  
 メソッドに渡された引数の型に実行時ポリシーを適用します。  
  
 [\<Property>](../../../docs/framework/net-native/property-element-net-native.md)  
 プロパティに実行時ポリシーを適用します。 これは、[\<Type>](../../../docs/framework/net-native/type-element-net-native.md) 要素と [\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) 要素の子です。  
  
 [\<Subtypes>](../../../docs/framework/net-native/subtypes-element-net-native.md)  
 それを含む型から継承されたすべてのクラスに実行時ポリシーを適用します。  
  
 [\<Type>](../../../docs/framework/net-native/type-element-net-native.md)  
 型に実行時ポリシーを適用します。  
  
 [\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)  
 構築されたジェネリック型に実行時ポリシーを適用します。  
  
 [\<TypeParameter>](../../../docs/framework/net-native/typeparameter-element-net-native.md)  
 メソッドに渡された <xref:System.Type> 引数によって表される型に実行時ポリシーを適用します。  
  
## <a name="see-also"></a>参照  
 [rd.xml 構成ファイル リファレンス](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)
