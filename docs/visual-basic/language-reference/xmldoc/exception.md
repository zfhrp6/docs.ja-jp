---
title: "&lt;例外&gt;(Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- <exception> XML tag
- exception XML tag
ms.assetid: c0517549-171e-4dae-ab88-a9c1700b6eee
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 8d718a7c2213a61f7f60ed80a04f9bd03f6c770a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="ltexceptiongt-visual-basic"></a>&lt;例外&gt;(Visual Basic)
どの例外がスローされる可能性を指定します。  
  
## <a name="syntax"></a>構文  
  
```xml  
<exception cref="member">description</exception>  
```  
  
#### <a name="parameters"></a>パラメーター  
 `member`  
 現在のコンパイル環境から使用できる例外の参照。 コンパイラは、指定された例外が存在し、出力の XML で `member` が正規要素名に変換されることを確認します。 `member` は、二重引用符 (" ") で囲む必要があります。  
  
 `description`  
 説明です。  
  
## <a name="remarks"></a>コメント  
 使用して、`<exception>`タグをどの例外をスローするを指定します。 このタグは、メソッドの定義に適用されます。  
  
 コンパイル時に [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) を指定して、ドキュメント コメントをファイルに出力します。  
  
## <a name="example"></a>例  
 この例では、`<exception>`例外を記述するタグを`IntDivide`関数がスローすることができます。  
  
 [!code-vb[VbVbcnXmlDocComments#3](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/exception_1.vb)]  
  
## <a name="see-also"></a>関連項目  
 [XML のコメント用タグ](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)
