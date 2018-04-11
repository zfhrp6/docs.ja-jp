---
title: 二重引用符は、EscapeQuote が True に設定されている区切り符号で分けられたフィールドには有効なコメント トークンではありません。
ms.date: 07/20/2015
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrTextFieldParser_InvalidComment
ms.assetid: 636d4b81-00ba-4cfd-98f7-4d57036f494d
caps.latest.revision: 9
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 5677ee7415fe385805413ccbdec20762ac0573a0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="a-double-quote-is-not-a-valid-comment-token-for-delimited-fields-where-escapequote-is-set-to-true"></a>二重引用符は、EscapeQuote が True に設定されている区切り符号で分けられたフィールドには有効なコメント トークンではありません。
`TextFieldParser`の区切り記号として二重引用符が指定されましたが、 `EscapeQuotes` に `True`が設定されています。  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
-   `EscapeQuotes` を `False`に設定します。  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.SetDelimiters%2A>  
 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.Delimiters%2A>  
 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser>  
 [方法: コンマ区切りのテキスト ファイルを読み取る](../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-comma-delimited-text-files.md)
