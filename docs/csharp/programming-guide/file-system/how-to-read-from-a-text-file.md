---
title: "方法: テキスト ファイルから読み込む (C# プログラミング ガイド) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "StreamReader.ReadToEnd"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "読み取り (データを), テキスト ファイル"
  - "読み取り (テキスト ファイルを)"
  - "テキスト ファイル, 読み取り"
  - "テキスト ファイル, 書き込み"
ms.assetid: 92246c5b-e819-4eea-9370-1a9460e12de3
caps.latest.revision: 17
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 17
---
# 方法: テキスト ファイルから読み込む (C# プログラミング ガイド)
この例では <xref:System.IO.File?displayProperty=fullName> クラスの静的メソッド <xref:System.IO.File.ReadAllText%2A> と <xref:System.IO.File.ReadAllLines%2A> を使用して、テキスト ファイルの内容を読み込みます。  
  
 <xref:System.IO.StreamReader> の使用例については、「[方法: テキスト ファイルを一度に 1 行読み込む](../../../csharp/programming-guide/file-system/how-to-read-a-text-file-one-line-at-a-time.md)」を参照してください。  
  
> [!NOTE]
>  この例で使用されているファイルは" "トピック [方法: テキスト ファイルに書き込む](../../../csharp/programming-guide/file-system/how-to-write-to-a-text-file.md)に作成されます。  
  
## 使用例  
 [!code-cs[csFilesandFolders#4](../../../csharp/programming-guide/file-system/codesnippet/csharp/csFilesFolders/FileIteration.cs#4)]  
  
## コードのコンパイル  
 コードをコピーして、Cのコンソール アプリケーションに貼り付けます。  
  
 [方法: テキスト ファイルに書き込む](../../../csharp/programming-guide/file-system/how-to-write-to-a-text-file.md)からテキスト ファイルを使用しない場合は、適切なパスで `ReadAllText` と `ReadAllLines` に引数およびコンピューターのファイル名を置き換えます。  
  
## 信頼性の高いプログラミング  
 次の条件を満たす場合は、例外が発生する可能性があります。  
  
-   ファイルは指定した場所に存在しないか、ありません。  パスとファイル名のスペルを確認します。  
  
## .NET Framework セキュリティ  
 ファイルの内容を決定するファイルの名前に依存しないでください。  たとえば、ファイル `myFile.cs` は、Cのソース ファイルではない可能性があります。  
  
## 参照  
 <xref:System.IO?displayProperty=fullName>   
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [ファイル システムとレジストリ](../../../csharp/programming-guide/file-system/file-system-and-the-registry.md)