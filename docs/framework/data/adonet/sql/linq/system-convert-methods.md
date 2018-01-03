---
title: "System.Convert メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3ca6c5b6-ea5d-4ab0-b675-f082135b342c
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 88193d7d8ca1544ad8db0947ff670f30ebddaa7d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="systemconvert-methods"></a><span data-ttu-id="eebe4-102">System.Convert メソッド</span><span class="sxs-lookup"><span data-stu-id="eebe4-102">System.Convert Methods</span></span>
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="eebe4-103"> は、次の <xref:System.Convert> メソッドをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="eebe4-103"> does not support the following <xref:System.Convert> methods.</span></span>  
  
-   <span data-ttu-id="eebe4-104"><xref:System.IFormatProvider> パラメーターを持つ形式。</span><span class="sxs-lookup"><span data-stu-id="eebe4-104">Versions with an <xref:System.IFormatProvider> parameter.</span></span>  
  
-   <span data-ttu-id="eebe4-105">文字配列またはバイト配列を扱うメソッド。</span><span class="sxs-lookup"><span data-stu-id="eebe4-105">Methods that involve char arrays or byte arrays:</span></span>  
  
    -   <xref:System.Convert.FromBase64CharArray%2A>  
  
    -   <xref:System.Convert.ToBase64CharArray%2A>  
  
    -   <xref:System.Convert.FromBase64String%2A>  
  
    -   <xref:System.Convert.ToBase64String%2A>  
  
-   <span data-ttu-id="eebe4-106">次のメソッド。</span><span class="sxs-lookup"><span data-stu-id="eebe4-106">The following methods:</span></span>  
  
    -   <span data-ttu-id="eebe4-107">`public static <Type2> To<Type2>(<Type1> value);` (</span><span class="sxs-lookup"><span data-stu-id="eebe4-107">`public static <Type2> To<Type2>(<Type1> value);` where</span></span>  
  
         <span data-ttu-id="eebe4-108">`Type1` および `Type2` は `sbyte`、`uint`、`ulong`、`ushort` のいずれか)</span><span class="sxs-lookup"><span data-stu-id="eebe4-108">`Type1` and `Type2` are each one of `sbyte`, `uint`, `ulong`, or `ushort`.</span></span>  
  
    -   <span data-ttu-id="eebe4-109">C#: </span><span class="sxs-lookup"><span data-stu-id="eebe4-109">C#:</span></span>  
  
         `int To<int type>(string value, int fromBase),`  
  
         `ToString(... value, int toBase)`  
  
    -   <span data-ttu-id="eebe4-110">Visual Basic: </span><span class="sxs-lookup"><span data-stu-id="eebe4-110">Visual Basic:</span></span>  
  
         `Function To(Of [Numeric])(value as String, fromBase As Integer)`  
  
         `As [Numeric], ToString( value As …, toBase As Integer)`  
  
    -   <xref:System.Convert.IsDBNull%2A>  
  
    -   <xref:System.Convert.GetTypeCode%2A>  
  
    -   <xref:System.Convert.ChangeType%2A>  
  
## <a name="see-also"></a><span data-ttu-id="eebe4-111">参照</span><span class="sxs-lookup"><span data-stu-id="eebe4-111">See Also</span></span>  
 [<span data-ttu-id="eebe4-112">データ型と関数</span><span class="sxs-lookup"><span data-stu-id="eebe4-112">Data Types and Functions</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/data-types-and-functions.md)
