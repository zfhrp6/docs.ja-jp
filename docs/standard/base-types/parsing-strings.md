---
title: ".NET での文字列の解析"
description: ".NET での文字列の解析"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
ms.date: 07/22/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: 8103c0a6-61d3-40dd-a3e9-2a32ba6a4c05
ms.translationtype: Human Translation
ms.sourcegitcommit: 90fe68f7f3c4b46502b5d3770b1a2d57c6af748a
ms.openlocfilehash: c741ae793d491f691a355df6ad064b81d609c7e5
ms.contentlocale: ja-jp
ms.lasthandoff: 03/03/2017

---

# <a name="parsing-strings-in-net"></a><span data-ttu-id="fad5f-104">.NET での文字列の解析</span><span class="sxs-lookup"><span data-stu-id="fad5f-104">Parsing strings in .NET</span></span>

<span data-ttu-id="fad5f-105">解析操作では、.NET の基本データ型を表す文字列をその基本データ型に変換します。</span><span class="sxs-lookup"><span data-stu-id="fad5f-105">A parsing operation converts a string that represents a .NET base type into that base type.</span></span> <span data-ttu-id="fad5f-106">たとえば解析操作は、文字列を浮動小数点数や日付と時刻の値に変換するために使用します。</span><span class="sxs-lookup"><span data-stu-id="fad5f-106">For example, a parsing operation is used to convert a string to a floating-point number or to a date and time value.</span></span> <span data-ttu-id="fad5f-107">解析操作を実行するには、`Parse` メソッドがよく使用されます。</span><span class="sxs-lookup"><span data-stu-id="fad5f-107">The method most commonly used to perform a parsing operation is the `Parse` method.</span></span> <span data-ttu-id="fad5f-108">解析は書式設定の逆の操作 (基本データ型のその文字列形式への変換を含む) であるため、多くの同じ規則が適用されます。</span><span class="sxs-lookup"><span data-stu-id="fad5f-108">Because parsing is the reverse operation of formatting (which involves converting a base type into its string representation), many of the same rules and conventions apply.</span></span> <span data-ttu-id="fad5f-109">カルチャに依存する書式情報を指定するために、書式設定で [IFormatProvider](xref:System.IFormatProvider) インターフェイスを実装するオブジェクトを使用するのと同じように、解析でも [IFormatProvider](xref:System.IFormatProvider) インターフェイスを実装するオブジェクトを使用し、文字列形式を解釈する方法を決定します。</span><span class="sxs-lookup"><span data-stu-id="fad5f-109">Just as formatting uses an object that implements the [IFormatProvider](xref:System.IFormatProvider) interface to provide culture-sensitive formatting information, parsing also uses an object that implements the [IFormatProvider](xref:System.IFormatProvider) interface to determine how to interpret a string representation.</span></span> <span data-ttu-id="fad5f-110">詳細については、「[.NET での型の書式設定](formatting-types.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="fad5f-110">For more information, see [Formatting Types in .NET](formatting-types.md).</span></span>

## <a name="in-this-section"></a><span data-ttu-id="fad5f-111">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="fad5f-111">In This Section</span></span>

<span data-ttu-id="fad5f-112">[.NET での数値文字列の解析](parsing-numeric.md) - 文字列を .NET の数値文字列に変換する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="fad5f-112">[Parsing Numeric Strings in .NET](parsing-numeric.md) - Describes how to convert strings into .NET numeric types.</span></span>

<span data-ttu-id="fad5f-113">[.NET での日付と時刻文字列の解析](parsing-datetime.md) - 文字列を .NET の `DateTime` 型に変換する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="fad5f-113">[Parsing Date and Time Strings in .NET](parsing-datetime.md) - Describes how to convert strings into .NET `DateTime` types.</span></span>

<span data-ttu-id="fad5f-114">[.NET でのその他の文字列の解析](parsing-other.md) - 文字列を [Char](xref:System.Char)、[Boolean](xref:System.Boolean)、および [Enum](xref:System.Enum) 型に変換する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="fad5f-114">[Parsing Other Strings in .NET](parsing-other.md) - Describes how to convert strings into [Char](xref:System.Char), [Boolean](xref:System.Boolean), and [Enum](xref:System.Enum) types.</span></span>

<span data-ttu-id="fad5f-115">[.NET での型の書式設定](formatting-types.md) - 書式指定子および書式プロバイダーなどの基本書式の概念について説明します。</span><span class="sxs-lookup"><span data-stu-id="fad5f-115">[Formatting Types in .NET](formatting-types.md) - Describes basic formatting concepts like format specifiers and format providers.</span></span>

<span data-ttu-id="fad5f-116">[.NET での型変換](type-conversion.md) - 型を変換する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="fad5f-116">[Type Conversion in .NET](type-conversion.md) - Describes how to convert types.</span></span>

<span data-ttu-id="fad5f-117">[.NET での基本データ型の操作](index.md) - .NET の基本データ型で実行できる一般的な操作について説明します。</span><span class="sxs-lookup"><span data-stu-id="fad5f-117">[Working with Base Types in .NET](index.md) - Describes common operations that you can perform on .NET base types.</span></span>


