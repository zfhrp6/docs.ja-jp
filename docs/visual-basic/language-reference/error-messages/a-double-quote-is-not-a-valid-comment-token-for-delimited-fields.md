---
title: 二重引用符は、EscapeQuote が True に設定されている区切り符号で分けられたフィールドには有効なコメント トークンではありません。
ms.date: 07/20/2015
f1_keywords:
- vbrTextFieldParser_InvalidComment
ms.assetid: 636d4b81-00ba-4cfd-98f7-4d57036f494d
ms.openlocfilehash: 5838ef168523e8ba31fe5db93781bc409690e7ce
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33584140"
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
