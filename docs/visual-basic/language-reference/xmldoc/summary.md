---
title: "&lt;概要&gt;(Visual Basic) |Microsoft ドキュメント"
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
- <summary> XML tag
- summary XML tag
ms.assetid: 861c847d-dd94-478a-aa23-bf4899cdc848
caps.latest.revision: 12
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
ms.openlocfilehash: ad2053e21e58c49205fe869a484cb2dffd2169ee
ms.lasthandoff: 03/13/2017

---
# <a name="ltsummarygt-visual-basic"></a>&lt;概要&gt;(Visual Basic)
メンバーの概要を指定します。  
  
## <a name="syntax"></a>構文  
  
```  
<summary>description</summary>  
```  
  
#### <a name="parameters"></a>パラメーター  
 `description`  
 オブジェクトの概要です。  
  
## <a name="remarks"></a>コメント  
 使用して、`<summary>`型または型のメンバーを記述するタグです。 使用[\<解説 >](../../../visual-basic/language-reference/xmldoc/remarks.md)型の説明に補足情報を追加します。  
  
 テキストを`<summary>`タグは、IntelliSense の種類に関する情報の唯一のソースであり、オブジェクト ブラウザーでも表示されます。 オブジェクト ブラウザーの詳細については、次を参照してください。[コードの構造を表示する](https://docs.microsoft.com/visualstudio/ide/viewing-the-structure-of-code)です。  
  
 使用してコンパイル[/doc](../../../visual-basic/reference/command-line-compiler/doc.md)してドキュメント コメントをファイルにします。  
  
## <a name="example"></a>例  
 この例では、`<summary>`を記述するタグ、`ResetCounter`メソッドと`Counter`プロパティです。  
  
 [!code-vb[VbVbcnXmlDocComments&#1;](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/summary_1.vb)]  
  
## <a name="see-also"></a>関連項目  
 [XML のコメント用タグ](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)
