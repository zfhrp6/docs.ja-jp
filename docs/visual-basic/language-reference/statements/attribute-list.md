---
title: "属性 (Visual Basic) の一覧 |Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- attribute list
- attributes [Visual Basic], applying
ms.assetid: 5880073a-68a4-4b6b-8a07-ace32959a4e2
caps.latest.revision: 18
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: e360794ad217784e2358967bfbcc03959cd043b1
ms.lasthandoff: 03/13/2017

---
# <a name="attribute-list-visual-basic"></a>属性リスト (Visual Basic)
宣言されているプログラミング要素に適用する属性を指定します。 複数の属性を指定するときは、コンマで区切ります。 1 つの属性の構文を次に示します。  
  
## <a name="syntax"></a>構文  
  
```  
[ attributemodifier ] attributename [ ( attributearguments | attributeinitializer ) ]  
```  
  
## <a name="parts"></a>指定項目  
 `attributemodifier`  
 ソース ファイルの先頭に適用される属性に必要です。 できる[アセンブリ](../../../visual-basic/language-reference/modifiers/assembly.md)または[モジュール](../../../visual-basic/language-reference/modifiers/module-keyword.md)します。  
  
 `attributename`  
 必須です。 属性の名前。  
  
 `attributearguments`  
 省略可能です。 この属性の位置指定引数のリスト。 複数の引数は、コンマで区切られます。  
  
 `attributeinitializer`  
 省略可能です。 この属性の変数やプロパティの初期化子の一覧です。 複数の初期化子は、コンマで区切られます。  
  
## <a name="remarks"></a>コメント  
 ほぼすべてのプログラミング要素 (型、プロシージャ、プロパティ、およびなど) には、1 つまたは複数の属性を適用できます。 属性がアセンブリのメタデータに表示され、コードに注釈を付けるか、特定のプログラミング要素を使用する方法を指定するのに役立ちます。 Visual Basic と .NET Framework で定義されている属性を適用して、独自の属性を定義することができます。  

 属性を使用する場合の詳細については、次を参照してください。[属性の概要](../../../visual-basic/programming-guide/concepts/attributes/index.md)します。 詳細については、属性名は、次を参照してください。[宣言された要素の名前](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)します。  
  
## <a name="rules"></a>ルール  
  
-   **配置します。** 宣言されたほとんどのプログラミング要素に属性を適用できます。 配置する&1; つまたは複数の属性を適用する、*属性ブロック*要素宣言の先頭にします。 属性リストの各エントリは、属性を適用して、補助キーと属性のこの呼び出しを使用している引数を指定します。  
  
-   **山かっこ。** 属性リストを指定する場合は、山かっこで囲む必要があります ("`<`「と」`>`") です。  
  
-   **宣言の一部です。** 属性では、個別のステートメントではなく、要素の宣言を含める必要があります。 行連結シーケンスを使用することができます (" `_`") を複数のソース コード行に宣言のステートメントを拡張します。  
  
-   **修飾子。** 属性の修飾子 (`Assembly`または`Module`) にソース ファイルの先頭のプログラミング要素に適用されるすべての属性が必要です。 ソース ファイルの先頭の要素に適用される属性で属性の修飾子を設定することはできません。  
  
-   **引数。** 属性のすべての位置指定引数には、任意の変数やプロパティ初期化子が前にする必要があります。  
  
## <a name="example"></a>例  
 次の例では、適用、<xref:System.Runtime.InteropServices.DllImportAttribute>属性のスケルトンの定義を`Function`プロシージャ</xref:System.Runtime.InteropServices.DllImportAttribute>。  
  
 [!code-vb[VbVbalrStatements&#1;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/attribute-list_1.vb)]  
  
 <xref:System.Runtime.InteropServices.DllImportAttribute>属性付きの手順がアンマネージ ダイナミック リンク ライブラリ (DLL) のエントリ ポイントを表すことを示します。</xref:System.Runtime.InteropServices.DllImportAttribute> 属性は、位置指定引数として DLL 名と変数の初期化子とその他の情報を提供します。  
  
## <a name="see-also"></a>関連項目  
 [アセンブリ](../../../visual-basic/language-reference/modifiers/assembly.md)   
 [モジュール\<キーワード >](../../../visual-basic/language-reference/modifiers/module-keyword.md)   
 [属性の概要](../../../visual-basic/programming-guide/concepts/attributes/index.md)   
 [方法 : コード内でステートメントを分割および連結する](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)
