---
title: CStr 関数の戻り値 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- times [Visual Basic], CStr Function return values
- type conversion [Visual Basic]
- dates [Visual Basic], CStr Function return values
- CStr function
- strings [Visual Basic], return value
- Date data type [Visual Basic], converting
- dates [Visual Basic]
- String data type [Visual Basic], converting
ms.assetid: 3aa744e7-1419-45d5-85e3-e5abc2953673
ms.openlocfilehash: 5312734633eea12aacd7e61afba616d31e06cd71
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33598525"
---
# <a name="return-values-for-the-cstr-function-visual-basic"></a><span data-ttu-id="93bee-102">CStr 関数の戻り値 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="93bee-102">Return Values for the CStr Function (Visual Basic)</span></span>
<span data-ttu-id="93bee-103">次の表に、値を返します`CStr`の各データ型に対して`expression`です。</span><span class="sxs-lookup"><span data-stu-id="93bee-103">The following table describes the return values for `CStr` for different data types of `expression`.</span></span>  
  
|<span data-ttu-id="93bee-104">場合`expression`型</span><span class="sxs-lookup"><span data-stu-id="93bee-104">If `expression` type is</span></span>|<span data-ttu-id="93bee-105">`CStr` 戻り値</span><span class="sxs-lookup"><span data-stu-id="93bee-105">`CStr` returns</span></span>|  
|-----------------------------|--------------------|  
|[<span data-ttu-id="93bee-106">Boolean データ型</span><span class="sxs-lookup"><span data-stu-id="93bee-106">Boolean Data Type</span></span>](../../../visual-basic/language-reference/data-types/boolean-data-type.md)|<span data-ttu-id="93bee-107">"True"を含む文字列または"False"です。</span><span class="sxs-lookup"><span data-stu-id="93bee-107">A string containing "True" or "False".</span></span>|  
|[<span data-ttu-id="93bee-108">Date データ型</span><span class="sxs-lookup"><span data-stu-id="93bee-108">Date Data Type</span></span>](../../../visual-basic/language-reference/data-types/date-data-type.md)|<span data-ttu-id="93bee-109">含む文字列、`Date`システムの短い日付形式での値 (日付と時刻)。</span><span class="sxs-lookup"><span data-stu-id="93bee-109">A string containing a `Date` value (date and time) in the short date format of your system.</span></span>|  
|[<span data-ttu-id="93bee-110">数値のデータ型</span><span class="sxs-lookup"><span data-stu-id="93bee-110">Numeric Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/numeric-data-types.md)|<span data-ttu-id="93bee-111">数を表す文字列。</span><span class="sxs-lookup"><span data-stu-id="93bee-111">A string representing the number.</span></span>|  
  
## <a name="cstr-and-date"></a><span data-ttu-id="93bee-112">CStr と日付</span><span class="sxs-lookup"><span data-stu-id="93bee-112">CStr and Date</span></span>  
 <span data-ttu-id="93bee-113">`Date`型には常に日付と時刻の両方の情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="93bee-113">The `Date` type always contains both date and time information.</span></span> <span data-ttu-id="93bee-114">型変換のため、Visual Basic 1/1/0001 (1 年 1 月、1) であると見なす、*ニュートラル値*日付、および 00時 00分: 00 (午前 0 時) に依存しない値であることにします。</span><span class="sxs-lookup"><span data-stu-id="93bee-114">For purposes of type conversion, Visual Basic considers 1/1/0001 (January 1 of the year 1) to be a *neutral value* for the date, and 00:00:00 (midnight) to be a neutral value for the time.</span></span> <span data-ttu-id="93bee-115">`CStr` 結果の文字列に中立的な値は含まれません。</span><span class="sxs-lookup"><span data-stu-id="93bee-115">`CStr` does not include neutral values in the resulting string.</span></span> <span data-ttu-id="93bee-116">変換する場合など、`#January 1, 0001 9:30:00#`文字列に、結果は"9時 30分: 00 AM"以外の場合は、日付情報は表示されません。</span><span class="sxs-lookup"><span data-stu-id="93bee-116">For example, if you convert `#January 1, 0001 9:30:00#` to a string, the result is "9:30:00 AM"; the date information is suppressed.</span></span> <span data-ttu-id="93bee-117">ただし、日付情報は、元にまだ存在している`Date`値し、などの関数で回復できる<xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A>です。</span><span class="sxs-lookup"><span data-stu-id="93bee-117">However, the date information is still present in the original `Date` value and can be recovered with functions such as <xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="93bee-118">`CStr`関数は、アプリケーションの現在のカルチャ設定に基づいて、変換を実行します。</span><span class="sxs-lookup"><span data-stu-id="93bee-118">The `CStr` function performs its conversion based on the current culture settings for the application.</span></span> <span data-ttu-id="93bee-119">特定のカルチャの数値の文字列形式を取得するには、数値を使用`ToString(IFormatProvider)`メソッドです。</span><span class="sxs-lookup"><span data-stu-id="93bee-119">To get the string representation of a number in a particular culture, use the number's `ToString(IFormatProvider)` method.</span></span> <span data-ttu-id="93bee-120">たとえば、使用して<xref:System.Double.ToString%2A?displayProperty=nameWithType>型の値を変換するときに`Double`を`String`です。</span><span class="sxs-lookup"><span data-stu-id="93bee-120">For example, use <xref:System.Double.ToString%2A?displayProperty=nameWithType> when converting a value of type `Double` to a `String`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93bee-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="93bee-121">See Also</span></span>  
 <xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A>  
 [<span data-ttu-id="93bee-122">データ型変換関数</span><span class="sxs-lookup"><span data-stu-id="93bee-122">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [<span data-ttu-id="93bee-123">Boolean データ型</span><span class="sxs-lookup"><span data-stu-id="93bee-123">Boolean Data Type</span></span>](../../../visual-basic/language-reference/data-types/boolean-data-type.md)  
 [<span data-ttu-id="93bee-124">Date データ型</span><span class="sxs-lookup"><span data-stu-id="93bee-124">Date Data Type</span></span>](../../../visual-basic/language-reference/data-types/date-data-type.md)
