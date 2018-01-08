---
title: "完全修飾型名の指定"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- names [.NET Framework], fully qualified type names
- reflection, fully qualified type names
- names [.NET Framework], assemblies
- tokens
- BNF
- assemblies [.NET Framework], names
- Backus-Naur form
- languages, BNF grammar
- fully qualified type names
- type names
- special characters
- IDENTIFIER
ms.assetid: d90b1e39-9115-4f2a-81c0-05e7e74e5580
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e19aebbeee7fd65e27704af49185a1b8d48b9639
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="specifying-fully-qualified-type-names"></a><span data-ttu-id="6ad33-102">完全修飾型名の指定</span><span class="sxs-lookup"><span data-stu-id="6ad33-102">Specifying Fully Qualified Type Names</span></span>
<span data-ttu-id="6ad33-103">多様なリフレクション操作に対して有効な入力の型名を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6ad33-103">You must specify type names to have valid input to various reflection operations.</span></span> <span data-ttu-id="6ad33-104">完全修飾型名は、アセンブリ名の指定、名前空間の指定、および型名で構成されます。</span><span class="sxs-lookup"><span data-stu-id="6ad33-104">A fully qualified type name consists of an assembly name specification, a namespace specification, and a type name.</span></span> <span data-ttu-id="6ad33-105">型名の指定は、<xref:System.Type.GetType%2A?displayProperty=nameWithType>、<xref:System.Reflection.Module.GetType%2A?displayProperty=nameWithType>、<xref:System.Reflection.Emit.ModuleBuilder.GetType%2A?displayProperty=nameWithType>、<xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> などのメソッドで使用されます。</span><span class="sxs-lookup"><span data-stu-id="6ad33-105">Type name specifications are used by methods such as <xref:System.Type.GetType%2A?displayProperty=nameWithType>, <xref:System.Reflection.Module.GetType%2A?displayProperty=nameWithType>, <xref:System.Reflection.Emit.ModuleBuilder.GetType%2A?displayProperty=nameWithType>, and <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType>.</span></span>  
  
## <a name="backus-naur-form-grammar-for-type-names"></a><span data-ttu-id="6ad33-106">型名の BNF 文法</span><span class="sxs-lookup"><span data-stu-id="6ad33-106">Backus-Naur Form Grammar for Type Names</span></span>  
 <span data-ttu-id="6ad33-107">バッカスナウア記法 (BNF) は、正式な言語の構文を定義しています。</span><span class="sxs-lookup"><span data-stu-id="6ad33-107">The Backus-Naur form (BNF) defines the syntax of formal languages.</span></span> <span data-ttu-id="6ad33-108">次の表は、有効な入力を認識する方法を示す BNF 構文規則の一覧です。</span><span class="sxs-lookup"><span data-stu-id="6ad33-108">The following table lists BNF lexical rules that describe how to recognize a valid input.</span></span> <span data-ttu-id="6ad33-109">終端要素 (これ以上は単純化できない要素) はすべて大文字で記載しています。</span><span class="sxs-lookup"><span data-stu-id="6ad33-109">Terminals (those elements that are not further reducible) are shown in all uppercase letters.</span></span> <span data-ttu-id="6ad33-110">非終端要素 (これ以上単純化することができる要素) は、大文字と小文字の混在、または単一引用符で囲まれた文字列で記載していますが、単一引用符 (') 自体は構文の一部ではありません。</span><span class="sxs-lookup"><span data-stu-id="6ad33-110">Nonterminals (those elements that are further reducible) are shown in mixed-case or singly quoted strings, but the single quote (') is not a part of the syntax itself.</span></span> <span data-ttu-id="6ad33-111">パイプ文字 (&#124;) は、サブ規則がある規則を示します。</span><span class="sxs-lookup"><span data-stu-id="6ad33-111">The pipe character (&#124;) denotes rules that have subrules.</span></span>  
  
|<span data-ttu-id="6ad33-112">完全修飾型名の BNF 文法</span><span class="sxs-lookup"><span data-stu-id="6ad33-112">BNF grammar of fully qualified type names</span></span>|  
|-----------------------------------------------|  
|<span data-ttu-id="6ad33-113">TypeSpec                          :=   ReferenceTypeSpec</span><span class="sxs-lookup"><span data-stu-id="6ad33-113">TypeSpec                          :=   ReferenceTypeSpec</span></span><br /><br /> <span data-ttu-id="6ad33-114">&#124;     SimpleTypeSpec</span><span class="sxs-lookup"><span data-stu-id="6ad33-114">&#124;     SimpleTypeSpec</span></span>|  
|<span data-ttu-id="6ad33-115">ReferenceTypeSpec            :=   SimpleTypeSpec '&'</span><span class="sxs-lookup"><span data-stu-id="6ad33-115">ReferenceTypeSpec            :=   SimpleTypeSpec '&'</span></span>|  
|<span data-ttu-id="6ad33-116">SimpleTypeSpec                :=   PointerTypeSpec</span><span class="sxs-lookup"><span data-stu-id="6ad33-116">SimpleTypeSpec                :=   PointerTypeSpec</span></span><br /><br /> <span data-ttu-id="6ad33-117">&#124;     ArrayTypeSpec</span><span class="sxs-lookup"><span data-stu-id="6ad33-117">&#124;     ArrayTypeSpec</span></span><br /><br /> <span data-ttu-id="6ad33-118">&#124;     TypeName</span><span class="sxs-lookup"><span data-stu-id="6ad33-118">&#124;     TypeName</span></span>|  
|<span data-ttu-id="6ad33-119">PointerTypeSpec                :=   SimpleTypeSpec '*'</span><span class="sxs-lookup"><span data-stu-id="6ad33-119">PointerTypeSpec                :=   SimpleTypeSpec '*'</span></span>|  
|<span data-ttu-id="6ad33-120">ArrayTypeSpec                  :=   SimpleTypeSpec '[ReflectionDimension]'</span><span class="sxs-lookup"><span data-stu-id="6ad33-120">ArrayTypeSpec                  :=   SimpleTypeSpec '[ReflectionDimension]'</span></span><br /><br /> <span data-ttu-id="6ad33-121">&#124;     SimpleTypeSpec '[ReflectionEmitDimension]'</span><span class="sxs-lookup"><span data-stu-id="6ad33-121">&#124;     SimpleTypeSpec '[ReflectionEmitDimension]'</span></span>|  
|<span data-ttu-id="6ad33-122">ReflectionDimension           :=   '*'</span><span class="sxs-lookup"><span data-stu-id="6ad33-122">ReflectionDimension           :=   '*'</span></span><br /><br /> <span data-ttu-id="6ad33-123">&#124;     ReflectionDimension ',' ReflectionDimension</span><span class="sxs-lookup"><span data-stu-id="6ad33-123">&#124;     ReflectionDimension ',' ReflectionDimension</span></span><br /><br /> <span data-ttu-id="6ad33-124">&#124;     NOTOKEN</span><span class="sxs-lookup"><span data-stu-id="6ad33-124">&#124;     NOTOKEN</span></span>|  
|<span data-ttu-id="6ad33-125">ReflectionEmitDimension    :=   '*'</span><span class="sxs-lookup"><span data-stu-id="6ad33-125">ReflectionEmitDimension    :=   '*'</span></span><br /><br /> <span data-ttu-id="6ad33-126">&#124;     Number '..'</span><span class="sxs-lookup"><span data-stu-id="6ad33-126">&#124;     Number '..'</span></span> <span data-ttu-id="6ad33-127">数値</span><span class="sxs-lookup"><span data-stu-id="6ad33-127">Number</span></span><br /><br /> <span data-ttu-id="6ad33-128">&#124;     Number '…'</span><span class="sxs-lookup"><span data-stu-id="6ad33-128">&#124;     Number '…'</span></span><br /><br /> <span data-ttu-id="6ad33-129">&#124;     ReflectionDimension ',' ReflectionDimension</span><span class="sxs-lookup"><span data-stu-id="6ad33-129">&#124;     ReflectionDimension ',' ReflectionDimension</span></span><br /><br /> <span data-ttu-id="6ad33-130">&#124;     NOTOKEN</span><span class="sxs-lookup"><span data-stu-id="6ad33-130">&#124;     NOTOKEN</span></span>|  
|<span data-ttu-id="6ad33-131">Number                            :=   [0-9]+</span><span class="sxs-lookup"><span data-stu-id="6ad33-131">Number                            :=   [0-9]+</span></span>|  
|<span data-ttu-id="6ad33-132">TypeName                         :=   NamespaceTypeName</span><span class="sxs-lookup"><span data-stu-id="6ad33-132">TypeName                         :=   NamespaceTypeName</span></span><br /><br /> <span data-ttu-id="6ad33-133">&#124;     NamespaceTypeName ',' AssemblyNameSpec</span><span class="sxs-lookup"><span data-stu-id="6ad33-133">&#124;     NamespaceTypeName ',' AssemblyNameSpec</span></span>|  
|<span data-ttu-id="6ad33-134">NamespaceTypeName        :=   NestedTypeName</span><span class="sxs-lookup"><span data-stu-id="6ad33-134">NamespaceTypeName        :=   NestedTypeName</span></span><br /><br /> <span data-ttu-id="6ad33-135">&#124;     NamespaceSpec '.'NestedTypeName</span><span class="sxs-lookup"><span data-stu-id="6ad33-135">&#124;     NamespaceSpec '.' NestedTypeName</span></span>|  
|<span data-ttu-id="6ad33-136">NestedTypeName               :=   IDENTIFIER</span><span class="sxs-lookup"><span data-stu-id="6ad33-136">NestedTypeName               :=   IDENTIFIER</span></span><br /><br /> <span data-ttu-id="6ad33-137">&#124;     NestedTypeName '+' IDENTIFIER</span><span class="sxs-lookup"><span data-stu-id="6ad33-137">&#124;     NestedTypeName '+' IDENTIFIER</span></span>|  
|<span data-ttu-id="6ad33-138">NamespaceSpec                 :=   IDENTIFIER</span><span class="sxs-lookup"><span data-stu-id="6ad33-138">NamespaceSpec                 :=   IDENTIFIER</span></span><br /><br /> <span data-ttu-id="6ad33-139">&#124;     NamespaceSpec '.'IDENTIFIER</span><span class="sxs-lookup"><span data-stu-id="6ad33-139">&#124;     NamespaceSpec '.' IDENTIFIER</span></span>|  
|<span data-ttu-id="6ad33-140">AssemblyNameSpec           :=   IDENTIFIER</span><span class="sxs-lookup"><span data-stu-id="6ad33-140">AssemblyNameSpec           :=   IDENTIFIER</span></span><br /><br /> <span data-ttu-id="6ad33-141">&#124;     IDENTIFIER ',' AssemblyProperties</span><span class="sxs-lookup"><span data-stu-id="6ad33-141">&#124;     IDENTIFIER ',' AssemblyProperties</span></span>|  
|<span data-ttu-id="6ad33-142">AssemblyProperties            :=   AssemblyProperty</span><span class="sxs-lookup"><span data-stu-id="6ad33-142">AssemblyProperties            :=   AssemblyProperty</span></span><br /><br /> <span data-ttu-id="6ad33-143">&#124;     AssemblyProperties ',' AssemblyProperty</span><span class="sxs-lookup"><span data-stu-id="6ad33-143">&#124;     AssemblyProperties ',' AssemblyProperty</span></span>|  
|<span data-ttu-id="6ad33-144">AssemblyProperty              :=   AssemblyPropertyName '=' AssemblyPropertyValue</span><span class="sxs-lookup"><span data-stu-id="6ad33-144">AssemblyProperty              :=   AssemblyPropertyName '=' AssemblyPropertyValue</span></span>|  
  
## <a name="specifying-special-characters"></a><span data-ttu-id="6ad33-145">特殊文字の指定</span><span class="sxs-lookup"><span data-stu-id="6ad33-145">Specifying Special Characters</span></span>  
 <span data-ttu-id="6ad33-146">型名の IDENTIFIER は、言語の規則で決められた任意の有効な名前です。</span><span class="sxs-lookup"><span data-stu-id="6ad33-146">In a type name, IDENTIFIER is any valid name determined by the rules of a language.</span></span>  
  
 <span data-ttu-id="6ad33-147">IDENTIFIER の一部として使用する場合、次のトークンを区切るには、エスケープ文字としてバックスラッシュ (\\) を使用します。</span><span class="sxs-lookup"><span data-stu-id="6ad33-147">Use the backslash (\\) as an escape character to separate the following tokens when used as part of IDENTIFIER.</span></span>  
  
|<span data-ttu-id="6ad33-148">トークン</span><span class="sxs-lookup"><span data-stu-id="6ad33-148">Token</span></span>|<span data-ttu-id="6ad33-149">説明</span><span class="sxs-lookup"><span data-stu-id="6ad33-149">Meaning</span></span>|  
|-----------|-------------|  
|<span data-ttu-id="6ad33-150">\\、</span><span class="sxs-lookup"><span data-stu-id="6ad33-150">\\,</span></span>|<span data-ttu-id="6ad33-151">アセンブリの区切り文字。</span><span class="sxs-lookup"><span data-stu-id="6ad33-151">Assembly separator.</span></span>|  
|\\+|<span data-ttu-id="6ad33-152">入れ子にされた型の区切り文字。</span><span class="sxs-lookup"><span data-stu-id="6ad33-152">Nested type separator.</span></span>|  
|\\&|<span data-ttu-id="6ad33-153">参照型。</span><span class="sxs-lookup"><span data-stu-id="6ad33-153">Reference type.</span></span>|  
|\\*|<span data-ttu-id="6ad33-154">ポインター型。</span><span class="sxs-lookup"><span data-stu-id="6ad33-154">Pointer type.</span></span>|  
|<span data-ttu-id="6ad33-155">\\[</span><span class="sxs-lookup"><span data-stu-id="6ad33-155">\\[</span></span>|<span data-ttu-id="6ad33-156">配列次元の区切り文字。</span><span class="sxs-lookup"><span data-stu-id="6ad33-156">Array dimension delimiter.</span></span>|  
|<span data-ttu-id="6ad33-157">\\]</span><span class="sxs-lookup"><span data-stu-id="6ad33-157">\\]</span></span>|<span data-ttu-id="6ad33-158">配列次元の区切り文字。</span><span class="sxs-lookup"><span data-stu-id="6ad33-158">Array dimension delimiter.</span></span>|  
|<span data-ttu-id="6ad33-159">\\。</span><span class="sxs-lookup"><span data-stu-id="6ad33-159">\\.</span></span>|<span data-ttu-id="6ad33-160">配列の指定内にピリオドを使用する場合にのみ、ピリオドの前にバックスラッシュを使用します。</span><span class="sxs-lookup"><span data-stu-id="6ad33-160">Use the backslash before a period only if the period is used in an array specification.</span></span> <span data-ttu-id="6ad33-161">NamespaceSpec 内のピリオドにはバックスラッシュを使用できません。</span><span class="sxs-lookup"><span data-stu-id="6ad33-161">Periods in NamespaceSpec do not take the backslash.</span></span>|  
|\\\|<span data-ttu-id="6ad33-162">文字列リテラルとして必要な場合のバックスラッシュ。</span><span class="sxs-lookup"><span data-stu-id="6ad33-162">Backslash when needed as a string literal.</span></span>|  
  
 <span data-ttu-id="6ad33-163">AssemblyNameSpec を除くすべての TypeSpec コンポーネントで、スペースは関係があります。</span><span class="sxs-lookup"><span data-stu-id="6ad33-163">Note that in all TypeSpec components except AssemblyNameSpec, spaces are relevant.</span></span> <span data-ttu-id="6ad33-164">AssemblyNameSpec の場合、',' 区切り文字の前にあるスペースは関係がありますが、',' の後のスペースは無視されます。</span><span class="sxs-lookup"><span data-stu-id="6ad33-164">In the AssemblyNameSpec, spaces before the ',' separator are relevant, but spaces after the ',' separator are ignored.</span></span>  
  
 <span data-ttu-id="6ad33-165"><xref:System.Type.FullName%2A?displayProperty=nameWithType> などのリフレクション クラスは、`MyType.GetType(myType.FullName)` と同様に返される名前を <xref:System.Type.GetType%2A> の呼び出しに使用できるように、壊れた名前を返します。</span><span class="sxs-lookup"><span data-stu-id="6ad33-165">Reflection classes, such as <xref:System.Type.FullName%2A?displayProperty=nameWithType>, return the mangled name so that the returned name can be used in a call to <xref:System.Type.GetType%2A>, as in `MyType.GetType(myType.FullName)`.</span></span>  
  
 <span data-ttu-id="6ad33-166">たとえば、型の完全修飾型名が `Ozzy.OutBack.Kangaroo+Wallaby,MyAssembly` だとします。</span><span class="sxs-lookup"><span data-stu-id="6ad33-166">For example, the fully qualified name for a type might be `Ozzy.OutBack.Kangaroo+Wallaby,MyAssembly`.</span></span>  
  
 <span data-ttu-id="6ad33-167">名前空間が `Ozzy.Out+Back` の場合、プラス記号の前にはバックスラッシュを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6ad33-167">If the namespace were `Ozzy.Out+Back`, then the plus sign must be preceded by a backslash.</span></span> <span data-ttu-id="6ad33-168">そうしないと、パーサーから入れ子の区切り文字として解釈されます。</span><span class="sxs-lookup"><span data-stu-id="6ad33-168">Otherwise, the parser would interpret it as a nesting separator.</span></span> <span data-ttu-id="6ad33-169">リフレクションからこの文字列は `Ozzy.Out\+Back.Kangaroo+Wallaby,MyAssembly` として出力されます。</span><span class="sxs-lookup"><span data-stu-id="6ad33-169">Reflection emits this string as `Ozzy.Out\+Back.Kangaroo+Wallaby,MyAssembly`.</span></span>  
  
## <a name="specifying-assembly-names"></a><span data-ttu-id="6ad33-170">アセンブリ名の指定</span><span class="sxs-lookup"><span data-stu-id="6ad33-170">Specifying Assembly Names</span></span>  
 <span data-ttu-id="6ad33-171">アセンブリ名の指定に必要な最小限の情報は、アセンブリのテキスト形式の名前 (IDENTIFIER) です。</span><span class="sxs-lookup"><span data-stu-id="6ad33-171">The minimum information required in an assembly name specification is the textual name (IDENTIFIER) of the assembly.</span></span> <span data-ttu-id="6ad33-172">次の表で説明されているプロパティ/値ペアのコンマ区切りの一覧で、IDENTIFIER に従うことができます。</span><span class="sxs-lookup"><span data-stu-id="6ad33-172">You can follow the IDENTIFIER by a comma-separated list of property/value pairs as described in the following table.</span></span> <span data-ttu-id="6ad33-173">IDENTIFIER の名前付けは、ファイルの名前付け規則に従う必要があります。</span><span class="sxs-lookup"><span data-stu-id="6ad33-173">IDENTIFIER naming should follow the rules for file naming.</span></span> <span data-ttu-id="6ad33-174">IDENTIFIER は大文字と小文字が区別されません。</span><span class="sxs-lookup"><span data-stu-id="6ad33-174">The IDENTIFIER is case-insensitive.</span></span>  
  
|<span data-ttu-id="6ad33-175">プロパティ名</span><span class="sxs-lookup"><span data-stu-id="6ad33-175">Property name</span></span>|<span data-ttu-id="6ad33-176">説明</span><span class="sxs-lookup"><span data-stu-id="6ad33-176">Description</span></span>|<span data-ttu-id="6ad33-177">使用できる値</span><span class="sxs-lookup"><span data-stu-id="6ad33-177">Allowable values</span></span>|  
|-------------------|-----------------|----------------------|  
|<span data-ttu-id="6ad33-178">**Version**</span><span class="sxs-lookup"><span data-stu-id="6ad33-178">**Version**</span></span>|<span data-ttu-id="6ad33-179">アセンブリのバージョン番号</span><span class="sxs-lookup"><span data-stu-id="6ad33-179">Assembly version number</span></span>|<span data-ttu-id="6ad33-180">*Major.Minor.Build.Revision*。*Major*、*Minor*、*Build*、*Revision* は 0 以上 65535 以下の整数です。</span><span class="sxs-lookup"><span data-stu-id="6ad33-180">*Major.Minor.Build.Revision*, where *Major*, *Minor*, *Build*, and *Revision* are integers between 0 and 65535 inclusive.</span></span>|  
|<span data-ttu-id="6ad33-181">**PublicKey**</span><span class="sxs-lookup"><span data-stu-id="6ad33-181">**PublicKey**</span></span>|<span data-ttu-id="6ad33-182">完全な公開鍵</span><span class="sxs-lookup"><span data-stu-id="6ad33-182">Full public key</span></span>|<span data-ttu-id="6ad33-183">16 進数形式の完全な公開鍵の文字列値。</span><span class="sxs-lookup"><span data-stu-id="6ad33-183">String value of full public key in hexadecimal format.</span></span> <span data-ttu-id="6ad33-184">プライベート アセンブリを明示的に指定するには、null 参照を指定します (Visual Basic では **Nothing**)。</span><span class="sxs-lookup"><span data-stu-id="6ad33-184">Specify a null reference (**Nothing** in Visual Basic) to explicitly indicate a private assembly.</span></span>|  
|<span data-ttu-id="6ad33-185">**PublicKeyToken**</span><span class="sxs-lookup"><span data-stu-id="6ad33-185">**PublicKeyToken**</span></span>|<span data-ttu-id="6ad33-186">公開鍵トークン (完全な公開鍵の 8 バイト ハッシュ)</span><span class="sxs-lookup"><span data-stu-id="6ad33-186">Public key token (8-byte hash of the full public key)</span></span>|<span data-ttu-id="6ad33-187">16 進数形式の公開鍵トークンの文字列値。</span><span class="sxs-lookup"><span data-stu-id="6ad33-187">String value of public key token in hexadecimal format.</span></span> <span data-ttu-id="6ad33-188">プライベート アセンブリを明示的に指定するには、null 参照を指定します (Visual Basic では **Nothing**)。</span><span class="sxs-lookup"><span data-stu-id="6ad33-188">Specify a null reference (**Nothing** in Visual Basic) to explicitly indicate a private assembly.</span></span>|  
|<span data-ttu-id="6ad33-189">**カルチャ**</span><span class="sxs-lookup"><span data-stu-id="6ad33-189">**Culture**</span></span>|<span data-ttu-id="6ad33-190">アセンブリのカルチャ</span><span class="sxs-lookup"><span data-stu-id="6ad33-190">Assembly culture</span></span>|<span data-ttu-id="6ad33-191">RFC 1766 形式のアセンブリのカルチャ。言語に依存しない (非サテライト) アセンブリの場合は "neutral"。</span><span class="sxs-lookup"><span data-stu-id="6ad33-191">Culture of the assembly in RFC-1766 format, or "neutral" for language-independent (nonsatellite) assemblies.</span></span>|  
|<span data-ttu-id="6ad33-192">**カスタム**</span><span class="sxs-lookup"><span data-stu-id="6ad33-192">**Custom**</span></span>|<span data-ttu-id="6ad33-193">カスタム バイナリ ラージ オブジェクト (BLOB)。</span><span class="sxs-lookup"><span data-stu-id="6ad33-193">Custom binary large object (BLOB).</span></span> <span data-ttu-id="6ad33-194">現在、 [Native Image Generator (Ngen)](../../../docs/framework/tools/ngen-exe-native-image-generator.md) で生成されたアセンブリでのみ使用されています。</span><span class="sxs-lookup"><span data-stu-id="6ad33-194">This is currently used only in assemblies generated by the [Native Image Generator (Ngen)](../../../docs/framework/tools/ngen-exe-native-image-generator.md).</span></span>|<span data-ttu-id="6ad33-195">アセンブリがインストールされていることをアセンブリ キャッシュに通知するために Native Image Generator ツールに使用されているカスタム文字列は、ネイティブ イメージです。そのため、ネイティブ イメージ キャッシュにインストールされます。</span><span class="sxs-lookup"><span data-stu-id="6ad33-195">Custom string used by the Native Image Generator tool to notify the assembly cache that the assembly being installed is a native image, and is therefore to be installed in the native image cache.</span></span> <span data-ttu-id="6ad33-196">zap 文字列とも呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="6ad33-196">Also called a zap string.</span></span>|  
  
 <span data-ttu-id="6ad33-197">次に、カルチャが既定で単純な名前のアセンブリの**AssemblyName** の例を示します。</span><span class="sxs-lookup"><span data-stu-id="6ad33-197">The following example shows an **AssemblyName** for a simply named assembly with default culture.</span></span>  
  
```csharp  
com.microsoft.crypto, Culture=""   
```  
  
 <span data-ttu-id="6ad33-198">次に、カルチャが "en" の厳密な名前のアセンブリに対する完全に指定された参照の例を示します。</span><span class="sxs-lookup"><span data-stu-id="6ad33-198">The following example shows a fully specified reference for a strongly named assembly with culture "en".</span></span>  
  
```csharp  
com.microsoft.crypto, Culture=en, PublicKeyToken=a5d015c7d5a0b012,  
    Version=1.0.0.0   
```  
  
 <span data-ttu-id="6ad33-199">次の各例は、部分的に指定された **AssemblyName** を示しています。これは厳密な名前または単純な名前のアセンブリで満たすことができます。</span><span class="sxs-lookup"><span data-stu-id="6ad33-199">The following examples each show a partially specified **AssemblyName**, which can be satisfied by either a strong or a simply named assembly.</span></span>  
  
```csharp  
com.microsoft.crypto  
com.microsoft.crypto, Culture=""  
com.microsoft.crypto, Culture=en   
```  
  
 <span data-ttu-id="6ad33-200">次の各例は、部分的に指定された **AssemblyName** を示しています。これは簡易な名前のアセンブリで満たす必要があります。</span><span class="sxs-lookup"><span data-stu-id="6ad33-200">The following examples each show a partially specified **AssemblyName**, which must be satisfied by a simply named assembly.</span></span>  
  
```csharp  
com.microsoft.crypto, Culture="", PublicKeyToken=null   
com.microsoft.crypto, Culture=en, PublicKeyToken=null  
```  
  
 <span data-ttu-id="6ad33-201">次の各例は、部分的に指定された **AssemblyName** を示しています。これは厳密な名前のアセンブリで満たす必要があります。</span><span class="sxs-lookup"><span data-stu-id="6ad33-201">The following examples each show a partially specified **AssemblyName**, which must be satisfied by a strongly named assembly.</span></span>  
  
```csharp  
com.microsoft.crypto, Culture="", PublicKeyToken=a5d015c7d5a0b012  
com.microsoft.crypto, Culture=en, PublicKeyToken=a5d015c7d5a0b012,  
    Version=1.0.0.0  
```  
  
## <a name="specifying-pointers"></a><span data-ttu-id="6ad33-202">ポインターの指定</span><span class="sxs-lookup"><span data-stu-id="6ad33-202">Specifying Pointers</span></span>  
 <span data-ttu-id="6ad33-203">SimpleTypeSpec* はアンマネージ ポインターを示します。</span><span class="sxs-lookup"><span data-stu-id="6ad33-203">SimpleTypeSpec* represents an unmanaged pointer.</span></span> <span data-ttu-id="6ad33-204">たとえば、型 MyType に対するポインターを取得するには、`Type.GetType("MyType*")` を使用します。</span><span class="sxs-lookup"><span data-stu-id="6ad33-204">For example, to get a pointer to type MyType, use `Type.GetType("MyType*")`.</span></span> <span data-ttu-id="6ad33-205">型 MyType のポインターに対するポインターを取得するには、`Type.GetType("MyType**")` を使用します。</span><span class="sxs-lookup"><span data-stu-id="6ad33-205">To get a pointer to a pointer to type MyType, use `Type.GetType("MyType**")`.</span></span>  
  
## <a name="specifying-references"></a><span data-ttu-id="6ad33-206">参照の指定</span><span class="sxs-lookup"><span data-stu-id="6ad33-206">Specifying References</span></span>  
 <span data-ttu-id="6ad33-207">SimpleTypeSpec & はマネージ ポインターまたは参照を表します。</span><span class="sxs-lookup"><span data-stu-id="6ad33-207">SimpleTypeSpec & represents a managed pointer or reference.</span></span> <span data-ttu-id="6ad33-208">たとえば、型 MyType に対する参照を取得するには、`Type.GetType("MyType &")` を使用します。</span><span class="sxs-lookup"><span data-stu-id="6ad33-208">For example, to get a reference to type MyType, use `Type.GetType("MyType &")`.</span></span> <span data-ttu-id="6ad33-209">ポインターとは異なり、参照は 1 つのレベルに制限されます。</span><span class="sxs-lookup"><span data-stu-id="6ad33-209">Note that unlike pointers, references are limited to one level.</span></span>  
  
## <a name="specifying-arrays"></a><span data-ttu-id="6ad33-210">配列の指定</span><span class="sxs-lookup"><span data-stu-id="6ad33-210">Specifying Arrays</span></span>  
 <span data-ttu-id="6ad33-211">BNF 文法では、ReflectionEmitDimension は <xref:System.Reflection.Emit.ModuleBuilder.GetType%2A?displayProperty=nameWithType> を使用して取得された不完全な型定義にのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="6ad33-211">In the BNF Grammar, ReflectionEmitDimension only applies to incomplete type definitions retrieved using <xref:System.Reflection.Emit.ModuleBuilder.GetType%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="6ad33-212">不完全な型定義とは、<xref:System.Reflection.Emit.TypeBuilder.CreateType%2A?displayProperty=nameWithType> で呼び出されていない、<xref:System.Reflection.Emit?displayProperty=nameWithType> を使用して構築された <xref:System.Reflection.Emit.TypeBuilder> オブジェクトです。</span><span class="sxs-lookup"><span data-stu-id="6ad33-212">Incomplete type definitions are <xref:System.Reflection.Emit.TypeBuilder> objects constructed using <xref:System.Reflection.Emit?displayProperty=nameWithType> but on which <xref:System.Reflection.Emit.TypeBuilder.CreateType%2A?displayProperty=nameWithType> has not been called.</span></span> <span data-ttu-id="6ad33-213">ReflectionDimension を使用して、完了している任意の型定義 (読み込まれている型) を取得できます。</span><span class="sxs-lookup"><span data-stu-id="6ad33-213">ReflectionDimension can be used to retrieve any type definition that has been completed, that is, a type that has been loaded.</span></span>  
  
 <span data-ttu-id="6ad33-214">配列のランクを指定して、リフレクションで配列にアクセスします。</span><span class="sxs-lookup"><span data-stu-id="6ad33-214">Arrays are accessed in reflection by specifying the rank of the array:</span></span>  
  
-   <span data-ttu-id="6ad33-215">`Type.GetType("MyArray[]")` は 0 個の下限がある 1 次元配列を取得します。</span><span class="sxs-lookup"><span data-stu-id="6ad33-215">`Type.GetType("MyArray[]")` gets a single-dimension array with 0 lower bound.</span></span>  
  
-   <span data-ttu-id="6ad33-216">`Type.GetType("MyArray[*]")` は不明な下限がある 1 次元配列を取得します。</span><span class="sxs-lookup"><span data-stu-id="6ad33-216">`Type.GetType("MyArray[*]")` gets a single-dimension array with unknown lower bound.</span></span>  
  
-   <span data-ttu-id="6ad33-217">`Type.GetType("MyArray[][]")` は 2 次元配列の配列です。</span><span class="sxs-lookup"><span data-stu-id="6ad33-217">`Type.GetType("MyArray[][]")` gets a two-dimensional array's array.</span></span>  
  
-   <span data-ttu-id="6ad33-218">`Type.GetType("MyArray[*,*]")` と `Type.GetType("MyArray[,]")` は、下限が不明な四角形の 2 次元配列を取得します。</span><span class="sxs-lookup"><span data-stu-id="6ad33-218">`Type.GetType("MyArray[*,*]")` and `Type.GetType("MyArray[,]")` gets a rectangular two-dimensional array with unknown lower bounds.</span></span>  
  
 <span data-ttu-id="6ad33-219">ランタイムの観点からは、多次元配列を別にすれば、`MyArray[] != MyArray[*]` の 2 つの表記は同等です。</span><span class="sxs-lookup"><span data-stu-id="6ad33-219">Note that from a runtime point of view, `MyArray[] != MyArray[*]`, but for multidimensional arrays, the two notations are equivalent.</span></span> <span data-ttu-id="6ad33-220">つまり、`Type.GetType("MyArray [,]") == Type.GetType("MyArray[*,*]")` は **true** と評価されます。</span><span class="sxs-lookup"><span data-stu-id="6ad33-220">That is, `Type.GetType("MyArray [,]") == Type.GetType("MyArray[*,*]")` evaluates to **true**.</span></span>  
  
 <span data-ttu-id="6ad33-221">**ModuleBuilder.GetType** の場合、`MyArray[0..5]` はサイズが 6 で下限が 0 の 1 次元配列です。</span><span class="sxs-lookup"><span data-stu-id="6ad33-221">For **ModuleBuilder.GetType**, `MyArray[0..5]` indicates a single-dimension array with size 6, lower bound 0.</span></span> <span data-ttu-id="6ad33-222">`MyArray[4…]` は、不明なサイズで下限が 4 の 1 次元配列です。</span><span class="sxs-lookup"><span data-stu-id="6ad33-222">`MyArray[4…]` indicates a single-dimension array of unknown size and lower bound 4.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ad33-223">参照</span><span class="sxs-lookup"><span data-stu-id="6ad33-223">See Also</span></span>  
 <xref:System.Reflection.AssemblyName>  
 <xref:System.Reflection.Emit.ModuleBuilder>  
 <xref:System.Reflection.Emit.TypeBuilder>  
 <xref:System.Type.FullName%2A?displayProperty=nameWithType>  
 <xref:System.Type.GetType%2A?displayProperty=nameWithType>  
 <xref:System.Type.AssemblyQualifiedName%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="6ad33-224">型情報の表示</span><span class="sxs-lookup"><span data-stu-id="6ad33-224">Viewing Type Information</span></span>](../../../docs/framework/reflection-and-codedom/viewing-type-information.md)
