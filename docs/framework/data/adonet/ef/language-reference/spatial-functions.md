---
title: "空間関数"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 90cb177d-88a0-45be-97e8-3b306283c6e0
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 935708457c3ebc8257b2495da36886468be1c706
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="spatial-functions"></a><span data-ttu-id="8c662-102">空間関数</span><span class="sxs-lookup"><span data-stu-id="8c662-102">Spatial Functions</span></span>
<span data-ttu-id="8c662-103">空間型のリテラル形式はありません。</span><span class="sxs-lookup"><span data-stu-id="8c662-103">There is no literal format for spatial types.</span></span> <span data-ttu-id="8c662-104">ただし、Well-Known Text 形式の文字列を使用して呼び出す正規の Entity Framework 関数を使用できます。</span><span class="sxs-lookup"><span data-stu-id="8c662-104">However, you can use canonical Entity Framework functions that you call using strings in Well-Known Text format.</span></span> <span data-ttu-id="8c662-105">たとえば、次の関数呼び出しでは、ジオメトリ ポイントが作成されます。</span><span class="sxs-lookup"><span data-stu-id="8c662-105">For example, the following function call creates a geometry point:</span></span>  
  
```  
GeometryFromText('POINT (43 -73)')  
```  
  
 <span data-ttu-id="8c662-106">[SpatialEdmFunctions メソッド](http://msdn.microsoft.com/library/hh749531.aspx)ページには、空間に関する正規 Entity Framework メソッドすべてが一覧表示されます。</span><span class="sxs-lookup"><span data-stu-id="8c662-106">The [SpatialEdmFunctions Methods](http://msdn.microsoft.com/library/hh749531.aspx) page lists all spatial canonical Entity Framework methods.</span></span> <span data-ttu-id="8c662-107">目的のメソッドをクリックすると、関数に渡す必要のあるパラメーターを確認できます。</span><span class="sxs-lookup"><span data-stu-id="8c662-107">Click on a method of interest to see what parameters should be passed to a function.</span></span>
