---
title: "ドキュメント コメント (Visual Basic) の推奨される XML タグ |Microsoft ドキュメント"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.XmlDocComment
dev_langs:
- VB
helpviewer_keywords:
- tags, XML
- XML comments, recommended tags [Visual Basic]
- comments, recommended XML tags
ms.assetid: 294e0736-ff1e-498e-af83-6db71ed41a72
caps.latest.revision: 14
author: stevehoag
ms.author: shoag
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
ms.openlocfilehash: c6a47c12bc24864ef6ac9f80054becad98ec97f1
ms.lasthandoff: 03/13/2017

---
# <a name="recommended-xml-tags-for-documentation-comments-visual-basic"></a>ドキュメント コメントとして推奨される XML タグ (Visual Basic)
[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]コンパイラは、XML ファイルに、コードのドキュメント コメントを処理します。 その他のツールを使用して、ドキュメントを XML ファイルに変換することができます。  
  
 XML コメントは、型などのコード コンス トラクターでは許可し、メンバーを入力します。 部分型の型の一部にすぎませんことができます XML コメントが、そのメンバーの注釈に制限はありません。  
  
> [!NOTE]
>  ドキュメントのコメントは、名前空間には適用できません。 理由は、1 つの名前空間がいくつかのアセンブリにまたがることができ、すべてのアセンブリを同時に読み込まれる必要があることです。  
  
 コンパイラは、有効な XML は、任意のタグを処理します。 次のタグは、ユーザー ドキュメントでよく使用される機能を提供します。  
  
||||  
|---|---|---|  
|[\<c >](../../../visual-basic/language-reference/xmldoc/c.md)|[\<コード >](../../../visual-basic/language-reference/xmldoc/code.md)|[\<例 >](../../../visual-basic/language-reference/xmldoc/example.md)|  
|[\<例外 >](../../../visual-basic/language-reference/xmldoc/exception.md) <sup>1</sup>|[\<含める >](../../../visual-basic/language-reference/xmldoc/include.md) <sup>1</sup>|[\<list>](../../../visual-basic/language-reference/xmldoc/list.md)|  
|[\<para >](../../../visual-basic/language-reference/xmldoc/para.md)|[\<param>](../../../visual-basic/language-reference/xmldoc/param.md) <sup>1</sup>|[\<paramref >](../../../visual-basic/language-reference/xmldoc/paramref.md)|  
|[\<アクセス許可 >](../../../visual-basic/language-reference/xmldoc/permission.md) <sup>1</sup>|[\<「解説」>](../../../visual-basic/language-reference/xmldoc/remarks.md)|[\<返します >](../../../visual-basic/language-reference/xmldoc/returns.md)|  
|[\<see>](../../../visual-basic/language-reference/xmldoc/see.md) <sup>1</sup>|[\<seealso >](../../../visual-basic/language-reference/xmldoc/seealso.md) <sup>1</sup>|[\<概要 >](../../../visual-basic/language-reference/xmldoc/summary.md)|  
|[\<typeparam >](../../../visual-basic/language-reference/xmldoc/typeparam.md) <sup>1</sup>|[\<値 >](../../../visual-basic/language-reference/xmldoc/value.md)||  
  
 (<sup>1</sup>コンパイラが構文を検証します)。  
  
> [!NOTE]
>  ドキュメント コメントのテキスト内に山かっこを実行する場合に、使用`<`と`>`です。 たとえば、文字列`"<text in angle brackets>"`でサポートされる`<text in angle``brackets>`します。  
  
## <a name="see-also"></a>関連項目  
 [XML を使用してコードを文書化します。](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md)   
 [/doc](../../../visual-basic/reference/command-line-compiler/doc.md)   
 [方法: XML ドキュメントを作成する](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)
