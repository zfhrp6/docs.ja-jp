---
title: '方法 : ログ ファイルを開いて情報を追加する'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- log files, opening
- streams, opening and appending to log file
- log files, appending to
- I/O [.NET Framework], log files
ms.assetid: 74423362-1721-49cb-aa0a-e04005f72a06
author: mairaw
ms.author: mairaw
ms.openlocfilehash: cd2d13a49d9b696541ac278b9f1847c8e4a48cf1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33571944"
---
# <a name="how-to-open-and-append-to-a-log-file"></a>方法 : ログ ファイルを開いて情報を追加する
<xref:System.IO.StreamWriter> および <xref:System.IO.StreamReader> は、ストリームから文字の書き込んだり、読み取りを行います。 次のコード例は、入力用に `log.txt` ファイルを開くか、まだファイルがない場合、ファイルを作成し、ファイルの末尾に情報を追加します。 ファイルの内容は、その後表示用に標準出力に書き込まれます。 この例の代わりとして、情報を 1 つの文字列または文字列の配列として格納して、<xref:System.IO.File.WriteAllText%2A> または <xref:System.IO.File.WriteAllLines%2A> メソッドを使用して、同じ機能を実現することができます。  
  
> [!NOTE]
>  Visual Basic を使用するユーザーは、ログ ファイルの作成またはログ ファイルへの書き込みのために、<xref:Microsoft.VisualBasic.Logging.Log> クラスまたは <xref:Microsoft.VisualBasic.FileIO.FileSystem> クラスによって提供されるメソッドまたはプロパティを使用することを選択できます。  
  
## <a name="example"></a>例  
 [!code-csharp[Conceptual.BasicIO.TextFiles#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/source2.cs#2)]
 [!code-vb[Conceptual.BasicIO.TextFiles#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/source2.vb#2)]  
  
## <a name="see-also"></a>参照  
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
