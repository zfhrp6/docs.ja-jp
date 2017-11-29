---
title: "関数型変換 (Visual Basic) の適用性"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3b74e134-e19b-44bc-8d06-e26c48305040
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 184f40aa5752a620a5a9af1f27efc598251a96c2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="applicability-of-functional-transformation-visual-basic"></a><span data-ttu-id="cb9ef-102">関数型変換 (Visual Basic) の適用性</span><span class="sxs-lookup"><span data-stu-id="cb9ef-102">Applicability of Functional Transformation (Visual Basic)</span></span>
<span data-ttu-id="cb9ef-103">純粋関数型変換は、さまざまな状況で適用できます。</span><span class="sxs-lookup"><span data-stu-id="cb9ef-103">Pure functional transformations are applicable in a wide variety of situations.</span></span>  
  
 <span data-ttu-id="cb9ef-104">関数型変換の方法は、構造化されたデータのクエリと操作に適しているため、LINQ テクノロジに適切に対応できます。</span><span class="sxs-lookup"><span data-stu-id="cb9ef-104">The functional transformation approach is ideally suited for querying and manipulating structured data; therefore it fits well with LINQ technologies.</span></span> <span data-ttu-id="cb9ef-105">ただし、関数型変換の適用範囲は、LINQ で使用する場合に比べてはるかに広範です。</span><span class="sxs-lookup"><span data-stu-id="cb9ef-105">However, functional transformation has a much wider applicability than use with LINQ.</span></span> <span data-ttu-id="cb9ef-106">データ形式の変換を中心とする処理はすべて、関数型変換の適用対象と考えることができます。</span><span class="sxs-lookup"><span data-stu-id="cb9ef-106">Any process where the main focus is on transforming data from one form to another should probably be considered as a candidate for functional transformation.</span></span>  
  
 <span data-ttu-id="cb9ef-107">この方法は、一見して適用対象とは思われない数多くの問題に適用できます。</span><span class="sxs-lookup"><span data-stu-id="cb9ef-107">This approach is applicable to many problems that might not appear at first glance to be a candidate.</span></span> <span data-ttu-id="cb9ef-108">次に示す適用対象では、関数型変換を LINQ と組み合わせて、または切り離して使用することを検討する必要があります。</span><span class="sxs-lookup"><span data-stu-id="cb9ef-108">Used in conjunction with or separately from LINQ, functional transformation should be considered for the following areas:</span></span>  
  
-   <span data-ttu-id="cb9ef-109">XML ベースのドキュメント。</span><span class="sxs-lookup"><span data-stu-id="cb9ef-109">XML-based documents.</span></span> <span data-ttu-id="cb9ef-110">XML 言語の整形式データは、関数型変換を通じて容易に操作できます。</span><span class="sxs-lookup"><span data-stu-id="cb9ef-110">Well-formed data of any XML dialect can be easily manipulated through functional transformation.</span></span> <span data-ttu-id="cb9ef-111">詳細については、次を参照してください。[関数型変換の XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/functional-transformation-of-xml.md)です。</span><span class="sxs-lookup"><span data-stu-id="cb9ef-111">For more information, see [Functional Transformation of XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/functional-transformation-of-xml.md).</span></span>  
  
-   <span data-ttu-id="cb9ef-112">その他の構造化されたファイル形式。</span><span class="sxs-lookup"><span data-stu-id="cb9ef-112">Other structured file formats.</span></span> <span data-ttu-id="cb9ef-113">Windows.ini ファイルからプレーンテキストのドキュメントに至るほとんどのファイルは、分析や変換に適した構造を備えています。</span><span class="sxs-lookup"><span data-stu-id="cb9ef-113">From Windows.ini files to plain text documents, most files have some structure that lends itself to analysis and transformation.</span></span>  
  
-   <span data-ttu-id="cb9ef-114">データ ストリーミング プロトコル。</span><span class="sxs-lookup"><span data-stu-id="cb9ef-114">Data streaming protocols.</span></span> <span data-ttu-id="cb9ef-115">通信プロトコルへのデータのエンコードおよび通信プロトコルからのデータのデコードは、単純な関数型変換で表せる場合がほとんどです。</span><span class="sxs-lookup"><span data-stu-id="cb9ef-115">Encoding data into and decoding data from communication protocols can often be represented by a simple functional transform.</span></span>  
  
-   <span data-ttu-id="cb9ef-116">RDBMS データと OODBMS データ。</span><span class="sxs-lookup"><span data-stu-id="cb9ef-116">RDBMS and OODBMS data.</span></span> <span data-ttu-id="cb9ef-117">リレーショナル データベースおよびオブジェクト指向データベースは、構造化されたデータ ソースとして XML と同様に広く使用されています。</span><span class="sxs-lookup"><span data-stu-id="cb9ef-117">Relational and object-oriented databases, just like XML, are widely-used structured data sources.</span></span>  
  
-   <span data-ttu-id="cb9ef-118">数学的、統計的、および科学的なソリューション。</span><span class="sxs-lookup"><span data-stu-id="cb9ef-118">Mathematic, statistic, and science solutions.</span></span> <span data-ttu-id="cb9ef-119">これらの分野では、視覚化、予測、重要な問題の解決などを支援する際に、大きなデータ セットが操作される傾向があります。</span><span class="sxs-lookup"><span data-stu-id="cb9ef-119">These fields tend to manipulate large data sets to assist the user in visualizing, estimating, or actually solving non-trivial problems.</span></span>  
  
 <span data-ttu-id="cb9ef-120">」の説明に従って[純粋に戻った関数にリファクタリング (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/refactoring-into-pure-functions.md)、関数型プログラミングの例は、純粋関数を使用します。</span><span class="sxs-lookup"><span data-stu-id="cb9ef-120">As described in [Refactoring Into Pure Functions (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/refactoring-into-pure-functions.md), using pure functions is an example of functional programming.</span></span> <span data-ttu-id="cb9ef-121">純粋関数は、その直接的な利点に加えて、関数型変換の観点から問題について考える場合に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="cb9ef-121">In additional to their immediate benefits, using pure functions provides valuable experience in thinking about problems from a functional transformation perspective.</span></span> <span data-ttu-id="cb9ef-122">この方法は、プログラムおよびクラスの設計にも大きな影響を与えます。</span><span class="sxs-lookup"><span data-stu-id="cb9ef-122">This approach can also have major impact on program and class design.</span></span> <span data-ttu-id="cb9ef-123">上に示したように、問題がデータ変換ソリューションに関連している場合は、特に影響を受けます。</span><span class="sxs-lookup"><span data-stu-id="cb9ef-123">This is especially true when a problem lends itself to a data transformation solution as described above.</span></span>  
  
 <span data-ttu-id="cb9ef-124">このチュートリアルでは扱いませんが、関数型変換の観点から影響を受ける設計は、アクターとしてオブジェクトよりもプロセスに重点を置く傾向があり、その結果であるソリューションは、個別のオブジェクト状態変更ではなく一連の大規模な変換として実装される傾向にあります。</span><span class="sxs-lookup"><span data-stu-id="cb9ef-124">Although they are beyond the scope of this tutorial, designs that are influenced by the functional transformation perspective tend to center on processes more than on objects as actors, and the resulting solution tends to be implemented as series of large-scale transformations, rather than individual object state changes.</span></span>  
  
 <span data-ttu-id="cb9ef-125">ここでも、Visual Basic では、アプリケーションにとって最善の設計は、両方の要素を組み込むことがありますので、命令型と機能の両方のアプローチがサポートしているに注意してください。</span><span class="sxs-lookup"><span data-stu-id="cb9ef-125">Again, remember that Visual Basic supports both imperative and functional approaches, so the best design for your application might incorporate elements of both.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb9ef-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="cb9ef-126">See Also</span></span>  
 [<span data-ttu-id="cb9ef-127">純粋関数型変換 (Visual Basic) の概要</span><span class="sxs-lookup"><span data-stu-id="cb9ef-127">Introduction to Pure Functional Transformations (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/introduction-to-pure-functional-transformations.md)  
 [<span data-ttu-id="cb9ef-128">XML の関数型変換 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cb9ef-128">Functional Transformation of XML (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/functional-transformation-of-xml.md)  
 [<span data-ttu-id="cb9ef-129">純粋関数 (Visual Basic) へのリファクタリング</span><span class="sxs-lookup"><span data-stu-id="cb9ef-129">Refactoring Into Pure Functions (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/refactoring-into-pure-functions.md)
