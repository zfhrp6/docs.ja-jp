---
title: '&lt;値&gt;(Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- <value> XML tag
- value XML tag
ms.assetid: 0b84b02e-9e6d-41b5-a926-0d5dc76dacb5
ms.openlocfilehash: f33a4ec32b45d8996bd39f0cc49097b5fd9252e4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="ltvaluegt-visual-basic"></a>&lt;値&gt;(Visual Basic)
プロパティの説明を指定します。  
  
## <a name="syntax"></a>構文  
  
```xml  
<value>property-description</value>  
```  
  
#### <a name="parameters"></a>パラメーター  
 `property-description`  
 プロパティの説明。  
  
## <a name="remarks"></a>コメント  
 使用して、`<value>`タグ プロパティについて説明します。 Visual Studio 開発環境で、コード ウィザードを使用してプロパティを追加する場合に追加、 [\<概要 >](../../../visual-basic/language-reference/xmldoc/summary.md)新しいプロパティのタグ。 手動で追加する必要がありますし、`<value>`プロパティを表す値を記述するタグです。  
  
 コンパイル時に [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) を指定して、ドキュメント コメントをファイルに出力します。  
  
## <a name="example"></a>例  
 この例では、`<value>`をどのような値を記述するタグ、`Counter`プロパティを保持します。  
  
 [!code-vb[VbVbcnXmlDocComments#1](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/value_1.vb)]  
  
## <a name="see-also"></a>関連項目  
 [XML のコメント用タグ](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)
