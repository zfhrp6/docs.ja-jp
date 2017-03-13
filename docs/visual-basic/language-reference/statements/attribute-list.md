---
title: "Attribute List (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "attribute list"
  - "attributes [Visual Basic], applying"
ms.assetid: 5880073a-68a4-4b6b-8a07-ace32959a4e2
caps.latest.revision: 18
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 18
---
# Attribute List (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

宣言されたプログラミング要素に適用する属性を指定します。  複数の属性を指定するときは、コンマ \(,\) で区切ります。  属性を 1 つ定義する場合の構文は次のとおりです。  
  
## 構文  
  
```  
[ attributemodifier ] attributename [ ( attributearguments | attributeinitializer ) ]  
```  
  
## 指定項目  
 `attributemodifier`  
 ソース ファイルの先頭に定義する属性に、必ず指定します。  [Assembly](../../../visual-basic/language-reference/modifiers/assembly.md) または [Module](../../../visual-basic/language-reference/modifiers/module-keyword.md) を指定できます。  
  
 `attributename`  
 必ず指定します。  属性の名前です。  
  
 `attributearguments`  
 省略可能です。  この属性の位置の引数のリストです。  複数の引数を指定するときは、コンマ \(,\) で区切ります。  
  
 `attributeinitializer`  
 省略可能です。  この属性の変数初期化子またはプロパティ初期化子のリストです。  複数の初期化子を指定するときは、コンマ \(,\) で区切ります。  
  
## 解説  
 ほとんどすべてのプログラミング要素 \(型、プロシージャ、プロパティなど\) に、1 つ以上の属性を適用できます。  属性はアセンブリのメタデータに格納され、コードに注釈を付けたり、特定のプログラミング要素の使い方を指定したりするのに役立ちます。  Visual Basic や .NET Framework で定義された属性を適用することも、独自の属性を定義することもできます。  
  
 属性を使用する状況の詳細については、「[属性](../Topic/Attributes%20\(C%23%20and%20Visual%20Basic\).md)」を参照してください。  属性名の詳細については、「[Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)」を参照してください。  
  
## 規則  
  
-   **定義する場所。**属性は、宣言されたほとんどのプログラミング要素に適用できます。  1 つ以上の属性を適用するには、要素の宣言の先頭に*属性ブロック*を記述します。  属性リストの各エントリには、適用する属性の他に、その属性を呼び出す際に使用する修飾子や引数を指定します。  
  
-   **山かっこ。**属性リストを指定するには、属性を山かっこ \("`<`" と "`>`"\) で囲む必要があります。  
  
-   **宣言に含める。**属性は独立したステートメントとして宣言するのではなく、要素の宣言に含める必要があります。  行連結シーケンス \(" `_`"\) を使用すると、宣言ステートメントを複数行に続くソース コードに記述できます。  
  
-   **修飾子。**ソース ファイルの先頭にあるプログラミング要素に適用する属性には、必ず属性修飾子 \(`Assembly` または `Module`\) を指定する必要があります。  それ以外のプログラミング要素に適用される属性に対して、属性修飾子を指定することはできません。  
  
-   **引数。**属性に対するすべての位置指定引数を、すべての変数初期化子またはプロパティ初期化子の前に置く必要があります。  
  
## 使用例  
 <xref:System.Runtime.InteropServices.DllImportAttribute> 属性を `Function` プロシージャのスケルトン定義に適用する例は次のようになります。  
  
 [!code-vb[VbVbalrStatements#1](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/attribute-list_1.vb)]  
  
 <xref:System.Runtime.InteropServices.DllImportAttribute> は、属性が適用されたプロシージャが、アンマネージ ダイナミック リンク ライブラリ \(DLL: Dynamic\-Link Library\) のエントリ ポイントであることを示します。  この属性は、DLL 名を位置指定引数として指定し、その他の情報を変数初期化子として指定します。  
  
## 参照  
 [Assembly](../../../visual-basic/language-reference/modifiers/assembly.md)   
 [Module \<keyword\>](../../../visual-basic/language-reference/modifiers/module-keyword.md)   
 [属性](../Topic/Attributes%20\(C%23%20and%20Visual%20Basic\).md)   
 [方法 : コード内でステートメントを分割および連結する](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)