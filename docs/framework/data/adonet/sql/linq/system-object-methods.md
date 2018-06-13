---
title: System.Object メソッド
ms.date: 03/30/2017
ms.assetid: 5397fca0-689e-443e-802f-e1cbdc866427
ms.openlocfilehash: bd4b30a65e7ad9391d9b867884d1c909491344bc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33355176"
---
# <a name="systemobject-methods"></a><span data-ttu-id="12440-102">System.Object メソッド</span><span class="sxs-lookup"><span data-stu-id="12440-102">System.Object Methods</span></span>
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="12440-103"> 次のサポート<xref:System.Object>メソッドです。</span><span class="sxs-lookup"><span data-stu-id="12440-103"> supports the following <xref:System.Object> methods.</span></span>  
  
|||  
|-|-|  
|<xref:System.Object.Equals%28System.Object%29?displayProperty=nameWithType>|<xref:System.Object.Equals%28System.Object%2CSystem.Object%29?displayProperty=nameWithType>|  
|<xref:System.Object.ToString?displayProperty=nameWithType>||  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="12440-104"> は、次の <xref:System.Object> メソッドをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="12440-104"> does not support the following <xref:System.Object> methods.</span></span>  
  
|||  
|-|-|  
|<xref:System.Object.GetHashCode?displayProperty=nameWithType>|<xref:System.Object.ReferenceEquals%28System.Object%2CSystem.Object%29?displayProperty=nameWithType>|  
|<xref:System.Object.MemberwiseClone?displayProperty=nameWithType>|<xref:System.Object.GetType?displayProperty=nameWithType>|  
|<span data-ttu-id="12440-105"><xref:System.Object.ToString?displayProperty=nameWithType>、`BINARY`、`VARBINARY`、`IMAGE` などのバイナリ型の `TIMESTAMP`</span><span class="sxs-lookup"><span data-stu-id="12440-105"><xref:System.Object.ToString?displayProperty=nameWithType> for binary types such as `BINARY`, `VARBINARY`, `IMAGE`, and `TIMESTAMP`.</span></span>||  
  
## <a name="differences-from-net"></a><span data-ttu-id="12440-106">.NET との相違</span><span class="sxs-lookup"><span data-stu-id="12440-106">Differences from .NET</span></span>  
 <span data-ttu-id="12440-107">出力<xref:System.Object.ToString?displayProperty=nameWithType>倍を使用する SQL `CONVERT`(nvarchar (30), @x, 2) SQL にします。</span><span class="sxs-lookup"><span data-stu-id="12440-107">The output of <xref:System.Object.ToString?displayProperty=nameWithType> for double uses SQL `CONVERT`(NVARCHAR(30), @x, 2) on SQL.</span></span> <span data-ttu-id="12440-108">このとき、SQL は常に 16 桁と指数表記を使用します (たとえば、0 に対して "0.000000000000000e+000" を使用)。</span><span class="sxs-lookup"><span data-stu-id="12440-108">SQL always uses 16 digits and scientific notation in this case (for example, "0.000000000000000e+000" for 0).</span></span> <span data-ttu-id="12440-109">そのため、<xref:System.Object.ToString?displayProperty=nameWithType> 変換では、.NET Framework 内の <xref:System.Convert.ToString%2A?displayProperty=nameWithType>  と同じ文字列は作成されません。</span><span class="sxs-lookup"><span data-stu-id="12440-109">As a result, <xref:System.Object.ToString?displayProperty=nameWithType> conversion does not produce the same string as <xref:System.Convert.ToString%2A?displayProperty=nameWithType> in the .NET Framework.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12440-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="12440-110">See Also</span></span>  
 [<span data-ttu-id="12440-111">データ型と関数</span><span class="sxs-lookup"><span data-stu-id="12440-111">Data Types and Functions</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/data-types-and-functions.md)
