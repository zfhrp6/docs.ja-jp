---
title: "方法 : ログ ファイルを開いて情報を追加する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- log files, opening
- streams, opening and appending to log file
- log files, appending to
- I/O [.NET Framework], log files
ms.assetid: 74423362-1721-49cb-aa0a-e04005f72a06
caps.latest.revision: "15"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 60c31339231405a1cbbb98dae37d36ad3c3709c1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-open-and-append-to-a-log-file"></a>方法 : ログ ファイルを開いて情報を追加する
<xref:System.IO.StreamWriter>および<xref:System.IO.StreamReader>する文字の書き込みおよびストリームから文字を読み取る。 次のコード例が開き、`log.txt`入力には、ファイルまたはファイルの末尾に情報を追加し、既に存在しない場合は、ファイルを作成します。 ファイルの内容は表示するための標準出力に書き込まれます。 この例を代わりに、情報を 1 つの文字列または文字列の配列として格納でした、<xref:System.IO.File.WriteAllText%2A>または<xref:System.IO.File.WriteAllLines%2A>メソッドは、同じ機能を実現するを使用する可能性があります。  
  
> [!NOTE]
>  メソッドおよびプロパティを使用する Visual Basic ユーザーは選択、<xref:Microsoft.VisualBasic.Logging.Log>クラスまたは<xref:Microsoft.VisualBasic.FileIO.FileSystem>作成またはログ ファイルに書き込むのためのクラスです。  
  
## <a name="example"></a>例  
 [!code-csharp[Conceptual.BasicIO.TextFiles#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/source2.cs#2)]
 [!code-vb[Conceptual.BasicIO.TextFiles#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/source2.vb#2)]  
  
## <a name="see-also"></a>関連項目  
 <xref:System.IO.StreamWriter>  
 <xref:System.IO.StreamReader>  
 <xref:System.IO.File.AppendText%2A?displayProperty=nameWithType>  
 <xref:System.IO.File.OpenText%2A?displayProperty=nameWithType>  
 <xref:System.IO.StreamReader.ReadLine%2A?displayProperty=nameWithType>  
 [方法: ディレクトリとファイルを列挙する](../../../docs/standard/io/how-to-enumerate-directories-and-files.md)  
 [方法: 新しく作成されたデータ ファイルに対して読み書きする](../../../docs/standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)  
 [方法: ファイルからテキストを読み取る](../../../docs/standard/io/how-to-read-text-from-a-file.md)  
 [方法: ファイルにテキストを書き込む](../../../docs/standard/io/how-to-write-text-to-a-file.md)  
 [方法: 文字列から文字を読み取る](../../../docs/standard/io/how-to-read-characters-from-a-string.md)  
 [方法: 文字列に文字を書き込む](../../../docs/standard/io/how-to-write-characters-to-a-string.md)  
 [ファイルおよびストリーム入出力](../../../docs/standard/io/index.md)
