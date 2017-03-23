---
title: "方法 : RTF をプレーンテキストに変換する (C# プログラミング ガイド) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "文字列 [C#]、RTF からの変換"
ms.assetid: 3b386a87-899d-4d98-bc82-a980526ddaac
caps.latest.revision: 21
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 21
---
# 方法 : RTF をプレーンテキストに変換する (C# プログラミング ガイド)
リッチ テキスト形式 \(RTF: Rich Text Format\) は、1980 年代の後半にマイクロソフトが開発したドキュメント形式で、オペレーティング システム間でドキュメントを交換できます。  Microsoft Word と WordPad のどちらでも、RTF ドキュメントの読み込みと書き込みを行うことができます。  .NET Framework では、<xref:System.Windows.Forms.RichTextBox> コントロールを使用して、RTF をサポートし、ユーザーが WYSIWIG 形式でテキストに書式設定を適用できるワード プロセッサを作成できます。  
  
 <xref:System.Windows.Forms.RichTextBox> コントロールを使用して、プログラムによってドキュメントから RTF 書式指定コードを削除し、プレーンテキストに変換することもできます。  このような操作を実行するために、Windows フォームにコントロールを埋め込む必要はありません。  
  
### プロジェクトで RichTextBox コントロールを使用するには  
  
1.  System.Windows.Forms.dll に対する参照を追加します。  
  
2.  `System.Windows.Forms` 名前空間の using ディレクティブを追加します \(省略可能\)。  
  
## 使用例  
 次の例では、プレーンテキストにサンプルの RTF ファイルを変換します。  ファイルは RTF 形式 \(フォント情報など\)、4 種類の Unicode 文字、および 4 個の拡張 ASCII 文字が含まれています。  このコード例は <xref:System.Windows.Forms.RichTextBox>、RTF はテキストとして、内容を取得し、<xref:System.Windows.Forms.MessageBox>のテキストを表示、および UTF\-8 ファイル形式のテキストをファイルに出力すると同時にファイルを渡すと、コンテンツを開きます。  
  
 `MessageBox` と出力ファイルに次のテキストが含まれています:  
  
```  
The Greek word for "psyche" is spelled ψυχή. The Greek letters are encoded in Unicode.  
These characters are from the extended ASCII character set (Windows code page 1252):  âäӑå  
  
```  
  
 [!code-cs[csProgGuideStrings#33](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-convert-rtf-to-plain-text_1.cs)]  
  
 RTF 文字は 8 ビットでエンコードされます。  ただし、ユーザーは指定されたコード ページから拡張 ASCII 文字に加えて Unicode 文字を指定できます。  <xref:System.Windows.Forms.RichTextBox.Text%2A?displayProperty=fullName> プロパティは [string](../../../csharp/language-reference/keywords/string.md) 型であるため、文字は Unicode UTF\-16 としてエンコードされます。  ソース RTF ドキュメントの拡張 ASCII 文字と Unicode 文字は、テキスト出力で正しくエンコードされます。  
  
 <xref:System.IO.File.WriteAllText%2A?displayProperty=fullName> メソッドを使用してテキストをディスクに書き込むと、テキストは UTF\-8 としてエンコードされます \(バイト オーダー マークなし\)。  
  
## 参照  
 <xref:System.Windows.Forms.RichTextBox?displayProperty=fullName>   
 [文字列](../../../csharp/programming-guide/strings/index.md)