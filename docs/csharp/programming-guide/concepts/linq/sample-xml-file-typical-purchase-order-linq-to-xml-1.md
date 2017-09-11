---
title: "サンプル XML ファイル : 一般的な購買発注書 (LINQ to XML)"
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
ms.assetid: dcbfb859-24fc-4758-b01c-51d1b6f644e6
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
ms.openlocfilehash: 19168f40729cf5d751c791b1dc98efae1f55fe89
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="sample-xml-file-typical-purchase-order-linq-to-xml"></a><span data-ttu-id="66a4d-102">サンプル XML ファイル : 一般的な購買発注書 (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="66a4d-102">Sample XML File: Typical Purchase Order (LINQ to XML)</span></span>
<span data-ttu-id="66a4d-103">次の XML ファイルは、[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] ドキュメントのさまざまな例で使用されます。</span><span class="sxs-lookup"><span data-stu-id="66a4d-103">The following XML file is used in various examples in the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] documentation.</span></span> <span data-ttu-id="66a4d-104">このファイルは、一般的な購買発注書です。</span><span class="sxs-lookup"><span data-stu-id="66a4d-104">This file is a typical purchase order.</span></span>  
  
## <a name="purchaseorderxml"></a><span data-ttu-id="66a4d-105">PurchaseOrder.xml</span><span class="sxs-lookup"><span data-stu-id="66a4d-105">PurchaseOrder.xml</span></span>  
  
```xml  
<?xml version="1.0"?>  
<PurchaseOrder PurchaseOrderNumber="99503" OrderDate="1999-10-20">  
  <Address Type="Shipping">  
    <Name>Ellen Adams</Name>  
    <Street>123 Maple Street</Street>  
    <City>Mill Valley</City>  
    <State>CA</State>  
    <Zip>10999</Zip>  
    <Country>USA</Country>  
  </Address>  
  <Address Type="Billing">  
    <Name>Tai Yee</Name>  
    <Street>8 Oak Avenue</Street>  
    <City>Old Town</City>  
    <State>PA</State>  
    <Zip>95819</Zip>  
    <Country>USA</Country>  
  </Address>  
  <DeliveryNotes>Please leave packages in shed by driveway.</DeliveryNotes>  
  <Items>  
    <Item PartNumber="872-AA">  
      <ProductName>Lawnmower</ProductName>  
      <Quantity>1</Quantity>  
      <USPrice>148.95</USPrice>  
      <Comment>Confirm this is electric</Comment>  
    </Item>  
    <Item PartNumber="926-AA">  
      <ProductName>Baby Monitor</ProductName>  
      <Quantity>2</Quantity>  
      <USPrice>39.98</USPrice>  
      <ShipDate>1999-05-21</ShipDate>  
    </Item>  
  </Items>  
</PurchaseOrder>  
```  
  
## <a name="see-also"></a><span data-ttu-id="66a4d-106">関連項目</span><span class="sxs-lookup"><span data-stu-id="66a4d-106">See Also</span></span>  
 [<span data-ttu-id="66a4d-107">サンプル XML ドキュメント (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="66a4d-107">Sample XML Documents (LINQ to XML)</span></span>](../../../../csharp/programming-guide/concepts/linq/sample-xml-documents-linq-to-xml.md)

