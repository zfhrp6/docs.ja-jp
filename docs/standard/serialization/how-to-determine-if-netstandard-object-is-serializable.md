---
title: "方法: .NET 標準オブジェクトがシリアル化可能なかどうかを判断します。"
description: "実行時に、標準の .NET 型をシリアル化できるかどうかを確認する方法を示します。"
ms.custom: 
ms.date: 10/20/2017
ms.prod: .net
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- serializing objects
- objects, serializing steps
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 0460fe27228fb9e17bde2d10652164707cd47a8b
ms.sourcegitcommit: bbde43da655ae7bea1977f7af7345eb87bd7fd5f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/21/2017
---
# <a name="how-to-determine-if-a-net-standard-object-is-serializable"></a><span data-ttu-id="2b880-103">方法: .NET 標準オブジェクトがシリアル化可能なかどうかを判断します。</span><span class="sxs-lookup"><span data-stu-id="2b880-103">How to: Determine if a .NET Standard object is serializable</span></span>

<span data-ttu-id="2b880-104">.NET 標準は、型とそのバージョンの標準に準拠している特定の .NET 実装上に存在する必要があるメンバーを定義する仕様です。</span><span class="sxs-lookup"><span data-stu-id="2b880-104">The .NET Standard is a specification that defines the types and members that must be present on specific .NET implementations that conform to that version of the standard.</span></span> <span data-ttu-id="2b880-105">ただし、.NET 標準定義しません、型がシリアル化できるかどうか。</span><span class="sxs-lookup"><span data-stu-id="2b880-105">However, the .NET Standard does not define whether a type is serializable.</span></span> <span data-ttu-id="2b880-106">.NET 標準ライブラリで定義された型がでマークされていない、<xref:System.SerializableAttribute>属性。</span><span class="sxs-lookup"><span data-stu-id="2b880-106">The types defined in the .NET Standard Library are not marked with the <xref:System.SerializableAttribute> attribute.</span></span> <span data-ttu-id="2b880-107">代わりに、.NET Core と .NET Framework などの特定の .NET 実装は、特定の型がシリアル化できるかどうかを判断するために解放します。</span><span class="sxs-lookup"><span data-stu-id="2b880-107">Instead, specific .NET implementations, such as the .NET Framework and .NET Core, are free to determine whether a particular type is serializable.</span></span> 

<span data-ttu-id="2b880-108">対象とする .NET 標準のライブラリを開発した場合は、.NET 標準をサポートする .NET の実装によって、ライブラリを使用できます。</span><span class="sxs-lookup"><span data-stu-id="2b880-108">If you've developed a library that targets the .NET Standard, your library can be consumed by any .NET implementation that supports the .NET Standard.</span></span> <span data-ttu-id="2b880-109">つまり、ことはできませんがわかっている事前に特定の型がシリアル化できるかどうかのみ、実行時にシリアル化可能なことがあるかどうかを判断できます。</span><span class="sxs-lookup"><span data-stu-id="2b880-109">This means that you cannot know in advance whether a particular type is serializable; you can only determine whether it is serializable at run time.</span></span>

<span data-ttu-id="2b880-110">値を取得することによって、オブジェクトが実行時にシリアル化可能かどうかを判断できます、<xref:System.Type.IsSerializable>のプロパティ、<xref:System.Type>そのオブジェクトの型を表すオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="2b880-110">You can determine whether an object is serializable at runtime by retrieving the value of the <xref:System.Type.IsSerializable> property of a <xref:System.Type> object that represents that object's type.</span></span> <span data-ttu-id="2b880-111">次の例では、1 つの実装を提供します。</span><span class="sxs-lookup"><span data-stu-id="2b880-111">The following example provides one implementation.</span></span> <span data-ttu-id="2b880-112">定義する、`IsSerializable(Object)`拡張メソッドを示すかどうか、<xref:System.Object>インスタンスをシリアル化することができます。</span><span class="sxs-lookup"><span data-stu-id="2b880-112">It defines an `IsSerializable(Object)` extension method that indicates whether any <xref:System.Object> instance can be serialized.</span></span>

[!code-csharp[is-a-type-serializable](~/samples/snippets/standard/serialization/is-serializable/csharp/program.cs#2)]
[!code-vb[is-a-type-serializable](~/samples/snippets/standard/serialization/is-serializable/vb/library.vb#2)]

<span data-ttu-id="2b880-113">かどうかをシリアル化して、次の例として、現在の .NET 実装に逆シリアル化を決定する方法を任意のオブジェクトを渡すことができますし、します。</span><span class="sxs-lookup"><span data-stu-id="2b880-113">You can then pass any object to the method to determine whether it can be serialized and deserialized on the current .NET implementation, as the following example shows:</span></span>

[!code-csharp[test-is-a-type-serializable](~/samples/snippets/standard/serialization/is-serializable/csharp/program.cs#1)]
[!code-vb[test-is-a-type-serializable](~/samples/snippets/standard/serialization/is-serializable/vb/program.vb#1)]

# <a name="see-also"></a><span data-ttu-id="2b880-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="2b880-114">See also</span></span>

<span data-ttu-id="2b880-115">[バイナリ シリアル化](binary-serialization.md) </span><span class="sxs-lookup"><span data-stu-id="2b880-115">[Binary serialization](binary-serialization.md) </span></span>  
<span data-ttu-id="2b880-116"><xref:System.SerializableAttribute?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="2b880-116"><xref:System.SerializableAttribute?displayProperty=fullName></span></span>    
<xref:System.Type.IsSerializable?displayProperty=nameWithType>   
