---
title: "LINQ to XML を使用した XML データの処理"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 059d6b9d-63f7-4011-9ba8-8406f0bbae7d
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 26258489742db3de108ddf68f68074682c30fe57
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/23/2017
---
# <a name="process-xml-data-using-linq-to-xml"></a><span data-ttu-id="a463d-102">LINQ to XML を使用した XML データの処理</span><span class="sxs-lookup"><span data-stu-id="a463d-102">Process XML Data Using LINQ to XML</span></span>
<span data-ttu-id="a463d-103">LINQ to XML は、XML データの処理を目的とした Microsoft .NET Framework version 3.5 の新しいモデルです。</span><span class="sxs-lookup"><span data-stu-id="a463d-103">LINQ to XML is the new model in the .NET Framework version 3.5 for processing XML data.</span></span> <span data-ttu-id="a463d-104">LINQ to XML を使用することで、XML ドキュメントのクエリ、変更、作成、保存、シリアル化など、XML データを扱う際に必要な処理をすべて実行できます。</span><span class="sxs-lookup"><span data-stu-id="a463d-104">LINQ to XML allows developers to do everything they would expect with XML data: querying, modifying, creating, saving, and serializing XML documents.</span></span> <span data-ttu-id="a463d-105">特に、クエリと作成の機能が役立ちます。</span><span class="sxs-lookup"><span data-stu-id="a463d-105">The real advantages lie in the query and creation capabilities.</span></span>  
  
 <span data-ttu-id="a463d-106">LINQ to XML のクエリでは、XPath や XQuery よりも SQL に類似した構文が使用され、簡潔で表現力に優れています。</span><span class="sxs-lookup"><span data-stu-id="a463d-106">Queries in LINQ to XML are succinct and expressive, using syntax more similar to SQL than to XPath or XQuery.</span></span> <span data-ttu-id="a463d-107">クエリの結果を要素や属性のコレクションとして返すことができ、XElement オブジェクトのパラメーターとして使用できるため、XML ツリーの形を簡単に変換することができます。</span><span class="sxs-lookup"><span data-stu-id="a463d-107">Because query results can be returned as collections of elements or attributes and can be used as parameters for XElement objects, XML trees can be easily transformed from one shape to another.</span></span>  
  
 <span data-ttu-id="a463d-108">LINQ to XML では、.NET Framework version 3.5 の統合言語クエリ (LINQ) テクノロジを利用しています。</span><span class="sxs-lookup"><span data-stu-id="a463d-108">LINQ to XML leverages the language-integrated query (LINQ) technology in the .NET Framework version 3.5.</span></span> <span data-ttu-id="a463d-109">LINQ は C# および Visual Basic の言語構文を拡張したもので、潜在的には任意のデータ ストアまで拡張できる強力なクエリ機能を備えています。</span><span class="sxs-lookup"><span data-stu-id="a463d-109">LINQ extends the language syntax of C# and Visual Basic to provide powerful query capabilities that can be extended to potentially any data store.</span></span>  
  
 <span data-ttu-id="a463d-110">LINQ の詳細な使用方法については、「[LINQ to XML](http://msdn.microsoft.com/library/f0fe21e9-ee43-4a55-b91a-0800e5782c13)」を参照してください。LINQ フレームワークの概要については、「[LINQ (Language-Integrated Query)](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d)」(LINQ (統合言語クエリ)) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a463d-110">See [LINQ to XML](http://msdn.microsoft.com/library/f0fe21e9-ee43-4a55-b91a-0800e5782c13) for a detailed discussion of its use, and see [LINQ (Language-Integrated Query)](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d) for an overview of the LINQ framework.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a463d-111">参照</span><span class="sxs-lookup"><span data-stu-id="a463d-111">See Also</span></span>  
 <xref:System.Xml.Linq>  
 <xref:System.Linq>  
 [<span data-ttu-id="a463d-112">LINQ to XML とDOM</span><span class="sxs-lookup"><span data-stu-id="a463d-112">LINQ to XML vs. DOM</span></span>](http://msdn.microsoft.com/library/19b5ed02-feb2-455a-8897-f7f0fd76aca3)  
 [<span data-ttu-id="a463d-113">LINQ to XML とその他の XML テクノロジ</span><span class="sxs-lookup"><span data-stu-id="a463d-113">LINQ to XML vs. Other XML Technologies</span></span>](http://msdn.microsoft.com/library/7ba1eecf-f09a-42de-bc80-22ca5b2e42d3)
