---
title: "&lt;enforceFIPSPolicy&gt;要素"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- enforceFIPSPolicy element
- FIPS
- <enforceFIPSPolicy> element
- Federal Information Processing Standards (FIPS)
ms.assetid: c35509c4-35cf-43c0-bb47-75e4208aa24e
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 9bd593c17d752b35919985aad37f675c62e6ce34
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="ltenforcefipspolicygt-element"></a><span data-ttu-id="ea0d5-102">&lt;enforceFIPSPolicy&gt;要素</span><span class="sxs-lookup"><span data-stu-id="ea0d5-102">&lt;enforceFIPSPolicy&gt; Element</span></span>
<span data-ttu-id="ea0d5-103">暗号化アルゴリズムが連邦情報処理規格 (FIPS: Federal Information Processing Standard) に準拠する必要があるコンピューターの構成要件を強制するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="ea0d5-103">Specifies whether to enforce a computer configuration requirement that cryptographic algorithms must comply with the Federal Information Processing Standards (FIPS).</span></span>  
  
 <span data-ttu-id="ea0d5-104">\<configuration > 要素</span><span class="sxs-lookup"><span data-stu-id="ea0d5-104">\<configuration> Element</span></span>  
<span data-ttu-id="ea0d5-105">\<ランタイム > 要素</span><span class="sxs-lookup"><span data-stu-id="ea0d5-105">\<runtime> Element</span></span>  
<span data-ttu-id="ea0d5-106">\<enforceFIPSPolicy > 要素</span><span class="sxs-lookup"><span data-stu-id="ea0d5-106">\<enforceFIPSPolicy> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ea0d5-107">構文</span><span class="sxs-lookup"><span data-stu-id="ea0d5-107">Syntax</span></span>  
  
```xml  
<enforceFIPSPolicy enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ea0d5-108">属性および要素</span><span class="sxs-lookup"><span data-stu-id="ea0d5-108">Attributes and Elements</span></span>  
 <span data-ttu-id="ea0d5-109">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="ea0d5-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ea0d5-110">属性</span><span class="sxs-lookup"><span data-stu-id="ea0d5-110">Attributes</span></span>  
  
|<span data-ttu-id="ea0d5-111">属性</span><span class="sxs-lookup"><span data-stu-id="ea0d5-111">Attribute</span></span>|<span data-ttu-id="ea0d5-112">説明</span><span class="sxs-lookup"><span data-stu-id="ea0d5-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ea0d5-113">enabled</span><span class="sxs-lookup"><span data-stu-id="ea0d5-113">enabled</span></span>|<span data-ttu-id="ea0d5-114">必須の属性です。</span><span class="sxs-lookup"><span data-stu-id="ea0d5-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="ea0d5-115">暗号化アルゴリズムは FIPS に準拠する必要があります、コンピューターの構成要件の適用を有効にするかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="ea0d5-115">Specifies whether to enable the enforcement of a computer configuration requirement that cryptographic algorithms must be compliant with FIPS.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="ea0d5-116">enabled 属性</span><span class="sxs-lookup"><span data-stu-id="ea0d5-116">enabled Attribute</span></span>  
  
|<span data-ttu-id="ea0d5-117">値</span><span class="sxs-lookup"><span data-stu-id="ea0d5-117">Value</span></span>|<span data-ttu-id="ea0d5-118">説明</span><span class="sxs-lookup"><span data-stu-id="ea0d5-118">Description</span></span>|  
|-----------|-----------------|  
|`true`|<span data-ttu-id="ea0d5-119">お使いのコンピューターが、FIPS 対応である暗号アルゴリズムを要求するように構成されている場合は、その要件が適用されます。</span><span class="sxs-lookup"><span data-stu-id="ea0d5-119">If your computer is configured to require cryptographic algorithms to be FIPS compliant, that requirement is enforced.</span></span> <span data-ttu-id="ea0d5-120">クラス コンス トラクターは、FIPS 準拠アルゴリズムを実装する場合または`Create`そのコンピューターで実行された場合、そのクラスのメソッドが例外をスローします。</span><span class="sxs-lookup"><span data-stu-id="ea0d5-120">If a class implements an algorithm that is not compliant with FIPS, the constructors or `Create` methods for that class throw exceptions when they are run on that computer.</span></span> <span data-ttu-id="ea0d5-121">既定値です。</span><span class="sxs-lookup"><span data-stu-id="ea0d5-121">This is the default.</span></span>|  
|`false`|<span data-ttu-id="ea0d5-122">アプリケーションで使用される暗号アルゴリズムは、コンピューターの構成に関係なく、FIPS に準拠する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="ea0d5-122">Cryptographic algorithms that are used by the application are not required to be compliant with FIPS, regardless of computer configuration.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ea0d5-123">子要素</span><span class="sxs-lookup"><span data-stu-id="ea0d5-123">Child Elements</span></span>  
 <span data-ttu-id="ea0d5-124">なし。</span><span class="sxs-lookup"><span data-stu-id="ea0d5-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ea0d5-125">親要素</span><span class="sxs-lookup"><span data-stu-id="ea0d5-125">Parent Elements</span></span>  
  
|<span data-ttu-id="ea0d5-126">要素</span><span class="sxs-lookup"><span data-stu-id="ea0d5-126">Element</span></span>|<span data-ttu-id="ea0d5-127">説明</span><span class="sxs-lookup"><span data-stu-id="ea0d5-127">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="ea0d5-128">共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。</span><span class="sxs-lookup"><span data-stu-id="ea0d5-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="ea0d5-129">アセンブリのバインディングとガベージ コレクションに関する情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="ea0d5-129">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ea0d5-130">コメント</span><span class="sxs-lookup"><span data-stu-id="ea0d5-130">Remarks</span></span>  
 <span data-ttu-id="ea0d5-131">以降、.NET Framework 2.0 では、暗号アルゴリズムを実装するクラスの作成は、コンピューターの構成によって制御されます。</span><span class="sxs-lookup"><span data-stu-id="ea0d5-131">Starting with the .NET Framework 2.0, the creation of classes that implement cryptographic algorithms is controlled by the configuration of the computer.</span></span> <span data-ttu-id="ea0d5-132">FIPS に準拠するアルゴリズムを要求するように、コンピューターが構成されており、クラスが FIPS に準拠していないするアルゴリズムを実装する、そのクラスのインスタンスを作成しようとするとは、例外をスローします。</span><span class="sxs-lookup"><span data-stu-id="ea0d5-132">If the computer is configured to require algorithms to be compliant with FIPS, and a class implements an algorithm that is not compliant with FIPS, any attempt to create an instance of that class throws an exception.</span></span> <span data-ttu-id="ea0d5-133">コンス トラクターをスロー、<xref:System.InvalidOperationException>例外、および`Create`メソッドをスロー、<xref:System.Reflection.TargetInvocationException>と内部例外<xref:System.InvalidOperationException>例外。</span><span class="sxs-lookup"><span data-stu-id="ea0d5-133">Constructors throw an <xref:System.InvalidOperationException> exception, and `Create` methods throw a <xref:System.Reflection.TargetInvocationException> exception with an inner <xref:System.InvalidOperationException> exception.</span></span>  
  
 <span data-ttu-id="ea0d5-134">アプリケーションの構成が FIPS 準拠を必要とするコンピューターで実行して、アルゴリズムが FIPS に準拠していないが使用されて、アプリケーション、することができます要素を使用してこの構成ファイルで、共通言語ランタイム (CLR) を防ぐためにFIPS 準拠を適用します。</span><span class="sxs-lookup"><span data-stu-id="ea0d5-134">If your application runs on computers whose configurations require compliance with FIPS, and your application uses an algorithm that is not compliant with FIPS, you can use this element in your configuration file to prevent the common language runtime (CLR) from enforcing FIPS compliance.</span></span> <span data-ttu-id="ea0d5-135">この要素で導入された、[!INCLUDE[net_v20SP1_long](../../../../../includes/net-v20sp1-long-md.md)]です。</span><span class="sxs-lookup"><span data-stu-id="ea0d5-135">This element was introduced in the [!INCLUDE[net_v20SP1_long](../../../../../includes/net-v20sp1-long-md.md)].</span></span>  
  
## <a name="example"></a><span data-ttu-id="ea0d5-136">例</span><span class="sxs-lookup"><span data-stu-id="ea0d5-136">Example</span></span>  
 <span data-ttu-id="ea0d5-137">次の例では、CLR が FIPS 準拠を適用することを防止する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="ea0d5-137">The following example shows how to prevent the CLR from enforcing FIPS compliance.</span></span>  
  
```xml  
<configuration>  
    <runtime>  
        <enforceFIPSPolicy enabled="false"/>  
    </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="ea0d5-138">関連項目</span><span class="sxs-lookup"><span data-stu-id="ea0d5-138">See Also</span></span>  
 [<span data-ttu-id="ea0d5-139">ランタイム設定スキーマ</span><span class="sxs-lookup"><span data-stu-id="ea0d5-139">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="ea0d5-140">構成ファイル スキーマ</span><span class="sxs-lookup"><span data-stu-id="ea0d5-140">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="ea0d5-141">暗号モデル</span><span class="sxs-lookup"><span data-stu-id="ea0d5-141">Cryptography Model</span></span>](../../../../../docs/standard/security/cryptography-model.md)
