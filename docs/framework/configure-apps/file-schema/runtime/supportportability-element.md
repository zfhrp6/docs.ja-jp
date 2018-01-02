---
title: "&lt;supportPortability&gt;要素"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- supportPortability element
- <supportPortability> element
ms.assetid: 6453ef66-19b4-41f3-b712-52d0c2abc9ca
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9776e900015dad8bce8c16991b8ce0aeb6067812
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ltsupportportabilitygt-element"></a><span data-ttu-id="78e27-102">&lt;supportPortability&gt;要素</span><span class="sxs-lookup"><span data-stu-id="78e27-102">&lt;supportPortability&gt; Element</span></span>
<span data-ttu-id="78e27-103">.NET Framework の 2 つの異なる実装にある同じアセンブリを 1 つのアプリケーションから参照できるように、既定の動作を無効にすることができます。既定の動作では、アプリケーションの移植性を高めるために、このようなアセンブリは同等のものとして扱われます。</span><span class="sxs-lookup"><span data-stu-id="78e27-103">Specifies that an application can reference the same assembly in two different implementations of the .NET Framework, by disabling the default behavior that treats the assemblies as equivalent for application portability purposes.</span></span>  
  
 <span data-ttu-id="78e27-104">\<configuration > 要素</span><span class="sxs-lookup"><span data-stu-id="78e27-104">\<configuration> Element</span></span>  
<span data-ttu-id="78e27-105">\<ランタイム > 要素</span><span class="sxs-lookup"><span data-stu-id="78e27-105">\<runtime> Element</span></span>  
<span data-ttu-id="78e27-106">\<assemblyBinding > 要素</span><span class="sxs-lookup"><span data-stu-id="78e27-106">\<assemblyBinding> Element</span></span>  
<span data-ttu-id="78e27-107">\<supportPortability > 要素</span><span class="sxs-lookup"><span data-stu-id="78e27-107">\<supportPortability> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="78e27-108">構文</span><span class="sxs-lookup"><span data-stu-id="78e27-108">Syntax</span></span>  
  
```xml  
<supportPortability PKT="public_key_token" enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="78e27-109">属性および要素</span><span class="sxs-lookup"><span data-stu-id="78e27-109">Attributes and Elements</span></span>  
 <span data-ttu-id="78e27-110">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="78e27-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="78e27-111">属性</span><span class="sxs-lookup"><span data-stu-id="78e27-111">Attributes</span></span>  
  
|<span data-ttu-id="78e27-112">属性</span><span class="sxs-lookup"><span data-stu-id="78e27-112">Attribute</span></span>|<span data-ttu-id="78e27-113">説明</span><span class="sxs-lookup"><span data-stu-id="78e27-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="78e27-114">PKT</span><span class="sxs-lookup"><span data-stu-id="78e27-114">PKT</span></span>|<span data-ttu-id="78e27-115">必須の属性です。</span><span class="sxs-lookup"><span data-stu-id="78e27-115">Required attribute.</span></span><br /><br /> <span data-ttu-id="78e27-116">対象となるアセンブリの公開キー トークンを文字列で指定します。</span><span class="sxs-lookup"><span data-stu-id="78e27-116">Specifies the public key token of the affected assembly, as a string.</span></span>|  
|<span data-ttu-id="78e27-117">enabled</span><span class="sxs-lookup"><span data-stu-id="78e27-117">enabled</span></span>|<span data-ttu-id="78e27-118">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="78e27-118">Optional attribute.</span></span><br /><br /> <span data-ttu-id="78e27-119">指定した .NET Framework アセンブリの複数の実装間での移植性に対するサポートを有効にするかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="78e27-119">Specifies whether support for portability between implementations of the specified .NET Framework assembly should be enabled.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="78e27-120">enabled 属性</span><span class="sxs-lookup"><span data-stu-id="78e27-120">enabled Attribute</span></span>  
  
|<span data-ttu-id="78e27-121">値</span><span class="sxs-lookup"><span data-stu-id="78e27-121">Value</span></span>|<span data-ttu-id="78e27-122">説明</span><span class="sxs-lookup"><span data-stu-id="78e27-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="78e27-123">TRUE</span><span class="sxs-lookup"><span data-stu-id="78e27-123">true</span></span>|<span data-ttu-id="78e27-124">指定した .NET Framework アセンブリの複数の実装間での移植性に対するサポートを有効にします。</span><span class="sxs-lookup"><span data-stu-id="78e27-124">Enable support for portability between implementations of the specified .NET Framework assembly.</span></span> <span data-ttu-id="78e27-125">既定値です。</span><span class="sxs-lookup"><span data-stu-id="78e27-125">This is the default.</span></span>|  
|<span data-ttu-id="78e27-126">false</span><span class="sxs-lookup"><span data-stu-id="78e27-126">false</span></span>|<span data-ttu-id="78e27-127">指定した .NET Framework アセンブリの複数の実装間での移植性に対するサポートを無効にします。</span><span class="sxs-lookup"><span data-stu-id="78e27-127">Disable support for portability between implementations of the specified .NET Framework assembly.</span></span> <span data-ttu-id="78e27-128">この場合、指定したアセンブリの複数の実装をアプリケーションで参照できます。</span><span class="sxs-lookup"><span data-stu-id="78e27-128">This enables the application to have references to multiple implementations of the specified assembly.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="78e27-129">子要素</span><span class="sxs-lookup"><span data-stu-id="78e27-129">Child Elements</span></span>  
 <span data-ttu-id="78e27-130">なし。</span><span class="sxs-lookup"><span data-stu-id="78e27-130">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="78e27-131">親要素</span><span class="sxs-lookup"><span data-stu-id="78e27-131">Parent Elements</span></span>  
  
|<span data-ttu-id="78e27-132">要素</span><span class="sxs-lookup"><span data-stu-id="78e27-132">Element</span></span>|<span data-ttu-id="78e27-133">説明</span><span class="sxs-lookup"><span data-stu-id="78e27-133">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="78e27-134">共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。</span><span class="sxs-lookup"><span data-stu-id="78e27-134">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="78e27-135">アセンブリのバインディングとガベージ コレクションに関する情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="78e27-135">Contains information about assembly binding and garbage collection.</span></span>|  
|`assemblyBinding`|<span data-ttu-id="78e27-136">アセンブリ バージョンのリダイレクトおよびアセンブリの位置に関する情報が含まれます。</span><span class="sxs-lookup"><span data-stu-id="78e27-136">Contains information about assembly version redirection and the locations of assemblies.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="78e27-137">コメント</span><span class="sxs-lookup"><span data-stu-id="78e27-137">Remarks</span></span>  
 <span data-ttu-id="78e27-138">以降で、[!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)]が自動的にサポート、.NET Framework の 2 つの実装のいずれかを使用するアプリケーションなど、.NET Framework の実装または .NET Framework for Silverlight の実装です。</span><span class="sxs-lookup"><span data-stu-id="78e27-138">Beginning with the [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], support is automatically provided for applications that can use either of two implementations of the .NET Framework, for example either the .NET Framework implementation or the .NET Framework for Silverlight implementation.</span></span> <span data-ttu-id="78e27-139">特定の .NET Framework アセンブリの 2 つの実装は、アセンブリ バインダーで同等と見なされます。</span><span class="sxs-lookup"><span data-stu-id="78e27-139">The two implementations of a particular .NET Framework assembly are seen as equivalent by the assembly binder.</span></span> <span data-ttu-id="78e27-140">一部のシナリオでは、アプリケーションの移植性を高めるためのこの機能が問題になります。</span><span class="sxs-lookup"><span data-stu-id="78e27-140">In a few scenarios, this application portability feature causes problems.</span></span> <span data-ttu-id="78e27-141">そのようなシナリオでは、`<supportPortability>` 要素を使用して、この機能を無効にすることができます。</span><span class="sxs-lookup"><span data-stu-id="78e27-141">In those scenarios, the `<supportPortability>` element can be used to disable the feature.</span></span>  
  
 <span data-ttu-id="78e27-142">一例として、特定の参照アセンブリの .NET Framework の実装と .NET Framework for Silverlight の実装の両方を参照する必要があるアセンブリが挙げられます。</span><span class="sxs-lookup"><span data-stu-id="78e27-142">One such scenario is an assembly that has to reference both the .NET Framework implementation and the .NET Framework for Silverlight implementation of a particular reference assembly.</span></span> <span data-ttu-id="78e27-143">たとえば、WPF (Windows Presentation Foundation) で作成された XAML デザイナーにおいて、デザイナーのユーザー インターフェイスとして WPF デスクトップの実装を参照すると共に、Silverlight の実装に組み込まれている WPF のサブセットも参照する必要がある場合があります。</span><span class="sxs-lookup"><span data-stu-id="78e27-143">For example, a XAML designer written in Windows Presentation Foundation (WPF) might need to reference both the WPF Desktop implementation, for the designer's user interface, and the subset of WPF that is included in the Silverlight implementation.</span></span> <span data-ttu-id="78e27-144">既定では、この 2 つのアセンブリはアセンブリ バインディングで同等と見なされるため、別々に参照するとコンパイラ エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="78e27-144">By default, the separate references cause a compiler error, because assembly binding sees the two assemblies as equivalent.</span></span> <span data-ttu-id="78e27-145">この要素を使用すると、既定の動作を無効にし、コンパイルを正常に実行できます。</span><span class="sxs-lookup"><span data-stu-id="78e27-145">This element disables the default behavior, and allows compilation to succeed.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="78e27-146">コンパイラから共通言語ランタイムのアセンブリ バインディング ロジックに情報を渡すには、`/appconfig` コンパイラ オプションを使用して、この要素を含む app.config ファイルの場所を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="78e27-146">In order for the compiler to pass the information to the common language runtime's assembly-binding logic, you must use the `/appconfig` compiler option to specify the location of the app.config file that contains this element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="78e27-147">例</span><span class="sxs-lookup"><span data-stu-id="78e27-147">Example</span></span>  
 <span data-ttu-id="78e27-148">.NET Framework と .NET Framework for Silverlight の両方の実装に存在する .NET Framework アセンブリについて、その両方の実装をアプリケーションで参照できるようにする例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="78e27-148">The following example enables an application to have references to both the .NET Framework implementation and the .NET Framework for Silverlight implementation of any .NET Framework assembly that exists in both implementations.</span></span> <span data-ttu-id="78e27-149">`/appconfig` コンパイラ オプションを使用して、この app.config ファイルの場所を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="78e27-149">The `/appconfig` compiler option must be used to specify the location of this app.config file.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding>  
         <supportPortability PKT="7cec85d7bea7798e" enable="false"/>  
         <supportPortability PKT="31bf3856ad364e35" enable="false"/>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="78e27-150">参照</span><span class="sxs-lookup"><span data-stu-id="78e27-150">See Also</span></span>  
 [<span data-ttu-id="78e27-151">/appconfig (c# コンパイラ オプション)</span><span class="sxs-lookup"><span data-stu-id="78e27-151">/appconfig (C# Compiler Options)</span></span>](http://msdn.microsoft.com/library/ee523958.aspx)  
 [<span data-ttu-id="78e27-152">.NET framework アセンブリの統一の概要</span><span class="sxs-lookup"><span data-stu-id="78e27-152">.NET Framework Assembly Unification Overview</span></span>](http://msdn.microsoft.com/en-us/8d8cc65e-031d-463b-bde3-2c6dc2e3bc48)
