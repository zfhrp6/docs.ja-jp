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
# <a name="composing-streams"></a><span data-ttu-id="acf4e-102">ストリームの構成</span><span class="sxs-lookup"><span data-stu-id="acf4e-102">Composing Streams</span></span>
<span data-ttu-id="acf4e-103">バッキング ストアは、ディスクやメモリなどの記憶域メディアです。</span><span class="sxs-lookup"><span data-stu-id="acf4e-103">A backing store is a storage medium, such as a disk or memory.</span></span> <span data-ttu-id="acf4e-104">さまざまなバッキング ストアが <xref:System.IO.Stream> クラスの実装としてそれぞれ独自のストリームを実装しています。</span><span class="sxs-lookup"><span data-stu-id="acf4e-104">Each different backing store implements its own stream as an implementation of the <xref:System.IO.Stream> class.</span></span> <span data-ttu-id="acf4e-105">各ストリームの種類は、指定されたバッキング ストアとの間でバイトの読み取りと書き込みを行います。</span><span class="sxs-lookup"><span data-stu-id="acf4e-105">Each stream type reads and writes bytes from and to its given backing store.</span></span> <span data-ttu-id="acf4e-106">バッキング ストアに接続するストリームは、基本ストリームと呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="acf4e-106">Streams that connect to backing stores are called base streams.</span></span> <span data-ttu-id="acf4e-107">基本ストリームには、ストリームをバッキング ストアに接続するために必要なパラメーターを持つコンストラクターがあります。</span><span class="sxs-lookup"><span data-stu-id="acf4e-107">Base streams have constructors that have the parameters necessary to connect the stream to the backing store.</span></span> <span data-ttu-id="acf4e-108">たとえば、<xref:System.IO.FileStream> には、プロセスでファイルを共有する方法を指定する path パラメーターなどを指定するコンストラクターがあります。</span><span class="sxs-lookup"><span data-stu-id="acf4e-108">For example, <xref:System.IO.FileStream> has constructors that specify a path parameter, which specifies how the file will be shared by processes, and so on.</span></span>  
  
 <span data-ttu-id="acf4e-109"><xref:System.IO> クラスは、簡易なストリーム構成で設計されています。</span><span class="sxs-lookup"><span data-stu-id="acf4e-109">The design of the <xref:System.IO> classes provides simplified stream composing.</span></span> <span data-ttu-id="acf4e-110">必要な機能を提供する 1 つ以上のパススルー ストリームに基本ストリームをアタッチすることができます。</span><span class="sxs-lookup"><span data-stu-id="acf4e-110">Base streams can be attached to one or more pass-through streams that provide the functionality you want.</span></span> <span data-ttu-id="acf4e-111">好みの種類の読み取りまたは書き込みを簡単に実行できるように、チェーンの末端に閲覧者またはライターをアタッチすることができます。</span><span class="sxs-lookup"><span data-stu-id="acf4e-111">A reader or writer can be attached to the end of the chain so that the preferred types can be read or written easily.</span></span>  
  
 <span data-ttu-id="acf4e-112">次のコード例では、`MyFile.txt` をバッファーするために既存の `MyFile.txt` を中心にして **FileStream** を作成します </span><span class="sxs-lookup"><span data-stu-id="acf4e-112">The following code example creates a **FileStream** around the existing `MyFile.txt` in order to buffer `MyFile.txt`.</span></span> <span data-ttu-id="acf4e-113">(**FileStreams** は既定でバッファーされます)。次に、**FileStream** から文字を読み取る <xref:System.IO.StreamReader> が作成されます。これはコンストラクター引数として **StreamReader** に渡されます。</span><span class="sxs-lookup"><span data-stu-id="acf4e-113">(Note that **FileStreams** are buffered by default.) Next, a <xref:System.IO.StreamReader> is created to read characters from the **FileStream**, which is passed to the **StreamReader** as its constructor argument.</span></span> <span data-ttu-id="acf4e-114"><xref:System.IO.StreamReader.ReadLine%2A> は、<xref:System.IO.StreamReader.Peek%2A> によって文字が検出されなくなるまで読み取りを行います。</span><span class="sxs-lookup"><span data-stu-id="acf4e-114"><xref:System.IO.StreamReader.ReadLine%2A> reads until <xref:System.IO.StreamReader.Peek%2A> finds no more characters.</span></span>  
  
 [!code-cpp[System.IO.StreamReader#20](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.IO.StreamReader/CPP/source2.cpp#20)]
 [!code-csharp[System.IO.StreamReader#20](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.StreamReader/CS/source2.cs#20)]
 [!code-vb[System.IO.StreamReader#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.StreamReader/VB/source2.vb#20)]  
  
 <span data-ttu-id="acf4e-115">次のコード例では、`MyFile.txt` をバッファーするために既存の `MyFile.txt` を中心にして **FileStream** を作成します </span><span class="sxs-lookup"><span data-stu-id="acf4e-115">The following code example creates a **FileStream** around the existing `MyFile.txt` in order to buffer `MyFile.txt`.</span></span> <span data-ttu-id="acf4e-116">(**FileStreams** は既定でバッファーされます)。次に、**FileStream** からバイトを読み取る **BinaryReader** が作成されます。これはコンストラクター引数として **BinaryReader** に渡されます。</span><span class="sxs-lookup"><span data-stu-id="acf4e-116">(Note that **FileStreams** are buffered by default.) Next, a **BinaryReader** is created to read bytes from the **FileStream**, which is passed to the **BinaryReader** as its constructor argument.</span></span> <span data-ttu-id="acf4e-117"><xref:System.IO.BinaryReader.ReadByte%2A> は、<xref:System.IO.BinaryReader.PeekChar%2A> によってバイトが検出されなくなるまで読み取りを行います。</span><span class="sxs-lookup"><span data-stu-id="acf4e-117"><xref:System.IO.BinaryReader.ReadByte%2A> reads until <xref:System.IO.BinaryReader.PeekChar%2A> finds no more bytes.</span></span>  
  
 [!code-cpp[System.IO.StreamReader#21](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.IO.StreamReader/CPP/source3.cpp#21)]
 [!code-csharp[System.IO.StreamReader#21](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.StreamReader/CS/source3.cs#21)]
 [!code-vb[System.IO.StreamReader#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.StreamReader/VB/source3.vb#21)]  
  
## <a name="see-also"></a><span data-ttu-id="acf4e-118">参照</span><span class="sxs-lookup"><span data-stu-id="acf4e-118">See Also</span></span>  
 <xref:System.IO.StreamReader>  
 <xref:System.IO.StreamReader.ReadLine%2A?displayProperty=nameWithType>  
 <xref:System.IO.StreamReader.Peek%2A?displayProperty=nameWithType>  
 <xref:System.IO.FileStream>  
 <xref:System.IO.BinaryReader>  
 <xref:System.IO.BinaryReader.ReadByte%2A?displayProperty=nameWithType>  
 <xref:System.IO.BinaryReader.PeekChar%2A?displayProperty=nameWithType>
