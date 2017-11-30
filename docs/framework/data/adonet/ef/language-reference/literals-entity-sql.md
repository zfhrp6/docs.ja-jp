---
title: "リテラル (Entity SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 092ef693-6e5f-41b4-b868-5b9e82928abf
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 50edfb344177dbec8cff9609aeab56d1db762eb7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="literals-entity-sql"></a><span data-ttu-id="6dfcb-102">リテラル (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="6dfcb-102">Literals (Entity SQL)</span></span>
<span data-ttu-id="6dfcb-103">このトピックでは、リテラルに関する [!INCLUDE[esql](../../../../../../includes/esql-md.md)] のサポートについて説明します。</span><span class="sxs-lookup"><span data-stu-id="6dfcb-103">This topic describes [!INCLUDE[esql](../../../../../../includes/esql-md.md)] support for literals.</span></span>  
  
## <a name="null"></a><span data-ttu-id="6dfcb-104">Null</span><span class="sxs-lookup"><span data-stu-id="6dfcb-104">Null</span></span>  
 <span data-ttu-id="6dfcb-105">NULL リテラルは、あらゆる型で NULL 値を表す際に使用されます。</span><span class="sxs-lookup"><span data-stu-id="6dfcb-105">The null literal is used to represent the value null for any type.</span></span> <span data-ttu-id="6dfcb-106">NULL リテラルは、すべての型と互換性があります。</span><span class="sxs-lookup"><span data-stu-id="6dfcb-106">A null literal is compatible with any type.</span></span>  
  
 <span data-ttu-id="6dfcb-107">NULL リテラルをキャストすることによって、型指定された NULL を作成できます。</span><span class="sxs-lookup"><span data-stu-id="6dfcb-107">Typed nulls can be created by a cast over a null literal.</span></span> <span data-ttu-id="6dfcb-108">詳細については、次を参照してください。[キャスト](../../../../../../docs/framework/data/adonet/ef/language-reference/cast-entity-sql.md)です。</span><span class="sxs-lookup"><span data-stu-id="6dfcb-108">For more information, see [CAST](../../../../../../docs/framework/data/adonet/ef/language-reference/cast-entity-sql.md).</span></span>  
  
 <span data-ttu-id="6dfcb-109">場所に関する規則空き浮動 null リテラルは使用できるを参照してください[Null リテラルと型推論](../../../../../../docs/framework/data/adonet/ef/language-reference/null-literals-and-type-inference-entity-sql.md)です。</span><span class="sxs-lookup"><span data-stu-id="6dfcb-109">For rules about where free floating null literals can be used, see [Null Literals and Type Inference](../../../../../../docs/framework/data/adonet/ef/language-reference/null-literals-and-type-inference-entity-sql.md).</span></span>  
  
## <a name="boolean"></a><span data-ttu-id="6dfcb-110">ブール型</span><span class="sxs-lookup"><span data-stu-id="6dfcb-110">Boolean</span></span>  
 <span data-ttu-id="6dfcb-111">ブール型リテラルは、`true` と `false` のキーワードで表されます。</span><span class="sxs-lookup"><span data-stu-id="6dfcb-111">Boolean literals are represented by the keywords `true` and `false`.</span></span>  
  
## <a name="integer"></a><span data-ttu-id="6dfcb-112">整数</span><span class="sxs-lookup"><span data-stu-id="6dfcb-112">Integer</span></span>  
 <span data-ttu-id="6dfcb-113">整数リテラルには、<xref:System.Int32> 型と <xref:System.Int64> 型とがあります。</span><span class="sxs-lookup"><span data-stu-id="6dfcb-113">Integer literals can be of type <xref:System.Int32> or <xref:System.Int64>.</span></span> <span data-ttu-id="6dfcb-114"><xref:System.Int32> リテラルは、一連の数字で構成されます。</span><span class="sxs-lookup"><span data-stu-id="6dfcb-114">An <xref:System.Int32> literal is a series of numeric characters.</span></span> <span data-ttu-id="6dfcb-115"><xref:System.Int64> リテラルは、一連の数字で構成され、最後に大文字の L が付きます。</span><span class="sxs-lookup"><span data-stu-id="6dfcb-115">An <xref:System.Int64> literal is series of numeric characters followed by an uppercase L.</span></span>  
  
## <a name="decimal"></a><span data-ttu-id="6dfcb-116">Decimal (10 進数型)</span><span class="sxs-lookup"><span data-stu-id="6dfcb-116">Decimal</span></span>  
 <span data-ttu-id="6dfcb-117">固定小数点数 (decimal) は、一連の数字、ドット (.)、および別の一連の数字で構成され、最後に大文字の "M" が付きます。</span><span class="sxs-lookup"><span data-stu-id="6dfcb-117">A fixed-point number (decimal) is a series of numeric characters, a dot (.) and another series of numeric characters followed by an uppercase "M".</span></span>  
  
## <a name="float-double"></a><span data-ttu-id="6dfcb-118">Float、Double</span><span class="sxs-lookup"><span data-stu-id="6dfcb-118">Float, Double</span></span>  
 <span data-ttu-id="6dfcb-119">倍精度浮動小数点数は、一連の数字、ドット (.)、および別の一連の数字で構成され、場合によっては最後に指数が付きます。</span><span class="sxs-lookup"><span data-stu-id="6dfcb-119">A double-precision floating point number is a series of numeric characters, a dot (.) and another series of numeric characters possibly followed by an exponent.</span></span> <span data-ttu-id="6dfcb-120">単精度浮動小数点数 (float) は、倍精度浮動小数点数の構文に続けて小文字の f が付きます。</span><span class="sxs-lookup"><span data-stu-id="6dfcb-120">A single-precisions floating point number (or float) is a double-precision floating point number syntax followed by the lowercase f.</span></span>  
  
## <a name="string"></a><span data-ttu-id="6dfcb-121">String</span><span class="sxs-lookup"><span data-stu-id="6dfcb-121">String</span></span>  
 <span data-ttu-id="6dfcb-122">文字列は、引用符で囲まれた一連の文字です。</span><span class="sxs-lookup"><span data-stu-id="6dfcb-122">A string is a series of characters enclosed in quote marks.</span></span> <span data-ttu-id="6dfcb-123">引用符には、単一引用符 (`'`) または二重引用符 (") を使用できますが、両者を混在させることはできません。</span><span class="sxs-lookup"><span data-stu-id="6dfcb-123">Quotes can be either both single-quotes (`'`) or both double-quotes (").</span></span> <span data-ttu-id="6dfcb-124">文字列リテラルには、Unicode と非 Unicode のどちらでも使用できます。</span><span class="sxs-lookup"><span data-stu-id="6dfcb-124">Character string literals can be either Unicode or non-Unicode.</span></span> <span data-ttu-id="6dfcb-125">文字列リテラルを Unicode として宣言するには、リテラルの前に大文字の "N" を付けます。</span><span class="sxs-lookup"><span data-stu-id="6dfcb-125">To declare a character string literal as Unicode, prefix the literal with an uppercase "N".</span></span> <span data-ttu-id="6dfcb-126">既定では、Unicode でない文字列リテラルです。</span><span class="sxs-lookup"><span data-stu-id="6dfcb-126">The default is non-Unicode character string literals.</span></span> <span data-ttu-id="6dfcb-127">N と文字列リテラルの間に空白は含めません。また、N は大文字にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="6dfcb-127">There can be no spaces between the N and the string literal payload, and the N must be uppercase.</span></span>  
  
```  
'hello' -- non-Unicode character string literal  
N'hello' -- Unicode character string literal  
"x"  
N"This is a string!"  
'so is THIS'  
```  
  
## <a name="datetime"></a><span data-ttu-id="6dfcb-128">DateTime</span><span class="sxs-lookup"><span data-stu-id="6dfcb-128">DateTime</span></span>  
 <span data-ttu-id="6dfcb-129">datetime リテラルは、日付部分と時刻部分とで構成され、ロケールに依存しません。</span><span class="sxs-lookup"><span data-stu-id="6dfcb-129">A datetime literal is independent of locale and is composed of a date part and a time part.</span></span> <span data-ttu-id="6dfcb-130">日付部分と時刻部分のどちらも省略することはできず、既定値はありません。</span><span class="sxs-lookup"><span data-stu-id="6dfcb-130">Both date and time parts are mandatory and there are no default values.</span></span>  
  
 <span data-ttu-id="6dfcb-131">日付の部分は、形式をいる必要があります: `YYYY` - `MM` -`DD`ここで、 `YYYY` 0001 ~ 9999 の 4 桁の年の値は、`MM`は 1 ~ 12 の月と`DD`は有効では、指定された月の日の値`MM`です。</span><span class="sxs-lookup"><span data-stu-id="6dfcb-131">The date part must have the format: `YYYY`-`MM`-`DD`, where `YYYY` is a four digit year value between 0001 and 9999, `MM` is the month between 1 and 12 and `DD` is the day value that is valid for the given month `MM`.</span></span>  
  
 <span data-ttu-id="6dfcb-132">時刻部分は `HH`:`MM`[:`SS`[.fffffff]] の形式にする必要があります。ここで、`HH` は 0 ～ 23 時の値、`MM` は 0 ～ 59 分の値、`SS` は 0 ～ 59 秒の値、fffffff は 0 ～ 9999999 の 1 秒未満部分の値を表します。</span><span class="sxs-lookup"><span data-stu-id="6dfcb-132">The time part must have the format: `HH`:`MM`[:`SS`[.fffffff]], where `HH` is the hour value between 0 and 23, `MM` is the minute value between 0 and 59, `SS` is the second value between 0 and 59 and fffffff is the fractional second value between 0 and 9999999.</span></span> <span data-ttu-id="6dfcb-133">いずれも両端の値を含みます。</span><span class="sxs-lookup"><span data-stu-id="6dfcb-133">All value ranges are inclusive.</span></span> <span data-ttu-id="6dfcb-134">1 秒未満部分は省略可能です。</span><span class="sxs-lookup"><span data-stu-id="6dfcb-134">Fractional seconds are optional.</span></span> <span data-ttu-id="6dfcb-135">1 秒未満部分を指定しなければ、秒は省略可能です。1 秒未満部分を指定する場合、秒は必須です。</span><span class="sxs-lookup"><span data-stu-id="6dfcb-135">Seconds are optional unless fractional seconds are specified; in this case, seconds are required.</span></span> <span data-ttu-id="6dfcb-136">秒も 1 秒未満部分も指定しない場合は、既定値の 0 が使用されます。</span><span class="sxs-lookup"><span data-stu-id="6dfcb-136">When seconds or fractional seconds are not specified, the default value of zero will be used instead.</span></span>  
  
 <span data-ttu-id="6dfcb-137">DATETIME 記号とリテラル ペイロード間の空白の数に制限はありませんが、改行はできません。</span><span class="sxs-lookup"><span data-stu-id="6dfcb-137">There can be any number of spaces between the DATETIME symbol and the literal payload, but no new lines.</span></span>  
  
```  
DATETIME'2006-10-1 23:11'  
DATETIME'2006-12-25 01:01:00.0000000' -- same as DATETIME'2006-12-25 01:01'  
```  
  
## <a name="time"></a><span data-ttu-id="6dfcb-138">時刻</span><span class="sxs-lookup"><span data-stu-id="6dfcb-138">Time</span></span>  
 <span data-ttu-id="6dfcb-139">time リテラルは、時刻部分のみで構成され、ロケールに依存しません。</span><span class="sxs-lookup"><span data-stu-id="6dfcb-139">A time literal is independent of locale and composed of a time part only.</span></span> <span data-ttu-id="6dfcb-140">時刻部分は必須で、既定値はありません。</span><span class="sxs-lookup"><span data-stu-id="6dfcb-140">The time part is mandatory and there is no default value.</span></span> <span data-ttu-id="6dfcb-141">時刻部分は HH:MM[:SS[.fffffff]] の形式にする必要があります。ここで、HH は 0 ～ 23 時の値、MM は 0 ～ 59 分の値、SS は 0 ～ 59 秒の値、fffffff は 0 ～ 9999999 の 1 秒未満部分の値を表します。</span><span class="sxs-lookup"><span data-stu-id="6dfcb-141">It must have the format HH:MM[:SS[.fffffff]], where HH is the hour value between 0 and 23, MM is the minute value between 0 and 59, SS is the second value between 0 and 59, and fffffff is the second fraction value between 0 and 9999999.</span></span> <span data-ttu-id="6dfcb-142">いずれも両端の値を含みます。</span><span class="sxs-lookup"><span data-stu-id="6dfcb-142">All value ranges are inclusive.</span></span> <span data-ttu-id="6dfcb-143">1 秒未満部分は省略可能です。</span><span class="sxs-lookup"><span data-stu-id="6dfcb-143">Fractional seconds are optional.</span></span> <span data-ttu-id="6dfcb-144">1 秒未満部分を指定しなければ、秒は省略可能です。1 秒未満部分を指定する場合、秒は必須です。</span><span class="sxs-lookup"><span data-stu-id="6dfcb-144">Seconds are optional unless fractional seconds are specified; in this case, seconds are required.</span></span> <span data-ttu-id="6dfcb-145">秒も 1 秒未満部分も指定しない場合は、既定値の 0 が使用されます。</span><span class="sxs-lookup"><span data-stu-id="6dfcb-145">When seconds or fractions are not specified, the default value of zero will be used instead.</span></span>  
  
 <span data-ttu-id="6dfcb-146">TIME 記号とリテラル ペイロード間の空白の数に制限はありませんが、改行はできません。</span><span class="sxs-lookup"><span data-stu-id="6dfcb-146">There can be any number of spaces between the TIME symbol and the literal payload, but no new lines.</span></span>  
  
```  
TIME‘23:11’  
TIME‘01:01:00.1234567’  
```  
  
## <a name="datetimeoffset"></a><span data-ttu-id="6dfcb-147">DateTimeOffset</span><span class="sxs-lookup"><span data-stu-id="6dfcb-147">DateTimeOffset</span></span>  
 <span data-ttu-id="6dfcb-148">datetimeoffset リテラルは、日付部分、時刻部分、およびオフセット部分で構成され、ロケールに依存しません。</span><span class="sxs-lookup"><span data-stu-id="6dfcb-148">A datetimeoffset literal is independent of locale and composed of a date part, a time part, and an offset part.</span></span> <span data-ttu-id="6dfcb-149">日付部分、時刻部分、オフセット部分はすべて必須で、既定値はありません。</span><span class="sxs-lookup"><span data-stu-id="6dfcb-149">All date, time, and offset parts are mandatory and there are no default values.</span></span> <span data-ttu-id="6dfcb-150">日付部分は YYYY-MM-DD の形式にする必要があります。ここで、YYYY は 0001 ～ 9999 の 4 桁の年、MM は 1 ～ 12 の月、DD は特定の月の有効な日付を表します。</span><span class="sxs-lookup"><span data-stu-id="6dfcb-150">The date part must have the format YYYY-MM-DD, where YYYY is a four digit year value between 0001 and 9999, MM is the month between 1 and 12, and DD is the day value that is valid for the given month.</span></span> <span data-ttu-id="6dfcb-151">時刻部分は HH:MM[:SS[.fffffff]] の形式にする必要があります。ここで、HH は 0 ～ 23 時の値、MM は 0 ～ 59 分の値、SS は 0 ～ 59 秒の値、fffffff は 0 ～ 9999999 の 1 秒未満部分の値を表します。</span><span class="sxs-lookup"><span data-stu-id="6dfcb-151">The time part must have the format HH:MM[:SS[.fffffff]], where HH is the hour value between 0 and 23, MM is the minute value between 0 and 59, SS is the second value between 0 and 59, and fffffff is the fractional second value between 0 and 9999999.</span></span> <span data-ttu-id="6dfcb-152">いずれも両端の値を含みます。</span><span class="sxs-lookup"><span data-stu-id="6dfcb-152">All value ranges are inclusive.</span></span> <span data-ttu-id="6dfcb-153">1 秒未満部分は省略可能です。</span><span class="sxs-lookup"><span data-stu-id="6dfcb-153">Fractional seconds are optional.</span></span> <span data-ttu-id="6dfcb-154">1 秒未満部分を指定しなければ、秒は省略可能です。1 秒未満部分を指定する場合、秒は必須です。</span><span class="sxs-lookup"><span data-stu-id="6dfcb-154">Seconds are optional unless fractional seconds are specified; in this case, seconds are required.</span></span> <span data-ttu-id="6dfcb-155">秒も 1 秒未満部分も指定しない場合は、既定値の 0 が使用されます。</span><span class="sxs-lookup"><span data-stu-id="6dfcb-155">When seconds or fractions are not specified, the default value of zero will be used instead.</span></span> <span data-ttu-id="6dfcb-156">オフセットの部分は、形式をいる必要があります {+ (& a) #124;-} HH:MM、HH と MM が時刻部分と同じ意味があります。</span><span class="sxs-lookup"><span data-stu-id="6dfcb-156">The offset part must have the format {+&#124;-}HH:MM, where HH and MM have the same meaning as in the time part.</span></span> <span data-ttu-id="6dfcb-157">オフセットの範囲は -14:00 ～ + 14:00 でなければなりません。</span><span class="sxs-lookup"><span data-stu-id="6dfcb-157">The range of the offset, however, must be between -14:00 and + 14:00</span></span>  
  
 <span data-ttu-id="6dfcb-158">DATETIMEOFFSET 記号とリテラル ペイロード間の空白の数に制限はありませんが、改行はできません。</span><span class="sxs-lookup"><span data-stu-id="6dfcb-158">There can be any number of spaces between the DATETIMEOFFSET symbol and the literal payload, but no new lines.</span></span>  
  
```  
DATETIMEOFFSET‘2006-10-1 23:11 +02:00’  
DATETIMEOFFSET‘2006-12-25 01:01:00.0000000 -08:30’  
```  
  
> [!NOTE]
>  <span data-ttu-id="6dfcb-159">有効な Entity SQL リテラル値は、CLR またはデータ ソースに対してサポートされている範囲に含まれないことがあります。</span><span class="sxs-lookup"><span data-stu-id="6dfcb-159">A valid Entity SQL literal value can fall outside the supported ranges for CLR or the data source.</span></span> <span data-ttu-id="6dfcb-160">その結果、例外が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="6dfcb-160">This might result in an exception</span></span>  
  
## <a name="binary"></a><span data-ttu-id="6dfcb-161">2 項</span><span class="sxs-lookup"><span data-stu-id="6dfcb-161">Binary</span></span>  
 <span data-ttu-id="6dfcb-162">バイナリ文字列リテラルは、binary キーワードあるいは簡略記号 `X` または `x` と、それに続く単一引用符で囲まれた一連の 16 進数字で構成されます。</span><span class="sxs-lookup"><span data-stu-id="6dfcb-162">A binary string literal is a sequence of hexadecimal digits delimited by single quotes following the keyword binary or the shortcut symbol `X` or `x`.</span></span> <span data-ttu-id="6dfcb-163">簡略記号 `X` は、大文字と小文字は区別されません。</span><span class="sxs-lookup"><span data-stu-id="6dfcb-163">The shortcut symbol `X` is case insensitive.</span></span> <span data-ttu-id="6dfcb-164">キーワード `binary` と、バイナリ文字列値との間には、0 個以上の空白文字が許容されます。</span><span class="sxs-lookup"><span data-stu-id="6dfcb-164">A zero or more spaces are allowed between the keyword `binary` and the binary string value.</span></span>  
  
 <span data-ttu-id="6dfcb-165">16 進文字についても、大文字と小文字は区別されません。</span><span class="sxs-lookup"><span data-stu-id="6dfcb-165">Hexadecimal characters are also case insensitive.</span></span> <span data-ttu-id="6dfcb-166">リテラルが奇数個の 16 進数字で構成されていた場合、桁数が次に大きな偶数個となるように、先頭に 16 進数の 0 を付けることによって調整されます。</span><span class="sxs-lookup"><span data-stu-id="6dfcb-166">If the literal is composed of an odd number of hexadecimal digits, the literal will be aligned to the next even hexadecimal digit by prefixing the literal with a hexadecimal zero digit.</span></span> <span data-ttu-id="6dfcb-167">バイナリ文字列にサイズの制限はありません。</span><span class="sxs-lookup"><span data-stu-id="6dfcb-167">There is no formal limit on the size of the binary string.</span></span>  
  
```  
Binary'00ffaabb'  
X'ABCabc'  
BINARY    '0f0f0f0F0F0F0F0F0F0F'  
X'' –- empty binary string  
```  
  
## <a name="guid"></a><span data-ttu-id="6dfcb-168">Guid</span><span class="sxs-lookup"><span data-stu-id="6dfcb-168">Guid</span></span>  
 <span data-ttu-id="6dfcb-169">`GUID` リテラルは、グローバル一意識別子を表します。</span><span class="sxs-lookup"><span data-stu-id="6dfcb-169">A `GUID` literal represents a globally unique identifier.</span></span> <span data-ttu-id="6dfcb-170">キーワードによって形成されるシーケンスは`GUID`と呼ばれる形式の 16 進数字が続く*レジストリ*形式: 8-4-4-4-12 単一引用符で囲みます。</span><span class="sxs-lookup"><span data-stu-id="6dfcb-170">It is a sequence formed by the keyword `GUID` followed by hexadecimal digits in the form known as *registry* format: 8-4-4-4-12 enclosed in single quotes.</span></span> <span data-ttu-id="6dfcb-171">16 進数字の大文字と小文字は区別されません。</span><span class="sxs-lookup"><span data-stu-id="6dfcb-171">Hexadecimal digits are case insensitive.</span></span>  
  
 <span data-ttu-id="6dfcb-172">GUID 記号とリテラル ペイロード間の空白の数に制限はありませんが、改行はできません。</span><span class="sxs-lookup"><span data-stu-id="6dfcb-172">There can be any number of spaces between the GUID symbol and the literal payload, but no new lines.</span></span>  
  
```  
Guid'1afc7f5c-ffa0-4741-81cf-f12eAAb822bf'  
GUID  '1AFC7F5C-FFA0-4741-81CF-F12EAAB822BF'  
```  
  
## <a name="see-also"></a><span data-ttu-id="6dfcb-173">関連項目</span><span class="sxs-lookup"><span data-stu-id="6dfcb-173">See Also</span></span>  
 [<span data-ttu-id="6dfcb-174">Entity SQL の概要</span><span class="sxs-lookup"><span data-stu-id="6dfcb-174">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
