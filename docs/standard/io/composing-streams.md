---
title: "ストリームの構成 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ストリーム、基本ストリーム"
  - "I/O [.NET Framework]、構成 (ストリームの)"
  - "Stream クラス、構成 (ストリームの)"
  - "基本ストリーム"
  - "ストリーム、バッキング ストア"
ms.assetid: da761658-a535-4f26-a452-b30df47f73d5
caps.latest.revision: 10
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 10
---
# ストリームの構成
バッキング ストアとは、ディスクやメモリのようなストレージ メディアのことです。  各種のバッキング ストアのそれぞれが、<xref:System.IO.Stream> クラスの実装として独自のストリームを実装しています。  各ストリーム型は、関連付けられたバッキング ストアからバイトを読み取ったり書き込んだりします。  バッキング ストアに関連付けられたストリームは、基本ストリームと呼ばれます。  基本ストリームには、ストリームをバッキング ストアに関連付けるために必要なパラメーターを持つコンストラクターがあります。  たとえば、<xref:System.IO.FileStream> には、プロセス間でファイルを共有する方法を指定するパス パラメーターなどを指定するコンストラクターがあります。  
  
 <xref:System.IO> クラスは、ストリームを簡単に構成できるようにデザインされています。  基本ストリームは、必要な機能を提供する 1 つ以上のパススルー ストリームに結合できます。  必要な型を簡単に読み取ったり書き込んだりできるように、チェインの末尾にリーダーまたはライターを結合できます。  
  
 既存の `MyFile.txt` をバッファリングするために、`MyFile.txt` に対して **FileStream** を作成するコードの例を次に示します。**FileStreams** は、既定でバッファリングされます。次に、**FileStream** から文字を読み取るために <xref:System.IO.StreamReader> を作成します。FileStream は、コンストラクター引数として **StreamReader** に渡されます  <xref:System.IO.StreamReader.ReadLine%2A> は、<xref:System.IO.StreamReader.Peek%2A> が文字を検出できなくなるまで文字を読み取ります。  
  
 [!code-cpp[System.IO.StreamReader#20](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.IO.StreamReader/CPP/source2.cpp#20)]
 [!code-csharp[System.IO.StreamReader#20](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.StreamReader/CS/source2.cs#20)]
 [!code-vb[System.IO.StreamReader#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.StreamReader/VB/source2.vb#20)]  
  
 既存の `MyFile.txt` をバッファリングするために、`MyFile.txt` に対して **FileStream** を作成するコードの例を次に示します。**FileStreams** は、既定でバッファリングされます。次に、**FileStream** からバイトを読み取るための **BinaryReader** を作成します。FileStream は、コンストラクター引数として **StreamReader** に渡されます  <xref:System.IO.BinaryReader.ReadByte%2A> は、<xref:System.IO.BinaryReader.PeekChar%2A> がバイトを検出できなくなるまでバイトを読み取ります。  
  
 [!code-cpp[System.IO.StreamReader#21](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.IO.StreamReader/CPP/source3.cpp#21)]
 [!code-csharp[System.IO.StreamReader#21](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.StreamReader/CS/source3.cs#21)]
 [!code-vb[System.IO.StreamReader#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.StreamReader/VB/source3.vb#21)]  
  
## 参照  
 <xref:System.IO.StreamReader>   
 <xref:System.IO.StreamReader.ReadLine%2A?displayProperty=fullName>   
 <xref:System.IO.StreamReader.Peek%2A?displayProperty=fullName>   
 <xref:System.IO.FileStream>   
 <xref:System.IO.BinaryReader>   
 <xref:System.IO.BinaryReader.ReadByte%2A?displayProperty=fullName>   
 <xref:System.IO.BinaryReader.PeekChar%2A?displayProperty=fullName>