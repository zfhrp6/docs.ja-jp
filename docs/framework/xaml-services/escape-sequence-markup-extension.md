---
title: '{} エスケープ シーケンスのマークアップ拡張機能'
ms.date: 03/30/2017
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
ms.openlocfilehash: a90f6928d68eddd29762e6206769dd7f07704e4c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33564522"
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
|*LiteralValue*|エスケープ シーケンスに続くリテラル文字列。 通常この文字列が、開くまたは閉じる中かっこ ({または})。|  
  
## <a name="remarks"></a>コメント  
 エスケープ シーケンス ({}) 始め中かっこ ({}) は、XAML でのリテラル文字として使用できるようにするために使用します。  
  
 右中かっこ (}) があるかどうかを判断するには、次の文字をチェックするただし、XAML リーダーは通常、マークアップ拡張機能のエントリ ポイントを表すために始め中かっこ ({}) を使用します。 のみときに、2 つ右中かっこ ({}) は隣接するは、それらのエスケープ シーケンスと見なされます。  
  
 エスケープ シーケンスが発生した場合、XAML リーダーは文字列として残りの文字列を処理する必要があります。 ただし、エスケープ シーケンスを実行する型コンバーターを持つメンバーに適用されている場合、文字列を行うことも型変換と XAML ライターによって解釈されます。  
  
 エスケープ シーケンスは、マークアップ拡張機能ではなく、クラスではサポートされません。 ただし、これは、XAML リーダー (カスタム XAML リーダーを含む) が遵守する必要があります規則です。  
  
 引用符 (") は、この方法でエスケープ シーケンスとして使用できません。 非プロパティのプロパティの値として、引用符を設定する必要がある場合は、プロパティ要素構文を使用またはプロパティ要素内の文字列として引用符を配置し XML 文字エンティティを使用します。 コンテンツのプロパティの引用符は、コンテンツ全体を指定できます。  
  
 エスケープ シーケンス ({}) は、XAML マークアップ拡張機能が表示される場所に名前空間の修飾子を含める必要のある XML 型を指定する場合に頻繁に必要です。 これには、等号 (=) の直後に、マークアップ拡張機能と、XAML 属性の値の開始が含まれます。 次の例では、XAML 属性の値の先頭に表示される XML 名前空間のエスケープ シーケンスを示します。  
  
 [!code-xaml[XLINQExample#StackPanelResources](../../../samples/snippets/csharp/VS_Snippets_Wpf/XLinqExample/CSharp/Window1.xaml#stackpanelresources)]  
  
## <a name="see-also"></a>関連項目  
 [XAML の型コンバーターおよびマークアップ拡張機能](../../../docs/framework/xaml-services/type-converters-and-markup-extensions-for-xaml.md)  
 [XML 文字エンティティと XAML](../../../docs/framework/xaml-services/xml-character-entities-and-xaml.md)
