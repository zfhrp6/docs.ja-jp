---
title: "サンプル XML ファイル: 名前空間内の数値データ 3"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: 51750cab-3c66-4511-90fb-b9d211308d31
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 5b02c0990a73aa18b4ce7e7b6ff652ad485ed854
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="sample-xml-file-numerical-data-in-a-namespace"></a><span data-ttu-id="86be0-102">サンプル XML ファイル : 名前空間内の数値データ</span><span class="sxs-lookup"><span data-stu-id="86be0-102">Sample XML File: Numerical Data in a Namespace</span></span>
<span data-ttu-id="86be0-103">次の XML ファイルは、[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] ドキュメントのさまざまな例で使用されます。</span><span class="sxs-lookup"><span data-stu-id="86be0-103">The following XML file is used in various examples in the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] documentation.</span></span> <span data-ttu-id="86be0-104">このファイルには、集計、平均、およびグループ化用の数値データが含まれています。</span><span class="sxs-lookup"><span data-stu-id="86be0-104">This file contains numerical data for summing, averaging, and grouping.</span></span> <span data-ttu-id="86be0-105">XML は名前空間に含まれています。</span><span class="sxs-lookup"><span data-stu-id="86be0-105">The XML is in a namespace.</span></span>  
  
## <a name="data"></a><span data-ttu-id="86be0-106">データ</span><span class="sxs-lookup"><span data-stu-id="86be0-106">Data</span></span>  
  
```xml  
<Root xmlns='http://www.adatum.com'>  
  <TaxRate>7.25</TaxRate>  
  <Data>  
    <Category>A</Category>  
    <Quantity>3</Quantity>  
    <Price>24.50</Price>  
  </Data>  
  <Data>  
    <Category>B</Category>  
    <Quantity>1</Quantity>  
    <Price>89.99</Price>  
  </Data>  
  <Data>  
    <Category>A</Category>  
    <Quantity>5</Quantity>  
    <Price>4.95</Price>  
  </Data>  
  <Data>  
    <Category>A</Category>  
    <Quantity>3</Quantity>  
    <Price>66.00</Price>  
  </Data>  
  <Data>  
    <Category>B</Category>  
    <Quantity>10</Quantity>  
    <Price>.99</Price>  
  </Data>  
  <Data>  
    <Category>A</Category>  
    <Quantity>15</Quantity>  
    <Price>29.00</Price>  
  </Data>  
  <Data>  
    <Category>B</Category>  
    <Quantity>8</Quantity>  
    <Price>6.99</Price>  
  </Data>  
</Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="86be0-107">関連項目</span><span class="sxs-lookup"><span data-stu-id="86be0-107">See Also</span></span>  
 [<span data-ttu-id="86be0-108">サンプル XML ドキュメント (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="86be0-108">Sample XML Documents (LINQ to XML)</span></span>](../../../../csharp/programming-guide/concepts/linq/sample-xml-documents-linq-to-xml.md)

