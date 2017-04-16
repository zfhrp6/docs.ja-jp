---
title: "{} Escape Sequence / Markup Extension | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "{}"
helpviewer_keywords: 
  - "XAML [XAML Services], quotation mark (")"
  - "{} escape sequence [XAML Services]"
  - "XAML [XAML Services], {} escape sequence"
  - "XAML [XAML Services], escape sequence"
  - "quotation mark (") [XAML Services]"
  - "escape sequence [XAML Services]"
ms.assetid: 3ce3e2ad-a868-43f9-9c98-b29561cb146e
caps.latest.revision: 21
author: "wadepickett"
ms.author: "wpickett"
manager: "wpickett"
---
# {} Escape Sequence / Markup Extension
属性値に XAML エスケープ シーケンスを提供します。  属性にエスケープ シーケンスを使用すると、その後続の値がリテラルとして解釈されます。  
  
## XAML 属性の使用方法  
  
```  
<object property="{} literalValue" .../>  
```  
  
## XAML プロパティ要素の使用方法  
  
```  
<object>  
  <object.property>  
    {} literalValue  
  </object.property>  
</object>  
```  
  
## XAML 値  
  
|||  
|-|-|  
|*literalValue*|エスケープ シーケンスの後に続くリテラル文字列。  通常、この文字列には、始め中かっこまたは終わり中かっこ \({ または }\) が含まれています。|  
  
## 解説  
 エスケープ シーケンス \({}\) を使用すると、XAML で始め中かっこ \({\) 文字をリテラル文字として使用できるようになります。  
  
 XAML リーダーは通常、始め中かっこ \({\) を使用してマークアップ拡張機能のエントリ ポイントを示しますが、最初に次の文字をチェックして右中かっこ \(}\) に該当するかどうかを確認します。  2 つの中かっこ \({}\) が隣接しているときに初めて、エスケープ シーケンスと見なされます。  
  
 エスケープ シーケンスが検出された場合、文字列の残りの部分はすべて XAML リーダーによって文字列として処理される必要があります。  ただし、型コンバーターを持つメンバーにエスケープ シーケンスが適用された場合、XAML ライターが文字列を解釈するときに、その文字列に型変換が適用されます。  
  
 エスケープ シーケンスはマークアップ拡張機能ではなく、クラスによってサポートされません。  ただし、これはエスケープ変換に該当し、XAML リーダー \(カスタム XAML リーダーを含む\) で必ず考慮されます。  
  
 この方法では、引用符 \("\) をエスケープ シーケンスとして使用することはできません。  引用符を非コンテンツ プロパティのプロパティ値として設定する必要がある場合は、プロパティ要素構文を使用して引用符をプロパティ要素の内部の文字列として配置するか、または XML の文字エンティティを使用します。  コンテンツ プロパティでは、引用符のみのコンテンツを指定できます。  
  
 エスケープ シーケンス \({}\) は、XAML マークアップ拡張機能が使用される可能性のある場所に名前空間修飾子を含める必要がある XML 型を指定するときによく必要になります。  たとえば、XAML 属性値の先頭やマークアップ拡張内での等号記号 \(\=\) の直後などです。  次の例は、XAML 属性値の先頭にある XML 名前空間のエスケープ シーケンスを示しています。  
  
 [!code-xml[XLINQExample#StackPanelResources](../../../samples/snippets/csharp/VS_Snippets_Wpf/XLinqExample/CSharp/Window1.xaml#stackpanelresources)]  
  
## 参照  
 [Type Converters and Markup Extensions for XAML](../../../docs/framework/xaml-services/type-converters-and-markup-extensions-for-xaml.md)   
 [XML Character Entities and XAML](../../../docs/framework/xaml-services/xml-character-entities-and-xaml.md)