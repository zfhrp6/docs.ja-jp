---
title: "Parsing Text Files with the TextFieldParser Object (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "TextFieldParser object, using"
  - "I/O [Visual Basic], parsing files"
  - "files, parsing"
ms.assetid: fc31d6e6-af0c-403f-8a00-d556b2c57567
caps.latest.revision: 20
caps.handback.revision: 20
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Parsing Text Files with the TextFieldParser Object (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

`TextFieldParser` オブジェクトを使用すると、ログ ファイルやレガシ データベース情報など、区切り文字や幅に応じて複数列に区切られたテキストとして構造化されている巨大なファイルを解析および処理できます。  テキスト ファイルを `TextFieldParser` で解析するのは、テキスト ファイルを反復処理するのと同様です。解析メソッドでテキストのフィールドを抽出するのは、区切り文字の付いた文字列を文字列操作メソッドでトークン化するのと同様です。  
  
## さまざまな種類のテキスト ファイルの解析  
 テキスト ファイルは、コンマやタブ空白などの文字で可変幅のフィールドに区切られている場合があります。  次の例のように、`TextFieldType` および区切り記号を定義します。この例では、`SetDelimiters` メソッドを使用して、タブ区切りのテキスト ファイルを定義しています。  
  
 [!CODE [VbVbalrTextFieldParser#21](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrTextFieldParser#21)]  
  
 また、テキスト ファイルによっては、固定幅のフィールドを持つ場合もあります。  その場合には、次の例のように、`TextFieldType` を `FixedWidth` と定義し、各フィールドの幅を定義する必要があります。  この例では、`SetFieldWidths` メソッドを使用して、テキストの列を定義しています。最初は幅が 5 文字、その次は 10、その次は 11、その次は可変幅です。  
  
 [!CODE [VbVbalrTextFieldParser#22](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrTextFieldParser#22)]  
  
 書式を定義したら、ファイルをループし、`ReadFields` メソッドを使用して、各行を順番に処理します。  
  
 フィールドが指定の書式に一致しない場合には、<xref:Microsoft.VisualBasic.FileIO.MalformedLineException> 例外がスローされます。  この例外がスローされた場合、`ErrorLine` プロパティと `ErrorLineNumber` プロパティに、例外の原因になったテキストと、そのテキストの行番号が保持されます。  
  
## 複数の書式を持つファイルの解析  
 `TextFieldParser` オブジェクトの `PeekChars` メソッドを使用すると、各フィールドを読み取り前にチェックできます。これにより、フィールドに対して複数の書式を定義して、適切に対応できます。  詳細については、「[How to: Read From Text Files with Multiple Formats](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files-with-multiple-formats.md)」を参照してください。  
  
## 参照  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.OpenTextFieldParser%2A>   
 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser>   
 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.PeekChars%2A>   
 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ReadFields%2A>   
 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.CommentTokens%2A>   
 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.Delimiters%2A>   
 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ErrorLine%2A>   
 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ErrorLineNumber%2A>   
 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.FieldWidths%2A>   
 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.HasFieldsEnclosedInQuotes%2A>   
 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.LineNumber%2A>   
 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.TextFieldType%2A>   
 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.TrimWhiteSpace%2A>   
 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.SetDelimiters%2A>   
 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.SetFieldWidths%2A>   
 [例外のトラブルシューティング : Microsoft.VisualBasic.FileIO.TextFieldParser.MalformedLineException](../Topic/Troubleshooting%20Exceptions:%20Microsoft.VisualBasic.FileIO.TextFieldParser.MalformedLineException.md)