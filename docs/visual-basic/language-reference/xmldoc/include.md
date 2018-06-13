---
title: '&lt;含める&gt;(Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- include XML tag
- <include> XML tag
ms.assetid: ba8e9173-82cd-460b-8938-a075a2dfb36d
ms.openlocfilehash: 65bc0439696612cd8331a9c0718efcfee83af574
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33602737"
---
# <a name="ltincludegt-visual-basic"></a>&lt;含める&gt;(Visual Basic)
型と、ソース コード内のメンバーを表す別のファイルを参照します。  
  
## <a name="syntax"></a>構文  
  
```xml  
<include file="filename" path="tagpath[@name='id']" />  
```  
  
#### <a name="parameters"></a>パラメーター  
 `filename`  
 必須。 ドキュメントを含むファイルの名前。 ファイル名をパスで修飾することができます。 囲む`filename`を二重引用符 ("") です。  
  
 `tagpath`  
 必須。 タグ `name` につながる `filename` 内のタグのパス。 パスを二重引用符で囲みます ("") です。  
  
 `name`  
 必須。 コメントの前に、タグの名前指定子。 `Name` `id`です。  
  
 `id`  
 必須。 コメントの前に配置するタグの ID。 ID を単一引用符で囲みます (' ')。  
  
## <a name="remarks"></a>コメント  
 使用して、`<include>`タイプを記述する別のファイル内のコメントおよびソース コード内のメンバーを参照するタグです。 これは文書化のコメントをソース コード ファイル内に直接配置する方法の代替です。  
  
 `<include>`タグは、W3C XML Path Language (XPath) Version 1.0 の推奨設定を使用します。 カスタマイズする方法の詳細については、`<include>`使用については、「http://www.w3.org/TR/xpathです。  
  
## <a name="example"></a>例  
 この例では、`<include>`メンバー ドキュメント コメントをという名前のファイルからインポートするタグ`commentFile.xml`です。  
  
 [!code-vb[VbVbcnXmlDocComments#4](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/include_1.vb)]  
  
 形式、`commentFile.xml`のとおりです。  
  
```xml  
<Docs>  
<Members name="Open">  
<summary>Opens a file.</summary>  
<param name="filename">File name to open.</param>  
</Members>  
<Members name="Close">  
<summary>Closes a file.</summary>  
<param name="filename">File name to close.</param>  
</Members>  
</Docs>  
```  
  
## <a name="see-also"></a>関連項目  
 [XML のコメント用タグ](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)
