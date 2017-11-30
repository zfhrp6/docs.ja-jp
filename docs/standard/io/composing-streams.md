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
# <a name="composing-streams"></a><span data-ttu-id="a36a1-102">ストリームの構成</span><span class="sxs-lookup"><span data-stu-id="a36a1-102">Composing Streams</span></span>
<span data-ttu-id="a36a1-103">バッキング ストアは、ディスク、メモリなどの記憶域メディアです。</span><span class="sxs-lookup"><span data-stu-id="a36a1-103">A backing store is a storage medium, such as a disk or memory.</span></span> <span data-ttu-id="a36a1-104">それぞれ異なるバッキング ストアの実装としての独自のストリームの実装、<xref:System.IO.Stream>クラスです。</span><span class="sxs-lookup"><span data-stu-id="a36a1-104">Each different backing store implements its own stream as an implementation of the <xref:System.IO.Stream> class.</span></span> <span data-ttu-id="a36a1-105">各ストリームの種類では、読み取り、特定のバッキング ストアとバイトを書き込みます。</span><span class="sxs-lookup"><span data-stu-id="a36a1-105">Each stream type reads and writes bytes from and to its given backing store.</span></span> <span data-ttu-id="a36a1-106">バッキング ストアに接続しているストリームには、基本ストリームは呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="a36a1-106">Streams that connect to backing stores are called base streams.</span></span> <span data-ttu-id="a36a1-107">基本ストリームでは、バッキング ストアにストリームを接続するために必要なパラメーターを持つコンス トラクターがあります。</span><span class="sxs-lookup"><span data-stu-id="a36a1-107">Base streams have constructors that have the parameters necessary to connect the stream to the backing store.</span></span> <span data-ttu-id="a36a1-108">たとえば、<xref:System.IO.FileStream>コンス トラクターで、プロセスというように、ファイルの共有方法を指定します、パスのパラメーターを指定します。</span><span class="sxs-lookup"><span data-stu-id="a36a1-108">For example, <xref:System.IO.FileStream> has constructors that specify a path parameter, which specifies how the file will be shared by processes, and so on.</span></span>  
  
 <span data-ttu-id="a36a1-109">デザイン、<xref:System.IO>簡略化されたストリームを構成するクラスを提供します。</span><span class="sxs-lookup"><span data-stu-id="a36a1-109">The design of the <xref:System.IO> classes provides simplified stream composing.</span></span> <span data-ttu-id="a36a1-110">基本ストリームは、必要な機能を提供する 1 つ以上のパススルー ストリームにアタッチできます。</span><span class="sxs-lookup"><span data-stu-id="a36a1-110">Base streams can be attached to one or more pass-through streams that provide the functionality you want.</span></span> <span data-ttu-id="a36a1-111">推奨される種類を読み取りまたは簡単に記述できるようにする、リーダーまたはライターが、チェーンの末尾にアタッチできます。</span><span class="sxs-lookup"><span data-stu-id="a36a1-111">A reader or writer can be attached to the end of the chain so that the preferred types can be read or written easily.</span></span>  
  
 <span data-ttu-id="a36a1-112">次のコード例を作成、 **FileStream** 、既存の周囲`MyFile.txt`バッファーへの順序で`MyFile.txt`です。</span><span class="sxs-lookup"><span data-stu-id="a36a1-112">The following code example creates a **FileStream** around the existing `MyFile.txt` in order to buffer `MyFile.txt`.</span></span> <span data-ttu-id="a36a1-113">(なお**Filestream**は既定ではバッファーに格納します)。次に、<xref:System.IO.StreamReader>から文字を読み取るには、 **FileStream**に渡される、 **StreamReader**コンス トラクター引数として。</span><span class="sxs-lookup"><span data-stu-id="a36a1-113">(Note that **FileStreams** are buffered by default.) Next, a <xref:System.IO.StreamReader> is created to read characters from the **FileStream**, which is passed to the **StreamReader** as its constructor argument.</span></span> <span data-ttu-id="a36a1-114"><xref:System.IO.StreamReader.ReadLine%2A>まで読み取ります<xref:System.IO.StreamReader.Peek%2A>文字を検索します。</span><span class="sxs-lookup"><span data-stu-id="a36a1-114"><xref:System.IO.StreamReader.ReadLine%2A> reads until <xref:System.IO.StreamReader.Peek%2A> finds no more characters.</span></span>  
  
 [!code-cpp[System.IO.StreamReader#20](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.IO.StreamReader/CPP/source2.cpp#20)]
 [!code-csharp[System.IO.StreamReader#20](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.StreamReader/CS/source2.cs#20)]
 [!code-vb[System.IO.StreamReader#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.StreamReader/VB/source2.vb#20)]  
  
 <span data-ttu-id="a36a1-115">次のコード例を作成、 **FileStream** 、既存の周囲`MyFile.txt`バッファーへの順序で`MyFile.txt`です。</span><span class="sxs-lookup"><span data-stu-id="a36a1-115">The following code example creates a **FileStream** around the existing `MyFile.txt` in order to buffer `MyFile.txt`.</span></span> <span data-ttu-id="a36a1-116">(なお**Filestream**は既定ではバッファーに格納します)。次に、 **BinaryReader**からバイトを読み取りが作成、 **FileStream**に渡される、 **BinaryReader**コンス トラクター引数として。</span><span class="sxs-lookup"><span data-stu-id="a36a1-116">(Note that **FileStreams** are buffered by default.) Next, a **BinaryReader** is created to read bytes from the **FileStream**, which is passed to the **BinaryReader** as its constructor argument.</span></span> <span data-ttu-id="a36a1-117"><xref:System.IO.BinaryReader.ReadByte%2A>まで読み取ります<xref:System.IO.BinaryReader.PeekChar%2A>以上のバイトを検索します。</span><span class="sxs-lookup"><span data-stu-id="a36a1-117"><xref:System.IO.BinaryReader.ReadByte%2A> reads until <xref:System.IO.BinaryReader.PeekChar%2A> finds no more bytes.</span></span>  
  
 [!code-cpp[System.IO.StreamReader#21](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.IO.StreamReader/CPP/source3.cpp#21)]
 [!code-csharp[System.IO.StreamReader#21](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.StreamReader/CS/source3.cs#21)]
 [!code-vb[System.IO.StreamReader#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.StreamReader/VB/source3.vb#21)]  
  
## <a name="see-also"></a><span data-ttu-id="a36a1-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="a36a1-118">See Also</span></span>  
 <xref:System.IO.StreamReader>  
 <xref:System.IO.StreamReader.ReadLine%2A?displayProperty=nameWithType>  
 <xref:System.IO.StreamReader.Peek%2A?displayProperty=nameWithType>  
 <xref:System.IO.FileStream>  
 <xref:System.IO.BinaryReader>  
 <xref:System.IO.BinaryReader.ReadByte%2A?displayProperty=nameWithType>  
 <xref:System.IO.BinaryReader.PeekChar%2A?displayProperty=nameWithType>
