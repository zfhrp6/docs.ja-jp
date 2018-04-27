---
title: 浮動小数点数
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-ado
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 73c218c6-1c44-4402-a167-4f6262629a91
caps.latest.revision: 3
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload:
- dotnet
ms.openlocfilehash: 08062e7c41a6173093db577bb52ea4fa3c7e0746
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="floating-point-numbers"></a><span data-ttu-id="932a1-102">浮動小数点数</span><span class="sxs-lookup"><span data-stu-id="932a1-102">Floating-Point Numbers</span></span>
<span data-ttu-id="932a1-103">このトピックでは、開発者が [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] で浮動小数点数を扱う際によく遭遇する問題について説明します。</span><span class="sxs-lookup"><span data-stu-id="932a1-103">This topic describes some of the issues that developers frequently encounter when they work with floating-point numbers in [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)].</span></span> <span data-ttu-id="932a1-104">これらはコンピューターによる浮動小数点数の格納方法に起因する問題であり、<xref:System.Data.SqlClient> や <xref:System.Data.OracleClient> など、特定のプロバイダーに固有の問題ではありません。</span><span class="sxs-lookup"><span data-stu-id="932a1-104">These issues are caused by the way that computers store floating-point numbers, and are not specific to a particular provider such as <xref:System.Data.SqlClient> or <xref:System.Data.OracleClient>.</span></span>  
  
 <span data-ttu-id="932a1-105">通常、浮動小数点数には正確なバイナリ表現がありません。</span><span class="sxs-lookup"><span data-stu-id="932a1-105">Floating-point numbers generally do not have an exact binary representation.</span></span> <span data-ttu-id="932a1-106">その代わり、数値の近似値がコンピューターによって格納されます。</span><span class="sxs-lookup"><span data-stu-id="932a1-106">Instead, the computer stores an approximation of the number.</span></span> <span data-ttu-id="932a1-107">浮動小数点数を表現するために使用されるバイナリ桁数はそのときどきで異なります。</span><span class="sxs-lookup"><span data-stu-id="932a1-107">At different times, different numbers of binary digits may be used to represent the number.</span></span> <span data-ttu-id="932a1-108">浮動小数点数をある表現から別の表現に変換した場合、その数値の最下位の桁がわずかに変わってしまう場合があります。</span><span class="sxs-lookup"><span data-stu-id="932a1-108">When a floating point number is converted from one representation to another representation, the least significant digits of that number may vary slightly.</span></span> <span data-ttu-id="932a1-109">一般に、変換が発生するのは型をキャストしたときです。</span><span class="sxs-lookup"><span data-stu-id="932a1-109">Conversion typically occurs when the number is cast from one type to another type.</span></span> <span data-ttu-id="932a1-110">この差異は、変換を 1 つのデータベース内で行うか、データベースの値を表す型間で行うか、型と型の間で行うかに関係なく生じます。</span><span class="sxs-lookup"><span data-stu-id="932a1-110">The variation occurs whether the conversion occurs within a database, between types that represent database values, or between types.</span></span> <span data-ttu-id="932a1-111">このような差が生じてしまう関係上、論理的には等しくなるはずの数値でも、最下位の桁の値が異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="932a1-111">Because of these changes, numbers that would logically be equal may have changes in their least-significant digits that cause them to have different values.</span></span> <span data-ttu-id="932a1-112">数値の有効桁数が、本来の桁数よりも大きくなったり小さくなったりすることもあります。</span><span class="sxs-lookup"><span data-stu-id="932a1-112">The number of digits of precision in the number may be larger or smaller than expected.</span></span> <span data-ttu-id="932a1-113">また、数値を文字列として表した場合に、期待した値が得られない場合もあります。</span><span class="sxs-lookup"><span data-stu-id="932a1-113">When formatted as a string, the number may not show the expected value.</span></span>  
  
 <span data-ttu-id="932a1-114">こうした影響を最小限に抑えるには、使用できる数値型のうち、最も近い型を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="932a1-114">To minimize these effects, you should use the closest match between numeric types that is available to you.</span></span> <span data-ttu-id="932a1-115">たとえば、SQL Server で作業している場合実際の型の TRANSACT-SQL 値を float 型の値に変換する場合の正確な数値では変更できます。</span><span class="sxs-lookup"><span data-stu-id="932a1-115">For example, if you are working with SQL Server, the exact numeric value may change if you convert a Transact-SQL value of real type to a value of float type.</span></span> <span data-ttu-id="932a1-116">同様に、[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] では、<xref:System.Single> を <xref:System.Double> に変換すると、予想外の結果になることがあります。</span><span class="sxs-lookup"><span data-stu-id="932a1-116">In the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], converting a <xref:System.Single> to a <xref:System.Double> may also produce unexpected results.</span></span> <span data-ttu-id="932a1-117">いずれの場合も、最善の方法は、アプリケーションのすべての値に同じ数値型を使用することです。</span><span class="sxs-lookup"><span data-stu-id="932a1-117">In both of these cases, a good strategy is to make all the values in the application use the same numeric type.</span></span> <span data-ttu-id="932a1-118">固定精度の decimal 型を使用したり、あらかじめ浮動小数点数を固定精度の decimal 型にキャストしておく方法もあります。</span><span class="sxs-lookup"><span data-stu-id="932a1-118">You can also use a fixed-precision decimal type, or cast floating-point numbers to a fixed-precision decimal type before you work with them.</span></span>  
  
 <span data-ttu-id="932a1-119">等価比較の問題を回避するには、最下位桁の差異を無視できるようにアプリケーションをコーディングすることを検討してください。</span><span class="sxs-lookup"><span data-stu-id="932a1-119">To work around problems with equality comparison, consider coding your application so that variations in the least significant digits are ignored.</span></span> <span data-ttu-id="932a1-120">たとえば、2 つの数値の等価性を比較するのではなく、一方の数値からもう一方の数値を減算するようにします。</span><span class="sxs-lookup"><span data-stu-id="932a1-120">For example, instead of comparing to see whether two numbers are equal, subtract one number from the other number.</span></span> <span data-ttu-id="932a1-121">その差が丸め処理の許容範囲内であれば、2 つの数値が等価であるものとして処理できます。</span><span class="sxs-lookup"><span data-stu-id="932a1-121">If the difference is within an acceptable margin of rounding, your application can treat the numbers as if they are the same.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="932a1-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="932a1-122">See Also</span></span>  
 [<span data-ttu-id="932a1-123">浮動小数点数の精度の低下</span><span class="sxs-lookup"><span data-stu-id="932a1-123">Why Floating-Point Numbers May Lose Precision</span></span>](http://msdn.microsoft.com/library/1acb1add-ac06-4134-a2fd-aff13d8c4c15)  
 [<span data-ttu-id="932a1-124">ADO.NET のマネージ プロバイダーと DataSet デベロッパー センター</span><span class="sxs-lookup"><span data-stu-id="932a1-124">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
