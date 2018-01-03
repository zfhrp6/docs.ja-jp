---
title: "&lt;Namespace&gt; 要素 (.NET ネイティブ)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 57c614e5-18a9-4e87-bfd5-d0fe3396a192
caps.latest.revision: "20"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ed448ea3af702706b45e27e923ebe540d83de868
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ltnamespacegt-element-net-native"></a><span data-ttu-id="7d2a9-102">&lt;Namespace&gt; 要素 (.NET ネイティブ)</span><span class="sxs-lookup"><span data-stu-id="7d2a9-102">&lt;Namespace&gt; Element (.NET Native)</span></span>
<span data-ttu-id="7d2a9-103">指定した名前空間内のすべての型にランタイム リフレクション ポリシーを適用します。</span><span class="sxs-lookup"><span data-stu-id="7d2a9-103">Applies runtime reflection policy to all the types in a specified namespace.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7d2a9-104">構文</span><span class="sxs-lookup"><span data-stu-id="7d2a9-104">Syntax</span></span>  
  
```xml  
<Namespace Name="namespace_name"   
           Activate="policy_type"   
           Browse="policy_type" />  
           Dynamic="policy_setting"  
           Serialize="policy_setting"  
           DataContractSerializer="policy_setting"  
           DataContractJsonSerializer="policy_setting"  
           XmlSerializer="policy_setting"  
           MarshalObject="policy_setting"  
           MarshalDelegate="policy_setting"  
           MarshalStructure="policy_setting" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7d2a9-105">属性および要素</span><span class="sxs-lookup"><span data-stu-id="7d2a9-105">Attributes and Elements</span></span>  
 <span data-ttu-id="7d2a9-106">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="7d2a9-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7d2a9-107">属性</span><span class="sxs-lookup"><span data-stu-id="7d2a9-107">Attributes</span></span>  
  
|<span data-ttu-id="7d2a9-108">属性</span><span class="sxs-lookup"><span data-stu-id="7d2a9-108">Attribute</span></span>|<span data-ttu-id="7d2a9-109">属性の型</span><span class="sxs-lookup"><span data-stu-id="7d2a9-109">Attribute type</span></span>|<span data-ttu-id="7d2a9-110">説明</span><span class="sxs-lookup"><span data-stu-id="7d2a9-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="7d2a9-111">全般</span><span class="sxs-lookup"><span data-stu-id="7d2a9-111">General</span></span>|<span data-ttu-id="7d2a9-112">必須の属性です。</span><span class="sxs-lookup"><span data-stu-id="7d2a9-112">Required attribute.</span></span> <span data-ttu-id="7d2a9-113">名前空間の名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="7d2a9-113">Specifies the name of the namespace.</span></span>|  
|`Activate`|<span data-ttu-id="7d2a9-114">リフレクション</span><span class="sxs-lookup"><span data-stu-id="7d2a9-114">Reflection</span></span>|<span data-ttu-id="7d2a9-115">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="7d2a9-115">Optional attribute.</span></span> <span data-ttu-id="7d2a9-116">コンストラクターへの実行時アクセスを制御して、インスタンスのアクティブ化を有効にします。</span><span class="sxs-lookup"><span data-stu-id="7d2a9-116">Controls runtime access to constructors to enable activation of instances.</span></span>|  
|`Browse`|<span data-ttu-id="7d2a9-117">リフレクション</span><span class="sxs-lookup"><span data-stu-id="7d2a9-117">Reflection</span></span>|<span data-ttu-id="7d2a9-118">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="7d2a9-118">Optional attribute.</span></span> <span data-ttu-id="7d2a9-119">プログラム要素に関する情報の照会を制御しますが、実行時アクセスは有効にしません。</span><span class="sxs-lookup"><span data-stu-id="7d2a9-119">Controls querying for information about program elements, but does not enable any runtime access.</span></span>|  
|`Dynamic`|<span data-ttu-id="7d2a9-120">リフレクション</span><span class="sxs-lookup"><span data-stu-id="7d2a9-120">Reflection</span></span>|<span data-ttu-id="7d2a9-121">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="7d2a9-121">Optional attribute.</span></span> <span data-ttu-id="7d2a9-122">コンストラクター、メソッド、フィールド、プロパティ、およびイベントを含むすべての型のメンバーへの実行時アクセスを制御して、動的プログラミングを有効にします。</span><span class="sxs-lookup"><span data-stu-id="7d2a9-122">Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span>|  
|`Serialize`|<span data-ttu-id="7d2a9-123">シリアル化</span><span class="sxs-lookup"><span data-stu-id="7d2a9-123">Serialization</span></span>|<span data-ttu-id="7d2a9-124">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="7d2a9-124">Optional attribute.</span></span> <span data-ttu-id="7d2a9-125">コンストラクター、フィールド、およびプロパティへの実行時アクセスを制御し、Newtonsoft の JSON シリアライザーなどのライブラリによって型インスタンスをシリアル化および逆シリアル化できるようにします。</span><span class="sxs-lookup"><span data-stu-id="7d2a9-125">Controls runtime access to constructors, fields, and properties, to enable type instances to be serialized and deserialized by libraries such as the Newtonsoft JSON serializer.</span></span>|  
|`DataContractSerializer`|<span data-ttu-id="7d2a9-126">シリアル化</span><span class="sxs-lookup"><span data-stu-id="7d2a9-126">Serialization</span></span>|<span data-ttu-id="7d2a9-127">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="7d2a9-127">Optional attribute.</span></span> <span data-ttu-id="7d2a9-128"><xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> クラスを使用するシリアル化のポリシーを制御します。</span><span class="sxs-lookup"><span data-stu-id="7d2a9-128">Controls policy for serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>|  
|`DataContractJsonSerializer`|<span data-ttu-id="7d2a9-129">シリアル化</span><span class="sxs-lookup"><span data-stu-id="7d2a9-129">Serialization</span></span>|<span data-ttu-id="7d2a9-130">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="7d2a9-130">Optional attribute.</span></span> <span data-ttu-id="7d2a9-131"><xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> クラスを使用する JSON シリアル化のポリシーを制御します。</span><span class="sxs-lookup"><span data-stu-id="7d2a9-131">Controls policy for JSON serialization that uses the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> class.</span></span>|  
|`XmlSerializer`|<span data-ttu-id="7d2a9-132">シリアル化</span><span class="sxs-lookup"><span data-stu-id="7d2a9-132">Serialization</span></span>|<span data-ttu-id="7d2a9-133">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="7d2a9-133">Optional attribute.</span></span> <span data-ttu-id="7d2a9-134"><xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> クラスを使用する XML シリアル化のポリシーを制御します。</span><span class="sxs-lookup"><span data-stu-id="7d2a9-134">Controls policy for XML serialization that uses the <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> class.</span></span>|  
|`MarshalObject`|<span data-ttu-id="7d2a9-135">Interop</span><span class="sxs-lookup"><span data-stu-id="7d2a9-135">Interop</span></span>|<span data-ttu-id="7d2a9-136">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="7d2a9-136">Optional attribute.</span></span> <span data-ttu-id="7d2a9-137">Windows ランタイムと COM に参照型をマーシャリングするためのポリシーを制御します。</span><span class="sxs-lookup"><span data-stu-id="7d2a9-137">Controls policy for marshaling reference types to Windows Runtime and COM.</span></span>|  
|`MarshalDelegate`|<span data-ttu-id="7d2a9-138">Interop</span><span class="sxs-lookup"><span data-stu-id="7d2a9-138">Interop</span></span>|<span data-ttu-id="7d2a9-139">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="7d2a9-139">Optional attribute.</span></span> <span data-ttu-id="7d2a9-140">ネイティブ コードへの関数ポインターとしてデリゲート型をマーシャリングするためのポリシーを制御します。</span><span class="sxs-lookup"><span data-stu-id="7d2a9-140">Controls policy for marshaling delegate types as function pointers to native code.</span></span>|  
|`MarshalStructure`|<span data-ttu-id="7d2a9-141">Interop</span><span class="sxs-lookup"><span data-stu-id="7d2a9-141">Interop</span></span>|<span data-ttu-id="7d2a9-142">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="7d2a9-142">Optional attribute.</span></span> <span data-ttu-id="7d2a9-143">ネイティブ コードに構造体をマーシャリングするためのポリシーを制御します。</span><span class="sxs-lookup"><span data-stu-id="7d2a9-143">Controls policy for marshaling structures to native code.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="7d2a9-144">Name 属性</span><span class="sxs-lookup"><span data-stu-id="7d2a9-144">Name attribute</span></span>  
  
|<span data-ttu-id="7d2a9-145">値</span><span class="sxs-lookup"><span data-stu-id="7d2a9-145">Value</span></span>|<span data-ttu-id="7d2a9-146">説明</span><span class="sxs-lookup"><span data-stu-id="7d2a9-146">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="7d2a9-147">*namespace_name*</span><span class="sxs-lookup"><span data-stu-id="7d2a9-147">*namespace_name*</span></span>|<span data-ttu-id="7d2a9-148">名前空間の名前。</span><span class="sxs-lookup"><span data-stu-id="7d2a9-148">The namespace name.</span></span> <span data-ttu-id="7d2a9-149">\<Namespace> 要素が [\<Application>](../../../docs/framework/net-native/application-element-net-native.md) 要素、[\<Library>](../../../docs/framework/net-native/library-element-net-native.md) 要素、または [\<Assembly>](../../../docs/framework/net-native/assembly-element-net-native.md) 要素の子である場合、*namespace_name* は名前空間の完全修飾名である必要があります。</span><span class="sxs-lookup"><span data-stu-id="7d2a9-149">If the \<Namespace> element is a child of an [\<Application>](../../../docs/framework/net-native/application-element-net-native.md), [\<Library>](../../../docs/framework/net-native/library-element-net-native.md), or [\<Assembly>](../../../docs/framework/net-native/assembly-element-net-native.md) element, *namespace_name* must be a fully qualified namespace name.</span></span> <span data-ttu-id="7d2a9-150">\<Namespace> 要素が別の \<Namespace> 要素の子である場合、*namespace_name* は名前空間の相対名である必要があります。</span><span class="sxs-lookup"><span data-stu-id="7d2a9-150">If the \<Namespace> element is a child of another \<Namespace> element, *namespace_name* must be a relative namespace name.</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="7d2a9-151">その他すべての属性</span><span class="sxs-lookup"><span data-stu-id="7d2a9-151">All other attributes</span></span>  
  
|<span data-ttu-id="7d2a9-152">値</span><span class="sxs-lookup"><span data-stu-id="7d2a9-152">Value</span></span>|<span data-ttu-id="7d2a9-153">説明</span><span class="sxs-lookup"><span data-stu-id="7d2a9-153">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="7d2a9-154">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="7d2a9-154">*policy_setting*</span></span>|<span data-ttu-id="7d2a9-155">名前空間内のすべての型について、このポリシーの種類に適用する設定です。</span><span class="sxs-lookup"><span data-stu-id="7d2a9-155">The setting to apply to this policy type for all types in the namespace.</span></span> <span data-ttu-id="7d2a9-156">指定できる値は、`All`、`Auto`、`Excluded`、`Public`、`PublicAndInternal`、`Required Public`、`Required PublicAndInternal`、および `Required All` です。</span><span class="sxs-lookup"><span data-stu-id="7d2a9-156">Possible values are `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, and `Required All`.</span></span> <span data-ttu-id="7d2a9-157">詳細については、「[ランタイム ディレクティブのポリシー設定](../../../docs/framework/net-native/runtime-directive-policy-settings.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7d2a9-157">For more information, see [Runtime Directive Policy Settings](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7d2a9-158">子要素</span><span class="sxs-lookup"><span data-stu-id="7d2a9-158">Child Elements</span></span>  
  
|<span data-ttu-id="7d2a9-159">要素</span><span class="sxs-lookup"><span data-stu-id="7d2a9-159">Element</span></span>|<span data-ttu-id="7d2a9-160">説明</span><span class="sxs-lookup"><span data-stu-id="7d2a9-160">Description</span></span>|  
|-------------|-----------------|  
|`<Namespace>`|<span data-ttu-id="7d2a9-161">親名前空間内のすべての型にランタイム リフレクション ポリシーを適用します。</span><span class="sxs-lookup"><span data-stu-id="7d2a9-161">Applies runtime reflection policy to all types in a parent namespace.</span></span>|  
|[<span data-ttu-id="7d2a9-162">\<Type></span><span class="sxs-lookup"><span data-stu-id="7d2a9-162">\<Type></span></span>](../../../docs/framework/net-native/type-element-net-native.md)|<span data-ttu-id="7d2a9-163">型にリフレクション ポリシーを適用します。</span><span class="sxs-lookup"><span data-stu-id="7d2a9-163">Applies reflection policy to a type.</span></span>|  
|[<span data-ttu-id="7d2a9-164">\<TypeInstantiation></span><span class="sxs-lookup"><span data-stu-id="7d2a9-164">\<TypeInstantiation></span></span>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)|<span data-ttu-id="7d2a9-165">構築されたジェネリック型にリフレクション ポリシーを適用します。</span><span class="sxs-lookup"><span data-stu-id="7d2a9-165">Applies reflection policy to a constructed generic type.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="7d2a9-166">親要素</span><span class="sxs-lookup"><span data-stu-id="7d2a9-166">Parent Elements</span></span>  
  
|<span data-ttu-id="7d2a9-167">要素</span><span class="sxs-lookup"><span data-stu-id="7d2a9-167">Element</span></span>|<span data-ttu-id="7d2a9-168">説明</span><span class="sxs-lookup"><span data-stu-id="7d2a9-168">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7d2a9-169">\<Application></span><span class="sxs-lookup"><span data-stu-id="7d2a9-169">\<Application></span></span>](../../../docs/framework/net-native/application-element-net-native.md)|<span data-ttu-id="7d2a9-170">実行時にリフレクションで使用可能なメタデータを持つ、アプリケーション全体の型と型のメンバーのコンテナーとして機能します。</span><span class="sxs-lookup"><span data-stu-id="7d2a9-170">Serves as a container for application-wide types and type members whose metadata is available for reflection at run time.</span></span> <span data-ttu-id="7d2a9-171">[\<Application>](../../../docs/framework/net-native/application-element-net-native.md) 要素は、0 個以上の [\<Assembly>](../../../docs/framework/net-native/assembly-element-net-native.md) 要素を持つことができます。</span><span class="sxs-lookup"><span data-stu-id="7d2a9-171">The [\<Application>](../../../docs/framework/net-native/application-element-net-native.md) element can have zero, one, or more [\<Assembly>](../../../docs/framework/net-native/assembly-element-net-native.md) elements.</span></span>|  
|[<span data-ttu-id="7d2a9-172">\<Assembly></span><span class="sxs-lookup"><span data-stu-id="7d2a9-172">\<Assembly></span></span>](../../../docs/framework/net-native/assembly-element-net-native.md)|<span data-ttu-id="7d2a9-173">指定したアセンブリ内のすべての型にランタイム リフレクション ポリシーを適用します。</span><span class="sxs-lookup"><span data-stu-id="7d2a9-173">Applies runtime reflection policy to all the types in a specified assembly.</span></span>|  
|[<span data-ttu-id="7d2a9-174">\<Library></span><span class="sxs-lookup"><span data-stu-id="7d2a9-174">\<Library></span></span>](../../../docs/framework/net-native/library-element-net-native.md)|<span data-ttu-id="7d2a9-175">実行時にリフレクションに使用可能なメタデータを持つ型と型のメンバーを含むアセンブリを定義します。</span><span class="sxs-lookup"><span data-stu-id="7d2a9-175">Defines the assembly that contains types and type members whose metadata is available for reflection at run time.</span></span> <span data-ttu-id="7d2a9-176">[\<Library>](../../../docs/framework/net-native/library-element-net-native.md) 要素は、0 または 1 個の [\<Assembly>](../../../docs/framework/net-native/assembly-element-net-native.md) 要素を持つことができます。</span><span class="sxs-lookup"><span data-stu-id="7d2a9-176">The [\<Library>](../../../docs/framework/net-native/library-element-net-native.md) element can have zero or one [\<Assembly>](../../../docs/framework/net-native/assembly-element-net-native.md) element.</span></span>|  
|`<Namespace>`|<span data-ttu-id="7d2a9-177">親名前空間内のすべての型にリフレクション ポリシーを適用します。</span><span class="sxs-lookup"><span data-stu-id="7d2a9-177">Applies reflection policy to all types in a parent namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7d2a9-178">コメント</span><span class="sxs-lookup"><span data-stu-id="7d2a9-178">Remarks</span></span>  
 <span data-ttu-id="7d2a9-179">`Activate` 属性、`Browse` 属性、`Dynamic`、および `Serialize` 属性はすべて省略可能です。</span><span class="sxs-lookup"><span data-stu-id="7d2a9-179">The `Activate`, `Browse`, `Dynamic`, and `Serialize` attributes are all optional.</span></span> <span data-ttu-id="7d2a9-180">いずれも存在しない場合、`<Namespace>` 要素は子要素のコンテナーとしてのみ機能します。</span><span class="sxs-lookup"><span data-stu-id="7d2a9-180">If none are present, the `<Namespace>` element serves only as a container for child elements.</span></span> <span data-ttu-id="7d2a9-181">存在する場合は、`<Namespace>` 要素は、指定された名前空間内のすべての型にランタイム リフレクション ポリシーを適用します。</span><span class="sxs-lookup"><span data-stu-id="7d2a9-181">If they are present, the `<Namespace>` element applies runtime reflection policy to all the types in the specified namespace.</span></span>  
  
 <span data-ttu-id="7d2a9-182">[\<Assembly>](../../../docs/framework/net-native/assembly-element-net-native.md) 要素の子である場合、`<Namespace>` 要素は [\<Assembly>](../../../docs/framework/net-native/assembly-element-net-native.md) 要素により定義されたランタイム リフレクション ポリシーをオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="7d2a9-182">When it is a child of the [\<Assembly>](../../../docs/framework/net-native/assembly-element-net-native.md) element, the `<Namespace>` element overrides the runtime reflection policy defined by the  [\<Assembly>](../../../docs/framework/net-native/assembly-element-net-native.md) element.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d2a9-183">参照</span><span class="sxs-lookup"><span data-stu-id="7d2a9-183">See Also</span></span>  
 [<span data-ttu-id="7d2a9-184">ランタイム ディレクティブ ポリシーの設定</span><span class="sxs-lookup"><span data-stu-id="7d2a9-184">Runtime Directive Policy Settings</span></span>](../../../docs/framework/net-native/runtime-directive-policy-settings.md)  
 [<span data-ttu-id="7d2a9-185">ランタイム ディレクティブ (rd.xml) 構成ファイル リファレンス</span><span class="sxs-lookup"><span data-stu-id="7d2a9-185">Runtime Directives (rd.xml) Configuration File Reference</span></span>](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)  
 [<span data-ttu-id="7d2a9-186">ランタイム ディレクティブ要素</span><span class="sxs-lookup"><span data-stu-id="7d2a9-186">Runtime Directive Elements</span></span>](../../../docs/framework/net-native/runtime-directive-elements.md)
