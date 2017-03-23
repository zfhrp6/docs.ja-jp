---
title: "方法: ファイル操作の [進行状況] ダイアログ ボックスを表示する (C# プログラミング ガイド) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "[進行状況] ダイアログ ボックス [C#]"
ms.assetid: 01b71fe7-8178-4dc8-aeb1-12053be7b51c
caps.latest.revision: 15
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 15
---
# 方法: ファイル操作の [進行状況] ダイアログ ボックスを表示する (C# プログラミング ガイド)
<xref:Microsoft.VisualBasic?displayProperty=fullName> 名前空間の <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%28System.String%2CSystem.String%2CMicrosoft.VisualBasic.FileIO.UIOption%29> メソッドを使用すると、Windows でのファイル操作に関する進行状況を示す標準ダイアログ ボックスを提供できます。  
  
 [!INCLUDE[note_settings_general](../../../csharp/language-reference/compiler-messages/includes/note-settings-general-md.md)]  
  
### Visual Studio で参照を追加するには  
  
1.  メニュー バーで、**\[プロジェクト\]**、**\[参照の追加\]** の順に選択します。  
  
     **\[参照マネージャー\]** ダイアログ ボックスが表示されます。  
  
2.  **\[アセンブリ\]** で、**\[フレームワーク\]** を選択します \(選択されていない場合\)。  
  
3.  名前の一覧で、**\[Microsoft.VisualBasic\]** のチェック ボックスをオンにし、**\[OK\]** をクリックしてダイアログ ボックスを閉じます。  
  
## 使用例  
 次のコードは、`sourcePath` で指定されたディレクトリを `destinationPath` で指定されたディレクトリにコピーします。  また、操作の完了までに必要な残りの予測時間を示す、標準的なダイアログ ボックスを表示します。  
  
 [!code-cs[csFilesandFolders#11](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-provide-a-progress-dialog-box-for-file-operations_1.cs)]  
  
## 参照  
 [ファイル システムとレジストリ](../../../csharp/programming-guide/file-system/file-system-and-the-registry.md)