---
title: '&lt;Property&gt; 要素 (.NET ネイティブ)'
ms.date: 03/30/2017
ms.assetid: ad4ba56d-3bcb-4c10-ba90-1cc66e2175a1
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8a857523b15631aa9c112c9c0d208d96b0ec0d4a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33396460"
---
# <a name="ltpropertygt-element-net-native"></a><span data-ttu-id="ab073-102">&lt;Property&gt; 要素 (.NET ネイティブ)</span><span class="sxs-lookup"><span data-stu-id="ab073-102">&lt;Property&gt; Element (.NET Native)</span></span>
<span data-ttu-id="ab073-103">プロパティにランタイム リフレクション ポリシーを適用します。</span><span class="sxs-lookup"><span data-stu-id="ab073-103">Applies runtime reflection policy to a property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ab073-104">構文</span><span class="sxs-lookup"><span data-stu-id="ab073-104">Syntax</span></span>  
  
```xml  
<Property Name="property_name"  
          Browse="policy_type"  
          Dynamic="policy_type"  
          Serialize="policy_type" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ab073-105">属性および要素</span><span class="sxs-lookup"><span data-stu-id="ab073-105">Attributes and Elements</span></span>  
 <span data-ttu-id="ab073-106">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="ab073-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ab073-107">属性</span><span class="sxs-lookup"><span data-stu-id="ab073-107">Attributes</span></span>  
  
|<span data-ttu-id="ab073-108">属性</span><span class="sxs-lookup"><span data-stu-id="ab073-108">Attribute</span></span>|<span data-ttu-id="ab073-109">属性の型</span><span class="sxs-lookup"><span data-stu-id="ab073-109">Attribute type</span></span>|<span data-ttu-id="ab073-110">説明</span><span class="sxs-lookup"><span data-stu-id="ab073-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="ab073-111">全般</span><span class="sxs-lookup"><span data-stu-id="ab073-111">General</span></span>|<span data-ttu-id="ab073-112">必須の属性です。</span><span class="sxs-lookup"><span data-stu-id="ab073-112">Required attribute.</span></span> <span data-ttu-id="ab073-113">プロパティ名を指定します。</span><span class="sxs-lookup"><span data-stu-id="ab073-113">Specifies the property name.</span></span>|  
|`Browse`|<span data-ttu-id="ab073-114">リフレクション</span><span class="sxs-lookup"><span data-stu-id="ab073-114">Reflection</span></span>|<span data-ttu-id="ab073-115">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="ab073-115">Optional attribute.</span></span> <span data-ttu-id="ab073-116">プロパティに関する情報の照会やプロパティの列挙を制御しますが、実行時の動的アクセスは有効にしません。</span><span class="sxs-lookup"><span data-stu-id="ab073-116">Controls querying for information about or enumerating the property but does not enable any dynamic access at run time.</span></span>|  
|`Dynamic`|<span data-ttu-id="ab073-117">リフレクション</span><span class="sxs-lookup"><span data-stu-id="ab073-117">Reflection</span></span>|<span data-ttu-id="ab073-118">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="ab073-118">Optional attribute.</span></span> <span data-ttu-id="ab073-119">プロパティへの実行時アクセスを制御して、動的プログラミングを有効にします。</span><span class="sxs-lookup"><span data-stu-id="ab073-119">Controls runtime access to the property to enable dynamic programming.</span></span> <span data-ttu-id="ab073-120">このポリシーによって、実行時にプロパティを動的に設定または取得できるようになります。</span><span class="sxs-lookup"><span data-stu-id="ab073-120">This policy ensures that a property can be set or retrieved dynamically at run time.</span></span>|  
|`Serialize`|<span data-ttu-id="ab073-121">シリアル化</span><span class="sxs-lookup"><span data-stu-id="ab073-121">Serialization</span></span>|<span data-ttu-id="ab073-122">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="ab073-122">Optional attribute.</span></span> <span data-ttu-id="ab073-123">プロパティへの実行時アクセスを制御して、型インスタンスを Newtonsoft の JSON シリアライザーなどのライブラリによってシリアル化できるようにしたり、データ バインディングで使用できるようにしたりします。</span><span class="sxs-lookup"><span data-stu-id="ab073-123">Controls runtime access to a property to enable type instances to be serialized by libraries such as the Newtonsoft JSON serializer or to be used for data binding.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="ab073-124">Name 属性</span><span class="sxs-lookup"><span data-stu-id="ab073-124">Name attribute</span></span>  
  
|<span data-ttu-id="ab073-125">値</span><span class="sxs-lookup"><span data-stu-id="ab073-125">Value</span></span>|<span data-ttu-id="ab073-126">説明</span><span class="sxs-lookup"><span data-stu-id="ab073-126">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="ab073-127">*method_name*</span><span class="sxs-lookup"><span data-stu-id="ab073-127">*method_name*</span></span>|<span data-ttu-id="ab073-128">プロパティ名。</span><span class="sxs-lookup"><span data-stu-id="ab073-128">The property name.</span></span> <span data-ttu-id="ab073-129">プロパティの型は、親の [\<Type>](../../../docs/framework/net-native/type-element-net-native.md) または [\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) 要素により定義されます。</span><span class="sxs-lookup"><span data-stu-id="ab073-129">The type of the property is defined by the parent [\<Type>](../../../docs/framework/net-native/type-element-net-native.md) or [\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) element.</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="ab073-130">その他すべての属性</span><span class="sxs-lookup"><span data-stu-id="ab073-130">All other attributes</span></span>  
  
|<span data-ttu-id="ab073-131">値</span><span class="sxs-lookup"><span data-stu-id="ab073-131">Value</span></span>|<span data-ttu-id="ab073-132">説明</span><span class="sxs-lookup"><span data-stu-id="ab073-132">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="ab073-133">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="ab073-133">*policy_setting*</span></span>|<span data-ttu-id="ab073-134">プロパティのこのポリシーの種類に適用する設定です。</span><span class="sxs-lookup"><span data-stu-id="ab073-134">The setting to apply to this policy type for the property.</span></span> <span data-ttu-id="ab073-135">指定できる値は、`Auto`、`Excluded`、`Included`、および `Required` です。</span><span class="sxs-lookup"><span data-stu-id="ab073-135">Possible values are `Auto`, `Excluded`, `Included`, and `Required`.</span></span> <span data-ttu-id="ab073-136">詳細については、「[ランタイム ディレクティブのポリシー設定](../../../docs/framework/net-native/runtime-directive-policy-settings.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ab073-136">For more information, see [Runtime Directive Policy Settings](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ab073-137">子要素</span><span class="sxs-lookup"><span data-stu-id="ab073-137">Child Elements</span></span>  
 <span data-ttu-id="ab073-138">なし。</span><span class="sxs-lookup"><span data-stu-id="ab073-138">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ab073-139">親要素</span><span class="sxs-lookup"><span data-stu-id="ab073-139">Parent Elements</span></span>  
  
|<span data-ttu-id="ab073-140">要素</span><span class="sxs-lookup"><span data-stu-id="ab073-140">Element</span></span>|<span data-ttu-id="ab073-141">説明</span><span class="sxs-lookup"><span data-stu-id="ab073-141">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ab073-142">\<Type></span><span class="sxs-lookup"><span data-stu-id="ab073-142">\<Type></span></span>](../../../docs/framework/net-native/type-element-net-native.md)|<span data-ttu-id="ab073-143">型とそのすべてのメンバーにリフレクション ポリシーを適用します。</span><span class="sxs-lookup"><span data-stu-id="ab073-143">Applies reflection policy to a type and all its members.</span></span>|  
|[<span data-ttu-id="ab073-144">\<TypeInstantiation></span><span class="sxs-lookup"><span data-stu-id="ab073-144">\<TypeInstantiation></span></span>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)|<span data-ttu-id="ab073-145">構築されたジェネリック型とそのすべてのメンバーにリフレクション ポリシーを適用します。</span><span class="sxs-lookup"><span data-stu-id="ab073-145">Applies reflection policy to a constructed generic type and all its members.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ab073-146">コメント</span><span class="sxs-lookup"><span data-stu-id="ab073-146">Remarks</span></span>  
 <span data-ttu-id="ab073-147">プロパティのポリシーが明示的に定義されていない場合は、親要素の実行時ポリシーを継承します。</span><span class="sxs-lookup"><span data-stu-id="ab073-147">If a property's policy is not explicitly defined, it inherits the runtime policy of its parent element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ab073-148">例</span><span class="sxs-lookup"><span data-stu-id="ab073-148">Example</span></span>  
 <span data-ttu-id="ab073-149">次の例では、リフレクションを使用して、`Book` オブジェクトをインスタンス化し、そのプロパティ値を表示します。</span><span class="sxs-lookup"><span data-stu-id="ab073-149">The following example uses reflection to instantiate a `Book` object and display its property values.</span></span> <span data-ttu-id="ab073-150">プロジェクトの既定の default.rd.xml ファイルは、次のように示されます。</span><span class="sxs-lookup"><span data-stu-id="ab073-150">The original default.rd.xml file for the project appears as follows:</span></span>  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
   <Application>  
      <Namespace Name="LibraryApplications"  Browse="Required Public" >  
         <Type Name="Book"   Activate="All" />  
      </Namespace>  
   </Application>  
</Directives>  
```  
  
 <span data-ttu-id="ab073-151">このファイルは、`All` クラスの `Activate` ポリシーに `Book` 値を適用します。これにより、リフレクションを介してクラス コンストラクターにアクセスできるようになります。</span><span class="sxs-lookup"><span data-stu-id="ab073-151">The file applies the `All` value to the `Activate` policy for the `Book` class, which allows access to class constructors through reflection.</span></span> <span data-ttu-id="ab073-152">`Browse` クラスの `Book` ポリシーは、その親名前空間から継承されます。</span><span class="sxs-lookup"><span data-stu-id="ab073-152">The `Browse` policy for the `Book` class is inherited from its parent namespace.</span></span> <span data-ttu-id="ab073-153">これは `Required Public` に設定され、メタデータが実行時に使用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="ab073-153">This is set to `Required Public`, which makes metadata available at runtime.</span></span>  
  
 <span data-ttu-id="ab073-154">この例のソース コードを次に示します。</span><span class="sxs-lookup"><span data-stu-id="ab073-154">The following is the source code for the example.</span></span> <span data-ttu-id="ab073-155">`outputBlock` 変数は、[TextBlock](http://msdn.microsoft.com/library/windows.ui.xaml.controls.textblock.aspx) コントロールを表します。</span><span class="sxs-lookup"><span data-stu-id="ab073-155">The `outputBlock` variable represents a [TextBlock](http://msdn.microsoft.com/library/windows.ui.xaml.controls.textblock.aspx) control.</span></span>  
  
 [!code-csharp[ProjectN_Reflection#6](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/property1.cs#6)]  
  
 <span data-ttu-id="ab073-156">ただし、この例をコンパイルして実行すると、[MissingRuntimeArtifactException](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md) 例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="ab073-156">However, compiling and executing this example throws a [MissingRuntimeArtifactException](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md) exception.</span></span> <span data-ttu-id="ab073-157">`Book` 型のメタデータは使用可能になりましたが、プロパティの getter の実装は動的に使用可能になりませんでした。</span><span class="sxs-lookup"><span data-stu-id="ab073-157">Although we've made metadata for the `Book` type available, we've failed to make the implementations of the property getters available dynamically.</span></span> <span data-ttu-id="ab073-158">このエラーは、次の 2 つの方法のいずれかを使用して修正できます。</span><span class="sxs-lookup"><span data-stu-id="ab073-158">We can correct this error by either in one of two ways:</span></span>  
  
-   <span data-ttu-id="ab073-159">[\<Type](../../../docs/framework/net-native/type-element-net-native.md) 要素で `Book` 型の `Dynamic` ポリシーを定義する。</span><span class="sxs-lookup"><span data-stu-id="ab073-159">by defining the `Dynamic` policy for the `Book` type in its [\<Type>](../../../docs/framework/net-native/type-element-net-native.md) element.</span></span>  
  
-   <span data-ttu-id="ab073-160">次の default.rd.xml ファイルのように、呼び出す getter を持つ各プロパティに入れ子になった [\<Property>](../../../docs/framework/net-native/property-element-net-native.md) 要素を追加する。</span><span class="sxs-lookup"><span data-stu-id="ab073-160">By adding a nested [\<Property>](../../../docs/framework/net-native/property-element-net-native.md) element for each property whose getter we'd like to invoke, as the following default.rd.xml file does.</span></span>  
  
    ```xml  
    <Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
       <Application>  
          <Namespace Name="LibraryApplications"  Browse="Required Public" >  
             <Type Name="Book"   Activate="All" >  
                <Property Name="Title" Dynamic="Required" />  
                <Property Name="Author" Dynamic="Required" />  
                  <Property Name="ISBN" Dynamic="Required" />  
             </Type>  
          </Namespace>  
       </Application>  
    </Directives>  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="ab073-161">関連項目</span><span class="sxs-lookup"><span data-stu-id="ab073-161">See Also</span></span>  
 [<span data-ttu-id="ab073-162">ランタイム ディレクティブ (rd.xml) 構成ファイル リファレンス</span><span class="sxs-lookup"><span data-stu-id="ab073-162">Runtime Directives (rd.xml) Configuration File Reference</span></span>](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)  
 [<span data-ttu-id="ab073-163">ランタイム ディレクティブ要素</span><span class="sxs-lookup"><span data-stu-id="ab073-163">Runtime Directive Elements</span></span>](../../../docs/framework/net-native/runtime-directive-elements.md)  
 [<span data-ttu-id="ab073-164">ランタイム ディレクティブ ポリシーの設定</span><span class="sxs-lookup"><span data-stu-id="ab073-164">Runtime Directive Policy Settings</span></span>](../../../docs/framework/net-native/runtime-directive-policy-settings.md)
