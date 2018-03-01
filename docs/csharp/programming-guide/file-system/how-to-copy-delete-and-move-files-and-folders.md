---
title: "方法: ファイルおよびフォルダーのコピー、削除、および移動を行う (C# プログラミング ガイド)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- I/O [C#]
ms.assetid: 62e52cd7-9597-4e4a-acf9-1315f5cdbf05
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 56383873674998fc0d6417a2abf4fa72e498f08f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-copy-delete-and-move-files-and-folders-c-programming-guide"></a>方法: ファイルおよびフォルダーのコピー、削除、および移動を行う (C# プログラミング ガイド)
次の例では、<xref:System.IO?displayProperty=nameWithType> 名前空間から <xref:System.IO.File?displayProperty=nameWithType>、<xref:System.IO.Directory?displayProperty=nameWithType>、<xref:System.IO.FileInfo?displayProperty=nameWithType>、および <xref:System.IO.DirectoryInfo?displayProperty=nameWithType> クラスを使用して、同期的な方法でファイルとフォルダーをコピー、移動および削除する方法を示します。 これらの例では、進行状況バーやその他のユーザー インターフェイスは表示されません。 標準の進行状況ダイアログ ボックスを表示する場合は、「[方法: ファイル操作の [進行状況] ダイアログ ボックスを表示する](how-to-provide-a-progress-dialog-box-for-file-operations.md)」を参照してください。  
  
 複数のファイルを操作するときに進行状況を計算できるイベントを提供するには、<xref:System.IO.FileSystemWatcher?displayProperty=nameWithType> を使用します。 プラットフォーム呼び出しを使用して、Windows シェルで関連するファイル関連メソッドを呼び出す方法もあります。 これらのファイル操作を非同期に実行する方法については、「[非同期ファイル I/O](https://msdn.microsoft.com/library/kztecsys)」を参照してください。  
  
## <a name="example"></a>例  
 次の例では、ファイルとディレクトリをコピーする方法を示します。  
  
 [!code-csharp[csFilesandFolders#7](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-copy-delete-and-move-files-and-folders_1.cs)]  
  
## <a name="example"></a>例  
 次の例では、ファイルとディレクトリを移動する方法を示します。  
  
 [!code-csharp[csFilesandFolders#8](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-copy-delete-and-move-files-and-folders_2.cs)]  
  
## <a name="example"></a>例  
 次の例では、ファイルとディレクトリを削除する方法を示します。  
  
 [!code-csharp[csFilesandFolders#9](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-copy-delete-and-move-files-and-folders_3.cs)]  
  
## <a name="see-also"></a>関連項目  
 <xref:System.IO?displayProperty=nameWithType>  
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)  
 [ファイル システムとレジストリ (C# プログラミング ガイド)](index.md)  
 [方法: ファイル操作の [進行状況] ダイアログ ボックスを表示する](how-to-provide-a-progress-dialog-box-for-file-operations.md)  
 [ファイルおよびストリーム入出力](https://msdn.microsoft.com/library/k3352a4t)  
 [共通 I/O タスク](https://msdn.microsoft.com/library/ms404278)
