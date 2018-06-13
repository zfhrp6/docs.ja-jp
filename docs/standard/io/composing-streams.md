---
title: ストリームの構成
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- streams, base streams
- I/O [.NET Framework], composing streams
- Stream class, composing streams
- base streams
- streams, backing stores
ms.assetid: da761658-a535-4f26-a452-b30df47f73d5
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 231bd98b556dafeb69091de4a6770c1462824659
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33572854"
---
# <a name="composing-streams"></a>ストリームの構成
バッキング ストアは、ディスクやメモリなどの記憶域メディアです。 さまざまなバッキング ストアが <xref:System.IO.Stream> クラスの実装としてそれぞれ独自のストリームを実装しています。 各ストリームの種類は、指定されたバッキング ストアとの間でバイトの読み取りと書き込みを行います。 バッキング ストアに接続するストリームは、基本ストリームと呼ばれます。 基本ストリームには、ストリームをバッキング ストアに接続するために必要なパラメーターを持つコンストラクターがあります。 たとえば、<xref:System.IO.FileStream> には、プロセスでファイルを共有する方法を指定する path パラメーターなどを指定するコンストラクターがあります。  
  
 <xref:System.IO> クラスは、簡易なストリーム構成で設計されています。 必要な機能を提供する 1 つ以上のパススルー ストリームに基本ストリームをアタッチすることができます。 好みの種類の読み取りまたは書き込みを簡単に実行できるように、チェーンの末端に閲覧者またはライターをアタッチすることができます。  
  
 次のコード例では、`MyFile.txt` をバッファーするために既存の `MyFile.txt` を中心にして **FileStream** を作成します  (**FileStreams** は既定でバッファーされます)。次に、**FileStream** から文字を読み取る <xref:System.IO.StreamReader> が作成されます。これはコンストラクター引数として **StreamReader** に渡されます。 <xref:System.IO.StreamReader.ReadLine%2A> は、<xref:System.IO.StreamReader.Peek%2A> によって文字が検出されなくなるまで読み取りを行います。  
  
 [!code-cpp[System.IO.StreamReader#20](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.IO.StreamReader/CPP/source2.cpp#20)]
 [!code-csharp[System.IO.StreamReader#20](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.StreamReader/CS/source2.cs#20)]
 [!code-vb[System.IO.StreamReader#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.StreamReader/VB/source2.vb#20)]  
  
 次のコード例では、`MyFile.txt` をバッファーするために既存の `MyFile.txt` を中心にして **FileStream** を作成します  (**FileStreams** は既定でバッファーされます)。次に、**FileStream** からバイトを読み取る **BinaryReader** が作成されます。これはコンストラクター引数として **BinaryReader** に渡されます。 <xref:System.IO.BinaryReader.ReadByte%2A> は、<xref:System.IO.BinaryReader.PeekChar%2A> によってバイトが検出されなくなるまで読み取りを行います。  
  
 [!code-cpp[System.IO.StreamReader#21](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.IO.StreamReader/CPP/source3.cpp#21)]
 [!code-csharp[System.IO.StreamReader#21](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.StreamReader/CS/source3.cs#21)]
 [!code-vb[System.IO.StreamReader#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.StreamReader/VB/source3.vb#21)]  
  
## <a name="see-also"></a>参照  
 <xref:System.IO.StreamReader>  
 <xref:System.IO.StreamReader.ReadLine%2A?displayProperty=nameWithType>  
 <xref:System.IO.StreamReader.Peek%2A?displayProperty=nameWithType>  
 <xref:System.IO.FileStream>  
 <xref:System.IO.BinaryReader>  
 <xref:System.IO.BinaryReader.ReadByte%2A?displayProperty=nameWithType>  
 <xref:System.IO.BinaryReader.PeekChar%2A?displayProperty=nameWithType>
