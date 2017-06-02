---
title: "&lt;「解説」&gt; (Visual Basic) |Microsoft ドキュメント"
ms.custom: 
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
- <remarks> XML tag
- remarks XML tag
ms.assetid: c6241773-a7ed-41c9-9a8b-9722a0c606a9
caps.latest.revision: 13
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 89f8d321505b528d07fd04780cec06fb65b0e05e
ms.contentlocale: ja-jp
ms.lasthandoff: 03/13/2017

---
# <a name="ltremarksgt-visual-basic"></a>&lt;「解説」&gt; (Visual Basic)
メンバーの「解説」セクションをを指定します。  
  
## <a name="syntax"></a>構文  
  
```xml  
<remarks>description</remarks>  
```  
  
#### <a name="parameters"></a>パラメーター  
 `description`  
 メンバーの説明。  
  
## <a name="remarks"></a>コメント  
 使用して、`<remarks>`で指定された情報を補足すると、型に関する情報を追加するタグ[\<概要 >](../../../visual-basic/language-reference/xmldoc/summary.md)します。  
  
 この情報は、オブジェクト ブラウザーで表示されます。 オブジェクト ブラウザーの詳細については、次を参照してください。[コードの構造を表示する](https://docs.microsoft.com/visualstudio/ide/viewing-the-structure-of-code)です。  
  
 使用してコンパイル[/doc](../../../visual-basic/reference/command-line-compiler/doc.md)してドキュメント コメントをファイルにします。  
  
## <a name="example"></a>例  
 この例では、`<remarks>`何かを説明するタグ、`UpdateRecord`メソッドです。  
  
 [!code-vb[VbVbcnXmlDocComments&6;](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/remarks_1.vb)]  
  
## <a name="see-also"></a>関連項目  
 [XML のコメント用タグ](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)
