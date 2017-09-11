---
title: "方法: バイト配列を int に変換する (C# プログラミング ガイド)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- conversions [C#], byte array to int
- byte arrays [C#], converting to int
ms.assetid: d6ac20e2-448e-4aea-99b9-faf04c6f1e79
caps.latest.revision: 18
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
ms.openlocfilehash: 86ecfe95ab6fb5ce60e7568050cdf974d0dc3d88
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-convert-a-byte-array-to-an-int-c-programming-guide"></a><span data-ttu-id="6b54a-102">方法: バイト配列を int に変換する (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="6b54a-102">How to: Convert a byte Array to an int (C# Programming Guide)</span></span>
<span data-ttu-id="6b54a-103">次の例では、<xref:System.BitConverter> クラスを使用して、バイト配列を [int](../../../csharp/language-reference/keywords/int.md) に変換する方法、またバイト配列に戻す方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="6b54a-103">This example shows you how to use the <xref:System.BitConverter> class to convert an array of bytes to an [int](../../../csharp/language-reference/keywords/int.md) and back to an array of bytes.</span></span> <span data-ttu-id="6b54a-104">たとえば、ネットワークからバイトを読み込んだ後、バイトから組み込みデータ型への変換が必要になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="6b54a-104">You may have to convert from bytes to a built-in data type after you read bytes off the network, for example.</span></span> <span data-ttu-id="6b54a-105">この例の [ToInt32(Byte\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32)) メソッド以外にも、バイト列を (バイト配列から) 他の組み込み型に変換する <xref:System.BitConverter> クラスのメソッドがあります。次の表にそれらのメソッドを示します。</span><span class="sxs-lookup"><span data-stu-id="6b54a-105">In addition to the [ToInt32(Byte\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32)) method in the example, the following table lists methods in the <xref:System.BitConverter> class that convert bytes (from an array of bytes) to other built-in types.</span></span>  
  
|<span data-ttu-id="6b54a-106">返される型</span><span class="sxs-lookup"><span data-stu-id="6b54a-106">Type returned</span></span>|<span data-ttu-id="6b54a-107">メソッド</span><span class="sxs-lookup"><span data-stu-id="6b54a-107">Method</span></span>|  
|-------------------|------------|  
|`bool`|<span data-ttu-id="6b54a-108">[ToBoolean(Byte\[\], Int32)](xref:System.BitConverter.ToBoolean(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="6b54a-108">[ToBoolean(Byte\[\], Int32)](xref:System.BitConverter.ToBoolean(System.Byte[],System.Int32))</span></span>|  
|`char`|<span data-ttu-id="6b54a-109">[ToChar(Byte\[\], Int32)](xref:System.BitConverter.ToChar(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="6b54a-109">[ToChar(Byte\[\], Int32)](xref:System.BitConverter.ToChar(System.Byte[],System.Int32))</span></span>|  
|`double`|<span data-ttu-id="6b54a-110">[ToDouble(Byte\[\], Int32)](xref:System.BitConverter.ToDouble(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="6b54a-110">[ToDouble(Byte\[\], Int32)](xref:System.BitConverter.ToDouble(System.Byte[],System.Int32))</span></span>|  
|`short`|<span data-ttu-id="6b54a-111">[ToInt16(Byte\[\], Int32)](xref:System.BitConverter.ToInt16(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="6b54a-111">[ToInt16(Byte\[\], Int32)](xref:System.BitConverter.ToInt16(System.Byte[],System.Int32))</span></span>|  
|`int`|<span data-ttu-id="6b54a-112">[ToInt32(Byte\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="6b54a-112">[ToInt32(Byte\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32))</span></span>|  
|`long`|<span data-ttu-id="6b54a-113">[ToInt64(Byte\[\], Int32)](xref:System.BitConverter.ToInt64(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="6b54a-113">[ToInt64(Byte\[\], Int32)](xref:System.BitConverter.ToInt64(System.Byte[],System.Int32))</span></span>|  
|`float`|<span data-ttu-id="6b54a-114">[ToSingle(Byte\[\], Int32)](xref:System.BitConverter.ToSingle(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="6b54a-114">[ToSingle(Byte\[\], Int32)](xref:System.BitConverter.ToSingle(System.Byte[],System.Int32))</span></span>|  
|`ushort`|<span data-ttu-id="6b54a-115">[ToUInt16(Byte\[\], Int32)](xref:System.BitConverter.ToUInt16(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="6b54a-115">[ToUInt16(Byte\[\], Int32)](xref:System.BitConverter.ToUInt16(System.Byte[],System.Int32))</span></span>|  
|`uint`|<span data-ttu-id="6b54a-116">[ToUInt32(Byte\[\], Int32)](xref:System.BitConverter.ToUInt32(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="6b54a-116">[ToUInt32(Byte\[\], Int32)](xref:System.BitConverter.ToUInt32(System.Byte[],System.Int32))</span></span>|  
|`ulong`|<span data-ttu-id="6b54a-117">[ToUInt64(Byte\[\], Int32)](xref:System.BitConverter.ToUInt64(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="6b54a-117">[ToUInt64(Byte\[\], Int32)](xref:System.BitConverter.ToUInt64(System.Byte[],System.Int32))</span></span>|  
  
## <a name="example"></a><span data-ttu-id="6b54a-118">例</span><span class="sxs-lookup"><span data-stu-id="6b54a-118">Example</span></span>  
 <span data-ttu-id="6b54a-119">この例では、バイトの配列を初期化して、コンピューター アーキテクチャがリトル エンディアンである場合 (つまり、下位バイトから先に格納する場合) は、配列を反転します。次に、[ToInt32(Byte\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32)) メソッドを呼び出して、配列内の 4 バイトを `int` に変換します。</span><span class="sxs-lookup"><span data-stu-id="6b54a-119">This example initializes an array of bytes, reverses the array if the computer architecture is little-endian (that is, the least significant byte is stored first), and then calls the [ToInt32(Byte\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32)) method to convert four bytes in the array to an `int`.</span></span> <span data-ttu-id="6b54a-120">[ToInt32(Byte\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32)) の 2 番目の引数は、バイト配列の開始インデックスを指定します。</span><span class="sxs-lookup"><span data-stu-id="6b54a-120">The second argument to [ToInt32(Byte\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32)) specifies the start index of the array of bytes.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6b54a-121">出力は、コンピューター アーキテクチャのエンディアンによって異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="6b54a-121">The output may differ depending on the endianess of your computer's architecture.</span></span>  
  
 <span data-ttu-id="6b54a-122">[!code-cs[csProgGuideTypes#22](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-byte-array-to-an-int_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="6b54a-122">[!code-cs[csProgGuideTypes#22](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-byte-array-to-an-int_1.cs)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="6b54a-123">例</span><span class="sxs-lookup"><span data-stu-id="6b54a-123">Example</span></span>  
 <span data-ttu-id="6b54a-124">この例では、<xref:System.BitConverter> クラスの <xref:System.BitConverter.GetBytes%28System.Int32%29> メソッドを呼び出して、`int` をバイト配列に変換します。</span><span class="sxs-lookup"><span data-stu-id="6b54a-124">In this example, the <xref:System.BitConverter.GetBytes%28System.Int32%29> method of the <xref:System.BitConverter> class is called to convert an `int` to an array of bytes.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6b54a-125">出力は、コンピューター アーキテクチャのエンディアンによって異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="6b54a-125">The output may differ depending on the endianess of your computer's architecture.</span></span>  
  
 <span data-ttu-id="6b54a-126">[!code-cs[csProgGuideTypes#23](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-byte-array-to-an-int_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="6b54a-126">[!code-cs[csProgGuideTypes#23](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-byte-array-to-an-int_2.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b54a-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="6b54a-127">See Also</span></span>  
 <span data-ttu-id="6b54a-128"><xref:System.BitConverter></span><span class="sxs-lookup"><span data-stu-id="6b54a-128"><xref:System.BitConverter></span></span>   
 <span data-ttu-id="6b54a-129"><xref:System.BitConverter.IsLittleEndian></span><span class="sxs-lookup"><span data-stu-id="6b54a-129"><xref:System.BitConverter.IsLittleEndian></span></span>   
 [<span data-ttu-id="6b54a-130">型</span><span class="sxs-lookup"><span data-stu-id="6b54a-130">Types</span></span>](../../../csharp/programming-guide/types/index.md)

