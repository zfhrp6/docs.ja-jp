---
title: "方法: テキスト ファイルに書き込む (C# プログラミング ガイド) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "TextWriter.WriteLine"
  - "StreamWriter.Close"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "ファイル [C#], テキスト ファイル"
  - "テキスト, 書き込み (ファイルへの) [C#]"
ms.assetid: 2e99f184-d88b-4719-a7f1-d9ec482aa809
caps.latest.revision: 23
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 23
---
# 方法: テキスト ファイルに書き込む (C# プログラミング ガイド)
テキストをファイルに書き込むさまざまな方法を次の例に示します。  最初の 2 つの例では、<xref:System.IO.File?displayProperty=fullName> クラスの静的なコンビニエンス メソッドを使用して、すべての IEnumerable\<string\> の各要素と文字列をテキスト ファイルに記述しています。  例 3 は、ファイルに書き込むときに各行を個別に処理する必要がある場合にテキストをファイルに追加する方法を示します。  例 1 ～ 3 ではすべての既存の内容が上書きされます。例 4 に、既存のファイルにテキストを追加する方法を示します。  
  
 これらの例はいずれもファイルにリテラル文字列を書き込みますが、通常は、さまざまな型の値の書き込み、フィールド内での右揃えや左揃え、パディングの有無などに対応する多くのコントロールを持つ <xref:System.String.Format%2A> メソッドを使用します。  C\# の[文字列の補間](../../../csharp/language-reference/keywords/interpolated-strings.md)機能を使用することもできます。  
  
## 使用例  
 [!code-cs[csFilesandFolders#3](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-write-to-a-text-file_1.cs)]  
  
 これらの例はいずれもファイルにリテラル文字列を書き込みますが、通常は、さまざまな型の値の書き込み、フィールド内での右揃えや左揃え、パディングの有無などに対応する多くのコントロールを持つ <xref:System.String.Format%2A> メソッドを使用します。  C\# の[文字列の補間](../../../csharp/language-reference/keywords/interpolated-strings.md)機能を使用することもできます。  
  
## 信頼性の高いプログラミング  
 次の条件を満たす場合は、例外が発生する可能性があります。  
  
-   ファイルは存在するが、読み取り専用である。  
  
-   パス名が長すぎる。  
  
-   ディスクがいっぱいになっている。  
  
## 参照  
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [ファイル システムとレジストリ](../../../csharp/programming-guide/file-system/file-system-and-the-registry.md)   
 [サンプル: カスタム オブジェクトのコレクションをローカル ストレージに保存する方法](http://code.msdn.microsoft.com/CSWinStoreAppSaveCollection-bed5d6e6)