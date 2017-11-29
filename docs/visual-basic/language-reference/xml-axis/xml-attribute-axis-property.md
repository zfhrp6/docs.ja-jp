---
title: "XML 属性軸プロパティ (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.XmlPropertyAttributeAxis
helpviewer_keywords:
- attribute axis property [Visual Basic]
- Visual Basic code, accessing XML
- XML attribute axis property [Visual Basic]
- XML axis [Visual Basic], attribute
- XML [Visual Basic], accessing
ms.assetid: 7a4777e1-0618-4de9-9510-fb9ace2bf4db
caps.latest.revision: "23"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a286c70f57128d0406b3a300610fea5e1c44b32d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="xml-attribute-axis-property-visual-basic"></a>XML 属性軸プロパティ (Visual Basic)
属性の値にアクセスできるように、<xref:System.Xml.Linq.XElement>オブジェクトのコレクションの最初の要素をまたは<xref:System.Xml.Linq.XElement>オブジェクト。  
  
## <a name="syntax"></a>構文  
  
```  
      object.@attribute  
-or-  
object.@<attribute>  
```  
  
## <a name="parts"></a>指定項目  
 `object`  
 必須です。 <xref:System.Xml.Linq.XElement>オブジェクトのコレクションまたは<xref:System.Xml.Linq.XElement>オブジェクト。  
  
 .@  
 必ず指定します。 属性軸プロパティの開始を示します。  
  
 <  
 省略可能です。 属性の名前の先頭を示すとき`attribute`で有効な識別子ではない[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]です。  
  
 `attribute`  
 必須です。 アクセスする場合、フォームの属性の名前 [`prefix`:]`name`です。  
  
|パーツ|説明|  
|----------|-----------------|  
|`prefix`|省略可能です。 属性の XML 名前空間プレフィックス。 `Imports` ステートメントを使用して定義されているグローバル XML 名前空間を指定する必要があります。|  
|`name`|必須です。 ローカルの属性名です。 参照してください[宣言する XML 要素と属性の名前](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)です。|  
  
 \>  
 省略可能です。 属性の名前の終了を示すとき`attribute`で有効な識別子ではない[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]です。  
  
## <a name="return-value"></a>戻り値  
 値を含む文字列`attribute`です。 属性名が存在しない場合`Nothing`が返されます。  
  
## <a name="remarks"></a>コメント  
 名を使用して、属性の値にアクセスする XML 属性軸プロパティを使用することができます、<xref:System.Xml.Linq.XElement>オブジェクトのコレクションの最初の要素から、または<xref:System.Xml.Linq.XElement>オブジェクト。 名前、属性値を取得またはスコアで始まる新しい名前を指定することによって要素に新しい属性を追加することができます、@ 識別子。  
  
 XML 属性を使用して、参照するとき、文字列として @ 識別子、属性の値が返され、明示的に指定する必要はありません、<xref:System.Xml.Linq.XAttribute.Value%2A>プロパティです。  
  
 XML 属性の名前付け規則の名前付け規則が異なる[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]識別子。 有効な Visual Basic 識別子ではない名前を持つ XML 属性にアクセスする名前は山かっこで囲みます (\<および >)。  
  
## <a name="xml-namespaces"></a>XML 名前空間  
 属性軸プロパティの名前を使用してグローバルに宣言されている XML 名前空間プレフィックスのみを使用できます、`Imports`ステートメントです。 XML 要素リテラル内でローカルに宣言されている XML 名前空間プレフィックスは使用できません。 詳細については、次を参照してください。 [Imports ステートメント (XML Namespace)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md)です。  
  
## <a name="example"></a>例  
 次の例は、という名前の XML 属性の値を取得する方法を示しています。`type`という XML 要素のコレクションから`phone`です。  
  
 [!code-vb[VbXMLSamples#12](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-attribute-axis-property_1.vb)]  
  
 このコードを実行すると、次のテキストが表示されます。  
  
 `<phoneTypes>`  
  
 `<type>home</type>`  
  
 `<type>work</type>`  
  
 `</phoneTypes>`  
  
## <a name="example"></a>例  
 次の例は、宣言の一部として、XML では、動的のインスタンスに属性を追加することで、両方の XML 要素の属性を作成する方法を示します、<xref:System.Xml.Linq.XElement>オブジェクト。 `type`属性が宣言によって作成されると、`owner`属性が動的に作成します。  
  
 [!code-vb[VbXMLSamples#44](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-attribute-axis-property_2.vb)]  
  
 このコードを実行すると、次のテキストが表示されます。  
  
```xml  
<phone type="home" owner="Harris, Phyllis">206-555-0144</phone>  
```  
  
## <a name="example"></a>例  
 次の例では、山かっこ構文を使用してという名前の XML 属性の値を取得`number-type`、有効な識別子ではない[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]です。  
  
 [!code-vb[VbXMLSamples#13](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-attribute-axis-property_3.vb)]  
  
 このコードを実行すると、次のテキストが表示されます。  
  
 `Phone type: work`  
  
## <a name="example"></a>例  
 次の例では、`ns` を名前空間プレフィックスとして宣言します。 使用して、名前空間のプレフィックスを XML リテラルを作成し、アクセスの修飾名を持つ最初の子ノード"`ns:name`"です。  
  
 [!code-vb[VbXMLSamples#14](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-attribute-axis-property_4.vb)]  
  
 このコードを実行すると、次のテキストが表示されます。  
  
 `Phone type: home`  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Xml.Linq.XElement>  
 [XML 軸プロパティ](../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md)  
 [XML リテラル](../../../visual-basic/language-reference/xml-literals/index.md)  
 [Visual Basic での XML の作成](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)  
 [宣言する XML 要素と属性の名前](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)
