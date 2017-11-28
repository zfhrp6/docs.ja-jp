---
title: "方法: テキスト ファイルに書き込む (C# プログラミング ガイド)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- TextWriter.WriteLine
- StreamWriter.Close
helpviewer_keywords:
- files [C#], text files
- text, writing to files [C#]
ms.assetid: 2e99f184-d88b-4719-a7f1-d9ec482aa809
caps.latest.revision: "23"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: c576536947cdb4984d6e5ce67c8377fe23b354c7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-write-to-a-text-file-c-programming-guide"></a>方法: テキスト ファイルに書き込む (C# プログラミング ガイド)
テキストをファイルに書き込むさまざまな方法を次の例に示します。  最初の 2 つの例では、<xref:System.IO.File?displayProperty=nameWithType> クラスの静的なコンビニエンス メソッドを使用して、すべての IEnumerable\<string> の各要素と文字列をテキスト ファイルに記述しています。  例 3 は、ファイルに書き込むときに各行を個別に処理する必要がある場合にテキストをファイルに追加する方法を示します。  例 1 ～ 3 ではすべての既存の内容が上書きされます。例 4 に、既存のファイルにテキストを追加する方法を示します。  
  
 これらの例はいずれもファイルにリテラル文字列を書き込みますが、通常は、さまざまな型の値の書き込み、フィールド内での右揃えや左揃え、パディングの有無などに対応する多くのコントロールを持つ <xref:System.String.Format%2A> メソッドを使用します。  C# の[文字列補間](../../../csharp/language-reference/keywords/interpolated-strings.md)機能を使用することもできます。  
  
## <a name="example"></a>例  
 [!code-csharp[csFilesandFolders#3](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-write-to-a-text-file_1.cs)]  
  
 これらの例はいずれもファイルにリテラル文字列を書き込みますが、通常は、さまざまな型の値の書き込み、フィールド内での右揃えや左揃え、パディングの有無などに対応する多くのコントロールを持つ <xref:System.String.Format%2A> メソッドを使用します。  C# の[文字列補間](../../../csharp/language-reference/keywords/interpolated-strings.md)機能を使用することもできます。  
  
## <a name="robust-programming"></a>信頼性の高いプログラミング  
 次の条件を満たす場合は、例外が発生する可能性があります。  
  
-   ファイルは存在するが、読み取り専用である。  
  
-   パス名が長すぎる。  
  
-   ディスクがいっぱいになっている。  
  
## <a name="see-also"></a>関連項目  
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)  
 [ファイル システムとレジストリ (C# プログラミング ガイド)](../../../csharp/programming-guide/file-system/index.md)  
 [サンプル: コレクションをアプリケーション ストレージに保存する](http://code.msdn.microsoft.com/CSWinStoreAppSaveCollection-bed5d6e6)
