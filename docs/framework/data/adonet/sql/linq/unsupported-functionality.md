---
title: "サポートされていない機能"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e480cfb5-697e-42c8-bed5-9264c945c4f9
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 6dd8ccebd278fdc36c536c49f7f1d4262b2de8c1
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="unsupported-functionality"></a><span data-ttu-id="231e1-102">サポートされていない機能</span><span class="sxs-lookup"><span data-stu-id="231e1-102">Unsupported Functionality</span></span>
<span data-ttu-id="231e1-103">LINQ to SQL では、次の SQL 機能は、既存の共通言語ランタイム (CLR) および .NET Framework の構成要素の変換からは公開できません。</span><span class="sxs-lookup"><span data-stu-id="231e1-103">In LINQ to SQL, the following SQL functionality cannot be exposed through translation of existing common language runtime (CLR) and .NET Framework constructs:</span></span>  
  
-   `STDDEV`  
  
-   `LIKE`  
  
     <span data-ttu-id="231e1-104">`LIKE` は直接変換によってサポートされませんが、同様の機能が <xref:System.Data.Linq.SqlClient.SqlMethods> クラスにあります。</span><span class="sxs-lookup"><span data-stu-id="231e1-104">Although `LIKE` is not supported through direct translation, similar functionality exists in the <xref:System.Data.Linq.SqlClient.SqlMethods> class.</span></span> <span data-ttu-id="231e1-105">詳細については、「<xref:System.Data.Linq.SqlClient.SqlMethods.Like%2A?displayProperty=nameWithType>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="231e1-105">For more information, see <xref:System.Data.Linq.SqlClient.SqlMethods.Like%2A?displayProperty=nameWithType>.</span></span>  
  
-   `DATEDIFF`  
  
     <span data-ttu-id="231e1-106">LINQ to SQL では、`DATEDIFF` のサポートが制限されています。</span><span class="sxs-lookup"><span data-stu-id="231e1-106">LINQ to SQL has limited support for `DATEDIFF`.</span></span> <span data-ttu-id="231e1-107">同様の機能が <xref:System.Data.Linq.SqlClient.SqlMethods> クラスにあります。</span><span class="sxs-lookup"><span data-stu-id="231e1-107">Similar functionality exists in the <xref:System.Data.Linq.SqlClient.SqlMethods> class.</span></span>  
  
-   `ROUND`  
  
     <span data-ttu-id="231e1-108">LINQ to SQL では、`ROUND` のサポートが制限されています。</span><span class="sxs-lookup"><span data-stu-id="231e1-108">LINQ to SQL has limited support for `ROUND`.</span></span> <span data-ttu-id="231e1-109">詳細については、次を参照してください。 [System.Math メソッド](system-math-methods.md)です。</span><span class="sxs-lookup"><span data-stu-id="231e1-109">For more information, see [System.Math Methods](system-math-methods.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="231e1-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="231e1-110">See Also</span></span>  
 [<span data-ttu-id="231e1-111">データ型および関数</span><span class="sxs-lookup"><span data-stu-id="231e1-111">Data Types and Functions</span></span>](data-types-and-functions.md)
