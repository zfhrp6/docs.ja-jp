---
title: '&lt;リスト&gt;(Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- listheader XML tag
- <item> XML tag
- <list> XML tag
- <listheader> XML tag
- term XML tag
- list XML tag
- <description> XML tag
- description XML tag
- item XML tag
- <term> XML tag
ms.assetid: ec35fced-d58e-4520-a764-0691256e014b
ms.openlocfilehash: f03924217393e1e909b086b282f1c62ddb471522
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="ltlistgt-visual-basic"></a>&lt;リスト&gt;(Visual Basic)
リストまたはテーブルを定義します。  
  
## <a name="syntax"></a>構文  
  
```xml  
<list type="type">  
   <listheader>  
      <term>term</term>  
      <description>description</description>  
   </listheader>  
   <item>  
      <term>term</term>  
      <description>description</description>  
   </item>  
</list>  
```  
  
#### <a name="parameters"></a>パラメーター  
 `type`  
 リストの型。 箇条書きリスト、番号付きリストは、または 2 つの列のテーブルには、"table"の"number"の「行頭文字」をする必要があります。  
  
 `term`  
 場合のみ使用`type`"table"には 説明タグで定義されている用語を定義します。  
  
 `description`  
 ときに`type`「の行頭文字」または「番号」 `description` 、リスト内の項目は、ときに`type`"table"は`description`の定義は、`term`です。  
  
## <a name="remarks"></a>コメント  
 `<listheader>`ブロックは、テーブルまたは定義の一覧の見出しを定義します。 のみのエントリを指定する必要があるテーブルを定義するときに`term`見出しにします。  
  
 リスト内の各項目を指定した、`<item>`ブロックします。 定義リストを作成するときに、両方を指定する必要があります`term`と`description`です。 ただし、テーブル、箇条書きリスト、または番号付きリストにのみ指定する必要のエントリ`description`です。  
  
 リストまたはテーブルに指定できるは多く`<item>`に応じてをブロックします。  
  
 コンパイル時に [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) を指定して、ドキュメント コメントをファイルに出力します。  
  
## <a name="example"></a>例  
 この例では、 `<list>` 「解説」セクションで、箇条書きリストを定義するタグです。  
  
 [!code-vb[VbVbcnXmlDocComments#5](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/list_1.vb)]  
  
## <a name="see-also"></a>関連項目  
 [XML のコメント用タグ](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)
