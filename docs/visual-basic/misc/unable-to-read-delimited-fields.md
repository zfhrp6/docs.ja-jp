---
title: "EscapeQuotes が True に設定されている場合、二重引用符は有効な区切り記号でないため、区切り記号で分けられたフィールドを読み取れません"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrTextFieldParser_IllegalDelimiter
ms.assetid: ab8a0c3a-b89c-4617-9e31-7e81f5dca433
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 3644165d0c25189f29f3f878a17b0d9bf4e2623b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="unable-to-read-delimited-fields-because-a-double-quote-is-not-a-legal-delimiter-when-escapequotes-is-set-to-true"></a>EscapeQuotes が True に設定されている場合、二重引用符は有効な区切り記号でないため、区切り記号で分けられたフィールドを読み取れません
引用符 (") が区切り文字として指定されており、 `TextFieldParser` が `EscapeQuotes` に設定されているため、 `True`はファイルからの読み取りができません。  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
-   `EscapeQuotes` を `False`に設定します。  
  
## <a name="see-also"></a>関連項目  
 [TextFieldParser.SetDelimiters メソッド](http://msdn.microsoft.com/en-us/21fa40ec-5866-4d0e-9fd9-c708a190dcc9)  
 [TextFieldParser.Delimiters プロパティ](http://msdn.microsoft.com/en-us/4eb18f4d-3011-40a9-b668-be93eed0444f)  
 [方法: コンマ区切りのテキスト ファイルを読み取る](../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-comma-delimited-text-files.md)  
 [TextFieldParser オブジェクト](../../visual-basic/language-reference/objects/textfieldparser-object.md)
