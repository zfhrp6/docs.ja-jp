---
title: '&lt;MethodInstantiation&gt; 要素 (.NET ネイティブ)'
ms.date: 03/30/2017
ms.assetid: a3355d78-2a88-4109-8521-830d7cae260a
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3d741e8df8f2b8c6d90a1d867c73495a2ffd1304
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33397794"
---
# <a name="ltmethodinstantiationgt-element-net-native"></a><span data-ttu-id="f3719-102">&lt;MethodInstantiation&gt; 要素 (.NET ネイティブ)</span><span class="sxs-lookup"><span data-stu-id="f3719-102">&lt;MethodInstantiation&gt; Element (.NET Native)</span></span>
<span data-ttu-id="f3719-103">構築されたジェネリック メソッドにランタイム リフレクション ポリシーを適用します。</span><span class="sxs-lookup"><span data-stu-id="f3719-103">Applies runtime reflection policy to a constructed generic method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f3719-104">構文</span><span class="sxs-lookup"><span data-stu-id="f3719-104">Syntax</span></span>  
  
```xml  
<MethodInstantiation Name="method_name"  
                     Signature="method_signature"  
                     Arguments="method_arguments"  
                     Browse="policy_type"  
                     Dynamic="policy_type" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f3719-105">属性および要素</span><span class="sxs-lookup"><span data-stu-id="f3719-105">Attributes and Elements</span></span>  
 <span data-ttu-id="f3719-106">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="f3719-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f3719-107">属性</span><span class="sxs-lookup"><span data-stu-id="f3719-107">Attributes</span></span>  
  
|<span data-ttu-id="f3719-108">属性</span><span class="sxs-lookup"><span data-stu-id="f3719-108">Attribute</span></span>|<span data-ttu-id="f3719-109">属性の型</span><span class="sxs-lookup"><span data-stu-id="f3719-109">Attribute type</span></span>|<span data-ttu-id="f3719-110">説明</span><span class="sxs-lookup"><span data-stu-id="f3719-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="f3719-111">全般</span><span class="sxs-lookup"><span data-stu-id="f3719-111">General</span></span>|<span data-ttu-id="f3719-112">必須の属性です。</span><span class="sxs-lookup"><span data-stu-id="f3719-112">Required attribute.</span></span> <span data-ttu-id="f3719-113">メソッド名を指定します。</span><span class="sxs-lookup"><span data-stu-id="f3719-113">Specifies the method name.</span></span>|  
|`Signature`|<span data-ttu-id="f3719-114">全般</span><span class="sxs-lookup"><span data-stu-id="f3719-114">General</span></span>|<span data-ttu-id="f3719-115">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="f3719-115">Optional attribute.</span></span> <span data-ttu-id="f3719-116">メソッドの名前付きパラメーターを指定します。</span><span class="sxs-lookup"><span data-stu-id="f3719-116">Specifies named parameters of the method.</span></span> <span data-ttu-id="f3719-117">複数の名前付きパラメーターはコンマで区切られます。</span><span class="sxs-lookup"><span data-stu-id="f3719-117">Multiple named parameters are separated by commas.</span></span> <span data-ttu-id="f3719-118">`Signature` 属性は、オーバー ロードされたメソッドを区別するために使用します。</span><span class="sxs-lookup"><span data-stu-id="f3719-118">The `Signature` attribute is used to differentiate overloaded methods.</span></span>|  
|`Arguments`|<span data-ttu-id="f3719-119">全般</span><span class="sxs-lookup"><span data-stu-id="f3719-119">General</span></span>|<span data-ttu-id="f3719-120">必須の属性です。</span><span class="sxs-lookup"><span data-stu-id="f3719-120">Required attribute.</span></span> <span data-ttu-id="f3719-121">ジェネリック型の引数を指定します。</span><span class="sxs-lookup"><span data-stu-id="f3719-121">Specifies the generic type arguments.</span></span> <span data-ttu-id="f3719-122">複数の引数が存在する場合は、コンマで区切られます。</span><span class="sxs-lookup"><span data-stu-id="f3719-122">If multiple arguments are present, they are separated by commas.</span></span>|  
|`Browse`|<span data-ttu-id="f3719-123">リフレクション</span><span class="sxs-lookup"><span data-stu-id="f3719-123">Reflection</span></span>|<span data-ttu-id="f3719-124">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="f3719-124">Optional attribute.</span></span> <span data-ttu-id="f3719-125">メソッドに関する情報の照会やメソッドの列挙を制御しますが、実行時の動的呼び出しは有効にしません。</span><span class="sxs-lookup"><span data-stu-id="f3719-125">Controls querying for information about or enumerating a method but does not enable any dynamic invocation at run time.</span></span>|  
|`Dynamic`|<span data-ttu-id="f3719-126">リフレクション</span><span class="sxs-lookup"><span data-stu-id="f3719-126">Reflection</span></span>|<span data-ttu-id="f3719-127">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="f3719-127">Optional attribute.</span></span> <span data-ttu-id="f3719-128">コンストラクターまたはメソッドへの実行時アクセスを制御して、動的プログラミングを有効にします。</span><span class="sxs-lookup"><span data-stu-id="f3719-128">Controls runtime access to a constructor or method to enable dynamic programming.</span></span> <span data-ttu-id="f3719-129">このポリシーにより、実行時にメンバーを動的に呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="f3719-129">This policy ensures that a member can be invoked dynamically at run time.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="f3719-130">Name 属性</span><span class="sxs-lookup"><span data-stu-id="f3719-130">Name attribute</span></span>  
  
|<span data-ttu-id="f3719-131">値</span><span class="sxs-lookup"><span data-stu-id="f3719-131">Value</span></span>|<span data-ttu-id="f3719-132">説明</span><span class="sxs-lookup"><span data-stu-id="f3719-132">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="f3719-133">*method_name*</span><span class="sxs-lookup"><span data-stu-id="f3719-133">*method_name*</span></span>|<span data-ttu-id="f3719-134">メソッド名。</span><span class="sxs-lookup"><span data-stu-id="f3719-134">The method name.</span></span> <span data-ttu-id="f3719-135">メソッドの型は、親の [\<Type>](../../../docs/framework/net-native/type-element-net-native.md) 要素または [\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) 要素により定義されます。</span><span class="sxs-lookup"><span data-stu-id="f3719-135">The type of the method is defined by the parent [\<Type>](../../../docs/framework/net-native/type-element-net-native.md) or [\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) element.</span></span>|  
  
## <a name="signature-attribute"></a><span data-ttu-id="f3719-136">シグネチャ属性</span><span class="sxs-lookup"><span data-stu-id="f3719-136">Signature attribute</span></span>  
  
|<span data-ttu-id="f3719-137">値</span><span class="sxs-lookup"><span data-stu-id="f3719-137">Value</span></span>|<span data-ttu-id="f3719-138">説明</span><span class="sxs-lookup"><span data-stu-id="f3719-138">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="f3719-139">*method_signature*</span><span class="sxs-lookup"><span data-stu-id="f3719-139">*method_signature*</span></span>|<span data-ttu-id="f3719-140">メソッドの名前付きパラメーターを指定します。</span><span class="sxs-lookup"><span data-stu-id="f3719-140">Specifies the named parameters of the method.</span></span> <span data-ttu-id="f3719-141">複数のパラメーターが存在する場合はコンマで区切られます。</span><span class="sxs-lookup"><span data-stu-id="f3719-141">If multiple parameters are present, they are separated by commas.</span></span>|  
  
## <a name="arguments-attribute"></a><span data-ttu-id="f3719-142">引数属性</span><span class="sxs-lookup"><span data-stu-id="f3719-142">Arguments attribute</span></span>  
  
|<span data-ttu-id="f3719-143">値</span><span class="sxs-lookup"><span data-stu-id="f3719-143">Value</span></span>|<span data-ttu-id="f3719-144">説明</span><span class="sxs-lookup"><span data-stu-id="f3719-144">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="f3719-145">*method_arguments*</span><span class="sxs-lookup"><span data-stu-id="f3719-145">*method_arguments*</span></span>|<span data-ttu-id="f3719-146">ジェネリック型引数を指定します。</span><span class="sxs-lookup"><span data-stu-id="f3719-146">Specifies the generic type arguments.</span></span> <span data-ttu-id="f3719-147">複数の引数が存在する場合は、コンマで区切られます。</span><span class="sxs-lookup"><span data-stu-id="f3719-147">If multiple arguments are present, they are separated by commas.</span></span> <span data-ttu-id="f3719-148">各引数は、完全修飾型名で構成されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="f3719-148">Each argument must consist of the fully qualified type name.</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="f3719-149">その他すべての属性</span><span class="sxs-lookup"><span data-stu-id="f3719-149">All other attributes</span></span>  
  
|<span data-ttu-id="f3719-150">値</span><span class="sxs-lookup"><span data-stu-id="f3719-150">Value</span></span>|<span data-ttu-id="f3719-151">説明</span><span class="sxs-lookup"><span data-stu-id="f3719-151">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="f3719-152">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="f3719-152">*policy_setting*</span></span>|<span data-ttu-id="f3719-153">メソッドのこのポリシーの種類に適用する設定です。</span><span class="sxs-lookup"><span data-stu-id="f3719-153">The setting to apply to this policy type for the method.</span></span> <span data-ttu-id="f3719-154">指定できる値は、`Auto`、`Excluded`、`Included`、および `Required` です。</span><span class="sxs-lookup"><span data-stu-id="f3719-154">Possible values are `Auto`, `Excluded`, `Included`, and `Required`.</span></span> <span data-ttu-id="f3719-155">詳細については、「[ランタイム ディレクティブのポリシー設定](../../../docs/framework/net-native/runtime-directive-policy-settings.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f3719-155">For more information, see [Runtime Directive Policy Settings](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f3719-156">子要素</span><span class="sxs-lookup"><span data-stu-id="f3719-156">Child Elements</span></span>  
 <span data-ttu-id="f3719-157">なし。</span><span class="sxs-lookup"><span data-stu-id="f3719-157">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f3719-158">親要素</span><span class="sxs-lookup"><span data-stu-id="f3719-158">Parent Elements</span></span>  
  
|<span data-ttu-id="f3719-159">要素</span><span class="sxs-lookup"><span data-stu-id="f3719-159">Element</span></span>|<span data-ttu-id="f3719-160">説明</span><span class="sxs-lookup"><span data-stu-id="f3719-160">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f3719-161">\<Type></span><span class="sxs-lookup"><span data-stu-id="f3719-161">\<Type></span></span>](../../../docs/framework/net-native/type-element-net-native.md)|<span data-ttu-id="f3719-162">型とそのすべてのメンバーにリフレクション ポリシーを適用します。</span><span class="sxs-lookup"><span data-stu-id="f3719-162">Applies reflection policy to a type and all its members.</span></span>|  
|[<span data-ttu-id="f3719-163">\<TypeInstantiation></span><span class="sxs-lookup"><span data-stu-id="f3719-163">\<TypeInstantiation></span></span>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)|<span data-ttu-id="f3719-164">構築されたジェネリック型とそのすべてのメンバーにリフレクション ポリシーを適用します。</span><span class="sxs-lookup"><span data-stu-id="f3719-164">Applies reflection policy to a constructed generic type and all its members.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f3719-165">コメント</span><span class="sxs-lookup"><span data-stu-id="f3719-165">Remarks</span></span>  
 <span data-ttu-id="f3719-166">`<MethodInstantiation>` 要素は、対応するオープン ジェネリック メソッドのランタイム リフレクション ポリシーをオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="f3719-166">The `<MethodInstantiation>` element overrides the runtime reflection policy of its corresponding open generic method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3719-167">関連項目</span><span class="sxs-lookup"><span data-stu-id="f3719-167">See Also</span></span>  
 [<span data-ttu-id="f3719-168">ランタイム ディレクティブ (rd.xml) 構成ファイル リファレンス</span><span class="sxs-lookup"><span data-stu-id="f3719-168">Runtime Directives (rd.xml) Configuration File Reference</span></span>](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)  
 [<span data-ttu-id="f3719-169">ランタイム ディレクティブ要素</span><span class="sxs-lookup"><span data-stu-id="f3719-169">Runtime Directive Elements</span></span>](../../../docs/framework/net-native/runtime-directive-elements.md)  
 [<span data-ttu-id="f3719-170">ランタイム ディレクティブ ポリシーの設定</span><span class="sxs-lookup"><span data-stu-id="f3719-170">Runtime Directive Policy Settings</span></span>](../../../docs/framework/net-native/runtime-directive-policy-settings.md)  
 [<span data-ttu-id="f3719-171">\<Method> 要素</span><span class="sxs-lookup"><span data-stu-id="f3719-171">\<Method> Element</span></span>](../../../docs/framework/net-native/method-element-net-native.md)
