---
title: "&lt;GenericParameter&gt; 要素 (.NET ネイティブ)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cbd49732-3615-49a5-a900-f96947cdc3e6
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 601118d2dcc42f9e35da0e24c782b218efd7a025
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ltgenericparametergt-element-net-native"></a><span data-ttu-id="704d8-102">&lt;GenericParameter&gt; 要素 (.NET ネイティブ)</span><span class="sxs-lookup"><span data-stu-id="704d8-102">&lt;GenericParameter&gt; Element (.NET Native)</span></span>
<span data-ttu-id="704d8-103">ジェネリック型またはメソッドのパラメーターの型にポリシーを適用します。</span><span class="sxs-lookup"><span data-stu-id="704d8-103">Applies policy to the parameter type of a generic type or method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="704d8-104">構文</span><span class="sxs-lookup"><span data-stu-id="704d8-104">Syntax</span></span>  
  
```xml  
<GenericParameter Name="generic_parameter_name"  
                  Activate="policy_type"  
                  Browse="policy_type"  
                  Dynamic="policy_type"  
                  Serialize="policy_type" />  
                  DataContractSerializer="policy_type"  
                  DataContractJsonSerializer="policy_type"  
                  XmlSerializer="policy_type"  
                  MarshalObject="policy_type"  
                  MarshalDelegate="policy_type"  
                  MarshalStructure="policy_type"  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="704d8-105">属性および要素</span><span class="sxs-lookup"><span data-stu-id="704d8-105">Attributes and Elements</span></span>  
 <span data-ttu-id="704d8-106">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="704d8-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="704d8-107">属性</span><span class="sxs-lookup"><span data-stu-id="704d8-107">Attributes</span></span>  
  
|<span data-ttu-id="704d8-108">属性</span><span class="sxs-lookup"><span data-stu-id="704d8-108">Attribute</span></span>|<span data-ttu-id="704d8-109">属性の型</span><span class="sxs-lookup"><span data-stu-id="704d8-109">Attribute type</span></span>|<span data-ttu-id="704d8-110">説明</span><span class="sxs-lookup"><span data-stu-id="704d8-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="704d8-111">全般</span><span class="sxs-lookup"><span data-stu-id="704d8-111">General</span></span>|<span data-ttu-id="704d8-112">必須の属性です。</span><span class="sxs-lookup"><span data-stu-id="704d8-112">Required attribute.</span></span> <span data-ttu-id="704d8-113">ジェネリック パラメーターの名前。</span><span class="sxs-lookup"><span data-stu-id="704d8-113">The name of the generic parameter.</span></span> <span data-ttu-id="704d8-114">たとえば、ジェネリック デリゲート <xref:System.Func%603> の場合、デリゲートの戻り値に実行時ポリシーを適用するための `Name` 属性の値は "TResult" です。</span><span class="sxs-lookup"><span data-stu-id="704d8-114">For example, for the generic delegate <xref:System.Func%603>, the value of the `Name` attribute is "TResult" to apply runtime policy to the delegate's return value.</span></span>|  
|`Activate`|<span data-ttu-id="704d8-115">リフレクション</span><span class="sxs-lookup"><span data-stu-id="704d8-115">Reflection</span></span>|<span data-ttu-id="704d8-116">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="704d8-116">Optional attribute.</span></span> <span data-ttu-id="704d8-117">コンストラクターへの実行時アクセスを制御して、インスタンスのアクティブ化を有効にします。</span><span class="sxs-lookup"><span data-stu-id="704d8-117">Controls runtime access to constructors to enable activation of instances.</span></span>|  
|`Browse`|<span data-ttu-id="704d8-118">リフレクション</span><span class="sxs-lookup"><span data-stu-id="704d8-118">Reflection</span></span>|<span data-ttu-id="704d8-119">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="704d8-119">Optional attribute.</span></span> <span data-ttu-id="704d8-120">プログラム要素に関する情報の照会を制御しますが、実行時アクセスは有効にしません。</span><span class="sxs-lookup"><span data-stu-id="704d8-120">Controls querying for information about program elements, but does not enable any runtime access.</span></span>|  
|`Dynamic`|<span data-ttu-id="704d8-121">リフレクション</span><span class="sxs-lookup"><span data-stu-id="704d8-121">Reflection</span></span>|<span data-ttu-id="704d8-122">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="704d8-122">Optional attribute.</span></span> <span data-ttu-id="704d8-123">コンストラクター、メソッド、フィールド、プロパティ、およびイベントを含むすべての型のメンバーへの実行時アクセスを制御して、動的プログラミングを有効にします。</span><span class="sxs-lookup"><span data-stu-id="704d8-123">Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span>|  
|`Serialize`|<span data-ttu-id="704d8-124">シリアル化</span><span class="sxs-lookup"><span data-stu-id="704d8-124">Serialization</span></span>|<span data-ttu-id="704d8-125">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="704d8-125">Optional attribute.</span></span> <span data-ttu-id="704d8-126">コンストラクター、フィールド、およびプロパティへの実行時アクセスを制御し、Newtonsoft の JSON シリアライザーなどのライブラリによって型インスタンスをシリアル化および逆シリアル化できるようにします。</span><span class="sxs-lookup"><span data-stu-id="704d8-126">Controls runtime access to constructors, fields, and properties, to enable type instances to be serialized and deserialized by libraries such as the Newtonsoft JSON serializer.</span></span>|  
|`DataContractSerializer`|<span data-ttu-id="704d8-127">シリアル化</span><span class="sxs-lookup"><span data-stu-id="704d8-127">Serialization</span></span>|<span data-ttu-id="704d8-128">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="704d8-128">Optional attribute.</span></span> <span data-ttu-id="704d8-129"><xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> クラスを使用するシリアル化のポリシーを制御します。</span><span class="sxs-lookup"><span data-stu-id="704d8-129">Controls policy for serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>|  
|`DataContractJsonSerializer`|<span data-ttu-id="704d8-130">シリアル化</span><span class="sxs-lookup"><span data-stu-id="704d8-130">Serialization</span></span>|<span data-ttu-id="704d8-131">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="704d8-131">Optional attribute.</span></span> <span data-ttu-id="704d8-132"><xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> クラスを使用する JSON シリアル化のポリシーを制御します。</span><span class="sxs-lookup"><span data-stu-id="704d8-132">Controls policy for JSON serialization that uses the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> class.</span></span>|  
|`XmlSerializer`|<span data-ttu-id="704d8-133">シリアル化</span><span class="sxs-lookup"><span data-stu-id="704d8-133">Serialization</span></span>|<span data-ttu-id="704d8-134">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="704d8-134">Optional attribute.</span></span> <span data-ttu-id="704d8-135"><xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> クラスを使用する XML シリアル化のポリシーを制御します。</span><span class="sxs-lookup"><span data-stu-id="704d8-135">Controls policy for XML serialization that uses the <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> class.</span></span>|  
|`MarshalObject`|<span data-ttu-id="704d8-136">Interop</span><span class="sxs-lookup"><span data-stu-id="704d8-136">Interop</span></span>|<span data-ttu-id="704d8-137">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="704d8-137">Optional attribute.</span></span> <span data-ttu-id="704d8-138">Windows ランタイムと COM に参照型をマーシャリングするためのポリシーを制御します。</span><span class="sxs-lookup"><span data-stu-id="704d8-138">Controls policy for marshaling reference types to Windows Runtime and COM.</span></span>|  
|`MarshalDelegate`|<span data-ttu-id="704d8-139">Interop</span><span class="sxs-lookup"><span data-stu-id="704d8-139">Interop</span></span>|<span data-ttu-id="704d8-140">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="704d8-140">Optional attribute.</span></span> <span data-ttu-id="704d8-141">ネイティブ コードへの関数ポインターとしてデリゲート型をマーシャリングするためのポリシーを制御します。</span><span class="sxs-lookup"><span data-stu-id="704d8-141">Controls policy for marshaling delegate types as function pointers to native code.</span></span>|  
|`MarshalStructure`|<span data-ttu-id="704d8-142">Interop</span><span class="sxs-lookup"><span data-stu-id="704d8-142">Interop</span></span>|<span data-ttu-id="704d8-143">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="704d8-143">Optional attribute.</span></span> <span data-ttu-id="704d8-144">値型をネイティブ コードにマーシャリングするためのポリシーを制御します。</span><span class="sxs-lookup"><span data-stu-id="704d8-144">Controls policy for marshaling value types to native code.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="704d8-145">Name 属性</span><span class="sxs-lookup"><span data-stu-id="704d8-145">Name attribute</span></span>  
  
|<span data-ttu-id="704d8-146">値</span><span class="sxs-lookup"><span data-stu-id="704d8-146">Value</span></span>|<span data-ttu-id="704d8-147">説明</span><span class="sxs-lookup"><span data-stu-id="704d8-147">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="704d8-148">*generic_parameter_name*</span><span class="sxs-lookup"><span data-stu-id="704d8-148">*generic_parameter_name*</span></span>|<span data-ttu-id="704d8-149">必須の属性です。</span><span class="sxs-lookup"><span data-stu-id="704d8-149">Required attribute.</span></span> <span data-ttu-id="704d8-150">ジェネリック型パラメーターの名前。</span><span class="sxs-lookup"><span data-stu-id="704d8-150">The name of the generic type parameter.</span></span> <span data-ttu-id="704d8-151">たとえば、ジェネリック デリゲート <xref:System.Func%603> の場合、*generic_parameter_name* の値 "TResult" によって、デリゲートの戻り値に実行時ポリシーが適用されます。</span><span class="sxs-lookup"><span data-stu-id="704d8-151">For example, for the generic delegate <xref:System.Func%603>, a *generic_parameter_name* value of "TResult" applies runtime policy to the delegate's return value.</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="704d8-152">その他すべての属性</span><span class="sxs-lookup"><span data-stu-id="704d8-152">All other attributes</span></span>  
  
|<span data-ttu-id="704d8-153">値</span><span class="sxs-lookup"><span data-stu-id="704d8-153">Value</span></span>|<span data-ttu-id="704d8-154">説明</span><span class="sxs-lookup"><span data-stu-id="704d8-154">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="704d8-155">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="704d8-155">*policy_setting*</span></span>|<span data-ttu-id="704d8-156">このポリシーの種類に適用する設定です。</span><span class="sxs-lookup"><span data-stu-id="704d8-156">The setting to apply to this policy type.</span></span> <span data-ttu-id="704d8-157">指定できる値は、`All`、`Public`、`PublicAndInternal`、`Required Public`、`Required PublicAndInternal`、および `Required All` です。</span><span class="sxs-lookup"><span data-stu-id="704d8-157">Possible values are `All`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, and `Required All`.</span></span> <span data-ttu-id="704d8-158">詳細については、「[ランタイム ディレクティブのポリシー設定](../../../docs/framework/net-native/runtime-directive-policy-settings.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="704d8-158">For more information, see [Runtime Directive Policy Settings](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="704d8-159">子要素</span><span class="sxs-lookup"><span data-stu-id="704d8-159">Child Elements</span></span>  
 <span data-ttu-id="704d8-160">なし。</span><span class="sxs-lookup"><span data-stu-id="704d8-160">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="704d8-161">親要素</span><span class="sxs-lookup"><span data-stu-id="704d8-161">Parent Elements</span></span>  
  
|<span data-ttu-id="704d8-162">要素</span><span class="sxs-lookup"><span data-stu-id="704d8-162">Element</span></span>|<span data-ttu-id="704d8-163">説明</span><span class="sxs-lookup"><span data-stu-id="704d8-163">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="704d8-164">\<Method></span><span class="sxs-lookup"><span data-stu-id="704d8-164">\<Method></span></span>](../../../docs/framework/net-native/method-element-net-native.md)|<span data-ttu-id="704d8-165">コンストラクターまたはメソッドにランタイム リフレクション ポリシーを適用します。</span><span class="sxs-lookup"><span data-stu-id="704d8-165">Applies runtime reflection policy to a constructor or method.</span></span>|  
|[<span data-ttu-id="704d8-166">\<Type></span><span class="sxs-lookup"><span data-stu-id="704d8-166">\<Type></span></span>](../../../docs/framework/net-native/type-element-net-native.md)|<span data-ttu-id="704d8-167">クラスや構造体など、特定の型にランタイム リフレクション ポリシーを適用します。</span><span class="sxs-lookup"><span data-stu-id="704d8-167">Applies runtime reflection policy to a particular type, such as a class or structure.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="704d8-168">コメント</span><span class="sxs-lookup"><span data-stu-id="704d8-168">Remarks</span></span>  
 <span data-ttu-id="704d8-169">`<GenericParameter>` 要素は [\<Method>](../../../docs/framework/net-native/method-element-net-native.md) 要素または [\<Type>](../../../docs/framework/net-native/type-element-net-native.md) 要素のいずれかの子で、ジェネリック型またはメソッド シグネチャでの名前によって指定される、特定のジェネリック型パラメーターにポリシーを適用するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="704d8-169">The `<GenericParameter>` element is a child of either the [\<Method>](../../../docs/framework/net-native/method-element-net-native.md) or [\<Type>](../../../docs/framework/net-native/type-element-net-native.md) element and is used to apply policy to a particular generic type parameter, which is specified by its name in the generic type or method signature.</span></span>  
  
 <span data-ttu-id="704d8-170">`<GenericParameter>` 要素は、シリアライザーで使用する場合に最も役立ちます。</span><span class="sxs-lookup"><span data-stu-id="704d8-170">The `<GenericParameter>` element is most useful when used with serializers.</span></span> <span data-ttu-id="704d8-171">次の例では、`<GenericParameter>` 要素を使用して、NewtonSoft の JSON シリアライザーの [JsonConvert.DeserializeObject\<T>(String)](http://james.newtonking.com/json/help/index.html?topic=html/T_Newtonsoft_Json_JsonConvert.htm) メソッド オーバーロードの呼び出しで、`T` 型にポリシーを適用します。</span><span class="sxs-lookup"><span data-stu-id="704d8-171">The following example uses the `<GenericParameter>` element to apply policy to the type `T` in calls to the NewtonSoft JSON serializer's [JsonConvert.DeserializeObject\<T>(String)](http://james.newtonking.com/json/help/index.html?topic=html/T_Newtonsoft_Json_JsonConvert.htm) method overloads.</span></span>  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
   <Type Name="Newtonsoft.Json.JsonConvert" >  
      <Method Name="DeserializeObject{T}">  
         <GenericParameter Name="T" Serialize="Required All" />  
      </Method>  
   </Type>  
</Directives>  
```  
  
## <a name="see-also"></a><span data-ttu-id="704d8-172">参照</span><span class="sxs-lookup"><span data-stu-id="704d8-172">See Also</span></span>  
 [<span data-ttu-id="704d8-173">\<Method> 要素</span><span class="sxs-lookup"><span data-stu-id="704d8-173">\<Method> Element</span></span>](../../../docs/framework/net-native/method-element-net-native.md)  
 [<span data-ttu-id="704d8-174">\<型 > 要素</span><span class="sxs-lookup"><span data-stu-id="704d8-174">\<Type> Element</span></span>](../../../docs/framework/net-native/type-element-net-native.md)  
 [<span data-ttu-id="704d8-175">ランタイム ディレクティブ (rd.xml) 構成ファイル リファレンス</span><span class="sxs-lookup"><span data-stu-id="704d8-175">Runtime Directives (rd.xml) Configuration File Reference</span></span>](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)  
 [<span data-ttu-id="704d8-176">ランタイム ディレクティブ ポリシーの設定</span><span class="sxs-lookup"><span data-stu-id="704d8-176">Runtime Directive Policy Settings</span></span>](../../../docs/framework/net-native/runtime-directive-policy-settings.md)  
 [<span data-ttu-id="704d8-177">ランタイム ディレクティブ要素</span><span class="sxs-lookup"><span data-stu-id="704d8-177">Runtime Directive Elements</span></span>](../../../docs/framework/net-native/runtime-directive-elements.md)
