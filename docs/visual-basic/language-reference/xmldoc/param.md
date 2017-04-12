---
title: "&lt;param&gt; (Visual Basic) |Microsoft ドキュメント"
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
- param XML tag
- <param> XML tag
ms.assetid: 4e32e86f-f6f3-4301-b7fc-2f321fb54368
caps.latest.revision: 14
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
ms.openlocfilehash: 41852a7fc41595050940d87f9e741df5cb23361c
ms.lasthandoff: 03/13/2017

---
# <a name="ltparamgt-visual-basic"></a>&lt;param&gt; (Visual Basic)
パラメーター名と説明を定義します。  
  
## <a name="syntax"></a>構文  
  
```  
<param name="name">description</param>  
```  
  
#### <a name="parameters"></a>パラメーター  
 `name`  
 メソッドのパラメーターの名前。 名前は二重引用符で囲みます ("") です。  
  
 `description`  
 パラメーターの説明です。  
  
## <a name="remarks"></a>コメント  
 `<param>`メソッドのパラメーターのいずれかを説明するメソッドの宣言のコメントでタグを使用する必要があります。  
  
 テキストを`<param>`タグは、次の場所に表示されます。  
  
-   IntelliSense のパラメーター情報です。 詳細については、「[IntelliSense の使用](https://docs.microsoft.com/visualstudio/ide/using-intellisense)」を参照してください。  
  
-   オブジェクト ブラウザー。 詳細については、「[コードの構造の表示](https://docs.microsoft.com/visualstudio/ide/viewing-the-structure-of-code)」を参照してください。  
  
 使用してコンパイル[/doc](../../../visual-basic/reference/command-line-compiler/doc.md)してドキュメント コメントをファイルにします。  
  
## <a name="example"></a>例  
 この例では、`<param>`を記述するタグ、`id`パラメーター。  
  
 [!code-vb[VbVbcnXmlDocComments&6;](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/param_1.vb)]  
  
## <a name="see-also"></a>関連項目  
 [XML のコメント用タグ](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)
