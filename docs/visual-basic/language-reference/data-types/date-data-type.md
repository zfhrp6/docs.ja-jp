---
title: 日付型 (Date) (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Date
helpviewer_keywords:
- Date data type
- dates [Visual Basic], Visual Basic data types
- times [Visual Basic], Date data type
- Date literals [Visual Basic]
- data values [Visual Basic]
- times [Visual Basic], Visual Basic data types
- dates [Visual Basic], Date data type
- data types [Visual Basic], assigning
- literals [Visual Basic], Date
- '# specifier for Date literals'
ms.assetid: d9edf5b0-e85e-438b-a1cf-1f321e7c831b
caps.latest.revision: 22
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 190b40888dc4a42075b7b6b27bdb1bd403a7efb5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="date-data-type-visual-basic"></a><span data-ttu-id="62dd6-102">日付型 (Date) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="62dd6-102">Date Data Type (Visual Basic)</span></span>
<span data-ttu-id="62dd6-103">IEEE 64 ビット (8 バイト) の値として格納され、西暦 0001 年 1 月 1 日から西暦 9999 年 12 月 31 日までの日付と、午前 12:00:00 (深夜) から午後 11:59:59.9999999 までの時刻を表します。</span><span class="sxs-lookup"><span data-stu-id="62dd6-103">Holds IEEE 64-bit (8-byte) values that represent dates ranging from January 1 of the year 0001 through December 31 of the year 9999, and times from 12:00:00 AM (midnight) through 11:59:59.9999999 PM.</span></span> <span data-ttu-id="62dd6-104">各インクリメントはグレゴリオ暦の西暦 1 年 1 月 1 日からの経過時間を 100 ナノ秒で表します。</span><span class="sxs-lookup"><span data-stu-id="62dd6-104">Each increment represents 100 nanoseconds of elapsed time since the beginning of January 1 of the year 1 in the Gregorian calendar.</span></span> <span data-ttu-id="62dd6-105">最大値は、西暦 10000 年 1 月 1 日の 100 ナノ秒前です。</span><span class="sxs-lookup"><span data-stu-id="62dd6-105">The maximum value represents 100 nanoseconds before the beginning of January 1 of the year 10000.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="62dd6-106">コメント</span><span class="sxs-lookup"><span data-stu-id="62dd6-106">Remarks</span></span>  
 <span data-ttu-id="62dd6-107">`Date` データ型は、日付、時刻、またはその両方の値を格納するのに使用します。</span><span class="sxs-lookup"><span data-stu-id="62dd6-107">Use the `Date` data type to contain date values, time values, or date and time values.</span></span>  
  
 <span data-ttu-id="62dd6-108">`Date` の既定値は 0001 年 1 月 1 日の 0:00:00 (深夜) です。</span><span class="sxs-lookup"><span data-stu-id="62dd6-108">The default value of `Date` is 0:00:00 (midnight) on January 1, 0001.</span></span>  
  
 <span data-ttu-id="62dd6-109"><xref:Microsoft.VisualBasic.DateAndTime> クラスから現在の日付および時刻を取得できます。</span><span class="sxs-lookup"><span data-stu-id="62dd6-109">You can get the current date and time from the <xref:Microsoft.VisualBasic.DateAndTime> class.</span></span>  
  
## <a name="format-requirements"></a><span data-ttu-id="62dd6-110">書式の要件</span><span class="sxs-lookup"><span data-stu-id="62dd6-110">Format Requirements</span></span>  
 <span data-ttu-id="62dd6-111">`Date` リテラルは、シャープ記号 (`# #`) で囲む必要があります。</span><span class="sxs-lookup"><span data-stu-id="62dd6-111">You must enclose a `Date` literal within number signs (`# #`).</span></span> <span data-ttu-id="62dd6-112">日付の値は、`#5/31/1993#` のように M/d/yyyy の形式で、または `#1993-5-31#` のように yyyy-MM-dd の形式で指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="62dd6-112">You must specify the date value in the format M/d/yyyy, for example `#5/31/1993#`, or yyyy-MM-dd, for example `#1993-5-31#`.</span></span> <span data-ttu-id="62dd6-113">最初に年を指定する場合は、スラッシュを使用できます。</span><span class="sxs-lookup"><span data-stu-id="62dd6-113">You can use slashes when specifying the year first.</span></span>  <span data-ttu-id="62dd6-114">この要件は、ロケールやコンピューターの日付と時刻の設定とは無関係です。</span><span class="sxs-lookup"><span data-stu-id="62dd6-114">This requirement is independent of your locale and your computer's date and time format settings.</span></span>  
  
 <span data-ttu-id="62dd6-115">この制限は、アプリケーションが実行されているロケールによってコードの意味が変わらないようにするために設けられています。</span><span class="sxs-lookup"><span data-stu-id="62dd6-115">The reason for this restriction is that the meaning of your code should never change depending on the locale in which your application is running.</span></span> <span data-ttu-id="62dd6-116">たとえば、`#3/4/1998#` という `Date` リテラルをハード コーディングし、これを 1998 年 3 月 4 日の意味で使用する場合を考えます。</span><span class="sxs-lookup"><span data-stu-id="62dd6-116">Suppose you hard-code a `Date` literal of `#3/4/1998#` and intend it to mean March 4, 1998.</span></span> <span data-ttu-id="62dd6-117">mm/dd/yyyy という形式を使用するロケールでは、3/4/1998 が意図したとおりにコンパイルされます。</span><span class="sxs-lookup"><span data-stu-id="62dd6-117">In a locale that uses mm/dd/yyyy, 3/4/1998 compiles as you intend.</span></span> <span data-ttu-id="62dd6-118">しかし、このアプリケーションを多くの国で展開する場合を考えてみましょう。</span><span class="sxs-lookup"><span data-stu-id="62dd6-118">But suppose you deploy your application in many countries.</span></span> <span data-ttu-id="62dd6-119">dd/mm/yyyy という形式を使用するロケールでは、ハード コーディングされたリテラルが 1998 年 4 月 3 日としてコンパイルされます。</span><span class="sxs-lookup"><span data-stu-id="62dd6-119">In a locale that uses dd/mm/yyyy, your hard-coded literal would compile to April 3, 1998.</span></span> <span data-ttu-id="62dd6-120">yyyy/mm/dd という形式を使用するロケールでは、このリテラルは無効な値 (0003 年 4 月 1998 日) となり、コンパイラ エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="62dd6-120">In a locale that uses yyyy/mm/dd, the literal would be invalid (April 1998, 0003) and cause a compiler error.</span></span>  
  
## <a name="workarounds"></a><span data-ttu-id="62dd6-121">問題回避</span><span class="sxs-lookup"><span data-stu-id="62dd6-121">Workarounds</span></span>  
 <span data-ttu-id="62dd6-122">`Date` リテラルを、使用されるロケールの形式やカスタム形式に変換するには、リテラルを <xref:Microsoft.VisualBasic.Strings.Format%2A> 関数に渡し、定義済みの日付形式またはユーザー定義の日付形式を指定します。</span><span class="sxs-lookup"><span data-stu-id="62dd6-122">To convert a `Date` literal to the format of your locale, or to a custom format, supply the literal to the <xref:Microsoft.VisualBasic.Strings.Format%2A> function, specifying either a predefined or user-defined date format.</span></span> <span data-ttu-id="62dd6-123">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="62dd6-123">The following example demonstrates this.</span></span>  
  
```  
MsgBox("The formatted date is " & Format(#5/31/1993#, "dddd, d MMM yyyy"))  
```  
  
 <span data-ttu-id="62dd6-124">または、<xref:System.DateTime> 構造体のいずれかのオーバーロードされたコンストラクターを使用して、日付と時刻の値をアセンブルします。</span><span class="sxs-lookup"><span data-stu-id="62dd6-124">Alternatively, you can use one of the overloaded constructors of the <xref:System.DateTime> structure to assemble a date and time value.</span></span> <span data-ttu-id="62dd6-125">次の例では、1993 年 5 月 31 日午後 12 時 14 分を表す値を作成します。</span><span class="sxs-lookup"><span data-stu-id="62dd6-125">The following example creates a value to represent May 31, 1993 at 12:14 in the afternoon.</span></span>  
  
```  
Dim dateInMay As New System.DateTime(1993, 5, 31, 12, 14, 0)  
```  
  
## <a name="hour-format"></a><span data-ttu-id="62dd6-126">時刻の形式</span><span class="sxs-lookup"><span data-stu-id="62dd6-126">Hour Format</span></span>  
 <span data-ttu-id="62dd6-127">時刻の値は 12 時間制または 24 時間制で指定できます。たとえば、`#1:15:30 PM#` または `#13:15:30#` のようになります。</span><span class="sxs-lookup"><span data-stu-id="62dd6-127">You can specify the time value in either 12-hour or 24-hour format, for example `#1:15:30 PM#` or `#13:15:30#`.</span></span> <span data-ttu-id="62dd6-128">ただし、分または秒を指定しない場合は、AM または PM を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="62dd6-128">However, if you do not specify either the minutes or the seconds, you must specify AM or PM.</span></span>  
  
## <a name="date-and-time-defaults"></a><span data-ttu-id="62dd6-129">日付と時刻の既定値</span><span class="sxs-lookup"><span data-stu-id="62dd6-129">Date and Time Defaults</span></span>  
 <span data-ttu-id="62dd6-130">日時のリテラルに日付が含まれない場合は、Visual Basic によって日付の部分の値が 0001 年 1 月 1 日に設定されます。</span><span class="sxs-lookup"><span data-stu-id="62dd6-130">If you do not include a date in a date/time literal, Visual Basic sets the date part of the value to January 1, 0001.</span></span> <span data-ttu-id="62dd6-131">日時のリテラルに時刻が含まれない場合は、時刻の部分の値が一日の始まり、つまり深夜 0 時 (0:00:00) に設定されます。</span><span class="sxs-lookup"><span data-stu-id="62dd6-131">If you do not include a time in a date/time literal, Visual Basic sets the time part of the value to the start of the day, that is, midnight (0:00:00).</span></span>  
  
## <a name="type-conversions"></a><span data-ttu-id="62dd6-132">型変換</span><span class="sxs-lookup"><span data-stu-id="62dd6-132">Type Conversions</span></span>  
 <span data-ttu-id="62dd6-133">`Date` の値を `String` 型に変換する場合、日付は実行時ロケールで指定された短い日付形式で表示され、時間は実行時ロケールで指定された時刻形式 (12 時間制または 24 時間制) で表示されます。</span><span class="sxs-lookup"><span data-stu-id="62dd6-133">If you convert a `Date` value to the `String` type, Visual Basic renders the date according to the short date format specified by the run-time locale, and it renders the time according to the time format (either 12-hour or 24-hour) specified by the run-time locale.</span></span>  
  
## <a name="programming-tips"></a><span data-ttu-id="62dd6-134">プログラミングのヒント</span><span class="sxs-lookup"><span data-stu-id="62dd6-134">Programming Tips</span></span>  
  
-   <span data-ttu-id="62dd6-135">**相互運用の考慮事項。**</span><span class="sxs-lookup"><span data-stu-id="62dd6-135">**Interop Considerations.**</span></span> <span data-ttu-id="62dd6-136">オートメーションまたは COM オブジェクトのように、.NET Framework 向けに作成されていないコンポーネントとやり取りする場合、他の環境の日付/時刻の型は Visual Basic の `Date` 型と互換性がないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="62dd6-136">If you are interfacing with components not written for the .NET Framework, for example Automation or COM objects, keep in mind that date/time types in other environments are not compatible with the Visual Basic `Date` type.</span></span> <span data-ttu-id="62dd6-137">そのようなコンポーネントに日付/時刻の引数を渡す場合は、新しい Visual Basic のコードで、`Date` 型ではなく `Double` 型として宣言し、<xref:System.DateTime.FromOADate%2A?displayProperty=nameWithType> および <xref:System.DateTime.ToOADate%2A?displayProperty=nameWithType> の変換メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="62dd6-137">If you are passing a date/time argument to such a component, declare it as `Double` instead of `Date` in your new Visual Basic code, and use the conversion methods <xref:System.DateTime.FromOADate%2A?displayProperty=nameWithType> and <xref:System.DateTime.ToOADate%2A?displayProperty=nameWithType>.</span></span>  
  
-   <span data-ttu-id="62dd6-138">**型宣言文字。**</span><span class="sxs-lookup"><span data-stu-id="62dd6-138">**Type Characters.**</span></span> <span data-ttu-id="62dd6-139">`Date`リテラルの型文字または識別子の型文字がありません。</span><span class="sxs-lookup"><span data-stu-id="62dd6-139">`Date` has no literal type character or identifier type character.</span></span> <span data-ttu-id="62dd6-140">ただし、コンパイラでは、シャープ記号 (`# #`) で囲まれたリテラルは、日付型 (`Date`) として処理されます。</span><span class="sxs-lookup"><span data-stu-id="62dd6-140">However, the compiler treats literals enclosed within number signs (`# #`) as `Date`.</span></span>  
  
-   <span data-ttu-id="62dd6-141">**Framework の型。**</span><span class="sxs-lookup"><span data-stu-id="62dd6-141">**Framework Type.**</span></span> <span data-ttu-id="62dd6-142">.NET Framework において対応する型は、<xref:System.DateTime?displayProperty=nameWithType> 構造体です。</span><span class="sxs-lookup"><span data-stu-id="62dd6-142">The corresponding type in the .NET Framework is the <xref:System.DateTime?displayProperty=nameWithType> structure.</span></span>  
  
## <a name="example"></a><span data-ttu-id="62dd6-143">例</span><span class="sxs-lookup"><span data-stu-id="62dd6-143">Example</span></span>  
 <span data-ttu-id="62dd6-144">`Date` データ型の変数または定数は、日付と時刻の両方を格納します。</span><span class="sxs-lookup"><span data-stu-id="62dd6-144">A variable or constant of the `Date` data type holds both the date and the time.</span></span> <span data-ttu-id="62dd6-145">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="62dd6-145">The following example illustrates this.</span></span>  
  
```  
Dim someDateAndTime As Date = #8/13/2002 12:14 PM#  
```  
  
## <a name="see-also"></a><span data-ttu-id="62dd6-146">関連項目</span><span class="sxs-lookup"><span data-stu-id="62dd6-146">See Also</span></span>  
 <xref:System.DateTime?displayProperty=nameWithType>  
 [<span data-ttu-id="62dd6-147">データの種類</span><span class="sxs-lookup"><span data-stu-id="62dd6-147">Data Types</span></span>](../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [<span data-ttu-id="62dd6-148">標準の日時書式指定文字列</span><span class="sxs-lookup"><span data-stu-id="62dd6-148">Standard Date and Time Format Strings</span></span>](../../../standard/base-types/standard-date-and-time-format-strings.md)  
 [<span data-ttu-id="62dd6-149">カスタム日時書式指定文字列</span><span class="sxs-lookup"><span data-stu-id="62dd6-149">Custom Date and Time Format Strings</span></span>](../../../standard/base-types/custom-date-and-time-format-strings.md)  
 [<span data-ttu-id="62dd6-150">データ型変換関数</span><span class="sxs-lookup"><span data-stu-id="62dd6-150">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [<span data-ttu-id="62dd6-151">変換の概要</span><span class="sxs-lookup"><span data-stu-id="62dd6-151">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [<span data-ttu-id="62dd6-152">データ型の有効な使用方法</span><span class="sxs-lookup"><span data-stu-id="62dd6-152">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
