---
title: "&lt;Event&gt; 要素 (.NET ネイティブ)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e53b029c-9d6d-4c0a-9cdc-5cfca8a5ca47
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: dabb780e24d1316a3d736f7d1f3da249704a4ff4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="lteventgt-element-net-native"></a><span data-ttu-id="208e7-102">&lt;Event&gt; 要素 (.NET ネイティブ)</span><span class="sxs-lookup"><span data-stu-id="208e7-102">&lt;Event&gt; Element (.NET Native)</span></span>
<span data-ttu-id="208e7-103">イベントにランタイム リフレクション ポリシーを適用します。</span><span class="sxs-lookup"><span data-stu-id="208e7-103">Applies runtime reflection policy to an event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="208e7-104">構文</span><span class="sxs-lookup"><span data-stu-id="208e7-104">Syntax</span></span>  
  
```xml  
<Event Name="event_name"   
       Browse="policy_type"   
       Dynamic="policy_type" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="208e7-105">属性および要素</span><span class="sxs-lookup"><span data-stu-id="208e7-105">Attributes and Elements</span></span>  
 <span data-ttu-id="208e7-106">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="208e7-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="208e7-107">属性</span><span class="sxs-lookup"><span data-stu-id="208e7-107">Attributes</span></span>  
  
|<span data-ttu-id="208e7-108">属性</span><span class="sxs-lookup"><span data-stu-id="208e7-108">Attribute</span></span>|<span data-ttu-id="208e7-109">属性の型</span><span class="sxs-lookup"><span data-stu-id="208e7-109">Attribute type</span></span>|<span data-ttu-id="208e7-110">説明</span><span class="sxs-lookup"><span data-stu-id="208e7-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="208e7-111">全般</span><span class="sxs-lookup"><span data-stu-id="208e7-111">General</span></span>|<span data-ttu-id="208e7-112">必須の属性です。</span><span class="sxs-lookup"><span data-stu-id="208e7-112">Required attribute.</span></span> <span data-ttu-id="208e7-113">イベントの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="208e7-113">Specifies the event name.</span></span>|  
|`Browse`|<span data-ttu-id="208e7-114">リフレクション</span><span class="sxs-lookup"><span data-stu-id="208e7-114">Reflection</span></span>|<span data-ttu-id="208e7-115">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="208e7-115">Optional attribute.</span></span> <span data-ttu-id="208e7-116">イベントに関する情報の照会やイベントの列挙を制御しますが、実行時の動的アクセスは有効にしません。</span><span class="sxs-lookup"><span data-stu-id="208e7-116">Controls querying for information about or enumerating the event but does not enable any dynamic access at run time.</span></span>|  
|`Dynamic`|<span data-ttu-id="208e7-117">リフレクション</span><span class="sxs-lookup"><span data-stu-id="208e7-117">Reflection</span></span>|<span data-ttu-id="208e7-118">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="208e7-118">Optional attribute.</span></span> <span data-ttu-id="208e7-119">イベントへの実行時アクセスを制御して、動的プログラミングを有効にします。</span><span class="sxs-lookup"><span data-stu-id="208e7-119">Controls runtime access to the event to enable dynamic programming.</span></span> <span data-ttu-id="208e7-120">このポリシーにより、実行時にイベントを動的に処理できるようになります。</span><span class="sxs-lookup"><span data-stu-id="208e7-120">This policy ensures that an event can be handled dynamically at run time.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="208e7-121">Name 属性</span><span class="sxs-lookup"><span data-stu-id="208e7-121">Name attribute</span></span>  
  
|<span data-ttu-id="208e7-122">値</span><span class="sxs-lookup"><span data-stu-id="208e7-122">Value</span></span>|<span data-ttu-id="208e7-123">説明</span><span class="sxs-lookup"><span data-stu-id="208e7-123">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="208e7-124">*method_name*</span><span class="sxs-lookup"><span data-stu-id="208e7-124">*method_name*</span></span>|<span data-ttu-id="208e7-125">イベントの名前です。</span><span class="sxs-lookup"><span data-stu-id="208e7-125">The event name.</span></span> <span data-ttu-id="208e7-126">イベントの型は親 [\<Type>](../../../docs/framework/net-native/type-element-net-native.md) または [\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) 要素により定義されます。</span><span class="sxs-lookup"><span data-stu-id="208e7-126">The type of the event is defined by the parent [\<Type>](../../../docs/framework/net-native/type-element-net-native.md) or [\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) element.</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="208e7-127">その他すべての属性</span><span class="sxs-lookup"><span data-stu-id="208e7-127">All other attributes</span></span>  
  
|<span data-ttu-id="208e7-128">値</span><span class="sxs-lookup"><span data-stu-id="208e7-128">Value</span></span>|<span data-ttu-id="208e7-129">説明</span><span class="sxs-lookup"><span data-stu-id="208e7-129">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="208e7-130">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="208e7-130">*policy_setting*</span></span>|<span data-ttu-id="208e7-131">イベントのこのポリシーの種類に適用する設定です。</span><span class="sxs-lookup"><span data-stu-id="208e7-131">The setting to apply to this policy type for the event.</span></span> <span data-ttu-id="208e7-132">指定できる値は、`Auto`、`Excluded`、`Included`、および `Required` です。</span><span class="sxs-lookup"><span data-stu-id="208e7-132">Possible values are `Auto`, `Excluded`, `Included`, and `Required`.</span></span> <span data-ttu-id="208e7-133">詳細については、「[ランタイム ディレクティブのポリシー設定](../../../docs/framework/net-native/runtime-directive-policy-settings.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="208e7-133">For more information, see [Runtime Directive Policy Settings](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="208e7-134">子要素</span><span class="sxs-lookup"><span data-stu-id="208e7-134">Child Elements</span></span>  
 <span data-ttu-id="208e7-135">なし。</span><span class="sxs-lookup"><span data-stu-id="208e7-135">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="208e7-136">親要素</span><span class="sxs-lookup"><span data-stu-id="208e7-136">Parent Elements</span></span>  
  
|<span data-ttu-id="208e7-137">要素</span><span class="sxs-lookup"><span data-stu-id="208e7-137">Element</span></span>|<span data-ttu-id="208e7-138">説明</span><span class="sxs-lookup"><span data-stu-id="208e7-138">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="208e7-139">\<Type></span><span class="sxs-lookup"><span data-stu-id="208e7-139">\<Type></span></span>](../../../docs/framework/net-native/type-element-net-native.md)|<span data-ttu-id="208e7-140">型とそのすべてのメンバーにリフレクション ポリシーを適用します。</span><span class="sxs-lookup"><span data-stu-id="208e7-140">Applies reflection policy to a type and all its members.</span></span>|  
|[<span data-ttu-id="208e7-141">\<TypeInstantiation></span><span class="sxs-lookup"><span data-stu-id="208e7-141">\<TypeInstantiation></span></span>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)|<span data-ttu-id="208e7-142">構築されたジェネリック型とそのすべてのメンバーにリフレクション ポリシーを適用します。</span><span class="sxs-lookup"><span data-stu-id="208e7-142">Applies reflection policy to a constructed generic type and all its members.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="208e7-143">コメント</span><span class="sxs-lookup"><span data-stu-id="208e7-143">Remarks</span></span>  
 <span data-ttu-id="208e7-144">イベントのポリシーが明示的に定義されていない場合は、その親要素の実行時ポリシーを継承します。</span><span class="sxs-lookup"><span data-stu-id="208e7-144">If an event's policy is not explicitly defined, it inherits the runtime policy of its parent element.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="208e7-145">関連項目</span><span class="sxs-lookup"><span data-stu-id="208e7-145">See Also</span></span>  
 [<span data-ttu-id="208e7-146">ランタイム ディレクティブ (rd.xml) 構成ファイル リファレンス</span><span class="sxs-lookup"><span data-stu-id="208e7-146">Runtime Directives (rd.xml) Configuration File Reference</span></span>](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)  
 [<span data-ttu-id="208e7-147">ランタイム ディレクティブ要素</span><span class="sxs-lookup"><span data-stu-id="208e7-147">Runtime Directive Elements</span></span>](../../../docs/framework/net-native/runtime-directive-elements.md)  
 [<span data-ttu-id="208e7-148">ランタイム ディレクティブ ポリシーの設定</span><span class="sxs-lookup"><span data-stu-id="208e7-148">Runtime Directive Policy Settings</span></span>](../../../docs/framework/net-native/runtime-directive-policy-settings.md)
