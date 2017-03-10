---
title: "最後の要素以外のすべてのフィールド幅は 0 より大きくなければなりません | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vbrTextFieldParser_FieldWidthsMustPositive"
ms.assetid: 41d8c661-a749-4c89-be56-905c6e7c3c9d
caps.latest.revision: 7
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 7
---
# 最後の要素以外のすべてのフィールド幅は 0 より大きくなければなりません
最後の要素以外のすべてのフィールド幅は 0 より大きくなければなりません。 最後の要素内の 0 以下のフィールド幅は、最後のフィールドが可変長であることを示しています。  
  
 最後の要素以外のフィールド幅が 0 以下に設定されているため、処理に失敗しました。 0 以下のフィールド幅を最後の要素として使用し、最後のフィールドが可変長であることを示すことができますが、他の要素として使用することはできません。  
  
### このエラーを解決するには  
  
-   フィールド幅を正しい長さに設定します。  
  
## 参照  
 [TextFieldParser.SetFieldWidths メソッド](http://msdn.microsoft.com/ja-jp/958fed9f-e0f3-4fc5-83b4-386156bdf036)   
 [TextFieldParser.FieldWidths プロパティ](http://msdn.microsoft.com/ja-jp/c6985360-60c6-494e-89e7-43b6b73f2597)   
 [How to: Read From Fixed\-width Text Files](../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-fixed-width-text-files.md)   
 [TextFieldParser Object](../../visual-basic/language-reference/objects/textfieldparser-object.md)