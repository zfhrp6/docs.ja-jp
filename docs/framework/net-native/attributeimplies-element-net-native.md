---
title: "&lt;AttributeImplies&gt; 要素 (.NET ネイティブ)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 82db7193-a860-418b-84fc-fff2fdf2e025
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: ec2bc90283aa39b8258ad14777cda7180c043c69
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="ltattributeimpliesgt-element-net-native"></a><span data-ttu-id="fe65c-102">&lt;AttributeImplies&gt; 要素 (.NET ネイティブ)</span><span class="sxs-lookup"><span data-stu-id="fe65c-102">&lt;AttributeImplies&gt; Element (.NET Native)</span></span>
<span data-ttu-id="fe65c-103">それを含む属性が適用されるコード要素のポリシーを定義します。</span><span class="sxs-lookup"><span data-stu-id="fe65c-103">Defines policy for code elements the containing attribute is applied to.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fe65c-104">構文</span><span class="sxs-lookup"><span data-stu-id="fe65c-104">Syntax</span></span>  
  
```xml  
<AttributeImplies Activate="policy_type"  
                  Browse="policy_type"  
                  Dynamic="policy_type"  
                  Serialize="policy_type"   
                  DataContractSerializer="policy_setting"  
                  DataContractJsonSerializer="policy_setting"  
                  XmlSerializer="policy_setting"  
                  MarshalObject="policy_setting"  
                  MarshalDelegate="policy_setting"  
                  MarshalStructure="policy_setting" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fe65c-105">属性および要素</span><span class="sxs-lookup"><span data-stu-id="fe65c-105">Attributes and Elements</span></span>  
 <span data-ttu-id="fe65c-106">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="fe65c-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fe65c-107">属性</span><span class="sxs-lookup"><span data-stu-id="fe65c-107">Attributes</span></span>  
  
|<span data-ttu-id="fe65c-108">属性</span><span class="sxs-lookup"><span data-stu-id="fe65c-108">Attribute</span></span>|<span data-ttu-id="fe65c-109">属性の型</span><span class="sxs-lookup"><span data-stu-id="fe65c-109">Attribute type</span></span>|<span data-ttu-id="fe65c-110">説明</span><span class="sxs-lookup"><span data-stu-id="fe65c-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Activate`|<span data-ttu-id="fe65c-111">リフレクション</span><span class="sxs-lookup"><span data-stu-id="fe65c-111">Reflection</span></span>|<span data-ttu-id="fe65c-112">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="fe65c-112">Optional attribute.</span></span> <span data-ttu-id="fe65c-113">コンストラクターへの実行時アクセスを制御して、インスタンスのアクティブ化を有効にします。</span><span class="sxs-lookup"><span data-stu-id="fe65c-113">Controls runtime access to constructors to enable activation of instances.</span></span>|  
|`Browse`|<span data-ttu-id="fe65c-114">リフレクション</span><span class="sxs-lookup"><span data-stu-id="fe65c-114">Reflection</span></span>|<span data-ttu-id="fe65c-115">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="fe65c-115">Optional attribute.</span></span> <span data-ttu-id="fe65c-116">プログラム要素に関する情報の照会を制御しますが、実行時アクセスは有効にしません。</span><span class="sxs-lookup"><span data-stu-id="fe65c-116">Controls querying for information about program elements, but does not enable any runtime access.</span></span>|  
|`Dynamic`|<span data-ttu-id="fe65c-117">リフレクション</span><span class="sxs-lookup"><span data-stu-id="fe65c-117">Reflection</span></span>|<span data-ttu-id="fe65c-118">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="fe65c-118">Optional attribute.</span></span> <span data-ttu-id="fe65c-119">コンストラクター、メソッド、フィールド、プロパティ、およびイベントを含むすべての型のメンバーへの実行時アクセスを制御して、動的プログラミングを有効にします。</span><span class="sxs-lookup"><span data-stu-id="fe65c-119">Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span>|  
|`Serialize`|<span data-ttu-id="fe65c-120">シリアル化</span><span class="sxs-lookup"><span data-stu-id="fe65c-120">Serialization</span></span>|<span data-ttu-id="fe65c-121">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="fe65c-121">Optional attribute.</span></span> <span data-ttu-id="fe65c-122">コンストラクター、フィールド、およびプロパティへの実行時アクセスを制御し、Newtonsoft の JSON シリアライザーなどのライブラリによって型インスタンスをシリアル化および逆シリアル化できるようにします。</span><span class="sxs-lookup"><span data-stu-id="fe65c-122">Controls runtime access to constructors, fields, and properties, to enable type instances to be serialized and deserialized by libraries such as the Newtonsoft JSON serializer.</span></span>|  
|`DataContractSerializer`|<span data-ttu-id="fe65c-123">シリアル化</span><span class="sxs-lookup"><span data-stu-id="fe65c-123">Serialization</span></span>|<span data-ttu-id="fe65c-124">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="fe65c-124">Optional attribute.</span></span> <span data-ttu-id="fe65c-125"><xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> クラスを使用するシリアル化のポリシーを制御します。</span><span class="sxs-lookup"><span data-stu-id="fe65c-125">Controls policy for serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>|  
|`DataContractJsonSerializer`|<span data-ttu-id="fe65c-126">シリアル化</span><span class="sxs-lookup"><span data-stu-id="fe65c-126">Serialization</span></span>|<span data-ttu-id="fe65c-127">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="fe65c-127">Optional attribute.</span></span> <span data-ttu-id="fe65c-128"><xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> クラスを使用する JSON シリアル化のポリシーを制御します。</span><span class="sxs-lookup"><span data-stu-id="fe65c-128">Controls policy for JSON serialization that uses the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> class.</span></span>|  
|`XmlSerializer`|<span data-ttu-id="fe65c-129">シリアル化</span><span class="sxs-lookup"><span data-stu-id="fe65c-129">Serialization</span></span>|<span data-ttu-id="fe65c-130">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="fe65c-130">Optional attribute.</span></span> <span data-ttu-id="fe65c-131"><xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> クラスを使用する XML シリアル化のポリシーを制御します。</span><span class="sxs-lookup"><span data-stu-id="fe65c-131">Controls policy for XML serialization that uses the <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> class.</span></span>|  
|`MarshalObject`|<span data-ttu-id="fe65c-132">Interop</span><span class="sxs-lookup"><span data-stu-id="fe65c-132">Interop</span></span>|<span data-ttu-id="fe65c-133">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="fe65c-133">Optional attribute.</span></span> <span data-ttu-id="fe65c-134">Windows ランタイムと COM に参照型をマーシャリングするためのポリシーを制御します。</span><span class="sxs-lookup"><span data-stu-id="fe65c-134">Controls policy for marshaling reference types to Windows Runtime and COM.</span></span>|  
|`MarshalDelegate`|<span data-ttu-id="fe65c-135">Interop</span><span class="sxs-lookup"><span data-stu-id="fe65c-135">Interop</span></span>|<span data-ttu-id="fe65c-136">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="fe65c-136">Optional attribute.</span></span> <span data-ttu-id="fe65c-137">ネイティブ コードへの関数ポインターとしてデリゲート型をマーシャリングするためのポリシーを制御します。</span><span class="sxs-lookup"><span data-stu-id="fe65c-137">Controls policy for marshaling delegate types as function pointers to native code.</span></span>|  
|`MarshalStructure`|<span data-ttu-id="fe65c-138">Interop</span><span class="sxs-lookup"><span data-stu-id="fe65c-138">Interop</span></span>|<span data-ttu-id="fe65c-139">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="fe65c-139">Optional attribute.</span></span> <span data-ttu-id="fe65c-140">値型をネイティブ コードにマーシャリングするためのポリシーを制御します。</span><span class="sxs-lookup"><span data-stu-id="fe65c-140">Controls policy for marshaling value types to native code.</span></span>|  
  
## <a name="all-attributes"></a><span data-ttu-id="fe65c-141">すべての属性</span><span class="sxs-lookup"><span data-stu-id="fe65c-141">All attributes</span></span>  
  
|<span data-ttu-id="fe65c-142">値</span><span class="sxs-lookup"><span data-stu-id="fe65c-142">Value</span></span>|<span data-ttu-id="fe65c-143">説明</span><span class="sxs-lookup"><span data-stu-id="fe65c-143">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="fe65c-144">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="fe65c-144">*policy_setting*</span></span>|<span data-ttu-id="fe65c-145">このポリシーの種類に適用する設定です。</span><span class="sxs-lookup"><span data-stu-id="fe65c-145">The setting to apply to this policy type.</span></span> <span data-ttu-id="fe65c-146">指定できる値は、`All`、`Auto`、`Excluded`、`Public`、`PublicAndInternal`、`Required Public`、`Required PublicAndInternal`、および `Required All` です。</span><span class="sxs-lookup"><span data-stu-id="fe65c-146">Possible values are `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, and `Required All`.</span></span> <span data-ttu-id="fe65c-147">詳細については、「[ランタイム ディレクティブのポリシー設定](../../../docs/framework/net-native/runtime-directive-policy-settings.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fe65c-147">For more information, see [Runtime Directive Policy Settings](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fe65c-148">子要素</span><span class="sxs-lookup"><span data-stu-id="fe65c-148">Child Elements</span></span>  
 <span data-ttu-id="fe65c-149">なし。</span><span class="sxs-lookup"><span data-stu-id="fe65c-149">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="fe65c-150">親要素</span><span class="sxs-lookup"><span data-stu-id="fe65c-150">Parent Elements</span></span>  
  
|<span data-ttu-id="fe65c-151">要素</span><span class="sxs-lookup"><span data-stu-id="fe65c-151">Element</span></span>|<span data-ttu-id="fe65c-152">説明</span><span class="sxs-lookup"><span data-stu-id="fe65c-152">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fe65c-153">\<Type></span><span class="sxs-lookup"><span data-stu-id="fe65c-153">\<Type></span></span>](../../../docs/framework/net-native/type-element-net-native.md)|<span data-ttu-id="fe65c-154">型とそのすべてのメンバーにリフレクション ポリシーを適用します。</span><span class="sxs-lookup"><span data-stu-id="fe65c-154">Applies reflection policy to a type and all its members.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fe65c-155">コメント</span><span class="sxs-lookup"><span data-stu-id="fe65c-155">Remarks</span></span>  
 <span data-ttu-id="fe65c-156">`<AttributeImplies>` 要素は、それを含む型が属性 (つまり、<xref:System.Attribute?displayProperty=nameWithType> から継承されるクラス) である場合に使用されます。</span><span class="sxs-lookup"><span data-stu-id="fe65c-156">The `<AttributeImplies>` element is used if its containing type is an attribute (that is, a class derived from <xref:System.Attribute?displayProperty=nameWithType>).</span></span> <span data-ttu-id="fe65c-157">特定のプログラム要素に属性が適用される場合、`<AttributeImplies>` 要素によって定義されるポリシーがそのプログラム要素に適用されます。</span><span class="sxs-lookup"><span data-stu-id="fe65c-157">If the attribute is applied to a particular program element, the policy defined by the `<AttributeImplies>` element applies to that program element.</span></span>  
  
 <span data-ttu-id="fe65c-158">リフレクション、シリアル化、および相互運用属性はいずれも省略可能ですが、そのうち少なくとも 1 つが存在する必要があります。</span><span class="sxs-lookup"><span data-stu-id="fe65c-158">The reflection, serialization, and interop attributes are all optional, although at least one should be present.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe65c-159">関連項目</span><span class="sxs-lookup"><span data-stu-id="fe65c-159">See Also</span></span>  
 [<span data-ttu-id="fe65c-160">\<型 > 要素</span><span class="sxs-lookup"><span data-stu-id="fe65c-160">\<Type> Element</span></span>](../../../docs/framework/net-native/type-element-net-native.md)  
 [<span data-ttu-id="fe65c-161">ランタイム ディレクティブ (rd.xml) 構成ファイル リファレンス</span><span class="sxs-lookup"><span data-stu-id="fe65c-161">Runtime Directives (rd.xml) Configuration File Reference</span></span>](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)  
 [<span data-ttu-id="fe65c-162">ランタイム ディレクティブ要素</span><span class="sxs-lookup"><span data-stu-id="fe65c-162">Runtime Directive Elements</span></span>](../../../docs/framework/net-native/runtime-directive-elements.md)  
 [<span data-ttu-id="fe65c-163">ランタイム ディレクティブ ポリシーの設定</span><span class="sxs-lookup"><span data-stu-id="fe65c-163">Runtime Directive Policy Settings</span></span>](../../../docs/framework/net-native/runtime-directive-policy-settings.md)
