---
title: "数値結果テーブルの書式設定 (C# リファレンス)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- formatting [C#]
- numeric formatting [C#]
- String.Format method
- Console.Write method
ms.assetid: 120ba537-4448-4c62-8676-7a8fdd98f496
caps.latest.revision: 14
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 16976f5a59bd4eb0eca29553aff87d4fe0b1d247
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="formatting-numeric-results-table-c-reference"></a><span data-ttu-id="6b9e4-102">数値結果テーブルの書式設定 (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="6b9e4-102">Formatting Numeric Results Table (C# Reference)</span></span>
<span data-ttu-id="6b9e4-103">数値結果の書式を指定するには、<xref:System.String.Format%2A?displayProperty=fullName> メソッドを使用するか、`String.Format` を呼び出す <xref:System.Console.Write%2A?displayProperty=fullName> メソッドまたは <xref:System.Console.WriteLine%2A?displayProperty=fullName> メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="6b9e4-103">You can format numeric results by using the <xref:System.String.Format%2A?displayProperty=fullName> method, or through the <xref:System.Console.Write%2A?displayProperty=fullName> or <xref:System.Console.WriteLine%2A?displayProperty=fullName> method, which calls `String.Format`.</span></span> <span data-ttu-id="6b9e4-104">書式を指定するには、書式指定文字列を使用します。</span><span class="sxs-lookup"><span data-stu-id="6b9e4-104">The format is specified by using format strings.</span></span> <span data-ttu-id="6b9e4-105">サポートされる標準の書式指定文字列を次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="6b9e4-105">The following table contains the supported standard format strings.</span></span> <span data-ttu-id="6b9e4-106">書式指定文字列は `Axx` という形式になります。この `A` は書式指定子、`xx` は精度指定子です。</span><span class="sxs-lookup"><span data-stu-id="6b9e4-106">The format string takes the following form: `Axx`, where `A` is the format specifier and `xx` is the precision specifier.</span></span> <span data-ttu-id="6b9e4-107">書式指定子は、数値に適用する書式の種類を制御し、精度指定子は、書式付き出力の有効桁数または小数点以下の桁数を制御します。</span><span class="sxs-lookup"><span data-stu-id="6b9e4-107">The format specifier controls the type of formatting applied to the numeric value, and the precision specifier controls the number of significant digits or decimal places of the formatted output.</span></span> <span data-ttu-id="6b9e4-108">精度指定子の値は 0 から 99 の範囲です。</span><span class="sxs-lookup"><span data-stu-id="6b9e4-108">The value of the precision specifier ranges from 0 to 99.</span></span>  
  
 <span data-ttu-id="6b9e4-109">標準およびカスタム書式指定文字列の詳細については、「[Formatting Types](../../../standard/base-types/formatting-types.md)」(型の書式設定) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6b9e4-109">For more information about standard and custom formatting strings, see [Formatting Types](../../../standard/base-types/formatting-types.md).</span></span> <span data-ttu-id="6b9e4-110">`String.Format` メソッドの詳細については、<xref:System.String.Format%2A?displayProperty=fullName> を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6b9e4-110">For more information about the `String.Format` method, see <xref:System.String.Format%2A?displayProperty=fullName>.</span></span>  
  
|<span data-ttu-id="6b9e4-111">書式指定子</span><span class="sxs-lookup"><span data-stu-id="6b9e4-111">Format Specifier</span></span>|<span data-ttu-id="6b9e4-112">説明</span><span class="sxs-lookup"><span data-stu-id="6b9e4-112">Description</span></span>|<span data-ttu-id="6b9e4-113">例</span><span class="sxs-lookup"><span data-stu-id="6b9e4-113">Examples</span></span>|<span data-ttu-id="6b9e4-114">出力</span><span class="sxs-lookup"><span data-stu-id="6b9e4-114">Output</span></span>|  
|----------------------|-----------------|--------------|------------|  
|<span data-ttu-id="6b9e4-115">C または c</span><span class="sxs-lookup"><span data-stu-id="6b9e4-115">C or c</span></span>|<span data-ttu-id="6b9e4-116">通貨</span><span class="sxs-lookup"><span data-stu-id="6b9e4-116">Currency</span></span>|<span data-ttu-id="6b9e4-117">Console.Write("{0:C}", 2.5);</span><span class="sxs-lookup"><span data-stu-id="6b9e4-117">Console.Write("{0:C}", 2.5);</span></span><br /><br /> <span data-ttu-id="6b9e4-118">Console.Write("{0:C}", -2.5);</span><span class="sxs-lookup"><span data-stu-id="6b9e4-118">Console.Write("{0:C}", -2.5);</span></span>|<span data-ttu-id="6b9e4-119">$2.50</span><span class="sxs-lookup"><span data-stu-id="6b9e4-119">$2.50</span></span><br /><br /> <span data-ttu-id="6b9e4-120">($2.50)</span><span class="sxs-lookup"><span data-stu-id="6b9e4-120">($2.50)</span></span>|  
|<span data-ttu-id="6b9e4-121">D または d</span><span class="sxs-lookup"><span data-stu-id="6b9e4-121">D or d</span></span>|<span data-ttu-id="6b9e4-122">Decimal (10 進数型)</span><span class="sxs-lookup"><span data-stu-id="6b9e4-122">Decimal</span></span>|<span data-ttu-id="6b9e4-123">Console.Write("{0:D5}", 25);</span><span class="sxs-lookup"><span data-stu-id="6b9e4-123">Console.Write("{0:D5}", 25);</span></span>|<span data-ttu-id="6b9e4-124">00025</span><span class="sxs-lookup"><span data-stu-id="6b9e4-124">00025</span></span>|  
|<span data-ttu-id="6b9e4-125">E または e</span><span class="sxs-lookup"><span data-stu-id="6b9e4-125">E or e</span></span>|<span data-ttu-id="6b9e4-126">指数</span><span class="sxs-lookup"><span data-stu-id="6b9e4-126">Scientific</span></span>|<span data-ttu-id="6b9e4-127">Console.Write("{0:E}", 250000);</span><span class="sxs-lookup"><span data-stu-id="6b9e4-127">Console.Write("{0:E}", 250000);</span></span>|<span data-ttu-id="6b9e4-128">2.500000E+005</span><span class="sxs-lookup"><span data-stu-id="6b9e4-128">2.500000E+005</span></span>|  
|<span data-ttu-id="6b9e4-129">F または f</span><span class="sxs-lookup"><span data-stu-id="6b9e4-129">F or f</span></span>|<span data-ttu-id="6b9e4-130">固定小数点</span><span class="sxs-lookup"><span data-stu-id="6b9e4-130">Fixed-point</span></span>|<span data-ttu-id="6b9e4-131">Console.Write("{0:F2}", 25);</span><span class="sxs-lookup"><span data-stu-id="6b9e4-131">Console.Write("{0:F2}", 25);</span></span><br /><br /> <span data-ttu-id="6b9e4-132">Console.Write("{0:F0}", 25);</span><span class="sxs-lookup"><span data-stu-id="6b9e4-132">Console.Write("{0:F0}", 25);</span></span>|<span data-ttu-id="6b9e4-133">25.00</span><span class="sxs-lookup"><span data-stu-id="6b9e4-133">25.00</span></span><br /><br /> <span data-ttu-id="6b9e4-134">25</span><span class="sxs-lookup"><span data-stu-id="6b9e4-134">25</span></span>|  
|<span data-ttu-id="6b9e4-135">G または g</span><span class="sxs-lookup"><span data-stu-id="6b9e4-135">G or g</span></span>|<span data-ttu-id="6b9e4-136">全般</span><span class="sxs-lookup"><span data-stu-id="6b9e4-136">General</span></span>|<span data-ttu-id="6b9e4-137">Console.Write("{0:G}", 2.5);</span><span class="sxs-lookup"><span data-stu-id="6b9e4-137">Console.Write("{0:G}", 2.5);</span></span>|<span data-ttu-id="6b9e4-138">2.5</span><span class="sxs-lookup"><span data-stu-id="6b9e4-138">2.5</span></span>|  
|<span data-ttu-id="6b9e4-139">N または n</span><span class="sxs-lookup"><span data-stu-id="6b9e4-139">N or n</span></span>|<span data-ttu-id="6b9e4-140">数値</span><span class="sxs-lookup"><span data-stu-id="6b9e4-140">Number</span></span>|<span data-ttu-id="6b9e4-141">Console.Write("{0:N}", 2500000);</span><span class="sxs-lookup"><span data-stu-id="6b9e4-141">Console.Write("{0:N}", 2500000);</span></span>|<span data-ttu-id="6b9e4-142">2,500,000.00</span><span class="sxs-lookup"><span data-stu-id="6b9e4-142">2,500,000.00</span></span>|  
|<span data-ttu-id="6b9e4-143">X または x</span><span class="sxs-lookup"><span data-stu-id="6b9e4-143">X or x</span></span>|<span data-ttu-id="6b9e4-144">16 進数</span><span class="sxs-lookup"><span data-stu-id="6b9e4-144">Hexadecimal</span></span>|<span data-ttu-id="6b9e4-145">Console.Write("{0:X}", 250);</span><span class="sxs-lookup"><span data-stu-id="6b9e4-145">Console.Write("{0:X}", 250);</span></span><br /><br /> <span data-ttu-id="6b9e4-146">Console.Write("{0:X}", 0xffff);</span><span class="sxs-lookup"><span data-stu-id="6b9e4-146">Console.Write("{0:X}", 0xffff);</span></span>|<span data-ttu-id="6b9e4-147">FA</span><span class="sxs-lookup"><span data-stu-id="6b9e4-147">FA</span></span><br /><br /> <span data-ttu-id="6b9e4-148">FFFF</span><span class="sxs-lookup"><span data-stu-id="6b9e4-148">FFFF</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6b9e4-149">関連項目</span><span class="sxs-lookup"><span data-stu-id="6b9e4-149">See Also</span></span>  
 <span data-ttu-id="6b9e4-150">[C# リファレンス](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="6b9e4-150">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="6b9e4-151">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="6b9e4-151">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="6b9e4-152">[標準の数値書式指定文字列](../../../standard/base-types/standard-numeric-format-strings.md) </span><span class="sxs-lookup"><span data-stu-id="6b9e4-152">[Standard Numeric Format Strings](../../../standard/base-types/standard-numeric-format-strings.md) </span></span>  
 <span data-ttu-id="6b9e4-153">[型のリファレンス表](../../../csharp/language-reference/keywords/reference-tables-for-types.md) </span><span class="sxs-lookup"><span data-stu-id="6b9e4-153">[Reference Tables for Types](../../../csharp/language-reference/keywords/reference-tables-for-types.md) </span></span>  
 [<span data-ttu-id="6b9e4-154">string</span><span class="sxs-lookup"><span data-stu-id="6b9e4-154">string</span></span>](../../../csharp/language-reference/keywords/string.md)

