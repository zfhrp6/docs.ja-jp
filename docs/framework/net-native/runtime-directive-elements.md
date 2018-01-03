---
title: "ランタイム ディレクティブ要素"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3fe5848c-ecd7-4136-970b-8e48d250bde6
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e2566c5ebe8c94610c8f7e258da7c77adb86a49f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="runtime-directive-elements"></a><span data-ttu-id="30ff5-102">ランタイム ディレクティブ要素</span><span class="sxs-lookup"><span data-stu-id="30ff5-102">Runtime Directive Elements</span></span>
<span data-ttu-id="30ff5-103">ランタイム ディレクティブ (rd.xml) ファイル形式は、次のランタイム ディレクティブ要素をサポートします。</span><span class="sxs-lookup"><span data-stu-id="30ff5-103">The runtime directives (rd.xml) file format supports the following runtime directive elements.</span></span> <span data-ttu-id="30ff5-104">階層表現については、「[ランタイム ディレクティブ (rd.xml) 構成ファイル リファレンス](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="30ff5-104">See [Runtime Directives (rd.xml) Configuration File Reference](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md) for a hierarchical representation.</span></span>  
  
 [<span data-ttu-id="30ff5-105">\<Application></span><span class="sxs-lookup"><span data-stu-id="30ff5-105">\<Application></span></span>](../../../docs/framework/net-native/application-element-net-native.md)  
 <span data-ttu-id="30ff5-106">アプリで使用されるすべての型にランタイム リフレクション ポリシーを適用し、実行時にリフレクションに使用できるメタデータを持つアプリケーション全体の型と型のメンバーのコンテナーとして機能します。</span><span class="sxs-lookup"><span data-stu-id="30ff5-106">Applies runtime reflection policy to all types used by the app, and serves as a container for application-wide types and type members whose metadata is available for reflection at run time.</span></span> <span data-ttu-id="30ff5-107">これは、[\<Directives>](../../../docs/framework/net-native/directives-element-net-native.md) 要素の子です。</span><span class="sxs-lookup"><span data-stu-id="30ff5-107">This is a child of the [\<Directives>](../../../docs/framework/net-native/directives-element-net-native.md) element.</span></span>  
  
 [<span data-ttu-id="30ff5-108">\<Assembly></span><span class="sxs-lookup"><span data-stu-id="30ff5-108">\<Assembly></span></span>](../../../docs/framework/net-native/assembly-element-net-native.md)  
 <span data-ttu-id="30ff5-109">アセンブリ内のすべての型に実行時ポリシーを適用します。</span><span class="sxs-lookup"><span data-stu-id="30ff5-109">Applies runnntime policy to all the types in an assembly.</span></span> <span data-ttu-id="30ff5-110">これは、[\<Application>](../../../docs/framework/net-native/application-element-net-native.md) 要素と [\<Library>](../../../docs/framework/net-native/library-element-net-native.md) 要素の子です。</span><span class="sxs-lookup"><span data-stu-id="30ff5-110">This is a child of the [\<Application>](../../../docs/framework/net-native/application-element-net-native.md) and [\<Library>](../../../docs/framework/net-native/library-element-net-native.md) elements.</span></span>  
  
 [<span data-ttu-id="30ff5-111">\<AttributeImplies></span><span class="sxs-lookup"><span data-stu-id="30ff5-111">\<AttributeImplies></span></span>](../../../docs/framework/net-native/attributeimplies-element-net-native.md)  
 <span data-ttu-id="30ff5-112">それを含んでいる [\<Type>](../../../docs/framework/net-native/type-element-net-native.md) ディレクティブが属性の場合、その属性が適用されるコード要素に実行時ポリシーを適用します。</span><span class="sxs-lookup"><span data-stu-id="30ff5-112">If its containing [\<Type>](../../../docs/framework/net-native/type-element-net-native.md) directive is an attribute, applies runtime policy to code elements to which that attribute is applied.</span></span>  
  
 [<span data-ttu-id="30ff5-113">\<Directives></span><span class="sxs-lookup"><span data-stu-id="30ff5-113">\<Directives></span></span>](../../../docs/framework/net-native/directives-element-net-native.md)  
 <span data-ttu-id="30ff5-114">[!INCLUDE[net_native](../../../includes/net-native-md.md)]のすべてのランタイム ディレクティブ ファイルのルート要素です。</span><span class="sxs-lookup"><span data-stu-id="30ff5-114">The root element in every runtime directives file for [!INCLUDE[net_native](../../../includes/net-native-md.md)].</span></span> <span data-ttu-id="30ff5-115">その子要素は、[\<Application>](../../../docs/framework/net-native/application-element-net-native.md) と [\<Library>](../../../docs/framework/net-native/library-element-net-native.md) です。</span><span class="sxs-lookup"><span data-stu-id="30ff5-115">Its child elements are [\<Application>](../../../docs/framework/net-native/application-element-net-native.md) and [\<Library>](../../../docs/framework/net-native/library-element-net-native.md).</span></span>  
  
 [<span data-ttu-id="30ff5-116">\<Event></span><span class="sxs-lookup"><span data-stu-id="30ff5-116">\<Event></span></span>](../../../docs/framework/net-native/event-element-net-native.md)  
 <span data-ttu-id="30ff5-117">イベントに実行時ポリシーを適用します。</span><span class="sxs-lookup"><span data-stu-id="30ff5-117">Applies runtime policy to an event.</span></span> <span data-ttu-id="30ff5-118">これは、[\<Type>](../../../docs/framework/net-native/type-element-net-native.md) 要素と [\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) 要素の子です。</span><span class="sxs-lookup"><span data-stu-id="30ff5-118">This is a child of the [\<Type>](../../../docs/framework/net-native/type-element-net-native.md) and [\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) elements.</span></span>  
  
 [<span data-ttu-id="30ff5-119">\<Field></span><span class="sxs-lookup"><span data-stu-id="30ff5-119">\<Field></span></span>](../../../docs/framework/net-native/field-element-net-native.md)  
 <span data-ttu-id="30ff5-120">フィールドに実行時ポリシーを適用します。</span><span class="sxs-lookup"><span data-stu-id="30ff5-120">Applies runtime policy to a field.</span></span> <span data-ttu-id="30ff5-121">これは、[\<Type>](../../../docs/framework/net-native/type-element-net-native.md) 要素と [\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) 要素の子です。</span><span class="sxs-lookup"><span data-stu-id="30ff5-121">This is a child of the [\<Type>](../../../docs/framework/net-native/type-element-net-native.md) and [\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) elements.</span></span>  
  
 [<span data-ttu-id="30ff5-122">\<GenericParameter></span><span class="sxs-lookup"><span data-stu-id="30ff5-122">\<GenericParameter></span></span>](../../../docs/framework/net-native/genericparameter-element-net-native.md)  
 <span data-ttu-id="30ff5-123">ジェネリック型またはメソッドのパラメーター型に実行時ポリシーを適用します。</span><span class="sxs-lookup"><span data-stu-id="30ff5-123">Applies runtime policy to the parameter type of a generic type or method.</span></span>  
  
 [<span data-ttu-id="30ff5-124">\<ImpliesType></span><span class="sxs-lookup"><span data-stu-id="30ff5-124">\<ImpliesType></span></span>](../../../docs/framework/net-native/impliestype-element-net-native.md)  
 <span data-ttu-id="30ff5-125">型に実行時ポリシーを適用します (それを含んでいる型またはメソッドにそのポリシーが適用されている場合)。</span><span class="sxs-lookup"><span data-stu-id="30ff5-125">Applies runtime policy to a type, if that policy has been applied to the containing type or method.</span></span>  
  
 [<span data-ttu-id="30ff5-126">\<Library></span><span class="sxs-lookup"><span data-stu-id="30ff5-126">\<Library></span></span>](../../../docs/framework/net-native/library-element-net-native.md)  
 <span data-ttu-id="30ff5-127">アセンブリ内のすべての型に実行時ポリシーを適用します。</span><span class="sxs-lookup"><span data-stu-id="30ff5-127">Applies runtime policy to all the types in an assembly.</span></span> <span data-ttu-id="30ff5-128">これは、[\<Application>](../../../docs/framework/net-native/application-element-net-native.md) 要素と [\<Library>](../../../docs/framework/net-native/library-element-net-native.md) 要素の子です。</span><span class="sxs-lookup"><span data-stu-id="30ff5-128">This is a child of the [\<Application>](../../../docs/framework/net-native/application-element-net-native.md) and [\<Library>](../../../docs/framework/net-native/library-element-net-native.md) elements.</span></span>  
  
 [<span data-ttu-id="30ff5-129">\<Method></span><span class="sxs-lookup"><span data-stu-id="30ff5-129">\<Method></span></span>](../../../docs/framework/net-native/method-element-net-native.md)  
 <span data-ttu-id="30ff5-130">メソッドに実行時ポリシーを適用します。</span><span class="sxs-lookup"><span data-stu-id="30ff5-130">Applies runtime policy to a method.</span></span> <span data-ttu-id="30ff5-131">これは、[\<Type>](../../../docs/framework/net-native/type-element-net-native.md) 要素と [\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) 要素の子です。</span><span class="sxs-lookup"><span data-stu-id="30ff5-131">This is a child of the [\<Type>](../../../docs/framework/net-native/type-element-net-native.md) and [\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) elements.</span></span>  
  
 [<span data-ttu-id="30ff5-132">\<MethodInstantiation></span><span class="sxs-lookup"><span data-stu-id="30ff5-132">\<MethodInstantiation></span></span>](../../../docs/framework/net-native/methodinstantiation-element-net-native.md)  
 <span data-ttu-id="30ff5-133">構築されたジェネリック メソッドに実行時ポリシーを適用します。</span><span class="sxs-lookup"><span data-stu-id="30ff5-133">Applies runtime policy to a constructed generic method.</span></span> <span data-ttu-id="30ff5-134">これは、[\<Type>](../../../docs/framework/net-native/type-element-net-native.md) 要素と [\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) 要素の子です。</span><span class="sxs-lookup"><span data-stu-id="30ff5-134">This is a child of the [\<Type>](../../../docs/framework/net-native/type-element-net-native.md) and [\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) elements.</span></span>  
  
 [<span data-ttu-id="30ff5-135">\<Namespace></span><span class="sxs-lookup"><span data-stu-id="30ff5-135">\<Namespace></span></span>](../../../docs/framework/net-native/namespace-element-net-native.md)  
 <span data-ttu-id="30ff5-136">名前空間内のすべての型に実行時ポリシーを適用します。</span><span class="sxs-lookup"><span data-stu-id="30ff5-136">Applies runtime policy to all the types in a namespace.</span></span>  
  
 [<span data-ttu-id="30ff5-137">\<Parameter></span><span class="sxs-lookup"><span data-stu-id="30ff5-137">\<Parameter></span></span>](../../../docs/framework/net-native/parameter-element-net-native.md)  
 <span data-ttu-id="30ff5-138">メソッドに渡された引数の型に実行時ポリシーを適用します。</span><span class="sxs-lookup"><span data-stu-id="30ff5-138">Applies runtime policy to the type of the argument passed to a method.</span></span>  
  
 [<span data-ttu-id="30ff5-139">\<Property></span><span class="sxs-lookup"><span data-stu-id="30ff5-139">\<Property></span></span>](../../../docs/framework/net-native/property-element-net-native.md)  
 <span data-ttu-id="30ff5-140">プロパティに実行時ポリシーを適用します。</span><span class="sxs-lookup"><span data-stu-id="30ff5-140">Applies runtime policy to a property.</span></span> <span data-ttu-id="30ff5-141">これは、[\<Type>](../../../docs/framework/net-native/type-element-net-native.md) 要素と [\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) 要素の子です。</span><span class="sxs-lookup"><span data-stu-id="30ff5-141">This is a child of the [\<Type>](../../../docs/framework/net-native/type-element-net-native.md) and [\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) elements.</span></span>  
  
 [<span data-ttu-id="30ff5-142">\<Subtypes></span><span class="sxs-lookup"><span data-stu-id="30ff5-142">\<Subtypes></span></span>](../../../docs/framework/net-native/subtypes-element-net-native.md)  
 <span data-ttu-id="30ff5-143">それを含む型から継承されたすべてのクラスに実行時ポリシーを適用します。</span><span class="sxs-lookup"><span data-stu-id="30ff5-143">Applies runtime policy to all classes inherited from the containing type.</span></span>  
  
 [<span data-ttu-id="30ff5-144">\<Type></span><span class="sxs-lookup"><span data-stu-id="30ff5-144">\<Type></span></span>](../../../docs/framework/net-native/type-element-net-native.md)  
 <span data-ttu-id="30ff5-145">型に実行時ポリシーを適用します。</span><span class="sxs-lookup"><span data-stu-id="30ff5-145">Applies runtime policy to a type.</span></span>  
  
 [<span data-ttu-id="30ff5-146">\<TypeInstantiation></span><span class="sxs-lookup"><span data-stu-id="30ff5-146">\<TypeInstantiation></span></span>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)  
 <span data-ttu-id="30ff5-147">構築されたジェネリック型に実行時ポリシーを適用します。</span><span class="sxs-lookup"><span data-stu-id="30ff5-147">Applies runtime policy to a constructed generic type.</span></span>  
  
 [<span data-ttu-id="30ff5-148">\<TypeParameter></span><span class="sxs-lookup"><span data-stu-id="30ff5-148">\<TypeParameter></span></span>](../../../docs/framework/net-native/typeparameter-element-net-native.md)  
 <span data-ttu-id="30ff5-149">メソッドに渡された <xref:System.Type> 引数によって表される型に実行時ポリシーを適用します。</span><span class="sxs-lookup"><span data-stu-id="30ff5-149">Applies runtime policy to the type represented by a <xref:System.Type> argument passed to a method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30ff5-150">参照</span><span class="sxs-lookup"><span data-stu-id="30ff5-150">See Also</span></span>  
 [<span data-ttu-id="30ff5-151">rd.xml 構成ファイル リファレンス</span><span class="sxs-lookup"><span data-stu-id="30ff5-151">rd.xml Configuration File Reference</span></span>](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)
