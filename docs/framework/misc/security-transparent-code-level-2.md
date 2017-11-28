---
title: "透過的セキュリティ コード、レベル 2"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- transparency
- level 2 transparency
- security-transparent code
- security-critical code
ms.assetid: 4d05610a-0da6-4f08-acea-d54c9d6143c0
caps.latest.revision: "37"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 0bd4ee6c43b5089c45789b4f22326e17ec2218c8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="security-transparent-code-level-2"></a><span data-ttu-id="baaea-102">透過的セキュリティ コード、レベル 2</span><span class="sxs-lookup"><span data-stu-id="baaea-102">Security-Transparent Code, Level 2</span></span>
<a name="top"></a>
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 <span data-ttu-id="baaea-103">レベル 2 の透過性は、[!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] で導入されました。</span><span class="sxs-lookup"><span data-stu-id="baaea-103">Level 2 transparency was introduced in the [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)].</span></span> <span data-ttu-id="baaea-104">このモデルには、透過的なコード、セキュリティ セーフ クリティカル コード、およびセキュリティ クリティカル コードの 3 つの基本思想があります。</span><span class="sxs-lookup"><span data-stu-id="baaea-104">The three tenets of this model are transparent code, security-safe-critical code, and security-critical code.</span></span>  
  
-   <span data-ttu-id="baaea-105">透過的なコード (完全に信頼されて実行されているコードを含む) は、他の透過的なコードまたはセキュリティ セーフ クリティカル コードのみを呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="baaea-105">Transparent code, including code that is running as full trust, can call other transparent code or security-safe-critical code only.</span></span> <span data-ttu-id="baaea-106">また、ドメインの部分信頼アクセス許可セット (存在する場合) で許可されるアクションのみを実行できます。</span><span class="sxs-lookup"><span data-stu-id="baaea-106">It can only perform actions allowed by the domain’s partial trust permission set (if one exists).</span></span> <span data-ttu-id="baaea-107">透過的なコードでは、次のアクションは実行できません。</span><span class="sxs-lookup"><span data-stu-id="baaea-107">Transparent code cannot do the following:</span></span>  
  
    -   <span data-ttu-id="baaea-108">特権の <xref:System.Security.CodeAccessPermission.Assert%2A> または昇格を実行する。</span><span class="sxs-lookup"><span data-stu-id="baaea-108">Perform an <xref:System.Security.CodeAccessPermission.Assert%2A> or elevation of privilege.</span></span>  
  
    -   <span data-ttu-id="baaea-109">アンセーフ コードまたは検証不可能なコードを含める。</span><span class="sxs-lookup"><span data-stu-id="baaea-109">Contain unsafe or unverifiable code.</span></span>  
  
    -   <span data-ttu-id="baaea-110">クリティカル コードを直接呼び出す。</span><span class="sxs-lookup"><span data-stu-id="baaea-110">Directly call critical code.</span></span>  
  
    -   <span data-ttu-id="baaea-111">ネイティブ コードまたは <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> 属性を持つコードを呼び出す。</span><span class="sxs-lookup"><span data-stu-id="baaea-111">Call native code or code with the <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> attribute.</span></span>  
  
    -   <span data-ttu-id="baaea-112"><xref:System.Security.Permissions.SecurityAction.LinkDemand> によって保護されているメンバーを呼び出す。</span><span class="sxs-lookup"><span data-stu-id="baaea-112">Call a member that is protected by a <xref:System.Security.Permissions.SecurityAction.LinkDemand>.</span></span>  
  
    -   <span data-ttu-id="baaea-113">クリティカルな型を継承する。</span><span class="sxs-lookup"><span data-stu-id="baaea-113">Inherit from critical types.</span></span>  
  
     <span data-ttu-id="baaea-114">また、透過的メソッドでは、クリティカルな仮想メソッドをオーバーライドしたりクリティカルなインターフェイス メソッドを実装したりすることはできません。</span><span class="sxs-lookup"><span data-stu-id="baaea-114">In addition, transparent methods cannot override critical virtual methods or implement critical interface methods.</span></span>  
  
-   <span data-ttu-id="baaea-115">セーフ クリティカル コードは完全に信頼されていますが、透過的なコードから呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="baaea-115">Safe-critical code is fully trusted but is callable by transparent code.</span></span> <span data-ttu-id="baaea-116">また、完全に信頼されたコードのうち限られた領域のみを公開します。正確性とセキュリティの検証はセーフ クリティカル コード内で実行されます。</span><span class="sxs-lookup"><span data-stu-id="baaea-116">It exposes a limited surface area of full-trust code; correctness and security verifications happen in safe-critical code.</span></span>  
  
-   <span data-ttu-id="baaea-117">セキュリティ クリティカル コードは任意のコードを呼び出すことができ、完全に信頼されていますが、透過的なコードから呼び出すことはできません。</span><span class="sxs-lookup"><span data-stu-id="baaea-117">Security-critical code can call any code and is fully trusted, but it cannot be called by transparent code.</span></span>  
  
 <span data-ttu-id="baaea-118">このトピックは、次のセクションで構成されています。</span><span class="sxs-lookup"><span data-stu-id="baaea-118">This topic contains the following sections:</span></span>  
  
-   [<span data-ttu-id="baaea-119">使用例と動作</span><span class="sxs-lookup"><span data-stu-id="baaea-119">Usage Examples and Behaviors</span></span>](#examples)  
  
-   [<span data-ttu-id="baaea-120">オーバーライドのパターン</span><span class="sxs-lookup"><span data-stu-id="baaea-120">Override Patterns</span></span>](#override)  
  
-   [<span data-ttu-id="baaea-121">継承規則</span><span class="sxs-lookup"><span data-stu-id="baaea-121">Inheritance Rules</span></span>](#inheritance)  
  
-   [<span data-ttu-id="baaea-122">追加情報と規則</span><span class="sxs-lookup"><span data-stu-id="baaea-122">Additional Information and Rules</span></span>](#additional)  
  
<a name="examples"></a>   
## <a name="usage-examples-and-behaviors"></a><span data-ttu-id="baaea-123">使用例と動作</span><span class="sxs-lookup"><span data-stu-id="baaea-123">Usage Examples and Behaviors</span></span>  
 <span data-ttu-id="baaea-124">[!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] の規則 (レベル 2 の透過性) を指定するには、アセンブリに対して次の注釈を使用します。</span><span class="sxs-lookup"><span data-stu-id="baaea-124">To specify [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] rules (level 2 transparency), use the following annotation for an assembly:</span></span>  
  
```  
[assembly: SecurityRules(SecurityRuleSet.Level2)]  
```  
  
 <span data-ttu-id="baaea-125">.NET Framework 2.0 のルール (レベル 1 の透過性) にロックするには、次の注釈に使用します。</span><span class="sxs-lookup"><span data-stu-id="baaea-125">To lock into the .NET Framework 2.0 rules (level 1 transparency), use the following annotation:</span></span>  
  
```  
[assembly: SecurityRules(SecurityRuleSet.Level1)]  
```  
  
 <span data-ttu-id="baaea-126">アセンブリに注釈を付けない場合は、既定で、[!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] の規則が使用されます。</span><span class="sxs-lookup"><span data-stu-id="baaea-126">If you do not annotate an assembly, the [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] rules are used by default.</span></span> <span data-ttu-id="baaea-127">ただし、推奨されるベスト プラクティスは、使用するは、<xref:System.Security.SecurityRulesAttribute>属性の既定値の代わりにします。</span><span class="sxs-lookup"><span data-stu-id="baaea-127">However, the recommended best practice is to use the <xref:System.Security.SecurityRulesAttribute> attribute instead of depending on the default.</span></span>  
  
### <a name="assembly-wide-annotation"></a><span data-ttu-id="baaea-128">アセンブリ全体の注釈</span><span class="sxs-lookup"><span data-stu-id="baaea-128">Assembly-wide Annotation</span></span>  
 <span data-ttu-id="baaea-129">アセンブリ レベルでの属性の使用には、次の規則が適用されます。</span><span class="sxs-lookup"><span data-stu-id="baaea-129">The following rules apply to the use of attributes at the assembly level:</span></span>  
  
-   <span data-ttu-id="baaea-130">属性なし: 属性を指定しない場合は、ランタイムによってすべてのコードがセキュリティ クリティカルとして解釈されます。ただし、セキュリティ クリティカルであると継承規則に違反する場合 (たとえば、透過的な仮想メソッドまたはインターフェイス メソッドをオーバーライドまたは実装する場合) は除きます。</span><span class="sxs-lookup"><span data-stu-id="baaea-130">No attributes: If you do not specify any attributes, the runtime interprets all code as security-critical, except where being security-critical violates an inheritance rule (for example, when overriding or implementing a transparent virtual or interface method).</span></span> <span data-ttu-id="baaea-131">そのような場合、メソッドはセーフ クリティカルになります。</span><span class="sxs-lookup"><span data-stu-id="baaea-131">In those cases, the methods are safe-critical.</span></span> <span data-ttu-id="baaea-132">属性を指定しない場合、透過性規則は共通言語ランタイムによって自動的に判断されます。</span><span class="sxs-lookup"><span data-stu-id="baaea-132">Specifying no attribute causes the common language runtime to determine the transparency rules for you.</span></span>  
  
-   <span data-ttu-id="baaea-133">`SecurityTransparent`: すべてのコードが透過的になります。アセンブリ全体で特権の必要な操作や安全でない操作は実行されません。</span><span class="sxs-lookup"><span data-stu-id="baaea-133">`SecurityTransparent`: All code is transparent; the entire assembly will not do anything privileged or unsafe.</span></span>  
  
-   <span data-ttu-id="baaea-134">`SecurityCritical`: このアセンブリ内の型によって導入されるすべてのコードはクリティカルになり、その他のすべてのコードは透過的になります。</span><span class="sxs-lookup"><span data-stu-id="baaea-134">`SecurityCritical`: All code that is introduced by types in this assembly is critical; all other code is transparent.</span></span> <span data-ttu-id="baaea-135">このシナリオは属性を指定しない場合に似ていますが、共通言語ランタイムによって透過性規則が自動的に判断されることはありません。</span><span class="sxs-lookup"><span data-stu-id="baaea-135">This scenario is similar to not specifying any attributes; however, the common language runtime does not automatically determine the transparency rules.</span></span> <span data-ttu-id="baaea-136">たとえば、仮想メソッドまたは抽象メソッドをオーバーライドしたり、インターフェイス メソッドを実装したりする場合、既定では、そのメソッドは透過的になります。</span><span class="sxs-lookup"><span data-stu-id="baaea-136">For example, if you override a virtual or abstract method or implement an interface method, by default, that method is transparent.</span></span> <span data-ttu-id="baaea-137">そのメソッドには `SecurityCritical` または `SecuritySafeCritical` の注釈を明示的に付ける必要があります。そうしないと、読み込み時に <xref:System.TypeLoadException> がスローされます。</span><span class="sxs-lookup"><span data-stu-id="baaea-137">You must explicitly annotate the method as `SecurityCritical` or `SecuritySafeCritical`; otherwise, a <xref:System.TypeLoadException> will be thrown at load time.</span></span> <span data-ttu-id="baaea-138">この規則は、基底クラスと派生クラスの両方が同じアセンブリ内にある場合にも適用されます。</span><span class="sxs-lookup"><span data-stu-id="baaea-138">This rule also applies when both the base class and the derived class are in the same assembly.</span></span>  
  
-   <span data-ttu-id="baaea-139">`AllowPartiallyTrustedCallers` (レベル 2 のみ): すべてのコードが既定で透過的になります。</span><span class="sxs-lookup"><span data-stu-id="baaea-139">`AllowPartiallyTrustedCallers` (level 2 only): All code defaults to transparent.</span></span> <span data-ttu-id="baaea-140">ただし、個々の型やメンバーに他の属性を設定することもできます。</span><span class="sxs-lookup"><span data-stu-id="baaea-140">However, individual types and members can have other attributes.</span></span>  
  
 <span data-ttu-id="baaea-141">レベル 2 とレベル 1 のアセンブリ レベルの動作の比較を次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="baaea-141">The following table compares the assembly level behavior for Level 2 with Level 1 .</span></span>  
  
|<span data-ttu-id="baaea-142">Assembly 属性</span><span class="sxs-lookup"><span data-stu-id="baaea-142">Assembly attribute</span></span>|<span data-ttu-id="baaea-143">レベル 2</span><span class="sxs-lookup"><span data-stu-id="baaea-143">Level 2</span></span>|<span data-ttu-id="baaea-144">レベル 1</span><span class="sxs-lookup"><span data-stu-id="baaea-144">Level 1</span></span>|  
|------------------------|-------------|-------------|  
|<span data-ttu-id="baaea-145">部分的に信頼されたアセンブリで属性なし</span><span class="sxs-lookup"><span data-stu-id="baaea-145">No attribute on a partially trusted assembly</span></span>|<span data-ttu-id="baaea-146">型およびメンバーは既定で透過的になりますが、セキュリティ クリティカルまたはセキュリティ セーフ クリティカルにすることもできます。</span><span class="sxs-lookup"><span data-stu-id="baaea-146">Types and members are by default transparent, but can be security-critical or security-safe-critical.</span></span>|<span data-ttu-id="baaea-147">すべての型およびメンバーは透過的です。</span><span class="sxs-lookup"><span data-stu-id="baaea-147">All types and members are transparent.</span></span>|  
|<span data-ttu-id="baaea-148">属性なし</span><span class="sxs-lookup"><span data-stu-id="baaea-148">No attribute</span></span>|<span data-ttu-id="baaea-149">属性を指定しない場合、透過性規則は共通言語ランタイムによって自動的に判断されます。</span><span class="sxs-lookup"><span data-stu-id="baaea-149">Specifying no attribute causes the common language runtime to determine the transparency rules for you.</span></span> <span data-ttu-id="baaea-150">すべての型およびメンバーはセキュリティ クリティカルになります (ただし、セキュリティ クリティカルになると継承ルールに違反する場所を除く)。</span><span class="sxs-lookup"><span data-stu-id="baaea-150">All types and members are security-critical, except where being security-critical violates an inheritance rule.</span></span>|<span data-ttu-id="baaea-151">完全に信頼されたアセンブリ (グローバル アセンブリ キャッシュ内に存在するか、`AppDomain` で完全に信頼と指定されている) では、すべての型は透過的であり、すべてのメンバーはセキュリティ セーフ クリティカルです。</span><span class="sxs-lookup"><span data-stu-id="baaea-151">On a fully trusted assembly (in the global assembly cache or identified as full trust in the `AppDomain`) all types are transparent and all members are security-safe-critical.</span></span>|  
|`SecurityTransparent`|<span data-ttu-id="baaea-152">すべての型およびメンバーは透過的です。</span><span class="sxs-lookup"><span data-stu-id="baaea-152">All types and members are transparent.</span></span>|<span data-ttu-id="baaea-153">すべての型およびメンバーは透過的です。</span><span class="sxs-lookup"><span data-stu-id="baaea-153">All types and members are transparent.</span></span>|  
|`SecurityCritical(SecurityCriticalScope.Everything)`|<span data-ttu-id="baaea-154">該当しない。</span><span class="sxs-lookup"><span data-stu-id="baaea-154">Not applicable.</span></span>|<span data-ttu-id="baaea-155">すべての型およびメンバーはセキュリティ クリティカルです。</span><span class="sxs-lookup"><span data-stu-id="baaea-155">All types and members are security-critical.</span></span>|  
|`SecurityCritical`|<span data-ttu-id="baaea-156">このアセンブリ内の型によって導入されるすべてのコードはクリティカルになり、その他のすべてのコードは透過的になります。</span><span class="sxs-lookup"><span data-stu-id="baaea-156">All code that is introduced by types in this assembly is critical; all other code is transparent.</span></span> <span data-ttu-id="baaea-157">仮想メソッドまたは抽象メソッドをオーバーライドしたり、インターフェイス メソッドを実装したりする場合は、メソッドに `SecurityCritical` または `SecuritySafeCritical` の注釈を明示的に付ける必要があります。</span><span class="sxs-lookup"><span data-stu-id="baaea-157">If you override a virtual or abstract method or implement an interface method, you must explicitly annotate the method as `SecurityCritical` or `SecuritySafeCritical`.</span></span>|<span data-ttu-id="baaea-158">すべてのコードは既定で透過的になります。</span><span class="sxs-lookup"><span data-stu-id="baaea-158">All code defaults to transparent.</span></span> <span data-ttu-id="baaea-159">ただし、個々の型やメンバーに他の属性を設定することもできます。</span><span class="sxs-lookup"><span data-stu-id="baaea-159">However, individual types and members can have other attributes.</span></span>|  
  
### <a name="type-and-member-annotation"></a><span data-ttu-id="baaea-160">型およびメンバーの注釈</span><span class="sxs-lookup"><span data-stu-id="baaea-160">Type and Member Annotation</span></span>  
 <span data-ttu-id="baaea-161">型に適用されるセキュリティ属性は、その型によって導入されるメンバーにも適用されます。</span><span class="sxs-lookup"><span data-stu-id="baaea-161">The security attributes that are applied to a type also apply to the members that are introduced by the type.</span></span> <span data-ttu-id="baaea-162">ただし、基底クラスまたはインターフェイスの実装の仮想オーバーライドや抽象オーバーライドには適用されません。</span><span class="sxs-lookup"><span data-stu-id="baaea-162">However, they do not apply to virtual or abstract overrides of the base class or interface implementations.</span></span> <span data-ttu-id="baaea-163">型およびメンバーのレベルでの属性の使用には、次の規則が適用されます。</span><span class="sxs-lookup"><span data-stu-id="baaea-163">The following rules apply to the use of attributes at the type and member level:</span></span>  
  
-   <span data-ttu-id="baaea-164">`SecurityCritical`: 型またはメンバーはクリティカルで、完全に信頼されているコードからのみ呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="baaea-164">`SecurityCritical`: The type or member is critical and can be called only by full-trust code.</span></span> <span data-ttu-id="baaea-165">セキュリティ クリティカルな型で導入されるメソッドはクリティカルです。</span><span class="sxs-lookup"><span data-stu-id="baaea-165">Methods that are introduced in a security-critical type are critical.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="baaea-166">基底クラスまたはインターフェイスで導入されてセキュリティ クリティカルなクラスでオーバーライドまたは実装される仮想メソッドおよび抽象メソッドは、既定では透過的です。</span><span class="sxs-lookup"><span data-stu-id="baaea-166">Virtual and abstract methods that are introduced in base classes or interfaces, and overridden or implemented in a security-critical class are transparent by default.</span></span> <span data-ttu-id="baaea-167">これらのメソッドは、`SecuritySafeCritical` または `SecurityCritical` のいずれかとして指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="baaea-167">They must be identified as either `SecuritySafeCritical` or `SecurityCritical`.</span></span>  
  
-   <span data-ttu-id="baaea-168">`SecuritySafeCritical`: 型またはメンバーはセーフ クリティカルです。</span><span class="sxs-lookup"><span data-stu-id="baaea-168">`SecuritySafeCritical`: The type or member is safe-critical.</span></span> <span data-ttu-id="baaea-169">ただし、型またはメンバーは透過的な (部分的に信頼された) コードから呼び出すことができ、機能的に他のクリティカル コードと同等になります。</span><span class="sxs-lookup"><span data-stu-id="baaea-169">However, the type or member can be called from transparent (partially trusted) code and is as capable as any other critical code.</span></span> <span data-ttu-id="baaea-170">コードはセキュリティ監査を受ける必要があります。</span><span class="sxs-lookup"><span data-stu-id="baaea-170">The code must be audited for security.</span></span>  
  
 [<span data-ttu-id="baaea-171">ページのトップへ</span><span class="sxs-lookup"><span data-stu-id="baaea-171">Back to top</span></span>](#top)  
  
<a name="override"></a>   
## <a name="override-patterns"></a><span data-ttu-id="baaea-172">オーバーライドのパターン</span><span class="sxs-lookup"><span data-stu-id="baaea-172">Override Patterns</span></span>  
 <span data-ttu-id="baaea-173">レベル 2 の透過性で使用できるメソッドのオーバーライドを次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="baaea-173">The following table shows the method overrides allowed for level 2 transparency.</span></span>  
  
|<span data-ttu-id="baaea-174">基底クラスの仮想/インターフェイス メンバー</span><span class="sxs-lookup"><span data-stu-id="baaea-174">Base virtual/interface member</span></span>|<span data-ttu-id="baaea-175">オーバーライド/インターフェイス</span><span class="sxs-lookup"><span data-stu-id="baaea-175">Override/interface</span></span>|  
|------------------------------------|-------------------------|  
|`Transparent`|`Transparent`|  
|`Transparent`|`SafeCritical`|  
|`SafeCritical`|`Transparent`|  
|`SafeCritical`|`SafeCritical`|  
|`Critical`|`Critical`|  
  
 [<span data-ttu-id="baaea-176">ページのトップへ</span><span class="sxs-lookup"><span data-stu-id="baaea-176">Back to top</span></span>](#top)  
  
<a name="inheritance"></a>   
## <a name="inheritance-rules"></a><span data-ttu-id="baaea-177">継承規則</span><span class="sxs-lookup"><span data-stu-id="baaea-177">Inheritance Rules</span></span>  
 <span data-ttu-id="baaea-178">このセクションでは、アクセスおよび機能に基づいて、次の順序が `Transparent`、`Critical`、および `SafeCritical` のコードに割り当てられています。</span><span class="sxs-lookup"><span data-stu-id="baaea-178">In this section, the following order is assigned to `Transparent`, `Critical`, and `SafeCritical` code based on access and capabilities:</span></span>  
  
 `Transparent` < `SafeCritical` < `Critical`  
  
-   <span data-ttu-id="baaea-179">型の規則: 左から右に向かってアクセス制限がより厳しくなります。</span><span class="sxs-lookup"><span data-stu-id="baaea-179">Rules for types: Going from left to right, access becomes more restrictive.</span></span> <span data-ttu-id="baaea-180">派生型は、基本型と少なくとも同じ程度に制限する必要があります。</span><span class="sxs-lookup"><span data-stu-id="baaea-180">Derived types must be at least as restrictive as the base type.</span></span>  
  
-   <span data-ttu-id="baaea-181">メソッドの規則。基底メソッドのアクセシビリティを派生メソッドで変更することはできません。</span><span class="sxs-lookup"><span data-stu-id="baaea-181">Rules for methods: Derived methods cannot change accessibility from the base method.</span></span> <span data-ttu-id="baaea-182">既定の動作では、注釈のない派生メソッドはすべて `Transparent` になります。</span><span class="sxs-lookup"><span data-stu-id="baaea-182">For default behavior, all derived methods that are not annotated are `Transparent`.</span></span> <span data-ttu-id="baaea-183">クリティカルな型の派生型では、オーバーライドしたメソッドに `SecurityCritical` の注釈が明示的に付けられていない場合に、例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="baaea-183">Derivatives of critical types cause an exception to be thrown if the overridden method is not explicitly annotated as `SecurityCritical`.</span></span>  
  
 <span data-ttu-id="baaea-184">次の表に、使用できる型の継承パターンを示します。</span><span class="sxs-lookup"><span data-stu-id="baaea-184">The following table shows the allowed type inheritance patterns.</span></span>  
  
|<span data-ttu-id="baaea-185">基底クラス</span><span class="sxs-lookup"><span data-stu-id="baaea-185">Base class</span></span>|<span data-ttu-id="baaea-186">派生クラスで可能なレベル</span><span class="sxs-lookup"><span data-stu-id="baaea-186">Derived class can be</span></span>|  
|----------------|--------------------------|  
|`Transparent`|`Transparent`|  
|`Transparent`|`SafeCritical`|  
|`Transparent`|`Critical`|  
|`SafeCritical`|`SafeCritical`|  
|`SafeCritical`|`Critical`|  
|`Critical`|`Critical`|  
  
 <span data-ttu-id="baaea-187">次の表に、使用できない型の継承パターンを示します。</span><span class="sxs-lookup"><span data-stu-id="baaea-187">The following table shows the disallowed type inheritance patterns.</span></span>  
  
|<span data-ttu-id="baaea-188">基底クラス</span><span class="sxs-lookup"><span data-stu-id="baaea-188">Base class</span></span>|<span data-ttu-id="baaea-189">派生クラスで不可のレベル</span><span class="sxs-lookup"><span data-stu-id="baaea-189">Derived class cannot be</span></span>|  
|----------------|-----------------------------|  
|`SafeCritical`|`Transparent`|  
|`Critical`|`Transparent`|  
|`Critical`|`SafeCritical`|  
  
 <span data-ttu-id="baaea-190">次の表に、使用できるメソッドの継承パターンを示します。</span><span class="sxs-lookup"><span data-stu-id="baaea-190">The following table shows the allowed method inheritance patterns.</span></span>  
  
|<span data-ttu-id="baaea-191">基底メソッド</span><span class="sxs-lookup"><span data-stu-id="baaea-191">Base method</span></span>|<span data-ttu-id="baaea-192">派生メソッドで可能なレベル</span><span class="sxs-lookup"><span data-stu-id="baaea-192">Derived method can be</span></span>|  
|-----------------|---------------------------|  
|`Transparent`|`Transparent`|  
|`Transparent`|`SafeCritical`|  
|`SafeCritical`|`Transparent`|  
|`SafeCritical`|`SafeCritical`|  
|`Critical`|`Critical`|  
  
 <span data-ttu-id="baaea-193">次の表に、使用できないメソッドの継承パターンを示します。</span><span class="sxs-lookup"><span data-stu-id="baaea-193">The following table shows the disallowed method inheritance patterns.</span></span>  
  
|<span data-ttu-id="baaea-194">基底メソッド</span><span class="sxs-lookup"><span data-stu-id="baaea-194">Base method</span></span>|<span data-ttu-id="baaea-195">派生メソッドで不可のレベル</span><span class="sxs-lookup"><span data-stu-id="baaea-195">Derived method cannot be</span></span>|  
|-----------------|------------------------------|  
|`Transparent`|`Critical`|  
|`SafeCritical`|`Critical`|  
|`Critical`|`Transparent`|  
|`Critical`|`SafeCritical`|  
  
> [!NOTE]
>  <span data-ttu-id="baaea-196">これらの継承規則は、レベル 2 の型およびメンバーに適用されます。</span><span class="sxs-lookup"><span data-stu-id="baaea-196">These inheritance rules apply to level 2 types and members.</span></span> <span data-ttu-id="baaea-197">レベル 1 アセンブリ内の型は、レベル 2 のセキュリティ クリティカルな型およびメンバーから継承できます。</span><span class="sxs-lookup"><span data-stu-id="baaea-197">Types in level 1 assemblies can inherit from level 2 security-critical types and members.</span></span> <span data-ttu-id="baaea-198">したがって、レベル 2 の型およびメンバーでは、レベル 1 の継承先に対して個別の継承確認要求が必要です。</span><span class="sxs-lookup"><span data-stu-id="baaea-198">Therefore, level 2 types and members must have separate inheritance demands for level 1 inheritors.</span></span>  
  
 [<span data-ttu-id="baaea-199">ページのトップへ</span><span class="sxs-lookup"><span data-stu-id="baaea-199">Back to top</span></span>](#top)  
  
<a name="additional"></a>   
## <a name="additional-information-and-rules"></a><span data-ttu-id="baaea-200">追加情報と規則</span><span class="sxs-lookup"><span data-stu-id="baaea-200">Additional Information and Rules</span></span>  
  
### <a name="linkdemand-support"></a><span data-ttu-id="baaea-201">LinkDemand のサポート</span><span class="sxs-lookup"><span data-stu-id="baaea-201">LinkDemand Support</span></span>  
 <span data-ttu-id="baaea-202">レベル 2 の透過性モデルでは、<xref:System.Security.Permissions.SecurityAction.LinkDemand> は <xref:System.Security.SecurityCriticalAttribute> 属性に置き換えられます。</span><span class="sxs-lookup"><span data-stu-id="baaea-202">The level 2 transparency model replaces the <xref:System.Security.Permissions.SecurityAction.LinkDemand> with the <xref:System.Security.SecurityCriticalAttribute> attribute.</span></span> <span data-ttu-id="baaea-203">レガシ (レベル 1) コードでは、<xref:System.Security.Permissions.SecurityAction.LinkDemand> は自動的 <xref:System.Security.Permissions.SecurityAction.Demand> として扱われます。</span><span class="sxs-lookup"><span data-stu-id="baaea-203">In legacy (level 1) code, a <xref:System.Security.Permissions.SecurityAction.LinkDemand> is automatically treated as a <xref:System.Security.Permissions.SecurityAction.Demand>.</span></span>  
  
### <a name="reflection"></a><span data-ttu-id="baaea-204">反射</span><span class="sxs-lookup"><span data-stu-id="baaea-204">Reflection</span></span>  
 <span data-ttu-id="baaea-205">クリティカル メソッドを呼び出したりクリティカル フィールドを読み取ったりすると、完全信頼の確認要求がトリガーされます (プライベート メソッドまたはプライベート フィールドを呼び出す場合と同様)。</span><span class="sxs-lookup"><span data-stu-id="baaea-205">Invoking a critical method or reading a critical field triggers a demand for full trust (just as if you were invoking a private method or field).</span></span> <span data-ttu-id="baaea-206">したがって、完全に信頼されているコードではクリティカル メソッドを呼び出すことができるのに対し、部分的に信頼されたコードでは呼び出すことができません。</span><span class="sxs-lookup"><span data-stu-id="baaea-206">Therefore, full-trust code can invoke a critical method, whereas partial-trust code cannot.</span></span>  
  
 <span data-ttu-id="baaea-207"><xref:System.Reflection> 名前空間に追加された <xref:System.Type.IsSecurityCritical%2A>、<xref:System.Reflection.MethodBase.IsSecuritySafeCritical%2A>、および <xref:System.Reflection.MethodBase.IsSecurityTransparent%2A> の各プロパティを使用すると、型、メソッド、またはフィールドが `SecurityCritical`、`SecuritySafeCritical`、または `SecurityTransparent` のどれであるかを判断できます。</span><span class="sxs-lookup"><span data-stu-id="baaea-207">The following properties have been added to the <xref:System.Reflection> namespace to determine whether the type, method, or field is `SecurityCritical`, `SecuritySafeCritical`, or `SecurityTransparent`:  <xref:System.Type.IsSecurityCritical%2A>, <xref:System.Reflection.MethodBase.IsSecuritySafeCritical%2A>, and <xref:System.Reflection.MethodBase.IsSecurityTransparent%2A>.</span></span> <span data-ttu-id="baaea-208">属性の存在を確認する代わりに、リフレクションを使用して透過性を判断するには、これらのプロパティを使用します。</span><span class="sxs-lookup"><span data-stu-id="baaea-208">Use these properties to determine transparency by using reflection instead of checking for the presence of the attribute.</span></span> <span data-ttu-id="baaea-209">透過性の規則は複雑なので、属性のチェックでは不十分なことがあります。</span><span class="sxs-lookup"><span data-stu-id="baaea-209">The transparency rules are complex, and checking for the attribute may not be sufficient.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="baaea-210">A`SafeCritical`メソッドを返します。`true`両方の<xref:System.Type.IsSecurityCritical%2A>と<xref:System.Reflection.MethodBase.IsSecuritySafeCritical%2A>ので、`SafeCritical`が実際にクリティカルである (クリティカル コードと同じ機能を備えているが、透過的なコードから呼び出すことができます)。</span><span class="sxs-lookup"><span data-stu-id="baaea-210">A `SafeCritical` method returns `true` for both <xref:System.Type.IsSecurityCritical%2A> and <xref:System.Reflection.MethodBase.IsSecuritySafeCritical%2A>, because `SafeCritical` is indeed critical (it has the same capabilities as critical code, but it can be called from transparent code).</span></span>  
  
 <span data-ttu-id="baaea-211">動的メソッドは、関連付けられているモジュールの透過性を継承します。型の透過性は継承しません (型に関連付けられている場合)。</span><span class="sxs-lookup"><span data-stu-id="baaea-211">Dynamic methods inherit the transparency of the modules they are attached to; they do not inherit the transparency of the type (if they are attached to a type).</span></span>  
  
### <a name="skip-verification-in-full-trust"></a><span data-ttu-id="baaea-212">完全な信頼での検証のスキップ</span><span class="sxs-lookup"><span data-stu-id="baaea-212">Skip Verification in Full Trust</span></span>  
 <span data-ttu-id="baaea-213">完全に信頼されている透過的なアセンブリの検証をスキップするには、<xref:System.Security.SecurityRulesAttribute> 属性の <xref:System.Security.SecurityRulesAttribute.SkipVerificationInFullTrust%2A> プロパティを `true` に設定します。</span><span class="sxs-lookup"><span data-stu-id="baaea-213">You can skip verification for fully trusted transparent assemblies by setting the <xref:System.Security.SecurityRulesAttribute.SkipVerificationInFullTrust%2A> property to `true` in the <xref:System.Security.SecurityRulesAttribute> attribute:</span></span>  
  
 `[assembly: SecurityRules(SecurityRuleSet.Level2, SkipVerificationInFullTrust = true)]`  
  
 <span data-ttu-id="baaea-214"><xref:System.Security.SecurityRulesAttribute.SkipVerificationInFullTrust%2A> プロパティは既定では `false` であるため、検証をスキップするにはこのプロパティを `true` に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="baaea-214">The <xref:System.Security.SecurityRulesAttribute.SkipVerificationInFullTrust%2A> property is `false` by default, so the property must be set to `true` to skip verification.</span></span> <span data-ttu-id="baaea-215">これをするのは、最適化のためだけにしてください。</span><span class="sxs-lookup"><span data-stu-id="baaea-215">This should be done for optimization purposes only.</span></span> <span data-ttu-id="baaea-216">使用して、アセンブリの透過的なコードが検証可能なことを確認、`transparent`オプション、 [PEVerify ツール](../../../docs/framework/tools/peverify-exe-peverify-tool.md)です。</span><span class="sxs-lookup"><span data-stu-id="baaea-216">You should ensure that the transparent code in the assembly is verifiable by using the `transparent` option in the [PEVerify tool](../../../docs/framework/tools/peverify-exe-peverify-tool.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="baaea-217">関連項目</span><span class="sxs-lookup"><span data-stu-id="baaea-217">See Also</span></span>  
 [<span data-ttu-id="baaea-218">セキュリティ透過的なコード、レベル 1</span><span class="sxs-lookup"><span data-stu-id="baaea-218">Security-Transparent Code, Level 1</span></span>](../../../docs/framework/misc/security-transparent-code-level-1.md)  
 [<span data-ttu-id="baaea-219">セキュリティの変更</span><span class="sxs-lookup"><span data-stu-id="baaea-219">Security Changes</span></span>](../../../docs/framework/security/security-changes.md)
