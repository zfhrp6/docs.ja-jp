---
title: "方法 : ファイルおよびフォルダーのコピー、削除、および移動を行う (C# プログラミング ガイド) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "I/O [C#]"
ms.assetid: 62e52cd7-9597-4e4a-acf9-1315f5cdbf05
caps.latest.revision: 13
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 13
---
# 方法 : ファイルおよびフォルダーのコピー、削除、および移動を行う (C# プログラミング ガイド)
<xref:System.IO?displayProperty=fullName> 名前空間から <xref:System.IO.File?displayProperty=fullName>、<xref:System.IO.Directory?displayProperty=fullName>、<xref:System.IO.FileInfo?displayProperty=fullName>、および <xref:System.IO.DirectoryInfo?displayProperty=fullName> の各クラスを使用して、同期的な方法でファイルやフォルダーをコピー、移動、および削除する方法を次の例に示します。  これらの例では、プログレス バーやその他のユーザー インターフェイスは表示されません。  標準の進行状況ダイアログ ボックスを表示する場合は、「[方法: ファイル操作の \[進行状況\] ダイアログ ボックスを表示する](../../../csharp/programming-guide/file-system/how-to-provide-a-progress-dialog-box-for-file-operations.md)」を参照してください。  
  
 複数のファイルを操作するときに進行状況を計算できるイベントを提供するには、<xref:System.IO.FileSystemWatcher?displayProperty=fullName> を使用します。  プラットフォーム呼び出しを使用して、Windows シェルで関連するファイル関連メソッドを呼び出すこともできます。  これらのファイル操作を非同期に実行する方法については、「[非同期ファイル I\/O](../Topic/Asynchronous%20File%20I-O.md)」を参照してください。  
  
## 使用例  
 ファイルおよびディレクトリをコピーする方法を次の例に示します。  
  
 [!code-cs[csFilesandFolders#7](../../../csharp/programming-guide/file-system/codesnippet/csharp/csFilesFolders/FileIteration.cs#7)]  
  
## 使用例  
 ファイルおよびディレクトリを移動する方法を次の例に示します。  
  
 [!code-cs[csFilesandFolders#8](../../../csharp/programming-guide/file-system/codesnippet/csharp/csFilesFolders/FileIteration.cs#8)]  
  
## 使用例  
 ファイルおよびディレクトリを削除する方法を次の例に示します。  
  
 [!code-cs[csFilesandFolders#9](../../../csharp/programming-guide/file-system/codesnippet/csharp/csFilesFolders/FileIteration.cs#9)]  
  
## 参照  
 <xref:System.IO?displayProperty=fullName>   
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [ファイル システムとレジストリ](../../../csharp/programming-guide/file-system/file-system-and-the-registry.md)   
 [方法: ファイル操作の \[進行状況\] ダイアログ ボックスを表示する](../../../csharp/programming-guide/file-system/how-to-provide-a-progress-dialog-box-for-file-operations.md)   
 [ファイルおよびストリーム入出力](../Topic/File%20and%20Stream%20I-O.md)   
 [共通 I\/O タスク](../Topic/Common%20I-O%20Tasks.md)