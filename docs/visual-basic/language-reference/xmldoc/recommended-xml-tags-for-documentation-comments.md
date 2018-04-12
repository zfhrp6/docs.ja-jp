---
title: ドキュメント コメントとして推奨される XML タグ (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.XmlDocComment
helpviewer_keywords:
- tags, XML
- XML comments, recommended tags [Visual Basic]
- comments, recommended XML tags
ms.assetid: 294e0736-ff1e-498e-af83-6db71ed41a72
caps.latest.revision: 14
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 54712deb8bb2a5ed1e7b1f5fb8aa073dcdaf76d6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="recommended-xml-tags-for-documentation-comments-visual-basic"></a>ドキュメント コメントとして推奨される XML タグ (Visual Basic)
[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]コンパイラは、コードを XML ファイルにドキュメント コメントを処理できます。 その他のツールを使用して、ドキュメントを XML ファイルに変換することができます。  
  
 XML コメントは、型など、コード コンス トラクターでは許可し、メンバーを入力します。 部分の型の型の 1 つだけの一部はそのメンバーをコメントに制限はありませんが XML コメントを持つことができます。  
  
> [!NOTE]
>  ドキュメント コメントは、名前空間には適用できません。 理由は、1 つの名前空間は、複数のアセンブリにまたがってこと、および同時に読み込まれるすべてのアセンブリがあることです。  
  
 コンパイラは、タグを有効な XML を処理します。 次のタグは、ユーザー ドキュメントでよく使用される機能を提供します。  
  
||||  
|---|---|---|  
|[\<c>](../../../visual-basic/language-reference/xmldoc/c.md)|[\<code>](../../../visual-basic/language-reference/xmldoc/code.md)|[\<example>](../../../visual-basic/language-reference/xmldoc/example.md)|  
|[\<例外 >](../../../visual-basic/language-reference/xmldoc/exception.md) <sup>1</sup>|[\<含める >](../../../visual-basic/language-reference/xmldoc/include.md) <sup>1</sup>|[\<list>](../../../visual-basic/language-reference/xmldoc/list.md)|  
|[\<para>](../../../visual-basic/language-reference/xmldoc/para.md)|[\<param >](../../../visual-basic/language-reference/xmldoc/param.md) <sup>1</sup>|[\<paramref>](../../../visual-basic/language-reference/xmldoc/paramref.md)|  
|[\<アクセス許可 >](../../../visual-basic/language-reference/xmldoc/permission.md) <sup>1</sup>|[\<remarks>](../../../visual-basic/language-reference/xmldoc/remarks.md)|[\<returns>](../../../visual-basic/language-reference/xmldoc/returns.md)|  
|[\<参照してください >](../../../visual-basic/language-reference/xmldoc/see.md) <sup>1</sup>|[\<seealso >](../../../visual-basic/language-reference/xmldoc/seealso.md) <sup>1</sup>|[\<summary>](../../../visual-basic/language-reference/xmldoc/summary.md)|  
|[\<typeparam >](../../../visual-basic/language-reference/xmldoc/typeparam.md) <sup>1</sup>|[\<value>](../../../visual-basic/language-reference/xmldoc/value.md)||  
  
 (<sup>1</sup>コンパイラが構文を検証します)。  
  
> [!NOTE]
>  山かっこドキュメント コメントのテキストに表示される場合を使用して`<`と`>`です。 たとえば、文字列`"<text in angle brackets>"`として表示されます`<text in angle``brackets>`です。  
  
## <a name="see-also"></a>関連項目  
 [XML の使用によるコードのドキュメントの作成](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md)  
 [/doc](../../../visual-basic/reference/command-line-compiler/doc.md)  
 [方法: XML ドキュメントを作成する](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)
