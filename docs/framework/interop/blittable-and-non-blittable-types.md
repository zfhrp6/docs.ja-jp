---
title: "Blittable 型と非 Blittable 型"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- interop marshaling, blittable types
- blittable types, interop marshaling
ms.assetid: d03b050e-2916-49a0-99ba-f19316e5c1b3
caps.latest.revision: "23"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b05d77df28b560b9236e467a914229c0fa9ae7e8
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="blittable-and-non-blittable-types"></a><span data-ttu-id="dd7fd-102">Blittable 型と非 Blittable 型</span><span class="sxs-lookup"><span data-stu-id="dd7fd-102">Blittable and Non-Blittable Types</span></span>
<span data-ttu-id="dd7fd-103">ほとんどのデータ型の表現はマネージ メモリとアンマネージ メモリの両方で共通しているため、相互運用マーシャラーによる特別な処理は必要ありません。</span><span class="sxs-lookup"><span data-stu-id="dd7fd-103">Most data types have a common representation in both managed and unmanaged memory and do not require special handling by the interop marshaler.</span></span> <span data-ttu-id="dd7fd-104">これらの型は、マネージ コードとアンマネージ コード間での受け渡しの際に変換が必要でないため、*blittable 型*と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="dd7fd-104">These types are called *blittable types* because they do not require conversion when they are passed between managed and unmanaged code.</span></span>  
  
 <span data-ttu-id="dd7fd-105">プラットフォーム呼び出しから返される構造体は blittable 型である必要があります。</span><span class="sxs-lookup"><span data-stu-id="dd7fd-105">Structures that are returned from platform invoke calls must be blittable types.</span></span> <span data-ttu-id="dd7fd-106">プラットフォーム呼び出しでは、戻り値の型として非 blittable 型の構造体はサポートされません。</span><span class="sxs-lookup"><span data-stu-id="dd7fd-106">Platform invoke does not support non-blittable structures as return types.</span></span>  
  
 <span data-ttu-id="dd7fd-107"><xref:System> 名前空間に属する次の型は blittable 型です。</span><span class="sxs-lookup"><span data-stu-id="dd7fd-107">The following types from the <xref:System> namespace are blittable types:</span></span>  
  
-   <xref:System.Byte?displayProperty=nameWithType>  
  
-   <xref:System.SByte?displayProperty=nameWithType>  
  
-   <xref:System.Int16?displayProperty=nameWithType>  
  
-   <xref:System.UInt16?displayProperty=nameWithType>  
  
-   <xref:System.Int32?displayProperty=nameWithType>  
  
-   <xref:System.UInt32?displayProperty=nameWithType>  
  
-   <xref:System.Int64?displayProperty=nameWithType>  
  
-   <xref:System.UInt64?displayProperty=nameWithType>  
  
-   <xref:System.IntPtr?displayProperty=nameWithType>  
  
-   <xref:System.UIntPtr?displayProperty=nameWithType>  
  
-   <xref:System.Single?displayProperty=nameWithType>  
  
-   <xref:System.Double?displayProperty=nameWithType>  
  
 <span data-ttu-id="dd7fd-108">次の複合型も blittable 型です。</span><span class="sxs-lookup"><span data-stu-id="dd7fd-108">The following complex types are also blittable types:</span></span>  
  
-   <span data-ttu-id="dd7fd-109">整数の配列など、blittable 型の 1 次元配列。</span><span class="sxs-lookup"><span data-stu-id="dd7fd-109">One-dimensional arrays of blittable types, such as an array of integers.</span></span> <span data-ttu-id="dd7fd-110">ただし、blittable 型の可変配列を含む型自体は blittable ではありません。</span><span class="sxs-lookup"><span data-stu-id="dd7fd-110">However, a type that contains a variable array of blittable types is not itself blittable.</span></span>  
  
-   <span data-ttu-id="dd7fd-111">blittable 型だけを含む、書式設定された値型 (および、それらが書式設定された型としてマーシャリングされる場合はクラス)。</span><span class="sxs-lookup"><span data-stu-id="dd7fd-111">Formatted value types that contain only blittable types (and classes if they are marshaled as formatted types).</span></span> <span data-ttu-id="dd7fd-112">書式設定された値型の詳細については、「[Default Marshaling for Value Types](http://msdn.microsoft.com/en-us/4d9a876c-e05a-40ba-bd85-bd22877f984a)」(値型に対する既定のマーシャリング) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="dd7fd-112">For more information about formatted value types, see [Default Marshaling for Value Types](http://msdn.microsoft.com/en-us/4d9a876c-e05a-40ba-bd85-bd22877f984a).</span></span>  
  
 <span data-ttu-id="dd7fd-113">オブジェクト参照は blittable ではありません。</span><span class="sxs-lookup"><span data-stu-id="dd7fd-113">Object references are not blittable.</span></span> <span data-ttu-id="dd7fd-114">これには、単独では blittable なオブジェクトへの参照の配列も含まれます。</span><span class="sxs-lookup"><span data-stu-id="dd7fd-114">This includes an array of references to objects that are blittable by themselves.</span></span> <span data-ttu-id="dd7fd-115">たとえば、blittable な構造体は定義できますが、それらの構造体への参照の配列を含む blittable 型は定義できません。</span><span class="sxs-lookup"><span data-stu-id="dd7fd-115">For example, you can define a structure that is blittable, but you cannot define a blittable type that contains an array of references to those structures.</span></span>  
  
 <span data-ttu-id="dd7fd-116">blittable 型の配列と、blittable 型のメンバーだけを含むクラスは、最適化のために、マーシャリング時にコピーされるのではなく[固定](../../../docs/framework/interop/copying-and-pinning.md)されます。</span><span class="sxs-lookup"><span data-stu-id="dd7fd-116">As an optimization, arrays of blittable types and classes that contain only blittable members are [pinned](../../../docs/framework/interop/copying-and-pinning.md) instead of copied during marshaling.</span></span> <span data-ttu-id="dd7fd-117">これらの型は、呼び出し元と呼び出し先が同じアパートメントに属する場合には、In/Out パラメーターとしてマーシャリングされるように見えることがあります。</span><span class="sxs-lookup"><span data-stu-id="dd7fd-117">These types can appear to be marshaled as In/Out parameters when the caller and callee are in the same apartment.</span></span> <span data-ttu-id="dd7fd-118">ただし、そのような型は実際には In パラメーターとしてマーシャリングされるため、引数を In/Out パラメーターとしてマーシャリングする必要がある場合には、<xref:System.Runtime.InteropServices.InAttribute> 属性と <xref:System.Runtime.InteropServices.OutAttribute> 属性を適用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="dd7fd-118">However, these types are actually marshaled as In parameters, and you must apply the <xref:System.Runtime.InteropServices.InAttribute> and <xref:System.Runtime.InteropServices.OutAttribute> attributes if you want to marshal the argument as an In/Out parameter.</span></span>  
  
 <span data-ttu-id="dd7fd-119">一部のマネージ データ型は、アンマネージ環境では異なる表現が必要です。</span><span class="sxs-lookup"><span data-stu-id="dd7fd-119">Some managed data types require a different representation in an unmanaged environment.</span></span> <span data-ttu-id="dd7fd-120">これらの非 blittable データ型は、マーシャリングできる形式に変換する必要があります。</span><span class="sxs-lookup"><span data-stu-id="dd7fd-120">These non-blittable data types must be converted into a form that can be marshaled.</span></span> <span data-ttu-id="dd7fd-121">たとえば、マネージ文字列は、文字列オブジェクトに変換しないとマーシャリングできないので、非 blittable 型です。</span><span class="sxs-lookup"><span data-stu-id="dd7fd-121">For example, managed strings are non-blittable types because they must be converted into string objects before they can be marshaled.</span></span>  
  
 <span data-ttu-id="dd7fd-122"><xref:System> 名前空間に属する非 blittable 型を次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="dd7fd-122">The following table lists non-blittable types from the <xref:System> namespace.</span></span> <span data-ttu-id="dd7fd-123">[デリゲート](http://msdn.microsoft.com/en-us/d176ee76-f982-494b-b03d-92e4118896e2)は静的メソッドまたはクラス インスタンスを参照するデータ構造体であり、これも非 blittable 型です。</span><span class="sxs-lookup"><span data-stu-id="dd7fd-123">[Delegates](http://msdn.microsoft.com/en-us/d176ee76-f982-494b-b03d-92e4118896e2), which are data structures that refer to a static method or to a class instance, are also non-blittable.</span></span>  
  
|<span data-ttu-id="dd7fd-124">非 blittable 型</span><span class="sxs-lookup"><span data-stu-id="dd7fd-124">Non-blittable type</span></span>|<span data-ttu-id="dd7fd-125">説明</span><span class="sxs-lookup"><span data-stu-id="dd7fd-125">Description</span></span>|  
|-------------------------|-----------------|  
|[<span data-ttu-id="dd7fd-126">System.Array</span><span class="sxs-lookup"><span data-stu-id="dd7fd-126">System.Array</span></span>](../../../docs/framework/interop/default-marshaling-for-arrays.md)|<span data-ttu-id="dd7fd-127">C スタイルの配列または `SAFEARRAY` に変換されます。</span><span class="sxs-lookup"><span data-stu-id="dd7fd-127">Converts to a C-style array or a `SAFEARRAY`.</span></span>|  
|[<span data-ttu-id="dd7fd-128">System.Boolean</span><span class="sxs-lookup"><span data-stu-id="dd7fd-128">System.Boolean</span></span>](http://msdn.microsoft.com/en-us/d4c00537-70f7-4ca6-8197-bfc1ec037ff9)|<span data-ttu-id="dd7fd-129">1、2、または 4 バイトの値に変換されます。`true` の場合は 1 または -1 になります。</span><span class="sxs-lookup"><span data-stu-id="dd7fd-129">Converts to a 1, 2, or 4-byte value with `true` as 1 or -1.</span></span>|  
|[<span data-ttu-id="dd7fd-130">System.Char</span><span class="sxs-lookup"><span data-stu-id="dd7fd-130">System.Char</span></span>](http://msdn.microsoft.com/en-us/cecc87c1-075e-4cde-aa56-33d189f66feb)|<span data-ttu-id="dd7fd-131">Unicode 文字または ANSI 文字に変換されます。</span><span class="sxs-lookup"><span data-stu-id="dd7fd-131">Converts to a Unicode or ANSI character.</span></span>|  
|[<span data-ttu-id="dd7fd-132">System.Class</span><span class="sxs-lookup"><span data-stu-id="dd7fd-132">System.Class</span></span>](http://msdn.microsoft.com/en-us/fe334af5-0123-43d8-be84-26f6f023ddb6)|<span data-ttu-id="dd7fd-133">クラス インターフェイスに変換されます。</span><span class="sxs-lookup"><span data-stu-id="dd7fd-133">Converts to a class interface.</span></span>|  
|[<span data-ttu-id="dd7fd-134">System.Object</span><span class="sxs-lookup"><span data-stu-id="dd7fd-134">System.Object</span></span>](../../../docs/framework/interop/default-marshaling-for-objects.md)|<span data-ttu-id="dd7fd-135">バリアントまたはインターフェイスに変換されます。</span><span class="sxs-lookup"><span data-stu-id="dd7fd-135">Converts to a variant or an interface.</span></span>|  
|[<span data-ttu-id="dd7fd-136">System.Mdarray</span><span class="sxs-lookup"><span data-stu-id="dd7fd-136">System.Mdarray</span></span>](../../../docs/framework/interop/default-marshaling-for-arrays.md)|<span data-ttu-id="dd7fd-137">C スタイルの配列または `SAFEARRAY` に変換されます。</span><span class="sxs-lookup"><span data-stu-id="dd7fd-137">Converts to a C-style array or a `SAFEARRAY`.</span></span>|  
|[<span data-ttu-id="dd7fd-138">System.String</span><span class="sxs-lookup"><span data-stu-id="dd7fd-138">System.String</span></span>](../../../docs/framework/interop/default-marshaling-for-strings.md)|<span data-ttu-id="dd7fd-139">null 参照で終わる文字列または BSTR に変換されます。</span><span class="sxs-lookup"><span data-stu-id="dd7fd-139">Converts to a string terminating in a null reference or to a BSTR.</span></span>|  
|[<span data-ttu-id="dd7fd-140">System.Valuetype</span><span class="sxs-lookup"><span data-stu-id="dd7fd-140">System.Valuetype</span></span>](http://msdn.microsoft.com/en-us/4d9a876c-e05a-40ba-bd85-bd22877f984a)|<span data-ttu-id="dd7fd-141">固定メモリ レイアウトを持つ構造体に変換されます。</span><span class="sxs-lookup"><span data-stu-id="dd7fd-141">Converts to a structure with a fixed memory layout.</span></span>|  
|[<span data-ttu-id="dd7fd-142">System.Szarray</span><span class="sxs-lookup"><span data-stu-id="dd7fd-142">System.Szarray</span></span>](../../../docs/framework/interop/default-marshaling-for-arrays.md)|<span data-ttu-id="dd7fd-143">C スタイルの配列または `SAFEARRAY` に変換されます。</span><span class="sxs-lookup"><span data-stu-id="dd7fd-143">Converts to a C-style array or a `SAFEARRAY`.</span></span>|  
  
 <span data-ttu-id="dd7fd-144">クラス型とオブジェクト型は COM 相互運用でのみサポートされます。</span><span class="sxs-lookup"><span data-stu-id="dd7fd-144">Class and object types are supported only by COM interop.</span></span> <span data-ttu-id="dd7fd-145">[!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)]、C#、および C++ の対応する型については、「[クラス ライブラリの概要](../../../docs/standard/class-library-overview.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="dd7fd-145">For corresponding types in [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)], C#, and C++, see the [Class Library Overview](../../../docs/standard/class-library-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd7fd-146">関連項目</span><span class="sxs-lookup"><span data-stu-id="dd7fd-146">See Also</span></span>  
 [<span data-ttu-id="dd7fd-147">既定のマーシャリング動作</span><span class="sxs-lookup"><span data-stu-id="dd7fd-147">Default Marshaling Behavior</span></span>](../../../docs/framework/interop/default-marshaling-behavior.md)
