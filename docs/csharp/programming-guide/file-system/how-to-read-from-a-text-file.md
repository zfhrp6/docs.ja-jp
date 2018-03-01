---
title: "方法: テキスト ファイルから読み込む (C# プログラミング ガイド)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- StreamReader.ReadToEnd
helpviewer_keywords:
- text files, writing to
- reading text files
- reading data, text files
- text files, reading
ms.assetid: 92246c5b-e819-4eea-9370-1a9460e12de3
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: d2af6102ac6793b4612a6fbc41f8c50189cc24d5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-read-from-a-text-file-c-programming-guide"></a>方法: テキスト ファイルから読み込む (C# プログラミング ガイド)
この例では、<xref:System.IO.File?displayProperty=nameWithType> クラスの静的メソッド <xref:System.IO.File.ReadAllText%2A> と <xref:System.IO.File.ReadAllLines%2A> を使用してテキスト ファイルの内容を読み取ります。  
  
 <xref:System.IO.StreamReader> の使用例については、「[方法: テキスト ファイルを一度に 1 行読み込む](../../../csharp/programming-guide/file-system/how-to-read-a-text-file-one-line-at-a-time.md)」を参照してください。  
  
> [!NOTE]
>  この例では、「[方法: テキスト ファイルに書き込む](../../../csharp/programming-guide/file-system/how-to-write-to-a-text-file.md)」のトピックで作成したファイルを使用しています。  
  
## <a name="example"></a>例  
 [!code-csharp[csFilesandFolders#4](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-read-from-a-text-file_1.cs)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 コードをコピーし、C# のコンソール アプリケーションに貼り付けます。  
  
 「[方法: テキスト ファイルに書き込む](../../../csharp/programming-guide/file-system/how-to-write-to-a-text-file.md)」のテキスト ファイルを使用せずに独自のテキスト ファイルを使用する場合は、`ReadAllText` と `ReadAllLines` の引数を、ご使用のコンピューター上の該当するパスおよびファイル名に置き換えてください。  
  
## <a name="robust-programming"></a>信頼性の高いプログラミング  
 次の条件を満たす場合は、例外が発生する可能性があります。  
  
-   ファイルが存在しない、または指定した場所に存在しない。 ファイル名のパスとスペルを確認してください。  
  
## <a name="net-framework-security"></a>.NET Framework セキュリティ  
 ファイル名に基づいてファイルの内容を判断しないでください。 たとえば、`myFile.cs` というファイルが C# のソース ファイルではない可能性もあります。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.IO?displayProperty=nameWithType>  
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)  
 [ファイル システムとレジストリ (C# プログラミング ガイド)](../../../csharp/programming-guide/file-system/index.md)
