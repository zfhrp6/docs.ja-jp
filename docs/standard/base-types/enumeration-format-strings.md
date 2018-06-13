---
title: 列挙型書式指定文字列
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- format specifiers, enumeration format strings
- enumeration format strings
- formatting [.NET Framework], enumeration
ms.assetid: dd1ff672-1052-42cf-8666-4924fb6cd1a1
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8e04c6137bcb2b3da7e9883fde4de35737788587
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33568109"
---
# <a name="enumeration-format-strings"></a><span data-ttu-id="27504-102">列挙型書式指定文字列</span><span class="sxs-lookup"><span data-stu-id="27504-102">Enumeration Format Strings</span></span>
<span data-ttu-id="27504-103"><xref:System.Enum.ToString%2A?displayProperty=nameWithType> メソッドを使用すると、列挙型メンバーの数値、16 進数、または文字列値を表す新しい文字列オブジェクトを作成できます。</span><span class="sxs-lookup"><span data-stu-id="27504-103">You can use the <xref:System.Enum.ToString%2A?displayProperty=nameWithType> method to create a new string object that represents the numeric, hexadecimal, or string value of an enumeration member.</span></span> <span data-ttu-id="27504-104">このメソッドは、列挙型書式指定文字列のいずれかを使って、返される値を指定します。</span><span class="sxs-lookup"><span data-stu-id="27504-104">This method takes one of the enumeration formatting strings to specify the value that you want returned.</span></span>  
  
 <span data-ttu-id="27504-105">次の表では、列挙型書式指定文字列とそれが返す値を一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="27504-105">The following table lists the enumeration formatting strings and the values they return.</span></span> <span data-ttu-id="27504-106">これらの書式指定子では大文字と小文字は区別されません。</span><span class="sxs-lookup"><span data-stu-id="27504-106">These format specifiers are not case-sensitive.</span></span>  
  
| <span data-ttu-id="27504-107">書式文字列</span><span class="sxs-lookup"><span data-stu-id="27504-107">Format string</span></span> | <span data-ttu-id="27504-108">結果</span><span class="sxs-lookup"><span data-stu-id="27504-108">Result</span></span> |  
| ------------- | ------ |  
| <span data-ttu-id="27504-109">G または g</span><span class="sxs-lookup"><span data-stu-id="27504-109">G or g</span></span> | <span data-ttu-id="27504-110">可能な場合には列挙エントリを文字列値として表示し、それ以外の場合は、現在のインスタンスの整数値を表示します。</span><span class="sxs-lookup"><span data-stu-id="27504-110">Displays the enumeration entry as a string value, if possible, and otherwise displays the integer value of the current instance.</span></span> <span data-ttu-id="27504-111">列挙型が **Flags** 属性セットで定義されている場合、有効な各エントリの文字列値はコンマで区切られて連結されます。</span><span class="sxs-lookup"><span data-stu-id="27504-111">If the enumeration is defined with the **Flags** attribute set, the string values of each valid entry are concatenated together, separated by commas.</span></span> <span data-ttu-id="27504-112">**Flags** 属性が設定されていない場合、無効な値が数値エントリとして表示されます。</span><span class="sxs-lookup"><span data-stu-id="27504-112">If the **Flags** attribute is not set, an invalid value is displayed as a numeric entry.</span></span> <span data-ttu-id="27504-113">次の例は、G 書式指定子を示しています。</span><span class="sxs-lookup"><span data-stu-id="27504-113">The following example illustrates the G format specifier.</span></span><br><br><span data-ttu-id="27504-114">[!code-csharp[Formatting.Enum#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#1)] [!code-vb[Formatting.Enum#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#1)]</span><span class="sxs-lookup"><span data-stu-id="27504-114">[!code-csharp[Formatting.Enum#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#1)] [!code-vb[Formatting.Enum#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#1)]</span></span> |  
| <span data-ttu-id="27504-115">F または f</span><span class="sxs-lookup"><span data-stu-id="27504-115">F or f</span></span> | <span data-ttu-id="27504-116">可能な場合には列挙エントリを文字列値として表示します。</span><span class="sxs-lookup"><span data-stu-id="27504-116">Displays the enumeration entry as a string value, if possible.</span></span> <span data-ttu-id="27504-117">(**Flags** 属性が存在しない場合でも) 値が列挙内のエントリの総和として完全に表示できる場合、有効な各エントリの文字列値はコンマで区切られて連結されます。</span><span class="sxs-lookup"><span data-stu-id="27504-117">If the value can be completely displayed as a summation of the entries in the enumeration (even if the **Flags** attribute is not present), the string values of each valid entry are concatenated together, separated by commas.</span></span> <span data-ttu-id="27504-118">値が列挙エントリによって完全に特定できない場合、その値は整数値として書式設定されます。</span><span class="sxs-lookup"><span data-stu-id="27504-118">If the value cannot be completely determined by the enumeration entries, then the value is formatted as the integer value.</span></span> <span data-ttu-id="27504-119">次の例は、F 書式指定子を示しています。</span><span class="sxs-lookup"><span data-stu-id="27504-119">The following example illustrates the F format specifier.</span></span><br><br><span data-ttu-id="27504-120">[!code-csharp[Formatting.Enum#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#2)] [!code-vb[Formatting.Enum#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#2)]</span><span class="sxs-lookup"><span data-stu-id="27504-120">[!code-csharp[Formatting.Enum#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#2)] [!code-vb[Formatting.Enum#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#2)]</span></span> |  
| <span data-ttu-id="27504-121">D または d</span><span class="sxs-lookup"><span data-stu-id="27504-121">D or d</span></span> | <span data-ttu-id="27504-122">列挙エントリを整数値として可能な限り短い表現で表示します。</span><span class="sxs-lookup"><span data-stu-id="27504-122">Displays the enumeration entry as an integer value in the shortest representation possible.</span></span> <span data-ttu-id="27504-123">次の例は、D 書式指定子を示しています。</span><span class="sxs-lookup"><span data-stu-id="27504-123">The following example illustrates the D format specifier.</span></span><br><br><span data-ttu-id="27504-124">[!code-csharp[Formatting.Enum#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#3)] [!code-vb[Formatting.Enum#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#3)]</span><span class="sxs-lookup"><span data-stu-id="27504-124">[!code-csharp[Formatting.Enum#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#3)] [!code-vb[Formatting.Enum#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#3)]</span></span> |  
| <span data-ttu-id="27504-125">X または x</span><span class="sxs-lookup"><span data-stu-id="27504-125">X or x</span></span> | <span data-ttu-id="27504-126">列挙エントリを 16 進値として表示します。</span><span class="sxs-lookup"><span data-stu-id="27504-126">Displays the enumeration entry as a hexadecimal value.</span></span> <span data-ttu-id="27504-127">値は、最小の 8 桁の長さにするため、必要に応じて先頭にゼロを付けて表されます。</span><span class="sxs-lookup"><span data-stu-id="27504-127">The value is represented with leading zeros as necessary, to ensure that the value is a minimum eight digits in length.</span></span> <span data-ttu-id="27504-128">次の例は、X 書式指定子を示しています。</span><span class="sxs-lookup"><span data-stu-id="27504-128">The following example illustrates the X format specifier.</span></span><br /><br /> <span data-ttu-id="27504-129">[!code-csharp[Formatting.Enum#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#4)] [!code-vb[Formatting.Enum#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#4)]</span><span class="sxs-lookup"><span data-stu-id="27504-129">[!code-csharp[Formatting.Enum#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#4)] [!code-vb[Formatting.Enum#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#4)]</span></span> |  
  
## <a name="example"></a><span data-ttu-id="27504-130">例</span><span class="sxs-lookup"><span data-stu-id="27504-130">Example</span></span>  
 <span data-ttu-id="27504-131">次の例では、`Red`、`Blue`、`Green` の 3 つのエントリから構成される、`Colors` と呼ばれる列挙型を定義します。</span><span class="sxs-lookup"><span data-stu-id="27504-131">The following example defines an enumeration called `Colors` that consists of three entries: `Red`, `Blue`, and `Green`.</span></span>  
  
 [!code-csharp[Formatting.Enum#5](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#5)]
 [!code-vb[Formatting.Enum#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#5)]  
  
 <span data-ttu-id="27504-132">列挙型を定義すると、次のようにインスタンスを宣言できます。</span><span class="sxs-lookup"><span data-stu-id="27504-132">After the enumeration is defined, an instance can be declared in the following manner.</span></span>  
  
 [!code-csharp[Formatting.Enum#6](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#6)]
 [!code-vb[Formatting.Enum#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#6)]  
  
 <span data-ttu-id="27504-133">これで `Color.ToString(System.String)` メソッドを使用して、渡された書式指定子に応じて、列挙値をさまざまな方法で表示することができます。</span><span class="sxs-lookup"><span data-stu-id="27504-133">The `Color.ToString(System.String)` method can then be used to display the enumeration value in different ways, depending on the format specifier passed to it.</span></span>  
  
 [!code-csharp[Formatting.Enum#7](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#7)]
 [!code-vb[Formatting.Enum#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#7)]  
  
## <a name="see-also"></a><span data-ttu-id="27504-134">参照</span><span class="sxs-lookup"><span data-stu-id="27504-134">See Also</span></span>  
 [<span data-ttu-id="27504-135">型の書式設定</span><span class="sxs-lookup"><span data-stu-id="27504-135">Formatting Types</span></span>](../../../docs/standard/base-types/formatting-types.md)
