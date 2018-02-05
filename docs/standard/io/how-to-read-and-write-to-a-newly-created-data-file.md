---
title: "方法 : 新しく作成されたデータ ファイルに対して読み書きする"
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
- cpp
helpviewer_keywords:
- streams, reading and writing data
- BinaryReader class, examples
- I/O [.NET Framework], reading data
- I/O [.NET Framework], writing data
- BinaryWriter class, examples
ms.assetid: e209d949-31e8-44ea-8e38-87f9093f3093
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 04ded71a23ba4cabab0a22e0d66c1084a726d8c8
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-read-and-write-to-a-newly-created-data-file"></a>方法 : 新しく作成されたデータ ファイルに対して読み書きする
<xref:System.IO.BinaryWriter> クラスおよび <xref:System.IO.BinaryReader?displayProperty=nameWithType> クラスは、文字列ではない形式でデータを書き込んだり読み取ったりするために使用します。 `Test.data` と呼ばれる新しい空のファイル ストリームに対するデータの書き込みと読み取りを実行するコードの例を次に示します。 現在のディレクトリにデータ ファイルを作成した後、そのファイルに関連付けた <xref:System.IO.BinaryWriter> オブジェクトと <xref:System.IO.BinaryReader> オブジェクトを作成し、<xref:System.IO.BinaryWriter> オブジェクトを使用して整数 0 ～ 10 を `Test.data` に書き込みます。ファイル ポインターはファイルの末尾に残っています。 <xref:System.IO.BinaryReader> オブジェクトはファイル ポインターを起点に戻してから、指定された内容を読み出します。  
  
## <a name="example"></a>例  
 [!code-cpp[System.IO.BinaryReaderWriter#7](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.IO.BinaryReaderWriter/CPP/source6.cpp#7)]
 [!code-csharp[System.IO.BinaryReaderWriter#7](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.BinaryReaderWriter/CS/source6.cs#7)]
 [!code-vb[System.IO.BinaryReaderWriter#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.BinaryReaderWriter/VB/source6.vb#7)]  
  
## <a name="robust-programming"></a>信頼性の高いプログラミング  
 `Test.data` が既に現在のディレクトリに存在する場合は、<xref:System.IO.IOException> 例外がスローされます。 ファイル ストリームを初期化するときにファイル モード オプション <xref:System.IO.FileMode.Create?displayProperty=nameWithType> を使用すると、例外がスローされずに新しいファイルが必ず作成されます。  
  
## <a name="see-also"></a>参照  
 <xref:System.IO.BinaryReader>  
 <xref:System.IO.BinaryWriter>  
 <xref:System.IO.FileStream>  
 <xref:System.IO.FileStream.Seek%2A?displayProperty=nameWithType>  
 <xref:System.IO.SeekOrigin>  
 [方法: ディレクトリとファイルを列挙する](../../../docs/standard/io/how-to-enumerate-directories-and-files.md)  
 [方法: ログ ファイルを開いて情報を追加する](../../../docs/standard/io/how-to-open-and-append-to-a-log-file.md)  
 [方法: ファイルからテキストを読み取る](../../../docs/standard/io/how-to-read-text-from-a-file.md)  
 [方法: ファイルにテキストを書き込む](../../../docs/standard/io/how-to-write-text-to-a-file.md)  
 [方法: 文字列から文字を読み取る](../../../docs/standard/io/how-to-read-characters-from-a-string.md)  
 [方法: 文字列に文字を書き込む](../../../docs/standard/io/how-to-write-characters-to-a-string.md)  
 [ファイルおよびストリーム入出力](../../../docs/standard/io/index.md)
