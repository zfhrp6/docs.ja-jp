---
title: "リーダーからのデータの読み込み"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7e74918c-bc72-4977-a49b-e1520a6d8f60
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 9e9f934d6bff2c9ff3733551bca89b43920f3104
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/23/2017
---
# <a name="load-data-from-a-reader"></a><span data-ttu-id="3d433-102">リーダーからのデータの読み込み</span><span class="sxs-lookup"><span data-stu-id="3d433-102">Load Data from a Reader</span></span>
<span data-ttu-id="3d433-103"><xref:System.Xml.XmlDocument.Load%2A> メソッドに <xref:System.Xml.XmlReader> パラメーターを渡して XML ドキュメントを読み込むと、他の形式からデータを読み込む場合と比較して、その動作に違いがあります。</span><span class="sxs-lookup"><span data-stu-id="3d433-103">If an XML document is loaded using the <xref:System.Xml.XmlDocument.Load%2A> method and a parameter of an <xref:System.Xml.XmlReader>, there are differences in the behavior that occurs when compared to the behavior of loading data from the other formats.</span></span> <span data-ttu-id="3d433-104">リーダーが初期状態のとき、<xref:System.Xml.XmlDocument.Load%2A> メソッドは、リーダーからのコンテンツ全体を使用して、リーダー内のすべてのデータから XML ドキュメント オブジェクト モデル (DOM) を構築します。</span><span class="sxs-lookup"><span data-stu-id="3d433-104">If the reader is in its initial state, <xref:System.Xml.XmlDocument.Load%2A> consumes the entire contents from the reader and builds the XML Document Object Model (DOM) from all the data in the reader.</span></span>  
  
 <span data-ttu-id="3d433-105">既にリーダーがドキュメント内のあるノード上に位置している場合、リーダーが <xref:System.Xml.XmlDocument.Load%2A> メソッドに渡されると、<xref:System.Xml.XmlDocument.Load%2A> は現在のノードと、現在の深さを閉じる終了タグまで、その兄弟すべてをメモリに読み込もうとします。</span><span class="sxs-lookup"><span data-stu-id="3d433-105">If the reader is already positioned on a node somewhere in the document, and the reader is then passed to the <xref:System.Xml.XmlDocument.Load%2A> method, <xref:System.Xml.XmlDocument.Load%2A> attempts to read the current node and all of its siblings, up to the end tag that closes the current depth into memory.</span></span> <span data-ttu-id="3d433-106"><xref:System.Xml.XmlDocument.Load%2A> はリーダーからの XML が整形式かどうかを検証するので、<xref:System.Xml.XmlDocument.Load%2A> が成功するかどうかは、読み込みを試みた時点でリーダーが位置していたノードに依存します。</span><span class="sxs-lookup"><span data-stu-id="3d433-106">The success of the attempted <xref:System.Xml.XmlDocument.Load%2A> depends on the node that the reader is on when the load is attempted, as <xref:System.Xml.XmlDocument.Load%2A> verifies that the XML from the reader is well-formed.</span></span> <span data-ttu-id="3d433-107">XML が整形式でない場合、<xref:System.Xml.XmlDocument.Load%2A> は例外をスローします。</span><span class="sxs-lookup"><span data-stu-id="3d433-107">If the XML is not well-formed, the <xref:System.Xml.XmlDocument.Load%2A> throws an exception.</span></span> <span data-ttu-id="3d433-108">たとえば、次のノード セットは、ルート レベルの要素が 2 つ含まれ、XML が整形式ではないため、<xref:System.Xml.XmlDocument.Load%2A> は例外をスローします。</span><span class="sxs-lookup"><span data-stu-id="3d433-108">For example, the following set of nodes contain two root-level elements, the XML is not well-formed, and <xref:System.Xml.XmlDocument.Load%2A> throws an exception.</span></span>  
  
-   <span data-ttu-id="3d433-109">Comment ノード、Element ノード、Element ノード、EndElement ノードの順序のノード セット</span><span class="sxs-lookup"><span data-stu-id="3d433-109">Comment node, followed by an Element node, followed by an Element node, followed by an EndElement node.</span></span>  
  
 <span data-ttu-id="3d433-110">次のノード セットは、ルート レベルの要素が存在しないため、不完全な DOM が作成されます。</span><span class="sxs-lookup"><span data-stu-id="3d433-110">The following set of nodes creates an incomplete DOM, because there is no root-level element.</span></span>  
  
-   <span data-ttu-id="3d433-111">Comment ノード、ProcessingInstruction ノード、Comment ノード、EndElement ノードの順序のノード セット</span><span class="sxs-lookup"><span data-stu-id="3d433-111">Comment node followed by a ProcessingInstruction node followed by a Comment node followed by an EndElement node.</span></span>  
  
 <span data-ttu-id="3d433-112">この場合、例外はスローされず、データが読み込まれます。</span><span class="sxs-lookup"><span data-stu-id="3d433-112">This does not throw an exception, and the data is loaded.</span></span> <span data-ttu-id="3d433-113">これらのノードの最上位にルート要素を追加すると、エラーなしで保存できる整形式の XML を作成できます。</span><span class="sxs-lookup"><span data-stu-id="3d433-113">You can add a root element to the top of these nodes and create well-formed XML that can be saved without error.</span></span>  
  
 <span data-ttu-id="3d433-114">ドキュメントのルート レベルとしては無効なリーフ ノード (たとえば空白ノードや属性ノード) にリーダーが位置している場合、リーダーはルートとして使用できるノードに移動するまで読み込みを続行します。</span><span class="sxs-lookup"><span data-stu-id="3d433-114">If the reader is positioned on a leaf node that is invalid for the root level of a document (for example, a white space or attribute node), the reader continues to read until it is positioned on a node that can be used for the root.</span></span> <span data-ttu-id="3d433-115">ドキュメントの読み込みは、この位置から開始されます。</span><span class="sxs-lookup"><span data-stu-id="3d433-115">The document begins loading at this point.</span></span>  
  
 <span data-ttu-id="3d433-116">既定では、<xref:System.Xml.XmlDocument.Load%2A> は、ドキュメント型定義 (DTD) またはスキーマ検証を使用して、XML が有効かどうかを検証しません。</span><span class="sxs-lookup"><span data-stu-id="3d433-116">By default, <xref:System.Xml.XmlDocument.Load%2A> does not verify whether the XML is valid using document type definition (DTD) or schema validation.</span></span> <span data-ttu-id="3d433-117">チェックするのは、XML が整形式かどうかだけです。</span><span class="sxs-lookup"><span data-stu-id="3d433-117">It only verifies whether the XML is well-formed.</span></span> <span data-ttu-id="3d433-118">検証を行うには、<xref:System.Xml.XmlReader> クラスを使用して <xref:System.Xml.XmlReaderSettings> を作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3d433-118">In order for validation to occur, you need to create an <xref:System.Xml.XmlReader> using the <xref:System.Xml.XmlReaderSettings> class.</span></span> <span data-ttu-id="3d433-119"><xref:System.Xml.XmlReader> クラスは、DTD またはスキーマ定義言語 (XSD) のスキーマを使用して検証を強制できます。</span><span class="sxs-lookup"><span data-stu-id="3d433-119">The <xref:System.Xml.XmlReader> class can enforce validation using a DTD or Schema definition language (XSD) schema.</span></span> <span data-ttu-id="3d433-120"><xref:System.Xml.ValidationType> クラスの <xref:System.Xml.XmlReaderSettings> プロパティによって、<xref:System.Xml.XmlReader> インスタンスが検証を強制するかどうかが決まります。</span><span class="sxs-lookup"><span data-stu-id="3d433-120">The <xref:System.Xml.ValidationType> property on the <xref:System.Xml.XmlReaderSettings> class determines whether the <xref:System.Xml.XmlReader> instance enforces validation.</span></span> <span data-ttu-id="3d433-121">XML データの検証の詳細については、<xref:System.Xml.XmlReader> のリファレンス ページの「解説」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3d433-121">For more information about validating XML data, see the Remarks section of the <xref:System.Xml.XmlReader> reference page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3d433-122">参照</span><span class="sxs-lookup"><span data-stu-id="3d433-122">See Also</span></span>  
 [<span data-ttu-id="3d433-123">XML ドキュメント オブジェクト モデル (DOM)</span><span class="sxs-lookup"><span data-stu-id="3d433-123">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
