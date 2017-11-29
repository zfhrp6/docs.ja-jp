---
title: "ランタイム ディレクティブ (rd.xml) 構成ファイル リファレンス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8241523f-d8e1-4fb6-bf6a-b29bfe07b38a
caps.latest.revision: "27"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2ecfc61c5b586dd3385890d73ded729a38fb41c2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="runtime-directives-rdxml-configuration-file-reference"></a><span data-ttu-id="c5d6c-102">ランタイム ディレクティブ (rd.xml) 構成ファイル リファレンス</span><span class="sxs-lookup"><span data-stu-id="c5d6c-102">Runtime Directives (rd.xml) Configuration File Reference</span></span>
<span data-ttu-id="c5d6c-103">ランタイム ディレクティブ (.rd.xml) ファイルは、指定されたプログラム要素をリフレクションに使用できるかどうかを示す XML 構成ファイルです。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-103">A runtime directives (.rd.xml) file is an XML configuration file that specifies whether designated program elements are available for reflection.</span></span> <span data-ttu-id="c5d6c-104">ランタイム ディレクティブ ファイルの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-104">Here’s an example of a runtime directives file:</span></span>  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
<Application>  
  <Namespace Name="Contoso.Cloud.AppServices" Serialize="Required Public" />  
  <Namespace Name="ContosoClient.ViewModels" Serialize="Required Public" />  
  <Namespace Name="ContosoClient.DataModel" Serialize="Required Public" />  
  <Namespace Name="Contoso.Reader.UtilityLib" Serialize="Required Public" />  
  
  <Namespace Name="System.Collections.ObjectModel" >  
    <TypeInstantiation Name="ObservableCollection"   
          Arguments="ContosoClient.DataModel.ProductItem" Serialize="Public" />  
    <TypeInstantiation Name="ReadOnlyObservableCollection"   
          Arguments="ContosoClient.DataModel.ProductGroup" Serialize="Public" />  
  </Namespace>  
</Application>  
</Directives>  
```  
  
## <a name="the-structure-of-a-runtime-directives-file"></a><span data-ttu-id="c5d6c-105">ランタイム ディレクティブ ファイルの構造</span><span class="sxs-lookup"><span data-stu-id="c5d6c-105">The structure of a runtime directives file</span></span>  
 <span data-ttu-id="c5d6c-106">ランタイム ディレクティブ ファイルは `http://schemas.microsoft.com/netfx/2013/01/metadata` 名前空間を使用します。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-106">The runtime directives file uses the `http://schemas.microsoft.com/netfx/2013/01/metadata` namespace.</span></span>  
  
 <span data-ttu-id="c5d6c-107">ルート要素は [Directives](../../../docs/framework/net-native/directives-element-net-native.md) 要素です。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-107">The root element is the [Directives](../../../docs/framework/net-native/directives-element-net-native.md) element.</span></span> <span data-ttu-id="c5d6c-108">これには、次の構造に示すように、0 個以上の [Library](../../../docs/framework/net-native/library-element-net-native.md) 要素と 0 または 1 個の [Application](../../../docs/framework/net-native/application-element-net-native.md) 要素を含めることができます。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-108">It can contain zero or more [Library](../../../docs/framework/net-native/library-element-net-native.md) elements, and zero or one [Application](../../../docs/framework/net-native/application-element-net-native.md) element, as shown in the following structure.</span></span> <span data-ttu-id="c5d6c-109">[Application](../../../docs/framework/net-native/application-element-net-native.md) 要素の属性は、アプリケーション全体のランタイム リフレクション ポリシーを定義できるか、子要素のコンテナーとして機能できます。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-109">The attributes of the [Application](../../../docs/framework/net-native/application-element-net-native.md) element can define application-wide runtime reflection policy, or it can serve as a container for child elements.</span></span> <span data-ttu-id="c5d6c-110">一方、[Library](../../../docs/framework/net-native/library-element-net-native.md) 要素は単にコンテナーです。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-110">The [Library](../../../docs/framework/net-native/library-element-net-native.md) element, on the other hand, is simply a container.</span></span> <span data-ttu-id="c5d6c-111">[Application](../../../docs/framework/net-native/application-element-net-native.md) 要素と [Library](../../../docs/framework/net-native/library-element-net-native.md) 要素の子は、リフレクションで使用できる型、メソッド、フィールド、プロパティ、およびイベントを定義します。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-111">The children of the [Application](../../../docs/framework/net-native/application-element-net-native.md) and [Library](../../../docs/framework/net-native/library-element-net-native.md) elements define the types, methods, fields, properties, and events that are available for reflection.</span></span>  
  
 <span data-ttu-id="c5d6c-112">参照情報については、次の構造から要素を選択するか、「[ランタイム ディレクティブ要素](../../../docs/framework/net-native/runtime-directive-elements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-112">For reference information, choose elements from the following structure or see [Runtime Directive Elements](../../../docs/framework/net-native/runtime-directive-elements.md).</span></span> <span data-ttu-id="c5d6c-113">次の階層で、省略記号は再帰構造を示します。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-113">In the following hierarchy, the ellipsis marks a recursive structure.</span></span> <span data-ttu-id="c5d6c-114">角かっこ内の情報は、その要素が省略可能または必須のいずれであるか、および使用される場合に許可されるインスタンスの数 (1 つまたは複数) を示します。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-114">The information in brackets indicates whether that element is optional or required, and if it is used, how many instances (one or many) are allowed.</span></span>  
  
 <span data-ttu-id="c5d6c-115">[Directives](../../../docs/framework/net-native/directives-element-net-native.md) [1:1]</span><span class="sxs-lookup"><span data-stu-id="c5d6c-115">[Directives](../../../docs/framework/net-native/directives-element-net-native.md) [1:1]</span></span>  
 <span data-ttu-id="c5d6c-116">[Application](../../../docs/framework/net-native/application-element-net-native.md) [0:1]</span><span class="sxs-lookup"><span data-stu-id="c5d6c-116">[Application](../../../docs/framework/net-native/application-element-net-native.md) [0:1]</span></span>  
 <span data-ttu-id="c5d6c-117">[Assembly](../../../docs/framework/net-native/assembly-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="c5d6c-117">[Assembly](../../../docs/framework/net-native/assembly-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="c5d6c-118">[Namespace](../../../docs/framework/net-native/namespace-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="c5d6c-118">[Namespace](../../../docs/framework/net-native/namespace-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="c5d6c-119">。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-119">.</span></span> <span data-ttu-id="c5d6c-120">です。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-120">.</span></span> <span data-ttu-id="c5d6c-121">。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-121">.</span></span>  
 <span data-ttu-id="c5d6c-122">[Type](../../../docs/framework/net-native/type-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="c5d6c-122">[Type](../../../docs/framework/net-native/type-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="c5d6c-123">。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-123">.</span></span> <span data-ttu-id="c5d6c-124">です。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-124">.</span></span> <span data-ttu-id="c5d6c-125">。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-125">.</span></span>  
 <span data-ttu-id="c5d6c-126">[TypeInstantiation](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) (構築されたジェネリック型) [0:M]</span><span class="sxs-lookup"><span data-stu-id="c5d6c-126">[TypeInstantiation](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) (constructed generic type) [0:M]</span></span>  
 <span data-ttu-id="c5d6c-127">。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-127">.</span></span> <span data-ttu-id="c5d6c-128">です。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-128">.</span></span> <span data-ttu-id="c5d6c-129">。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-129">.</span></span>  
 <span data-ttu-id="c5d6c-130">[Namespace](../../../docs/framework/net-native/namespace-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="c5d6c-130">[Namespace](../../../docs/framework/net-native/namespace-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="c5d6c-131">[Namespace](../../../docs/framework/net-native/namespace-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="c5d6c-131">[Namespace](../../../docs/framework/net-native/namespace-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="c5d6c-132">。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-132">.</span></span> <span data-ttu-id="c5d6c-133">です。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-133">.</span></span> <span data-ttu-id="c5d6c-134">。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-134">.</span></span>  
 <span data-ttu-id="c5d6c-135">[Type](../../../docs/framework/net-native/type-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="c5d6c-135">[Type](../../../docs/framework/net-native/type-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="c5d6c-136">。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-136">.</span></span> <span data-ttu-id="c5d6c-137">です。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-137">.</span></span> <span data-ttu-id="c5d6c-138">。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-138">.</span></span>  
 <span data-ttu-id="c5d6c-139">[TypeInstantiation](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) (構築されたジェネリック型) [0:M]</span><span class="sxs-lookup"><span data-stu-id="c5d6c-139">[TypeInstantiation](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) (constructed generic type) [0:M]</span></span>  
 <span data-ttu-id="c5d6c-140">。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-140">.</span></span> <span data-ttu-id="c5d6c-141">です。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-141">.</span></span> <span data-ttu-id="c5d6c-142">。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-142">.</span></span>  
 <span data-ttu-id="c5d6c-143">[Type](../../../docs/framework/net-native/type-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="c5d6c-143">[Type](../../../docs/framework/net-native/type-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="c5d6c-144">[Subtypes](../../../docs/framework/net-native/subtypes-element-net-native.md) (それを含む型のサブクラス) [O:1]</span><span class="sxs-lookup"><span data-stu-id="c5d6c-144">[Subtypes](../../../docs/framework/net-native/subtypes-element-net-native.md) (subclasses of the containing type) [O:1]</span></span>  
 <span data-ttu-id="c5d6c-145">[Type](../../../docs/framework/net-native/type-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="c5d6c-145">[Type](../../../docs/framework/net-native/type-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="c5d6c-146">。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-146">.</span></span> <span data-ttu-id="c5d6c-147">です。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-147">.</span></span> <span data-ttu-id="c5d6c-148">。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-148">.</span></span>  
 <span data-ttu-id="c5d6c-149">[TypeInstantiation](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) (構築されたジェネリック型) [0:M]</span><span class="sxs-lookup"><span data-stu-id="c5d6c-149">[TypeInstantiation](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) (constructed generic type) [0:M]</span></span>  
 <span data-ttu-id="c5d6c-150">。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-150">.</span></span> <span data-ttu-id="c5d6c-151">です。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-151">.</span></span> <span data-ttu-id="c5d6c-152">。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-152">.</span></span>  
 <span data-ttu-id="c5d6c-153">[AttributeImplies](../../../docs/framework/net-native/attributeimplies-element-net-native.md) (それを含む型が属性) [O:1]</span><span class="sxs-lookup"><span data-stu-id="c5d6c-153">[AttributeImplies](../../../docs/framework/net-native/attributeimplies-element-net-native.md) (containing type is an attribute) [O:1]</span></span>  
 <span data-ttu-id="c5d6c-154">[GenericParameter](../../../docs/framework/net-native/genericparameter-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="c5d6c-154">[GenericParameter](../../../docs/framework/net-native/genericparameter-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="c5d6c-155">[Method](../../../docs/framework/net-native/method-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="c5d6c-155">[Method](../../../docs/framework/net-native/method-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="c5d6c-156">[Parameter](../../../docs/framework/net-native/parameter-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="c5d6c-156">[Parameter](../../../docs/framework/net-native/parameter-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="c5d6c-157">[TypeParameter](../../../docs/framework/net-native/typeparameter-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="c5d6c-157">[TypeParameter](../../../docs/framework/net-native/typeparameter-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="c5d6c-158">[GenericParameter](../../../docs/framework/net-native/genericparameter-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="c5d6c-158">[GenericParameter](../../../docs/framework/net-native/genericparameter-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="c5d6c-159">[MethodInstantiation](../../../docs/framework/net-native/methodinstantiation-element-net-native.md) (構築されたジェネリック メソッド) [0:M]</span><span class="sxs-lookup"><span data-stu-id="c5d6c-159">[MethodInstantiation](../../../docs/framework/net-native/methodinstantiation-element-net-native.md) (constructed generic method) [0:M]</span></span>  
 <span data-ttu-id="c5d6c-160">[Property](../../../docs/framework/net-native/property-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="c5d6c-160">[Property](../../../docs/framework/net-native/property-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="c5d6c-161">[Field](../../../docs/framework/net-native/field-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="c5d6c-161">[Field](../../../docs/framework/net-native/field-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="c5d6c-162">[Event](../../../docs/framework/net-native/event-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="c5d6c-162">[Event](../../../docs/framework/net-native/event-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="c5d6c-163">[TypeInstantiation](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) (構築されたジェネリック型) [0:M]</span><span class="sxs-lookup"><span data-stu-id="c5d6c-163">[TypeInstantiation](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) (constructed generic type) [0:M]</span></span>  
 <span data-ttu-id="c5d6c-164">[Type](../../../docs/framework/net-native/type-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="c5d6c-164">[Type](../../../docs/framework/net-native/type-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="c5d6c-165">。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-165">.</span></span> <span data-ttu-id="c5d6c-166">です。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-166">.</span></span> <span data-ttu-id="c5d6c-167">。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-167">.</span></span>  
 <span data-ttu-id="c5d6c-168">[TypeInstantiation](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) (構築されたジェネリック型) [0:M]</span><span class="sxs-lookup"><span data-stu-id="c5d6c-168">[TypeInstantiation](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) (constructed generic type) [0:M]</span></span>  
 <span data-ttu-id="c5d6c-169">。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-169">.</span></span> <span data-ttu-id="c5d6c-170">です。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-170">.</span></span> <span data-ttu-id="c5d6c-171">。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-171">.</span></span>  
 <span data-ttu-id="c5d6c-172">[Method](../../../docs/framework/net-native/method-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="c5d6c-172">[Method](../../../docs/framework/net-native/method-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="c5d6c-173">[Parameter](../../../docs/framework/net-native/parameter-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="c5d6c-173">[Parameter](../../../docs/framework/net-native/parameter-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="c5d6c-174">[TypeParameter](../../../docs/framework/net-native/typeparameter-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="c5d6c-174">[TypeParameter](../../../docs/framework/net-native/typeparameter-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="c5d6c-175">[GenericParameter](../../../docs/framework/net-native/genericparameter-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="c5d6c-175">[GenericParameter](../../../docs/framework/net-native/genericparameter-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="c5d6c-176">[MethodInstantiation](../../../docs/framework/net-native/methodinstantiation-element-net-native.md) (構築されたジェネリック メソッド) [0:M]</span><span class="sxs-lookup"><span data-stu-id="c5d6c-176">[MethodInstantiation](../../../docs/framework/net-native/methodinstantiation-element-net-native.md) (constructed generic method) [0:M]</span></span>  
 <span data-ttu-id="c5d6c-177">[Property](../../../docs/framework/net-native/property-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="c5d6c-177">[Property](../../../docs/framework/net-native/property-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="c5d6c-178">[Field](../../../docs/framework/net-native/field-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="c5d6c-178">[Field](../../../docs/framework/net-native/field-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="c5d6c-179">[Event](../../../docs/framework/net-native/event-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="c5d6c-179">[Event](../../../docs/framework/net-native/event-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="c5d6c-180">[Library](../../../docs/framework/net-native/library-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="c5d6c-180">[Library](../../../docs/framework/net-native/library-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="c5d6c-181">[Assembly](../../../docs/framework/net-native/assembly-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="c5d6c-181">[Assembly](../../../docs/framework/net-native/assembly-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="c5d6c-182">[Namespace](../../../docs/framework/net-native/namespace-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="c5d6c-182">[Namespace](../../../docs/framework/net-native/namespace-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="c5d6c-183">。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-183">.</span></span> <span data-ttu-id="c5d6c-184">です。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-184">.</span></span> <span data-ttu-id="c5d6c-185">。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-185">.</span></span>  
 <span data-ttu-id="c5d6c-186">[Type](../../../docs/framework/net-native/type-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="c5d6c-186">[Type](../../../docs/framework/net-native/type-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="c5d6c-187">。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-187">.</span></span> <span data-ttu-id="c5d6c-188">です。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-188">.</span></span> <span data-ttu-id="c5d6c-189">。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-189">.</span></span>  
 <span data-ttu-id="c5d6c-190">[TypeInstantiation](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) (構築されたジェネリック型) [0:M]</span><span class="sxs-lookup"><span data-stu-id="c5d6c-190">[TypeInstantiation](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) (constructed generic type) [0:M]</span></span>  
 <span data-ttu-id="c5d6c-191">。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-191">.</span></span> <span data-ttu-id="c5d6c-192">です。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-192">.</span></span> <span data-ttu-id="c5d6c-193">。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-193">.</span></span>  
 <span data-ttu-id="c5d6c-194">[Namespace](../../../docs/framework/net-native/namespace-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="c5d6c-194">[Namespace](../../../docs/framework/net-native/namespace-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="c5d6c-195">[Namespace](../../../docs/framework/net-native/namespace-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="c5d6c-195">[Namespace](../../../docs/framework/net-native/namespace-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="c5d6c-196">。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-196">.</span></span> <span data-ttu-id="c5d6c-197">です。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-197">.</span></span> <span data-ttu-id="c5d6c-198">。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-198">.</span></span>  
 <span data-ttu-id="c5d6c-199">[Type](../../../docs/framework/net-native/type-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="c5d6c-199">[Type](../../../docs/framework/net-native/type-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="c5d6c-200">。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-200">.</span></span> <span data-ttu-id="c5d6c-201">です。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-201">.</span></span> <span data-ttu-id="c5d6c-202">。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-202">.</span></span>  
 <span data-ttu-id="c5d6c-203">[TypeInstantiation](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) (構築されたジェネリック型) [0:M]</span><span class="sxs-lookup"><span data-stu-id="c5d6c-203">[TypeInstantiation](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) (constructed generic type) [0:M]</span></span>  
 <span data-ttu-id="c5d6c-204">。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-204">.</span></span> <span data-ttu-id="c5d6c-205">です。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-205">.</span></span> <span data-ttu-id="c5d6c-206">。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-206">.</span></span>  
 <span data-ttu-id="c5d6c-207">[Type](../../../docs/framework/net-native/type-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="c5d6c-207">[Type](../../../docs/framework/net-native/type-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="c5d6c-208">[Subtypes](../../../docs/framework/net-native/subtypes-element-net-native.md) (それを含む型のサブクラス) [O:1]</span><span class="sxs-lookup"><span data-stu-id="c5d6c-208">[Subtypes](../../../docs/framework/net-native/subtypes-element-net-native.md) (subclasses of the containing type) [O:1]</span></span>  
 <span data-ttu-id="c5d6c-209">[Type](../../../docs/framework/net-native/type-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="c5d6c-209">[Type](../../../docs/framework/net-native/type-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="c5d6c-210">。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-210">.</span></span> <span data-ttu-id="c5d6c-211">です。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-211">.</span></span> <span data-ttu-id="c5d6c-212">。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-212">.</span></span>  
 <span data-ttu-id="c5d6c-213">[TypeInstantiation](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) (構築されたジェネリック型) [0:M]</span><span class="sxs-lookup"><span data-stu-id="c5d6c-213">[TypeInstantiation](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) (constructed generic type) [0:M]</span></span>  
 <span data-ttu-id="c5d6c-214">。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-214">.</span></span> <span data-ttu-id="c5d6c-215">です。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-215">.</span></span> <span data-ttu-id="c5d6c-216">。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-216">.</span></span>  
 <span data-ttu-id="c5d6c-217">[AttributeImplies](../../../docs/framework/net-native/attributeimplies-element-net-native.md) (それを含む型が属性) [O:1]</span><span class="sxs-lookup"><span data-stu-id="c5d6c-217">[AttributeImplies](../../../docs/framework/net-native/attributeimplies-element-net-native.md) (containing type is an attribute) [O:1]</span></span>  
 <span data-ttu-id="c5d6c-218">[GenericParameter](../../../docs/framework/net-native/genericparameter-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="c5d6c-218">[GenericParameter](../../../docs/framework/net-native/genericparameter-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="c5d6c-219">[Method](../../../docs/framework/net-native/method-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="c5d6c-219">[Method](../../../docs/framework/net-native/method-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="c5d6c-220">[MethodInstantiation](../../../docs/framework/net-native/methodinstantiation-element-net-native.md) (構築されたジェネリック メソッド) [0:M]</span><span class="sxs-lookup"><span data-stu-id="c5d6c-220">[MethodInstantiation](../../../docs/framework/net-native/methodinstantiation-element-net-native.md) (constructed generic method) [0:M]</span></span>  
 <span data-ttu-id="c5d6c-221">[Property](../../../docs/framework/net-native/property-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="c5d6c-221">[Property](../../../docs/framework/net-native/property-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="c5d6c-222">[Field](../../../docs/framework/net-native/field-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="c5d6c-222">[Field](../../../docs/framework/net-native/field-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="c5d6c-223">[Event](../../../docs/framework/net-native/event-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="c5d6c-223">[Event](../../../docs/framework/net-native/event-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="c5d6c-224">[TypeInstantiation](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) (構築されたジェネリック型) [0:M]</span><span class="sxs-lookup"><span data-stu-id="c5d6c-224">[TypeInstantiation](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) (constructed generic type) [0:M]</span></span>  
 <span data-ttu-id="c5d6c-225">[Type](../../../docs/framework/net-native/type-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="c5d6c-225">[Type](../../../docs/framework/net-native/type-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="c5d6c-226">。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-226">.</span></span> <span data-ttu-id="c5d6c-227">です。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-227">.</span></span> <span data-ttu-id="c5d6c-228">。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-228">.</span></span>  
 <span data-ttu-id="c5d6c-229">[TypeInstantiation](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) (構築されたジェネリック型) [0:M]</span><span class="sxs-lookup"><span data-stu-id="c5d6c-229">[TypeInstantiation](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) (constructed generic type) [0:M]</span></span>  
 <span data-ttu-id="c5d6c-230">。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-230">.</span></span> <span data-ttu-id="c5d6c-231">です。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-231">.</span></span> <span data-ttu-id="c5d6c-232">。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-232">.</span></span>  
 <span data-ttu-id="c5d6c-233">[Method](../../../docs/framework/net-native/method-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="c5d6c-233">[Method](../../../docs/framework/net-native/method-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="c5d6c-234">[MethodInstantiation](../../../docs/framework/net-native/methodinstantiation-element-net-native.md) (構築されたジェネリック メソッド) [0:M]</span><span class="sxs-lookup"><span data-stu-id="c5d6c-234">[MethodInstantiation](../../../docs/framework/net-native/methodinstantiation-element-net-native.md) (constructed generic method) [0:M]</span></span>  
 <span data-ttu-id="c5d6c-235">[Property](../../../docs/framework/net-native/property-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="c5d6c-235">[Property](../../../docs/framework/net-native/property-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="c5d6c-236">[Field](../../../docs/framework/net-native/field-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="c5d6c-236">[Field](../../../docs/framework/net-native/field-element-net-native.md) [0:M]</span></span>  
 <span data-ttu-id="c5d6c-237">[Event](../../../docs/framework/net-native/event-element-net-native.md) [0:M]</span><span class="sxs-lookup"><span data-stu-id="c5d6c-237">[Event](../../../docs/framework/net-native/event-element-net-native.md) [0:M]</span></span>  
  
 <span data-ttu-id="c5d6c-238">[Application](../../../docs/framework/net-native/application-element-net-native.md) 要素は属性を持たないか、「[ランタイム ディレクティブとポリシー](#Directives)」セクションで説明しているポリシー属性を持つことができます。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-238">The [Application](../../../docs/framework/net-native/application-element-net-native.md) element can have no attributes, or it can have the policy attributes discussed in the [Runtime directive and policy section](#Directives).</span></span>  
  
 <span data-ttu-id="c5d6c-239">[Library](../../../docs/framework/net-native/library-element-net-native.md) 要素は、ライブラリまたはアセンブリの名前をファイル拡張子なしで指定する、`Name` 属性 1 つを持ちます。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-239">A [Library](../../../docs/framework/net-native/library-element-net-native.md) element has a single attribute, `Name`, that specifies the name of a library or assembly, without its file extension.</span></span> <span data-ttu-id="c5d6c-240">たとえば、次の [Library](../../../docs/framework/net-native/library-element-net-native.md) 要素は、Extensions.dll という名前のアセンブリに適用されます。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-240">For example, the following [Library](../../../docs/framework/net-native/library-element-net-native.md) element applies to an assembly named Extensions.dll.</span></span>  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
  <Application>  
     <!-- Child elements go here -->    
  </Application>  
  <Library Name="Extensions">  
     <!-- Child elements go here -->    
  </Library>  
</Directives>  
```  
  
<a name="Directives"></a>   
## <a name="runtime-directives-and-policy"></a><span data-ttu-id="c5d6c-241">ランタイム ディレクティブとポリシー</span><span class="sxs-lookup"><span data-stu-id="c5d6c-241">Runtime directives and policy</span></span>  
 <span data-ttu-id="c5d6c-242">[Application](../../../docs/framework/net-native/application-element-net-native.md) 要素自体と [Library](../../../docs/framework/net-native/library-element-net-native.md) 要素と [Application](../../../docs/framework/net-native/application-element-net-native.md) 要素の子要素はポリシーを表します。つまり、アプリがプログラム要素にリフレクションを適用できる方法を定義します。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-242">The [Application](../../../docs/framework/net-native/application-element-net-native.md) element itself and the child elements of the [Library](../../../docs/framework/net-native/library-element-net-native.md) and [Application](../../../docs/framework/net-native/application-element-net-native.md) elements express policy; that is, they define the way in which an app can apply reflection to a program element.</span></span> <span data-ttu-id="c5d6c-243">ポリシーの種類は要素の属性 (たとえば、`Serialize`) により定義されます。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-243">The policy type is defined by an attribute of the element (for example, `Serialize`).</span></span> <span data-ttu-id="c5d6c-244">ポリシーの値は属性の値 (たとえば、`Serialize="Required"`) により定義されます。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-244">The policy value is defined by the attribute’s value (for example, `Serialize="Required"`).</span></span>  
  
 <span data-ttu-id="c5d6c-245">要素の属性により指定されるすべてのポリシーは、そのポリシーの値を指定しないすべての子要素に適用されます。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-245">Any policy specified by an attribute of an element applies to all child elements that don’t specify a value for that policy.</span></span> <span data-ttu-id="c5d6c-246">たとえば、[Type](../../../docs/framework/net-native/type-element-net-native.md) 要素で指定されたポリシーは、ポリシーが明示的に指定されていない、その要素に含まれる型とメンバーすべてに適用されます。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-246">For example, if a policy is specified by a [Type](../../../docs/framework/net-native/type-element-net-native.md) element, that policy applies to all contained types and members for which a policy is not explicitly specified.</span></span>  
  
 <span data-ttu-id="c5d6c-247">[Application](../../../docs/framework/net-native/application-element-net-native.md)、[Assembly](../../../docs/framework/net-native/assembly-element-net-native.md)、[AttributeImplies](../../../docs/framework/net-native/attributeimplies-element-net-native.md)、[Namespace](../../../docs/framework/net-native/namespace-element-net-native.md)、[Subtypes](../../../docs/framework/net-native/subtypes-element-net-native.md)、および [Type](../../../docs/framework/net-native/type-element-net-native.md) 要素で表すことができるポリシーは、個々のメンバーについて ([Method](../../../docs/framework/net-native/method-element-net-native.md)、[Property](../../../docs/framework/net-native/property-element-net-native.md)、[Field](../../../docs/framework/net-native/field-element-net-native.md)、および [Event](../../../docs/framework/net-native/event-element-net-native.md) 要素で) 表すことができるポリシーとは異なります。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-247">The policy that can be expressed by the [Application](../../../docs/framework/net-native/application-element-net-native.md), [Assembly](../../../docs/framework/net-native/assembly-element-net-native.md), [AttributeImplies](../../../docs/framework/net-native/attributeimplies-element-net-native.md), [Namespace](../../../docs/framework/net-native/namespace-element-net-native.md), [Subtypes](../../../docs/framework/net-native/subtypes-element-net-native.md), and [Type](../../../docs/framework/net-native/type-element-net-native.md) elements differs from the policy that can be expressed for individual members (by the [Method](../../../docs/framework/net-native/method-element-net-native.md), [Property](../../../docs/framework/net-native/property-element-net-native.md), [Field](../../../docs/framework/net-native/field-element-net-native.md), and [Event](../../../docs/framework/net-native/event-element-net-native.md) elements).</span></span>  
  
### <a name="specifying-policy-for-assemblies-namespaces-and-types"></a><span data-ttu-id="c5d6c-248">アセンブリ、名前空間、型に対するポリシーの指定</span><span class="sxs-lookup"><span data-stu-id="c5d6c-248">Specifying policy for assemblies, namespaces, and types</span></span>  
 <span data-ttu-id="c5d6c-249">[Application](../../../docs/framework/net-native/application-element-net-native.md)、[Assembly](../../../docs/framework/net-native/assembly-element-net-native.md)、[AttributeImplies](../../../docs/framework/net-native/attributeimplies-element-net-native.md)、[Namespace](../../../docs/framework/net-native/namespace-element-net-native.md)、[Subtypes](../../../docs/framework/net-native/subtypes-element-net-native.md)、および [Type](../../../docs/framework/net-native/type-element-net-native.md) 要素は、次のポリシーの種類をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-249">The [Application](../../../docs/framework/net-native/application-element-net-native.md), [Assembly](../../../docs/framework/net-native/assembly-element-net-native.md), [AttributeImplies](../../../docs/framework/net-native/attributeimplies-element-net-native.md), [Namespace](../../../docs/framework/net-native/namespace-element-net-native.md), [Subtypes](../../../docs/framework/net-native/subtypes-element-net-native.md), and [Type](../../../docs/framework/net-native/type-element-net-native.md) elements support the following policy types:</span></span>  
  
-   <span data-ttu-id="c5d6c-250">`Activate`。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-250">`Activate`.</span></span> <span data-ttu-id="c5d6c-251">コンストラクターへの実行時アクセスを制御して、インスタンスのアクティブ化を有効にします。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-251">Controls runtime access to constructors, to enable activation of instances.</span></span>  
  
-   <span data-ttu-id="c5d6c-252">`Browse`。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-252">`Browse`.</span></span> <span data-ttu-id="c5d6c-253">プログラム要素に関する情報の照会を制御しますが、実行時アクセスは有効にしません。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-253">Controls querying for information about program elements but does not enable any runtime access.</span></span>  
  
-   <span data-ttu-id="c5d6c-254">`Dynamic`。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-254">`Dynamic`.</span></span> <span data-ttu-id="c5d6c-255">コンストラクター、メソッド、フィールド、プロパティ、およびイベントを含むすべての型のメンバーへの実行時アクセスを制御して、動的プログラミングを有効にします。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-255">Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span>  
  
-   <span data-ttu-id="c5d6c-256">`Serialize`。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-256">`Serialize`.</span></span> <span data-ttu-id="c5d6c-257">コンストラクター、フィールド、およびプロパティへの実行時アクセスを制御し、Newtonsoft の JSON シリアライザーなどのサードパーティ ライブラリによって型インスタンスをシリアル化および逆シリアル化できるようにします。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-257">Controls runtime access to constructors, fields, and properties, to enable type instances to be serialized and serialized by third-party libraries such as the Newtonsoft JSON serializer.</span></span>  
  
-   <span data-ttu-id="c5d6c-258">`DataContractSerializer`。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-258">`DataContractSerializer`.</span></span> <span data-ttu-id="c5d6c-259"><xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> クラスを使用するシリアル化のポリシーを制御します。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-259">Controls policy for serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>  
  
-   <span data-ttu-id="c5d6c-260">`DataContractJsonSerializer`。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-260">`DataContractJsonSerializer`.</span></span> <span data-ttu-id="c5d6c-261"><xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> クラスを使用する JSON シリアル化のポリシーを制御します。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-261">Controls policy for JSON serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>  
  
-   <span data-ttu-id="c5d6c-262">`XmlSerializer`。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-262">`XmlSerializer`.</span></span> <span data-ttu-id="c5d6c-263"><xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> クラスを使用する XML シリアル化のポリシーを制御します。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-263">Controls policy for XML serialization that uses the <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> class.</span></span>  
  
-   <span data-ttu-id="c5d6c-264">`MarshalObject`。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-264">`MarshalObject`.</span></span> <span data-ttu-id="c5d6c-265">WinRT と COM に参照型をマーシャリングするためのポリシーを制御します。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-265">Controls policy for marshaling reference types to WinRT and COM.</span></span>  
  
-   <span data-ttu-id="c5d6c-266">`MarshalDelegate`。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-266">`MarshalDelegate`.</span></span> <span data-ttu-id="c5d6c-267">ネイティブ コードへの関数ポインターとしてデリゲート型をマーシャリングするためのポリシーを制御します。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-267">Controls policy for marshaling delegate types as function pointers to native code.</span></span>  
  
-   <span data-ttu-id="c5d6c-268">`MarshalStructure` .</span><span class="sxs-lookup"><span data-stu-id="c5d6c-268">`MarshalStructure` .</span></span> <span data-ttu-id="c5d6c-269">ネイティブ コードに構造体をマーシャリングするためのポリシーを制御します。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-269">Controls policy for marshaling structures to native code.</span></span>  
  
 <span data-ttu-id="c5d6c-270">これらのポリシーの種類に関連付けられている設定を次に示します。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-270">The settings associated with these policy types are:</span></span>  
  
-   <span data-ttu-id="c5d6c-271">`All`。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-271">`All`.</span></span> <span data-ttu-id="c5d6c-272">ツール チェーンが削除しないすべての型とメンバーに対するポリシーを有効にします。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-272">Enable the policy for all types and members that the tool chain does not remove.</span></span>  
  
-   <span data-ttu-id="c5d6c-273">`Auto`。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-273">`Auto`.</span></span> <span data-ttu-id="c5d6c-274">既定の動作を使用します。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-274">Use the default behavior.</span></span> <span data-ttu-id="c5d6c-275">(親要素などによってポリシーがオーバーライドされない限り、ポリシーを指定しないことは、そのポリシーを `Auto` に設定することと同じです。)</span><span class="sxs-lookup"><span data-stu-id="c5d6c-275">(Not specifying a policy is equivalent to setting that policy to `Auto` unless that policy is overridden, for example by a parent element.)</span></span>  
  
-   <span data-ttu-id="c5d6c-276">`Excluded`。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-276">`Excluded`.</span></span> <span data-ttu-id="c5d6c-277">プログラム要素のポリシーを無効にします。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-277">Disable the policy for the program element.</span></span>  
  
-   <span data-ttu-id="c5d6c-278">`Public`。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-278">`Public`.</span></span> <span data-ttu-id="c5d6c-279">ツール チェーンがメンバーが不要なために削除すると判断した場合を除き、パブリック型またはメンバーのポリシーを有効にします。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-279">Enable the policy for public types or members unless the tool chain determines that the member is unnecessary and therefore removes it.</span></span> <span data-ttu-id="c5d6c-280">(後者の場合は、`Required Public` を使用して、メンバーが保持されており、リフレクション機能があることを確認する必要があります。)</span><span class="sxs-lookup"><span data-stu-id="c5d6c-280">(In the latter case, you must use `Required Public` to ensure that the member is kept and has reflection capabilities.)</span></span>  
  
-   <span data-ttu-id="c5d6c-281">`PublicAndInternal`。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-281">`PublicAndInternal`.</span></span> <span data-ttu-id="c5d6c-282">パブリックおよび内部型またはメンバーがツール チェーンによって削除されていない場合、それらのポリシーを有効にします。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-282">Enable the policy for public and internal types or members if the tool chain doesn't remove them.</span></span>  
  
-   <span data-ttu-id="c5d6c-283">`Required Public`。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-283">`Required Public`.</span></span> <span data-ttu-id="c5d6c-284">使用されているかどうかに関係なく、パブリック型とメンバーを保持し、それらのポリシーを有効にするためにツール チェーンを要求します。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-284">Require the tool chain to keep public types and members whether or not they are used, and enable the policy for them.</span></span>  
  
-   <span data-ttu-id="c5d6c-285">`Required PublicAndInternal`。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-285">`Required PublicAndInternal`.</span></span> <span data-ttu-id="c5d6c-286">使用されているかどうかに関係なく、パブリックおよび内部両方の型とメンバーを保持し、それらのポリシーを有効にするためにツール チェーンを要求します。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-286">Require the tool chain to keep both public and internal types and members whether or not they are used, and enable the policy for them.</span></span>  
  
-   <span data-ttu-id="c5d6c-287">`Required All`。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-287">`Required All`.</span></span> <span data-ttu-id="c5d6c-288">使用されているかどうかに関係なく、すべての型とメンバーを保持し、それらのポリシーを有効にするために、ツール チェーンを要求します。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-288">Require the tool chain to keep all types and members whether or not they are used, and enable the policy for them.</span></span>  
  
 <span data-ttu-id="c5d6c-289">たとえば、次のランタイム ディレクティブ ファイルは、DataClasses.dll アセンブリ内のすべての型とメンバーのポリシーを定義します。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-289">For example, the following runtime directives file defines policy for all types and members in the assembly DataClasses.dll.</span></span> <span data-ttu-id="c5d6c-290">これは、すべてのパブリック プロパティのシリアル化のリフレクションを有効にし、すべての型と型のメンバーの参照を有効にし、すべての型のアクティブ化を (`Dynamic` 属性により) 有効にして、すべてのパブリック型とメンバーのリフレクションを有効にします。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-290">It enables reflection for serialization of all public properties, enables browsing for all types and type members, enables activation for all types (because of the `Dynamic` attribute), and enables reflection for all public types and members.</span></span>  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
   <Application>  
      <Assembly Name="DataClasses" Serialize="Required Public"   
                Browse="All" Activate="PublicAndInternal"   
                Dynamic="Public"  />  
   </Application>  
   <Library Name="UtilityLibrary">  
     <!-- Child elements go here -->    
   </Library>  
</Directives>  
```  
  
### <a name="specifying-policy-for-members"></a><span data-ttu-id="c5d6c-291">メンバーのポリシーの指定</span><span class="sxs-lookup"><span data-stu-id="c5d6c-291">Specifying policy for members</span></span>  
 <span data-ttu-id="c5d6c-292">[Property](../../../docs/framework/net-native/property-element-net-native.md) 要素と [Field](../../../docs/framework/net-native/field-element-net-native.md) 要素は次のポリシーの種類をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-292">The [Property](../../../docs/framework/net-native/property-element-net-native.md) and [Field](../../../docs/framework/net-native/field-element-net-native.md) elements support the following policy types:</span></span>  
  
-   <span data-ttu-id="c5d6c-293">`Browse`: このメンバーに関する情報の照会を制御しますが、実行時アクセスは有効にしません。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-293">`Browse` - Controls querying for information about this member but does not enable any runtime access.</span></span>  
  
-   <span data-ttu-id="c5d6c-294">`Dynamic`: コンストラクター、メソッド、フィールド、プロパティ、およびイベントを含むすべての型のメンバーへの実行時アクセスを制御して、動的プログラミングを有効にします。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-294">`Dynamic` - Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span> <span data-ttu-id="c5d6c-295">また、それを含む型に関する情報の照会も制御します。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-295">Also controls querying for information about the containing type.</span></span>  
  
-   <span data-ttu-id="c5d6c-296">`Serialize`: メンバーへの実行時アクセスを制御し、Newtonsoft の JSON シリアライザーなどのライブラリによって型インスタンスをシリアル化および逆シリアル化できるようにします。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-296">`Serialize` - Controls runtime access to the member to enable type instances to be serialized and deserialized by libraries such as the Newtonsoft JSON serializer.</span></span> <span data-ttu-id="c5d6c-297">このポリシーは、コンストラクター、フィールド、およびプロパティに適用できます。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-297">This policy can be applied to constructors, fields, and properties.</span></span>  
  
 <span data-ttu-id="c5d6c-298">[Method](../../../docs/framework/net-native/method-element-net-native.md) 要素と [Event](../../../docs/framework/net-native/event-element-net-native.md) 要素は次のポリシーの種類をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-298">The [Method](../../../docs/framework/net-native/method-element-net-native.md) and [Event](../../../docs/framework/net-native/event-element-net-native.md) elements support the following policy types:</span></span>  
  
-   <span data-ttu-id="c5d6c-299">`Browse`: このメンバーに関する情報の照会を制御しますが、実行時アクセスは有効にしません。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-299">`Browse` - Controls querying for information about this member but doesn’t enable any runtime access.</span></span>  
  
-   <span data-ttu-id="c5d6c-300">`Dynamic`: コンストラクター、メソッド、フィールド、プロパティ、およびイベントを含むすべての型のメンバーへの実行時アクセスを制御して、動的プログラミングを有効にします。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-300">`Dynamic` - Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span> <span data-ttu-id="c5d6c-301">また、それを含む型に関する情報の照会も制御します。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-301">Also controls querying for information about the containing type.</span></span>  
  
 <span data-ttu-id="c5d6c-302">これらのポリシーの種類に関連付けられている設定を次に示します。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-302">The settings associated with these policy types are:</span></span>  
  
-   <span data-ttu-id="c5d6c-303">`Auto`: 既定の動作を使用します。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-303">`Auto` - Use the default behavior.</span></span> <span data-ttu-id="c5d6c-304">(何かにオーバーライドされない限り、ポリシーを指定しないことは、そのポリシーを `Auto` に設定することと同じです。)</span><span class="sxs-lookup"><span data-stu-id="c5d6c-304">(Not specifying a policy is equivalent to setting that policy to `Auto` unless something overrides it.)</span></span>  
  
-   <span data-ttu-id="c5d6c-305">`Excluded`: メンバーのメタデータを含めません。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-305">`Excluded` - Never include metadata for the member.</span></span>  
  
-   <span data-ttu-id="c5d6c-306">`Included`: 親型が出力に存在する場合、ポリシーを有効にします。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-306">`Included` - Enable the policy if the parent type is present in the output.</span></span>  
  
-   <span data-ttu-id="c5d6c-307">`Required`: このメンバーが未使用と見なされる場合でもこれを保持し、そのメンバーのポリシーを有効にするためにツール チェーンを要求します。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-307">`Required` - Require the tool chain to keep this member even if appears to be unused, and enable policy for it.</span></span>  
  
## <a name="runtime-directives-file-semantics"></a><span data-ttu-id="c5d6c-308">ランタイム ディレクティブ ファイルのセマンティクス</span><span class="sxs-lookup"><span data-stu-id="c5d6c-308">Runtime directives file semantics</span></span>  
 <span data-ttu-id="c5d6c-309">ポリシーは、上位レベルと下位レベルの要素両方に同時に定義できます。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-309">Policy can be defined simultaneously for both higher-level and lower-level elements.</span></span> <span data-ttu-id="c5d6c-310">たとえば、アセンブリと、そのアセンブリに含まれる型の一部にポリシーを定義できます。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-310">For example, policy can be defined for an assembly, and for some of the types contained in that assembly.</span></span> <span data-ttu-id="c5d6c-311">特定の下位レベル要素が表されていない場合、その親のポリシーを継承します。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-311">If a particular lower-level element is not represented, it inherits the policy of its parent.</span></span> <span data-ttu-id="c5d6c-312">たとえば、`Assembly` 要素は存在するが `Type` 要素は存在しない場合、`Assembly` 要素で指定されるポリシーはアセンブリ内のすべての型に適用されます。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-312">For example, if an `Assembly` element is present but `Type` elements are not, the policy specified in the `Assembly` element applies to each type in the assembly.</span></span> <span data-ttu-id="c5d6c-313">複数の要素が同じプログラム要素にポリシーを適用することもできます。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-313">Multiple elements can also apply policy to the same program element.</span></span> <span data-ttu-id="c5d6c-314">たとえば、個別の [Assembly](../../../docs/framework/net-native/assembly-element-net-native.md) 要素が、同じアセンブリの同じポリシー要素を別々に定義するとします。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-314">For example, separate [Assembly](../../../docs/framework/net-native/assembly-element-net-native.md) elements might define the same policy element for the same assembly differently.</span></span> <span data-ttu-id="c5d6c-315">次のセクションで、このような場合に特定の型のポリシーがどのように解決されるかを説明します。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-315">The following sections explain how the policy for a particular type is resolved in those cases.</span></span>  
  
 <span data-ttu-id="c5d6c-316">ジェネリック型またはメソッドの [Type](../../../docs/framework/net-native/type-element-net-native.md) 要素または [Method](../../../docs/framework/net-native/method-element-net-native.md) 要素は、独自のポリシーを持たないすべてのインスタンス化にそのポリシーを適用します。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-316">A [Type](../../../docs/framework/net-native/type-element-net-native.md) or [Method](../../../docs/framework/net-native/method-element-net-native.md) element of a generic type or method applies its policy to all instantiations that do not have their own policy.</span></span> <span data-ttu-id="c5d6c-317">たとえば、`Type` のポリシーを指定する <xref:System.Collections.Generic.List%601> 要素は、構築された特定のジェネリック型 (`List<Int32>` など) について `TypeInstantiation` 要素によってオーバーライドされない限り、そのジェネリック型のすべての構築されたインスタンスに適用されます。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-317">For example, a `Type` element that specifies policy for <xref:System.Collections.Generic.List%601> applies to all constructed instances of that generic type, unless it's overridden for a particular constructed generic type (such as a `List<Int32>`) by a `TypeInstantiation` element.</span></span> <span data-ttu-id="c5d6c-318">そうでない場合、要素は指定されたプログラム要素のポリシーを定義します。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-318">Otherwise, elements define policy for the program element named.</span></span>  
  
 <span data-ttu-id="c5d6c-319">要素があいまいな場合、エンジンが一致を検索し、完全一致が見つかるとそれを使用します。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-319">When an element is ambiguous, the engine looks for matches, and if it finds an exact match, it will use it.</span></span> <span data-ttu-id="c5d6c-320">複数の一致が見つかった場合は警告またはエラーになります。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-320">If it finds multiple matches, there will be a warning or error.</span></span>  
  
### <a name="if-two-directives-apply-policy-to-the-same-program-element"></a><span data-ttu-id="c5d6c-321">2 つのディレクティブが同じプログラム要素にポリシーを適用する場合</span><span class="sxs-lookup"><span data-stu-id="c5d6c-321">If two directives apply policy to the same program element</span></span>  
 <span data-ttu-id="c5d6c-322">別のランタイム ディレクティブ ファイルにある 2 つの要素が同じプログラム要素 (アセンブリや型など) の同じポリシーの種類を異なる値に設定しようとした場合、次のように競合が解決されます。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-322">If two elements in different runtime directives files try to set the same policy type for the same program element (such as an assembly or type) to different values, the conflict is resolved as follows:</span></span>  
  
1.  <span data-ttu-id="c5d6c-323">`Excluded` 要素が存在する場合はこれが優先されます。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-323">If the `Excluded` element is present, it has precedence.</span></span>  
  
2.  <span data-ttu-id="c5d6c-324">`Required` は `Required` 以外より優先されます。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-324">`Required` has precedence over not `Required`.</span></span>  
  
3.  <span data-ttu-id="c5d6c-325">`All` は `PublicAndInternal` (`Public` より優先) より優先されされます。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-325">`All` has precedence over `PublicAndInternal`, which has precedence over `Public`.</span></span>  
  
4.  <span data-ttu-id="c5d6c-326">明示的な設定はいずれも `Auto` より優先されます。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-326">Any explicit setting has precedence over `Auto`.</span></span>  
  
 <span data-ttu-id="c5d6c-327">たとえば、1 つのプロジェクトに次の 2 つのランタイム ディレクティブ ファイルが含まれている場合、DataClasses.dll のシリアル化ポリシーは `Required Public` と `All` の両方に設定されます。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-327">For example, if a single project includes the following two runtime directives files, the serialization policy for DataClasses.dll is set to both `Required Public` and `All`.</span></span> <span data-ttu-id="c5d6c-328">この場合、シリアル化ポリシーは `Required All` として解決されます。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-328">In this case, the serialization policy would be resolved as `Required All`.</span></span>  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
   <Application>  
      <Assembly Name="DataClasses" Serialize="Required Public"/>  
   </Application>  
   <Library Name="DataClasses">  
      <!-- any other elements -->  
   </Library>  
</Directives>  
```  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
   <Application>  
      <Assembly Name="DataClasses" Serialize="All" />  
   </Application>  
   <Library Name="DataClasses">  
      <!-- any other elements -->  
   </Library>  
</Directives>  
```  
  
 <span data-ttu-id="c5d6c-329">ただし、1 つのランタイム ディレクティブ ファイル内の 2 つのディレクティブが同じプログラム要素に同じポリシーの種類を設定しようとした場合、XML スキーマ定義ツールからエラー メッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-329">However, if two directives in a single runtime directives file try to set the same policy type for the same program element, the XML Scheme Definition tool displays an error message.</span></span>  
  
### <a name="if-child-and-parent-elements-apply-the-same-policy-type"></a><span data-ttu-id="c5d6c-330">子要素と親要素が同じポリシーの種類を適用する場合</span><span class="sxs-lookup"><span data-stu-id="c5d6c-330">If child and parent elements apply the same policy type</span></span>  
 <span data-ttu-id="c5d6c-331">`Excluded` 設定を含め、子要素はその親要素をオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-331">Child elements override their parent elements, including the `Excluded` setting.</span></span> <span data-ttu-id="c5d6c-332">オーバーライドは、`Auto` を指定する必要がある主な理由です。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-332">Overriding is the main reason you would want to specify `Auto`.</span></span>  
  
 <span data-ttu-id="c5d6c-333">次の例では、`DataClasses` にはあるが `DataClasses.ViewModels` にはないものすべてのシリアル化ポリシー設定が `Required Public` になり、`DataClasses` と `DataClasses.ViewModels` の両方にあるものすべてのシリアル化ポリシー設定は `All` になります。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-333">In the following example, the serialization policy setting for everything in `DataClasses` that’s not in `DataClasses.ViewModels` would be `Required Public`, and everything that's in both `DataClasses` and `DataClasses.ViewModels` would be `All`.</span></span>  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
   <Application>  
      <Assembly Name="DataClasses" Serialize="Required Public" >  
         <Namespace Name="DataClasses.ViewModels" Seralize="All" />  
      </Assembly>  
   </Appliction>  
   <Library Name="DataClasses">  
      <!-- any other elements -->  
   </Library>  
</Directives>  
```  
  
### <a name="if-open-generics-and-instantiated-elements-apply-the-same-policy-type"></a><span data-ttu-id="c5d6c-334">オープン ジェネリックとインスタンス化された要素が同じポリシーの種類を適用する場合</span><span class="sxs-lookup"><span data-stu-id="c5d6c-334">If open generics and instantiated elements apply the same policy type</span></span>  
 <span data-ttu-id="c5d6c-335">次の例では、`Dictionary<int,int>` には、特に `Browse` ポリシーを割り当てる理由がエンジンにある場合にのみ、`Browse` ポリシーが割り当てられます (通常は、これが既定の動作です)。それ以外の <xref:System.Collections.Generic.Dictionary%602> のすべてのインスタンス化では、そのメンバーのすべてが参照可能になります。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-335">In the following example, `Dictionary<int,int>` is assigned the `Browse` policy only if the engine has another reason to give it the `Browse` policy (which would otherwise be the default behavior); every other instantiation of <xref:System.Collections.Generic.Dictionary%602> will have all of its members browsable.</span></span>  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
   <Application>  
      <Assembly Name="DataClasses" Serialize="Required Public" >  
         <Namespace Name="DataClasses.ViewModels" Seralize="All" />  
      </Assembly>  
      <Namespace Name="DataClasses.Generics" />  
      <Type Name="Dictionary" Browse="All" />  
      <TypeInstantiation Name="Dictionary"   
                         Arguments="System.Int32,System.Int32" Browse="Auto" />  
   </Application>  
   <Library Name="DataClasses">  
      <!-- any other elements -->  
   </Library>  
</Directives>  
```  
  
### <a name="how-policy-is-inferred"></a><span data-ttu-id="c5d6c-336">ポリシーの推論方法</span><span class="sxs-lookup"><span data-stu-id="c5d6c-336">How policy is inferred</span></span>  
 <span data-ttu-id="c5d6c-337">ポリシーの種類ごとに、そのポリシーの種類の存在が他の構造体にどう影響するかを決定する一連のルールが異なります。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-337">Each policy type has a different set of rules that determine how the presence of that policy type affects other constructs.</span></span>  
  
#### <a name="the-effect-of-browse-policy"></a><span data-ttu-id="c5d6c-338">Browse ポリシーの効果</span><span class="sxs-lookup"><span data-stu-id="c5d6c-338">The effect of Browse policy</span></span>  
 <span data-ttu-id="c5d6c-339">`Browse` ポリシーを型に適用すると、ポリシーが次のように変更されます。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-339">Applying the `Browse` policy to a type involves the following policy changes:</span></span>  
  
-   <span data-ttu-id="c5d6c-340">型の基本型が `Browse` ポリシーでマークされます。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-340">The base type of the type is marked with the `Browse` policy.</span></span>  
  
-   <span data-ttu-id="c5d6c-341">型がインスタンス化されたジェネリックである場合、インスタンス化されていないその型が `Browse` ポリシーでマークされます。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-341">If the type is an instantiated generic, the uninstantiated version of the type is marked with the `Browse` policy.</span></span>  
  
-   <span data-ttu-id="c5d6c-342">型がデリゲートの場合、型の `Invoke` メソッドが `Dynamic` ポリシーでマークされます。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-342">If the type is a delegate, the `Invoke` method on the type is marked with the `Dynamic` policy.</span></span>  
  
-   <span data-ttu-id="c5d6c-343">型の各インターフェイスが `Browse` ポリシーでマークされます。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-343">Each interface of the type is marked with the `Browse` policy.</span></span>  
  
-   <span data-ttu-id="c5d6c-344">型に適用されている各属性の型が `Browse` ポリシーでマークされます。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-344">The type of each attribute applied to the type is marked with the `Browse` policy.</span></span>  
  
-   <span data-ttu-id="c5d6c-345">型がジェネリックの場合、各制約型が `Browse` ポリシーでマークされます。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-345">If the type is generic, each constraint type is marked with the `Browse` policy.</span></span>  
  
-   <span data-ttu-id="c5d6c-346">型がジェネリックの場合、その型のインスタンス化対象である型が `Browse` ポリシーでマークされます。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-346">If the type is generic, the types over which the type is instantiated are marked with the `Browse` policy.</span></span>  
  
 <span data-ttu-id="c5d6c-347">メソッドに `Browse` ポリシーを適用すると、ポリシーが次のように変更されます。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-347">Applying the `Browse` policy to a method involves the following policy changes:</span></span>  
  
-   <span data-ttu-id="c5d6c-348">メソッドの各パラメーター型が `Browse` ポリシーでマークされます。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-348">Each parameter type of the method is marked with the `Browse` policy.</span></span>  
  
-   <span data-ttu-id="c5d6c-349">メソッドの戻り型が `Browse` ポリシーでマークされます。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-349">The return type of the method is marked with the `Browse` policy.</span></span>  
  
-   <span data-ttu-id="c5d6c-350">メソッドを含む型が `Browse` ポリシーでマークされます。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-350">The containing type of the method is marked with the `Browse` policy.</span></span>  
  
-   <span data-ttu-id="c5d6c-351">メソッドがインスタンス化されたジェネリック メソッドである場合、インスタンス化されていないジェネリック メソッドが `Browse` ポリシーでマークされます。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-351">If the method is an instantiated generic method, the uninstantiated generic method is marked with the `Browse` policy.</span></span>  
  
-   <span data-ttu-id="c5d6c-352">メソッドに適用される各属性の型が `Browse` ポリシーでマークされます。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-352">The type of each attribute applied to the method is marked with the `Browse` policy.</span></span>  
  
-   <span data-ttu-id="c5d6c-353">メソッドがジェネリックの場合、各制約型が `Browse` ポリシーでマークされます。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-353">If the method is generic, each constraint type is marked with the `Browse` policy.</span></span>  
  
-   <span data-ttu-id="c5d6c-354">メソッドがジェネリックの場合、そのメソッドのインスタンス化対象である型が `Browse` ポリシーでマークされます。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-354">If the method is generic, the types over which the method is instantiated are marked with the `Browse` policy.</span></span>  
  
 <span data-ttu-id="c5d6c-355">フィールドに `Browse` ポリシーを適用すると、ポリシーが次のように変更されます。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-355">Applying the `Browse` policy to a field involves the following policy changes:</span></span>  
  
-   <span data-ttu-id="c5d6c-356">フィールドに適用される各属性の型が `Browse` ポリシーでマークされます。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-356">The type of each attribute applied to the field is marked with the `Browse` policy.</span></span>  
  
-   <span data-ttu-id="c5d6c-357">フィールドの型が `Browse` ポリシーでマークされます。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-357">The type of the field is marked with the `Browse` policy.</span></span>  
  
-   <span data-ttu-id="c5d6c-358">フィールドが属する型が `Browse` ポリシーでマークされます。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-358">The type to which the field belongs is marked with the `Browse` policy.</span></span>  
  
#### <a name="the-effect-of-dynamic-policy"></a><span data-ttu-id="c5d6c-359">Dynamic ポリシーの効果</span><span class="sxs-lookup"><span data-stu-id="c5d6c-359">The effect of Dynamic policy</span></span>  
 <span data-ttu-id="c5d6c-360">`Dynamic` ポリシーを型に適用すると、ポリシーが次のように変更されます。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-360">Applying the `Dynamic` policy to a type involves the following policy changes:</span></span>  
  
-   <span data-ttu-id="c5d6c-361">型の基本型が `Dynamic` ポリシーでマークされます。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-361">The base type of the type is marked with the `Dynamic` policy.</span></span>  
  
-   <span data-ttu-id="c5d6c-362">型がインスタンス化されたジェネリックである場合、インスタンス化されていないその型が `Dynamic` ポリシーでマークされます。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-362">If the type is an instantiated generic, the uninstantiated version of the type is marked with the `Dynamic` policy.</span></span>  
  
-   <span data-ttu-id="c5d6c-363">型がデリゲート型の場合、型の `Invoke` メソッドが `Dynamic` ポリシーでマークされます。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-363">If the type is a delegate type, the `Invoke` method on the type is marked with the `Dynamic` policy.</span></span>  
  
-   <span data-ttu-id="c5d6c-364">型の各インターフェイスが `Browse` ポリシーでマークされます。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-364">Each interface of the type is marked with the `Browse` policy.</span></span>  
  
-   <span data-ttu-id="c5d6c-365">型に適用されている各属性の型が `Browse` ポリシーでマークされます。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-365">The type of each attribute applied to the type is marked with the `Browse` policy.</span></span>  
  
-   <span data-ttu-id="c5d6c-366">型がジェネリックの場合、各制約型が `Browse` ポリシーでマークされます。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-366">If the type is generic, each constraint type is marked with the `Browse` policy.</span></span>  
  
-   <span data-ttu-id="c5d6c-367">型がジェネリックの場合、その型のインスタンス化対象である型が `Browse` ポリシーでマークされます。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-367">If the type is generic, the types over which the type is instantiated are marked with the `Browse` policy.</span></span>  
  
 <span data-ttu-id="c5d6c-368">メソッドに `Dynamic` ポリシーを適用すると、ポリシーが次のように変更されます。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-368">Applying the `Dynamic` policy to a method involves the following policy changes:</span></span>  
  
-   <span data-ttu-id="c5d6c-369">メソッドの各パラメーター型が `Browse` ポリシーでマークされます。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-369">Each parameter type of the method is marked with the `Browse` policy.</span></span>  
  
-   <span data-ttu-id="c5d6c-370">メソッドの戻り型が `Dynamic` ポリシーでマークされます。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-370">The return type of the method is marked with the `Dynamic` policy.</span></span>  
  
-   <span data-ttu-id="c5d6c-371">メソッドを含む型が `Dynamic` ポリシーでマークされます。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-371">The containing type of the method is marked with the `Dynamic` policy.</span></span>  
  
-   <span data-ttu-id="c5d6c-372">メソッドがインスタンス化されたジェネリック メソッドである場合、インスタンス化されていないジェネリック メソッドが `Browse` ポリシーでマークされます。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-372">If the method is an instantiated generic method, the uninstantiated generic method is marked with the `Browse` policy.</span></span>  
  
-   <span data-ttu-id="c5d6c-373">メソッドに適用される各属性の型が `Browse` ポリシーでマークされます。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-373">The type of each attribute applied to the method is marked with the `Browse` policy.</span></span>  
  
-   <span data-ttu-id="c5d6c-374">メソッドがジェネリックの場合、各制約型が `Browse` ポリシーでマークされます。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-374">If the method is generic, each constraint type is marked with the `Browse` policy.</span></span>  
  
-   <span data-ttu-id="c5d6c-375">メソッドがジェネリックの場合、そのメソッドのインスタンス化対象である型が `Browse` ポリシーでマークされます。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-375">If the method is generic, the types over which the method is instantiated are marked with the `Browse` policy.</span></span>  
  
-   <span data-ttu-id="c5d6c-376">メソッドを `MethodInfo.Invoke` により呼び出すことができ、<xref:System.Reflection.MethodInfo.CreateDelegate%2A?displayProperty=nameWithType> によりデリゲートの作成が可能になります。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-376">The method can be invoked by `MethodInfo.Invoke`, and delegate creation becomes possible by <xref:System.Reflection.MethodInfo.CreateDelegate%2A?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="c5d6c-377">フィールドに `Dynamic` ポリシーを適用すると、ポリシーが次のように変更されます。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-377">Applying the `Dynamic` policy to a field involves the following policy changes:</span></span>  
  
-   <span data-ttu-id="c5d6c-378">フィールドに適用される各属性の型が `Browse` ポリシーでマークされます。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-378">The type of each attribute applied to the field is marked with the `Browse` policy.</span></span>  
  
-   <span data-ttu-id="c5d6c-379">フィールドの型が `Dynamic` ポリシーでマークされます。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-379">The type of the field is marked with the `Dynamic` policy.</span></span>  
  
-   <span data-ttu-id="c5d6c-380">フィールドが属する型が `Dynamic` ポリシーでマークされます。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-380">The type to which the field belongs is marked with the `Dynamic` policy.</span></span>  
  
#### <a name="the-effect-of-activation-policy"></a><span data-ttu-id="c5d6c-381">Activation ポリシーの効果</span><span class="sxs-lookup"><span data-stu-id="c5d6c-381">The effect of Activation policy</span></span>  
 <span data-ttu-id="c5d6c-382">型に Activation ポリシーを適用すると、ポリシーが次のように変更されます。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-382">Applying the Activation policy to a type involves the following policy changes:</span></span>  
  
-   <span data-ttu-id="c5d6c-383">型がインスタンス化されたジェネリックである場合、インスタンス化されていないその型が `Browse` ポリシーでマークされます。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-383">If the type is an instantiated generic, the uninstantiated version of the type is marked with the `Browse` policy.</span></span>  
  
-   <span data-ttu-id="c5d6c-384">型がデリゲート型の場合、型の `Invoke` メソッドが `Dynamic` ポリシーでマークされます。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-384">If the type is a delegate type, the `Invoke` method on the type is marked with the `Dynamic` policy.</span></span>  
  
-   <span data-ttu-id="c5d6c-385">型のコンストラクターが `Activation` ポリシーでマークされます。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-385">Constructors of the type are marked with the `Activation` policy.</span></span>  
  
 <span data-ttu-id="c5d6c-386">メソッドに `Activation` ポリシーを適用すると、ポリシーが次のように変更されます。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-386">Applying the `Activation` policy to a method involves the following policy change:</span></span>  
  
-   <span data-ttu-id="c5d6c-387">コンストラクターを <xref:System.Reflection.ConstructorInfo.Invoke%2A?displayProperty=nameWithType> メソッドと <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType> メソッドにより呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-387">The constructor can be invoked by the <xref:System.Reflection.ConstructorInfo.Invoke%2A?displayProperty=nameWithType> and <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType> methods.</span></span> <span data-ttu-id="c5d6c-388">メソッドに関しては、`Activation` ポリシーはコンストラクターにのみ影響します。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-388">For methods, the `Activation` policy affects constructors only.</span></span>  
  
 <span data-ttu-id="c5d6c-389">フィールドに `Activation` ポリシーを適用しても効果はありません。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-389">Applying the `Activation` policy to a field has no effect.</span></span>  
  
#### <a name="the-effect-of-serialize-policy"></a><span data-ttu-id="c5d6c-390">Serialize ポリシーの効果</span><span class="sxs-lookup"><span data-stu-id="c5d6c-390">The effect of Serialize policy</span></span>  
 <span data-ttu-id="c5d6c-391">`Serialize` ポリシーにより、一般的なリフレクション ベースのシリアライザーを使用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-391">The `Serialize` policy enables the use of common reflection-based serializers.</span></span> <span data-ttu-id="c5d6c-392">ただし、Microsoft では、Microsoft 以外のシリアライザーの正確なリフレクション アクセス パターンを認識していないため、このポリシーが常に効果的であるとは限りません。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-392">However, because the exact reflection access patterns of non-Microsoft serializers are not known to Microsoft, this policy may not be entirely effective.</span></span>  
  
 <span data-ttu-id="c5d6c-393">`Serialize` ポリシーを型に適用すると、ポリシーが次のように変更されます。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-393">Applying the `Serialize` policy to a type involves the following policy changes:</span></span>  
  
-   <span data-ttu-id="c5d6c-394">型の基本型が `Serialize` ポリシーでマークされます。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-394">The base type of the type is marked with the `Serialize` policy.</span></span>  
  
-   <span data-ttu-id="c5d6c-395">型がインスタンス化されたジェネリックである場合、インスタンス化されていないその型が `Browse` ポリシーでマークされます。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-395">If the type is an instantiated generic, the uninstantiated version of the type is marked with the `Browse` policy.</span></span>  
  
-   <span data-ttu-id="c5d6c-396">型がデリゲート型の場合、型の `Invoke` メソッドが `Dynamic` ポリシーでマークされます。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-396">If the type is a delegate type, the `Invoke` method on the type is marked with the `Dynamic` policy.</span></span>  
  
-   <span data-ttu-id="c5d6c-397">型が列挙の場合、型の配列が `Serialize` ポリシーでマークされます。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-397">If the type is an enumeration, an array of the type is marked with the `Serialize` policy.</span></span>  
  
-   <span data-ttu-id="c5d6c-398">型が <xref:System.Collections.Generic.IEnumerable%601> を実装する場合、`T` が `Serialize` ポリシーでマークされます。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-398">If the type implements <xref:System.Collections.Generic.IEnumerable%601>, `T` is marked with the `Serialize` policy.</span></span>  
  
-   <span data-ttu-id="c5d6c-399">型が <xref:System.Collections.Generic.IEnumerable%601>、<xref:System.Collections.Generic.IList%601>、<xref:System.Collections.Generic.ICollection%601>、<xref:System.Collections.Generic.IReadOnlyCollection%601>、または <xref:System.Collections.Generic.IReadOnlyList%601> の場合、`T[]` と <xref:System.Collections.Generic.List%601> が `Serialize` ポリシーでマークされますが、インターフェイス型のメンバーは `Serialize` ポリシーでマークされません。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-399">If the type is <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.Generic.IList%601>, <xref:System.Collections.Generic.ICollection%601>, <xref:System.Collections.Generic.IReadOnlyCollection%601>, or <xref:System.Collections.Generic.IReadOnlyList%601>, then `T[]` and <xref:System.Collections.Generic.List%601> marked with the `Serialize` policy., but no members of the interface type are marked with the `Serialize` policy.</span></span>  
  
-   <span data-ttu-id="c5d6c-400">型が <xref:System.Collections.Generic.List%601> の場合、型のどのメンバーも `Serialize` ポリシーでマークされません。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-400">If the type is <xref:System.Collections.Generic.List%601>, no members of the type are marked with the `Serialize` policy.</span></span>  
  
-   <span data-ttu-id="c5d6c-401">型が <xref:System.Collections.Generic.IDictionary%602> の場合、<xref:System.Collections.Generic.Dictionary%602> が `Serialize` ポリシーでマークされます。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-401">If the type is <xref:System.Collections.Generic.IDictionary%602>, <xref:System.Collections.Generic.Dictionary%602> is marked with the `Serialize` policy.</span></span> <span data-ttu-id="c5d6c-402">ただし、型のどのメンバーも `Serialize` ポリシーでマークされません。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-402">but no members of the type are marked with the `Serialize` policy.</span></span>  
  
-   <span data-ttu-id="c5d6c-403">型が <xref:System.Collections.Generic.Dictionary%602> の場合、型のどのメンバーも `Serialize` ポリシーでマークされません。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-403">If the type is <xref:System.Collections.Generic.Dictionary%602>, no members of the type are marked with the `Serialize` policy.</span></span>  
  
-   <span data-ttu-id="c5d6c-404">型が <xref:System.Collections.Generic.IDictionary%602> を実装している場合、`TKey` と `TValue` が `Serialize` ポリシーでマークされます。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-404">If the type implements <xref:System.Collections.Generic.IDictionary%602>, `TKey` and `TValue` are marked with the `Serialize` policy.</span></span>  
  
-   <span data-ttu-id="c5d6c-405">各コンストラクター、各プロパティ アクセサー、および各フィールドが `Serialize` ポリシーでマークされます。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-405">Each constructor, each property accessor, and each field is marked with the `Serialize` policy.</span></span>  
  
 <span data-ttu-id="c5d6c-406">メソッドに `Serialize` ポリシーを適用すると、ポリシーが次のように変更されます。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-406">Applying the `Serialize` policy to a method involves the following policy changes:</span></span>  
  
-   <span data-ttu-id="c5d6c-407">それを含む型が `Serialize` ポリシーでマークされます。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-407">The containing type is marked with the `Serialize` policy.</span></span>  
  
-   <span data-ttu-id="c5d6c-408">メソッドの戻り型が `Serialize` ポリシーでマークされます。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-408">The return type of the method is marked with the `Serialize` policy.</span></span>  
  
 <span data-ttu-id="c5d6c-409">フィールドに `Serialize` ポリシーを適用すると、ポリシーが次のように変更されます。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-409">Applying the `Serialize` policy to a field involves the following policy changes:</span></span>  
  
-   <span data-ttu-id="c5d6c-410">それを含む型が `Serialize` ポリシーでマークされます。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-410">The containing type is marked with the `Serialize` policy.</span></span>  
  
-   <span data-ttu-id="c5d6c-411">フィールドの型が `Serialize` ポリシーでマークされます。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-411">The type of the field is marked with the `Serialize` policy.</span></span>  
  
#### <a name="the-effect-of-xmlserializer-datacontractserializer-and-datacontractjsonserialier-policies"></a><span data-ttu-id="c5d6c-412">XmlSerializer、DataContractSerializer、および DataContractJsonSerialier ポリシーの効果</span><span class="sxs-lookup"><span data-stu-id="c5d6c-412">The effect of XmlSerializer, DataContractSerializer, and DataContractJsonSerialier policies</span></span>  
 <span data-ttu-id="c5d6c-413">リフレクション ベースのシリアライザーを対象とした `Serialize` ポリシーとは異なり、`XmlSerializer`、`DataContractSerializer`、および `DataContractJsonSerializer` ポリシーは、[!INCLUDE[net_native](../../../includes/net-native-md.md)] ツール チェーンで認識されている一連のシリアライザーを有効にするために使用されます。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-413">Unlike the `Serialize` policy, which is intended for reflection-based serializers, the `XmlSerializer`, `DataContractSerializer`, and `DataContractJsonSerializer` policies are used to enable a set of serializers that are known to the [!INCLUDE[net_native](../../../includes/net-native-md.md)] tool chain.</span></span> <span data-ttu-id="c5d6c-414">これらのシリアライザーはリフレクションを使用して実装されるのではなく、実行時にシリアル化可能な型のセットが、リフレクション可能な型と同様の方法で決定されます。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-414">These serializers are not implemented by using reflection, but the set of types that can be serialized at run time is determined in a similar manner as types that are reflectable.</span></span>  
  
 <span data-ttu-id="c5d6c-415">これらのポリシーのいずれかを型に適用すると、対応するシリアライザーで型をシリアル化できるようになります。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-415">Applying one of these policies to a type enables the type to be serialized with the matching serializer.</span></span> <span data-ttu-id="c5d6c-416">また、シリアル化が必要であることをシリアル化エンジンが静的に決定できる、すべての型もシリアル化されます。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-416">Also, any types that the serialization engine can statically determine as needing serialization will also be serializable.</span></span>  
  
 <span data-ttu-id="c5d6c-417">これらのポリシーは、メソッドとフィールドには影響しません。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-417">These policies have no effect on methods or fields.</span></span>  
  
 <span data-ttu-id="c5d6c-418">詳細については、「[Windows ストア アプリの .NET ネイティブへの移行](../../../docs/framework/net-native/migrating-your-windows-store-app-to-net-native.md)」の「シリアライザーの違い」セクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="c5d6c-418">For more information, see the "Differences in Serializers" section in [Migrating Your Windows Store App to .NET Native](../../../docs/framework/net-native/migrating-your-windows-store-app-to-net-native.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5d6c-419">関連項目</span><span class="sxs-lookup"><span data-stu-id="c5d6c-419">See Also</span></span>  
 [<span data-ttu-id="c5d6c-420">ランタイム ディレクティブ要素</span><span class="sxs-lookup"><span data-stu-id="c5d6c-420">Runtime Directive Elements</span></span>](../../../docs/framework/net-native/runtime-directive-elements.md)  
 [<span data-ttu-id="c5d6c-421">リフレクションおよび .NET ネイティブ</span><span class="sxs-lookup"><span data-stu-id="c5d6c-421">Reflection and .NET Native</span></span>](../../../docs/framework/net-native/reflection-and-net-native.md)
