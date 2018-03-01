---
title: "{} エスケープ シーケンスのマークアップ拡張機能"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- '{}'
helpviewer_keywords:
- XAML [XAML Services], quotation mark (")
- '{} escape sequence [XAML Services]'
- XAML [XAML Services], {} escape sequence
- XAML [XAML Services], escape sequence
- quotation mark (") [XAML Services]
- escape sequence [XAML Services]
ms.assetid: 3ce3e2ad-a868-43f9-9c98-b29561cb146e
caps.latest.revision: 
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 8419a1e89d5e94b9868b0fd1fb81540253efca5d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="-escape-sequence--markup-extension"></a>{} エスケープ シーケンス/マークアップ拡張機能
属性値を XAML エスケープ シーケンスを提供します。 エスケープ シーケンスは、リテラルとして解釈する属性内の後続の値を許可します。  
  
## <a name="xaml-attribute-usage"></a>XAML 属性の使用方法  
  
```xml  
<object property="{} literalValue" .../>  
```  
  
## <a name="xaml-property-element-usage"></a>XAML プロパティ要素の使用  
  
```  
<object>  
  <object.property>  
    {} literalValue  
  </object.property>  
</object>  
```  
  
## <a name="xaml-values"></a>XAML 値  
  
|||  
|-|-|  
|*literalValue*|エスケープ シーケンスに続くリテラル文字列。 通常この文字列が、開くまたは閉じる中かっこ ({または})。|  
  
## <a name="remarks"></a>コメント  
 始め中かっこ ({}) は、XAML でのリテラル文字として使用できるようにする、エスケープ シーケンス ({}) が使用されます。  
  
 右中かっこ (}) があるかどうかを判断するには、次の文字をチェックするただし、XAML リーダーは通常、マークアップ拡張機能のエントリ ポイントを表すために始め中かっこ ({}) を使用します。 2 つの中かっこ ({}) は、隣接するが、場合にのみと見なされます、エスケープ シーケンス。  
  
 エスケープ シーケンスが発生した場合、XAML リーダーは文字列として残りの文字列を処理する必要があります。 ただし、エスケープ シーケンスを実行する型コンバーターを持つメンバーに適用されている場合、文字列を行うことも型変換と XAML ライターによって解釈されます。  
  
 エスケープ シーケンスは、マークアップ拡張機能ではなく、クラスではサポートされません。 ただし、これは、XAML リーダー (カスタム XAML リーダーを含む) が遵守する必要があります規則です。  
  
 引用符 (") は、この方法でエスケープ シーケンスとして使用できません。 非プロパティのプロパティの値として、引用符を設定する必要がある場合は、プロパティ要素構文を使用またはプロパティ要素内の文字列として引用符を配置し XML 文字エンティティを使用します。 コンテンツのプロパティの引用符は、コンテンツ全体を指定できます。  
  
 エスケープ シーケンス ({}) は、XAML マークアップ拡張機能が表示される場所に名前空間の修飾子を含める必要のある XML 型を指定するときに頻繁に必要です。 これには、等号 (=) の直後に、マークアップ拡張機能と、XAML 属性の値の開始が含まれます。 次の例では、XAML 属性の値の先頭に表示される XML 名前空間のエスケープ シーケンスを示します。  
  
 [!code-xaml[XLINQExample#StackPanelResources](../../../samples/snippets/csharp/VS_Snippets_Wpf/XLinqExample/CSharp/Window1.xaml#stackpanelresources)]  
  
## <a name="see-also"></a>参照  
 [XAML の型コンバーターおよびマークアップ拡張機能](../../../docs/framework/xaml-services/type-converters-and-markup-extensions-for-xaml.md)  
 [XML 文字エンティティと XAML](../../../docs/framework/xaml-services/xml-character-entities-and-xaml.md)
