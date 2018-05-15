---
title: '&lt;Field&gt; 要素 (.NET ネイティブ)'
ms.date: 03/30/2017
ms.assetid: 6a14125f-1a8d-41a1-8a32-659ca0ad12de
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b713eefa4f23aec34b5f55c0c3457381f54ef931
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="ltfieldgt-element-net-native"></a><span data-ttu-id="1861d-102">&lt;Field&gt; 要素 (.NET ネイティブ)</span><span class="sxs-lookup"><span data-stu-id="1861d-102">&lt;Field&gt; Element (.NET Native)</span></span>
<span data-ttu-id="1861d-103">フィールドにランタイム リフレクション ポリシーを適用します。</span><span class="sxs-lookup"><span data-stu-id="1861d-103">Applies runtime reflection policy to a field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1861d-104">構文</span><span class="sxs-lookup"><span data-stu-id="1861d-104">Syntax</span></span>  
  
```xml  
<Field Name="field_name"  
       Browse="policy_type"  
       Dynamic="policy_type"  
       Serialize="policy_type" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1861d-105">属性および要素</span><span class="sxs-lookup"><span data-stu-id="1861d-105">Attributes and Elements</span></span>  
 <span data-ttu-id="1861d-106">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="1861d-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1861d-107">属性</span><span class="sxs-lookup"><span data-stu-id="1861d-107">Attributes</span></span>  
  
|<span data-ttu-id="1861d-108">属性</span><span class="sxs-lookup"><span data-stu-id="1861d-108">Attribute</span></span>|<span data-ttu-id="1861d-109">属性の型</span><span class="sxs-lookup"><span data-stu-id="1861d-109">Attribute type</span></span>|<span data-ttu-id="1861d-110">説明</span><span class="sxs-lookup"><span data-stu-id="1861d-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="1861d-111">全般</span><span class="sxs-lookup"><span data-stu-id="1861d-111">General</span></span>|<span data-ttu-id="1861d-112">必須の属性です。</span><span class="sxs-lookup"><span data-stu-id="1861d-112">Required attribute.</span></span> <span data-ttu-id="1861d-113">フィールド名を指定します。</span><span class="sxs-lookup"><span data-stu-id="1861d-113">Specifies the field name.</span></span>|  
|`Browse`|<span data-ttu-id="1861d-114">リフレクション</span><span class="sxs-lookup"><span data-stu-id="1861d-114">Reflection</span></span>|<span data-ttu-id="1861d-115">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="1861d-115">Optional attribute.</span></span> <span data-ttu-id="1861d-116">フィールドに関する情報の照会やフィールドの列挙を制御しますが、実行時の動的アクセスは有効にしません。</span><span class="sxs-lookup"><span data-stu-id="1861d-116">Controls querying for information about or enumerating the field but does not enable any dynamic access at run time.</span></span>|  
|`Dynamic`|<span data-ttu-id="1861d-117">リフレクション</span><span class="sxs-lookup"><span data-stu-id="1861d-117">Reflection</span></span>|<span data-ttu-id="1861d-118">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="1861d-118">Optional attribute.</span></span> <span data-ttu-id="1861d-119">フィールドへの実行時アクセスを制御して、動的プログラミングを有効にします。</span><span class="sxs-lookup"><span data-stu-id="1861d-119">Controls runtime access to the field to enable dynamic programming.</span></span> <span data-ttu-id="1861d-120">このポリシーにより、実行時にフィールドを動的に設定または取得できるようになります。</span><span class="sxs-lookup"><span data-stu-id="1861d-120">This policy ensures that a field can be set or retrieved dynamically at run time.</span></span>|  
|`Serialize`|<span data-ttu-id="1861d-121">シリアル化</span><span class="sxs-lookup"><span data-stu-id="1861d-121">Serialization</span></span>|<span data-ttu-id="1861d-122">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="1861d-122">Optional attribute.</span></span> <span data-ttu-id="1861d-123">フィールドへの実行時アクセスを制御して、型インスタンスを Newtonsoft の JSON シリアライザーなどのライブラリによってシリアル化できるようにしたり、データ バインディングで使用できるようにしたりします。</span><span class="sxs-lookup"><span data-stu-id="1861d-123">Controls runtime access to a field to enable type instances to be serialized by libraries such as the Newtonsoft JSON serializer or to be used for data binding.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="1861d-124">Name 属性</span><span class="sxs-lookup"><span data-stu-id="1861d-124">Name attribute</span></span>  
  
|<span data-ttu-id="1861d-125">値</span><span class="sxs-lookup"><span data-stu-id="1861d-125">Value</span></span>|<span data-ttu-id="1861d-126">説明</span><span class="sxs-lookup"><span data-stu-id="1861d-126">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="1861d-127">*method_name*</span><span class="sxs-lookup"><span data-stu-id="1861d-127">*method_name*</span></span>|<span data-ttu-id="1861d-128">フィールド名。</span><span class="sxs-lookup"><span data-stu-id="1861d-128">The field name.</span></span> <span data-ttu-id="1861d-129">フィールドの種類は、親 [\<Type>](../../../docs/framework/net-native/type-element-net-native.md) または [\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) 要素によって定義されます。</span><span class="sxs-lookup"><span data-stu-id="1861d-129">The type of the field is defined by the parent [\<Type>](../../../docs/framework/net-native/type-element-net-native.md) or [\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) element.</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="1861d-130">その他すべての属性</span><span class="sxs-lookup"><span data-stu-id="1861d-130">All other attributes</span></span>  
  
|<span data-ttu-id="1861d-131">値</span><span class="sxs-lookup"><span data-stu-id="1861d-131">Value</span></span>|<span data-ttu-id="1861d-132">説明</span><span class="sxs-lookup"><span data-stu-id="1861d-132">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="1861d-133">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="1861d-133">*policy_setting*</span></span>|<span data-ttu-id="1861d-134">フィールドのこのポリシーの種類に適用する設定です。</span><span class="sxs-lookup"><span data-stu-id="1861d-134">The setting to apply to this policy type for the field.</span></span> <span data-ttu-id="1861d-135">指定できる値は、`Auto`、`Excluded`、`Included`、および `Required` です。</span><span class="sxs-lookup"><span data-stu-id="1861d-135">Possible values are `Auto`, `Excluded`, `Included`, and `Required`.</span></span> <span data-ttu-id="1861d-136">詳細については、「[ランタイム ディレクティブのポリシー設定](../../../docs/framework/net-native/runtime-directive-policy-settings.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1861d-136">For more information, see [Runtime Directive Policy Settings](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1861d-137">子要素</span><span class="sxs-lookup"><span data-stu-id="1861d-137">Child Elements</span></span>  
 <span data-ttu-id="1861d-138">なし。</span><span class="sxs-lookup"><span data-stu-id="1861d-138">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1861d-139">親要素</span><span class="sxs-lookup"><span data-stu-id="1861d-139">Parent Elements</span></span>  
  
|<span data-ttu-id="1861d-140">要素</span><span class="sxs-lookup"><span data-stu-id="1861d-140">Element</span></span>|<span data-ttu-id="1861d-141">説明</span><span class="sxs-lookup"><span data-stu-id="1861d-141">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1861d-142">\<Type></span><span class="sxs-lookup"><span data-stu-id="1861d-142">\<Type></span></span>](../../../docs/framework/net-native/type-element-net-native.md)|<span data-ttu-id="1861d-143">型とそのすべてのメンバーにリフレクション ポリシーを適用します。</span><span class="sxs-lookup"><span data-stu-id="1861d-143">Applies reflection policy to a type and all its members.</span></span>|  
|[<span data-ttu-id="1861d-144">\<TypeInstantiation></span><span class="sxs-lookup"><span data-stu-id="1861d-144">\<TypeInstantiation></span></span>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)|<span data-ttu-id="1861d-145">構築されたジェネリック型とそのすべてのメンバーにリフレクション ポリシーを適用します。</span><span class="sxs-lookup"><span data-stu-id="1861d-145">Applies reflection policy to a constructed generic type and all its members.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1861d-146">コメント</span><span class="sxs-lookup"><span data-stu-id="1861d-146">Remarks</span></span>  
 <span data-ttu-id="1861d-147">フィールドのポリシーが明示的に定義されていない場合は、その親要素の実行時ポリシーを継承します。</span><span class="sxs-lookup"><span data-stu-id="1861d-147">If a field's policy is not explicitly defined, it inherits the runtime policy of its parent element.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1861d-148">関連項目</span><span class="sxs-lookup"><span data-stu-id="1861d-148">See Also</span></span>  
 [<span data-ttu-id="1861d-149">ランタイム ディレクティブ要素</span><span class="sxs-lookup"><span data-stu-id="1861d-149">Runtime Directive Elements</span></span>](../../../docs/framework/net-native/runtime-directive-elements.md)  
 [<span data-ttu-id="1861d-150">ランタイム ディレクティブ (rd.xml) 構成ファイル リファレンス</span><span class="sxs-lookup"><span data-stu-id="1861d-150">Runtime Directives (rd.xml) Configuration File Reference</span></span>](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)  
 [<span data-ttu-id="1861d-151">ランタイム ディレクティブ ポリシーの設定</span><span class="sxs-lookup"><span data-stu-id="1861d-151">Runtime Directive Policy Settings</span></span>](../../../docs/framework/net-native/runtime-directive-policy-settings.md)
