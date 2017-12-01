---
title: "ストリームの構成"
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
- streams, base streams
- I/O [.NET Framework], composing streams
- Stream class, composing streams
- base streams
- streams, backing stores
ms.assetid: da761658-a535-4f26-a452-b30df47f73d5
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 75800210a52620c5b08a01c5f8fa888bf40843fe
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="composing-streams"></a>ストリームの構成
バッキング ストアは、ディスク、メモリなどの記憶域メディアです。 それぞれ異なるバッキング ストアの実装としての独自のストリームの実装、<xref:System.IO.Stream>クラスです。 各ストリームの種類では、読み取り、特定のバッキング ストアとバイトを書き込みます。 バッキング ストアに接続しているストリームには、基本ストリームは呼び出されます。 基本ストリームでは、バッキング ストアにストリームを接続するために必要なパラメーターを持つコンス トラクターがあります。 たとえば、<xref:System.IO.FileStream>コンス トラクターで、プロセスというように、ファイルの共有方法を指定します、パスのパラメーターを指定します。  
  
 デザイン、<xref:System.IO>簡略化されたストリームを構成するクラスを提供します。 基本ストリームは、必要な機能を提供する 1 つ以上のパススルー ストリームにアタッチできます。 推奨される種類を読み取りまたは簡単に記述できるようにする、リーダーまたはライターが、チェーンの末尾にアタッチできます。  
  
 次のコード例を作成、 **FileStream** 、既存の周囲`MyFile.txt`バッファーへの順序で`MyFile.txt`です。 (なお**Filestream**は既定ではバッファーに格納します)。次に、<xref:System.IO.StreamReader>から文字を読み取るには、 **FileStream**に渡される、 **StreamReader**コンス トラクター引数として。 <xref:System.IO.StreamReader.ReadLine%2A>まで読み取ります<xref:System.IO.StreamReader.Peek%2A>文字を検索します。  
  
 [!code-cpp[System.IO.StreamReader#20](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.IO.StreamReader/CPP/source2.cpp#20)]
 [!code-csharp[System.IO.StreamReader#20](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.StreamReader/CS/source2.cs#20)]
 [!code-vb[System.IO.StreamReader#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.StreamReader/VB/source2.vb#20)]  
  
 次のコード例を作成、 **FileStream** 、既存の周囲`MyFile.txt`バッファーへの順序で`MyFile.txt`です。 (なお**Filestream**は既定ではバッファーに格納します)。次に、 **BinaryReader**からバイトを読み取りが作成、 **FileStream**に渡される、 **BinaryReader**コンス トラクター引数として。 <xref:System.IO.BinaryReader.ReadByte%2A>まで読み取ります<xref:System.IO.BinaryReader.PeekChar%2A>以上のバイトを検索します。  
  
 [!code-cpp[System.IO.StreamReader#21](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.IO.StreamReader/CPP/source3.cpp#21)]
 [!code-csharp[System.IO.StreamReader#21](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.StreamReader/CS/source3.cs#21)]
 [!code-vb[System.IO.StreamReader#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.StreamReader/VB/source3.vb#21)]  
  
## <a name="see-also"></a>関連項目  
 <xref:System.IO.StreamReader>  
 <xref:System.IO.StreamReader.ReadLine%2A?displayProperty=nameWithType>  
 <xref:System.IO.StreamReader.Peek%2A?displayProperty=nameWithType>  
 <xref:System.IO.FileStream>  
 <xref:System.IO.BinaryReader>  
 <xref:System.IO.BinaryReader.ReadByte%2A?displayProperty=nameWithType>  
 <xref:System.IO.BinaryReader.PeekChar%2A?displayProperty=nameWithType>
