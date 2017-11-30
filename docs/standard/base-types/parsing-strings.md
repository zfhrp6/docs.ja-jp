---
title: ".NET における文字列の解析"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- parsing strings, about parsing strings
- IFormatProvider interface, parsing strings
- base types, parsing strings
- Parse method
- parsing strings
ms.assetid: 5e758b41-db93-456b-8999-99b7304b090d
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 811db42e04e73d7acbc03e303297b19fdf643384
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="parsing-strings-in-net"></a><span data-ttu-id="31ec6-102">.NET における文字列の解析</span><span class="sxs-lookup"><span data-stu-id="31ec6-102">Parsing Strings in .NET</span></span>
<span data-ttu-id="31ec6-103">解析操作では、.NET の基本データ型を表す文字列をその基本データ型に変換します。</span><span class="sxs-lookup"><span data-stu-id="31ec6-103">A parsing operation converts a string that represents a .NET base type into that base type.</span></span> <span data-ttu-id="31ec6-104">たとえば解析操作は、文字列を浮動小数点数や日付と時刻の値に変換するために使用します。</span><span class="sxs-lookup"><span data-stu-id="31ec6-104">For example, a parsing operation is used to convert a string to a floating-point number or to a date and time value.</span></span> <span data-ttu-id="31ec6-105">解析操作を実行するには、`Parse` メソッドがよく使用されます。</span><span class="sxs-lookup"><span data-stu-id="31ec6-105">The method most commonly used to perform a parsing operation is the `Parse` method.</span></span> <span data-ttu-id="31ec6-106">解析は書式設定の逆の操作 (基本データ型のその文字列形式への変換を含む) であるため、多くの同じ規則が適用されます。</span><span class="sxs-lookup"><span data-stu-id="31ec6-106">Because parsing is the reverse operation of formatting (which involves converting a base type into its string representation), many of the same rules and conventions apply.</span></span> <span data-ttu-id="31ec6-107">実装するオブジェクトを使用して書式設定と同様、<xref:System.IFormatProvider>インターフェイスを実装するオブジェクトの使用の解析もカルチャの書式情報を提供する、<xref:System.IFormatProvider>文字列表現を解釈する方法を決定するインターフェイス.</span><span class="sxs-lookup"><span data-stu-id="31ec6-107">Just as formatting uses an object that implements the <xref:System.IFormatProvider> interface to provide culture-sensitive formatting information, parsing also uses an object that implements the <xref:System.IFormatProvider> interface to determine how to interpret a string representation.</span></span> <span data-ttu-id="31ec6-108">詳細については、次を参照してください。[型の書式設定](../../../docs/standard/base-types/formatting-types.md)です。</span><span class="sxs-lookup"><span data-stu-id="31ec6-108">For more information, see [Formatting Types](../../../docs/standard/base-types/formatting-types.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="31ec6-109">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="31ec6-109">In This Section</span></span>  
 [<span data-ttu-id="31ec6-110">数値文字列の解析</span><span class="sxs-lookup"><span data-stu-id="31ec6-110">Parsing Numeric Strings</span></span>](../../../docs/standard/base-types/parsing-numeric.md)  
 <span data-ttu-id="31ec6-111">文字列を .NET 型の数値に変換する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="31ec6-111">Describes how to convert strings into .NET numeric types.</span></span>  
  
 [<span data-ttu-id="31ec6-112">日付と時刻文字列の解析</span><span class="sxs-lookup"><span data-stu-id="31ec6-112">Parsing Date and Time Strings</span></span>](../../../docs/standard/base-types/parsing-datetime.md)  
 <span data-ttu-id="31ec6-113">文字列を .NET に変換する方法について説明**DateTime**型です。</span><span class="sxs-lookup"><span data-stu-id="31ec6-113">Describes how to convert strings into .NET **DateTime** types.</span></span>  
  
 [<span data-ttu-id="31ec6-114">その他の文字列の解析</span><span class="sxs-lookup"><span data-stu-id="31ec6-114">Parsing Other Strings</span></span>](../../../docs/standard/base-types/parsing-other.md)  
 <span data-ttu-id="31ec6-115">文字列に変換する方法について説明します**Char**、**ブール**、および**Enum**型です。</span><span class="sxs-lookup"><span data-stu-id="31ec6-115">Describes how to convert strings into **Char**, **Boolean**, and **Enum** types.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="31ec6-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="31ec6-116">Related Sections</span></span>  
 [<span data-ttu-id="31ec6-117">型の書式設定</span><span class="sxs-lookup"><span data-stu-id="31ec6-117">Formatting Types</span></span>](../../../docs/standard/base-types/formatting-types.md)  
 <span data-ttu-id="31ec6-118">書式指定子と書式プロバイダーのような基本的な書式の概念について説明します。</span><span class="sxs-lookup"><span data-stu-id="31ec6-118">Describes basic formatting concepts like format specifiers and format providers.</span></span>  
  
 [<span data-ttu-id="31ec6-119">.NET での型変換</span><span class="sxs-lookup"><span data-stu-id="31ec6-119">Type Conversion in .NET</span></span>](../../../docs/standard/base-types/type-conversion.md)  
 <span data-ttu-id="31ec6-120">型に変換する方法をについて説明します。</span><span class="sxs-lookup"><span data-stu-id="31ec6-120">Describes how to convert types.</span></span>  
  
 [<span data-ttu-id="31ec6-121">基本データ型</span><span class="sxs-lookup"><span data-stu-id="31ec6-121">Base Types</span></span>](../../../docs/standard/base-types/index.md)  
 <span data-ttu-id="31ec6-122">.NET の基本型で実行できる一般的な操作をについて説明します。</span><span class="sxs-lookup"><span data-stu-id="31ec6-122">Describes common operations that you can perform on .NET base types.</span></span>
