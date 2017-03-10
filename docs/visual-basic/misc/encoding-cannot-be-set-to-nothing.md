---
title: "エンコードは Nothing に設定できません | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
ms.assetid: 59f7c731-8291-4a85-bf51-c225e48cdc84
caps.latest.revision: 8
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 8
---
# エンコードは Nothing に設定できません
パラメーター `encoding` が `Nothing` に設定されていますが、正しい値が必要なため、ファイルへの読み取りまたは書き込みに失敗しました。  
  
 <xref:System.Text.Encoding> は、ファイルへの書き込み時に使用するエンコードを判別するのに使用されます。 既定は UTF\-8 です。  
  
### このエラーを解決するには  
  
-   正しい値を `encoding` パラメーターに指定します。  
  
## 参照  
 [File Encodings](../../visual-basic/developing-apps/programming/drives-directories-files/file-encodings.md)   
 [Reading from Files](../../visual-basic/developing-apps/programming/drives-directories-files/reading-from-files.md)   
 [Writing to Files](../../visual-basic/developing-apps/programming/drives-directories-files/writing-to-files.md)   
 [My.Computer.FileSystem.ReadAllText メソッド](http://msdn.microsoft.com/ja-jp/3a7ac8be-fb1d-4087-bc65-167d6754d57f)   
 [My.Computer.FileSystem.WriteAllText メソッド](http://msdn.microsoft.com/ja-jp/f507460c-87d9-4504-b74f-3ff825c7d5c4)