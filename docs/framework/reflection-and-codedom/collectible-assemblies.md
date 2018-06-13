---
title: 動的な型生成のための収集可能なアセンブリ
description: ''
ms.date: 08/29/2017
helpviewer_keywords:
- reflection, dynamic assembly
- assemblies, collectible
- collectible assemblies, retrieving
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 04a04e422fec14055d8ac3f50b9f2f18658a0f9f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33398262"
---
# <a name="collectible-assemblies-for-dynamic-type-generation"></a><span data-ttu-id="21619-102">動的な型生成のための収集可能なアセンブリ</span><span class="sxs-lookup"><span data-stu-id="21619-102">Collectible assemblies for dynamic type generation</span></span>

<span data-ttu-id="21619-103">*収集可能なアセンブリ*とは、それらが作成されたアプリケーション ドメインをアンロードせずにアンロードできる動的アセンブリです。</span><span class="sxs-lookup"><span data-stu-id="21619-103">*Collectible assemblies* are dynamic assemblies that can be unloaded without unloading the application domain in which they were created.</span></span> <span data-ttu-id="21619-104">収集可能アセンブリとそれに含まれる型によって使用されているすべてのマネージ メモリとアンマネージ メモリは、再利用することができます。</span><span class="sxs-lookup"><span data-stu-id="21619-104">All managed and unmanaged memory used by a collectible assembly and the types it contains can be reclaimed.</span></span> <span data-ttu-id="21619-105">アセンブリ名などの情報は、内部テーブルから削除されます。</span><span class="sxs-lookup"><span data-stu-id="21619-105">Information such as the assembly name is removed from internal tables.</span></span>

<span data-ttu-id="21619-106">アンロードを有効にするには、動的アセンブリを作成するときに <xref:System.Reflection.Emit.AssemblyBuilderAccess.RunAndCollect?displayProperty=nameWithType> フラグを使用します。</span><span class="sxs-lookup"><span data-stu-id="21619-106">To enable unloading, use the <xref:System.Reflection.Emit.AssemblyBuilderAccess.RunAndCollect?displayProperty=nameWithType> flag when you create a dynamic assembly.</span></span> <span data-ttu-id="21619-107">このアセンブリは一時的なもので (つまり、保存できません)、「[収集可能なアセンブリに対する制限](#restrictions-on-collectible-assemblies)」セクションで説明されている制限事項が該当します。</span><span class="sxs-lookup"><span data-stu-id="21619-107">The assembly is transient (that is, it cannot be saved) and is subject to limitations described in the [Restrictions on Collectible Assemblies](#restrictions-on-collectible-assemblies) section.</span></span> <span data-ttu-id="21619-108">収集可能なアセンブリは、そのアセンブリに関連付けられているすべてのオブジェクトが解放されると、共通言語ランタイム (CLR) によって自動的にアンロードされます。</span><span class="sxs-lookup"><span data-stu-id="21619-108">The common language runtime (CLR) unloads a collectible assembly automatically when you release all objects associated with the assembly.</span></span> <span data-ttu-id="21619-109">その他のすべての点では、収集可能なアセンブリは他の動的アセンブリと同じように作成および使用されます。</span><span class="sxs-lookup"><span data-stu-id="21619-109">In all other respects, collectible assemblies are created and used in the same way as other dynamic assemblies.</span></span>

## <a name="lifetime-of-collectible-assemblies"></a><span data-ttu-id="21619-110">収集可能なアセンブリの有効期間</span><span class="sxs-lookup"><span data-stu-id="21619-110">Lifetime of collectible assemblies</span></span>

<span data-ttu-id="21619-111">収集可能な動的アセンブリの有効期間は、そのアセンブリに含まれる型への参照があるかどうかと、それらの型から作成されたオブジェクトがあるかどうかによって決まります。</span><span class="sxs-lookup"><span data-stu-id="21619-111">The lifetime of a collectible assembly is controlled by the existence of references to the types it contains and the objects that are created from those types.</span></span> <span data-ttu-id="21619-112">次の 1 つ以上が存在する場合、共通言語ランタイムはアセンブリをアンロードしません (`T` は、アセンブリで定義されている任意の型です)。</span><span class="sxs-lookup"><span data-stu-id="21619-112">The common language runtime does not unload an assembly as long as one or more of the following exist (`T` is any type that is defined in the assembly):</span></span> 

- <span data-ttu-id="21619-113">`T` のインスタンス。</span><span class="sxs-lookup"><span data-stu-id="21619-113">An instance of `T`.</span></span>

- <span data-ttu-id="21619-114">`T` の配列のインスタンス。</span><span class="sxs-lookup"><span data-stu-id="21619-114">An instance of an array of `T`.</span></span>
 
- <span data-ttu-id="21619-115">`T` を型引数の 1 つとして含んでいるジェネリック型のインスタンス。</span><span class="sxs-lookup"><span data-stu-id="21619-115">An instance of a generic type that has `T` as one of its type arguments.</span></span> <span data-ttu-id="21619-116">これには、そのコレクションが空の場合も含め、`T` のジェネリック コレクションを含みます。</span><span class="sxs-lookup"><span data-stu-id="21619-116">This includes generic collections of `T`, even if that collection is empty.</span></span>

- <span data-ttu-id="21619-117">`T` を表す <xref:System.Type> または <xref:System.Reflection.Emit.TypeBuilder> のインスタンス。</span><span class="sxs-lookup"><span data-stu-id="21619-117">An instance of <xref:System.Type> or <xref:System.Reflection.Emit.TypeBuilder> that represents `T`.</span></span> 

   > [!IMPORTANT]
   > <span data-ttu-id="21619-118">アセンブリの一部を表すオブジェクトは、すべて解放する必要があります。</span><span class="sxs-lookup"><span data-stu-id="21619-118">You must release all objects that represent parts of the assembly.</span></span> <span data-ttu-id="21619-119">`T` を定義した <xref:System.Reflection.Emit.ModuleBuilder> は <xref:System.Reflection.Emit.TypeBuilder> への参照を保持し、<xref:System.Reflection.Emit.AssemblyBuilder> オブジェクトは <xref:System.Reflection.Emit.ModuleBuilder> への参照を保持します。したがって、これらのオブジェクトへの参照は解放する必要があります。</span><span class="sxs-lookup"><span data-stu-id="21619-119">The <xref:System.Reflection.Emit.ModuleBuilder> that defines `T` keeps a reference to the <xref:System.Reflection.Emit.TypeBuilder>, and the <xref:System.Reflection.Emit.AssemblyBuilder> object keeps a reference to the <xref:System.Reflection.Emit.ModuleBuilder>, so references to these objects must be released.</span></span> <span data-ttu-id="21619-120">`T` の構築に使用された <xref:System.Reflection.Emit.LocalBuilder> や <xref:System.Reflection.Emit.ILGenerator> が存在している場合も、アンロードは行われません。</span><span class="sxs-lookup"><span data-stu-id="21619-120">Even the existence of a <xref:System.Reflection.Emit.LocalBuilder> or an <xref:System.Reflection.Emit.ILGenerator> used in the construction of `T` prevents unloading.</span></span>

- <span data-ttu-id="21619-121">実行コードから到達できる動的に定義された別の型 `T1` による、`T` への静的参照。</span><span class="sxs-lookup"><span data-stu-id="21619-121">A static reference to `T` by another dynamically defined type `T1` that is still reachable by executing code.</span></span> <span data-ttu-id="21619-122">たとえば、`T1` が `T` から派生している場合や、`T` が `T1` のメソッドのパラメーターの型である場合があります。</span><span class="sxs-lookup"><span data-stu-id="21619-122">For example, `T1` might derive from `T`, or `T` might be the type of a parameter in a method of `T1`.</span></span>
 
- <span data-ttu-id="21619-123">`T` に属する静的フィールドに対する **ByRef**。</span><span class="sxs-lookup"><span data-stu-id="21619-123">A **ByRef** to a static field that belongs to `T`.</span></span>

- <span data-ttu-id="21619-124">`T` または `T` のコンポーネントを参照する <xref:System.RuntimeTypeHandle>、<xref:System.RuntimeFieldHandle>、または <xref:System.RuntimeMethodHandle>。</span><span class="sxs-lookup"><span data-stu-id="21619-124">A <xref:System.RuntimeTypeHandle>, <xref:System.RuntimeFieldHandle>, or <xref:System.RuntimeMethodHandle> that refers to `T` or to a component of `T`.</span></span>

- <span data-ttu-id="21619-125">`T` を表す <xref:System.Type> オブジェクトへのアクセスに間接または直接に使用できるリフレクション オブジェクトのインスタンス。</span><span class="sxs-lookup"><span data-stu-id="21619-125">An instance of any reflection object that could be used indirectly or directly to access the <xref:System.Type> object that represents `T`.</span></span> <span data-ttu-id="21619-126">たとえば、`T` の <xref:System.Type> オブジェクトは、要素型が `T` である配列型や、`T` を型引数として持つジェネリック型から取得できます。</span><span class="sxs-lookup"><span data-stu-id="21619-126">For example, the <xref:System.Type> object for `T` can be obtained from an array type whose element type is `T`, or from a generic type that has `T` as a type argument.</span></span> 

- <span data-ttu-id="21619-127">任意のスレッドの呼び出し履歴にあるメソッド `M`。この `M` は、`T` のメソッド、またはアセンブリで定義されているモジュール レベルのメソッドです。</span><span class="sxs-lookup"><span data-stu-id="21619-127">A method `M` on the call stack of any thread, where `M` is a method of `T` or a module-level method that is defined in the assembly.</span></span>

- <span data-ttu-id="21619-128">アセンブリのモジュール内で定義されている静的メソッドに対するデリゲート。</span><span class="sxs-lookup"><span data-stu-id="21619-128">A delegate to a static method that is defined in a module of the assembly.</span></span>

<span data-ttu-id="21619-129">アセンブリ内の 1 つの型または 1 つのメソッドについてだけでも、この一覧の項目が 1 つでも存在する場合、ランタイムはそのアセンブリをアンロードできません。</span><span class="sxs-lookup"><span data-stu-id="21619-129">If only one item from this list exists for only one type or one method in the assembly, the runtime cannot unload the assembly.</span></span>

> [!NOTE]
> <span data-ttu-id="21619-130">実際には、この一覧にあるすべての項目に対してファイナライザーが実行されるまで、アセンブリはアンロードされません。</span><span class="sxs-lookup"><span data-stu-id="21619-130">The runtime does not actually unload the assembly until finalizers have run for all items in the list.</span></span>

<span data-ttu-id="21619-131">有効期間の追跡では、収集可能なアセンブリの生成時に作成および使用される (C# の) `List<int>` または (Visual Basic の) `List(Of Integer)` などの構築ジェネリック型は、そのジェネリック型定義を含むアセンブリか、その型引数のいずれかの定義を含む別のアセンブリで定義されていると見なされます。</span><span class="sxs-lookup"><span data-stu-id="21619-131">For purposes of tracking lifetime, a constructed generic type such as `List<int>` (in C#) or `List(Of Integer)` (in Visual Basic) that is created and used in the generation of a collectible assembly is considered to have been defined either in the assembly that contains the generic type definition or in an assembly that contains the definition of one of its type arguments.</span></span> <span data-ttu-id="21619-132">使用される正確なアセンブリは実装の詳細であり、変更されることがあります。</span><span class="sxs-lookup"><span data-stu-id="21619-132">The exact assembly that is used is an implementation detail and subject to change.</span></span>
 
## <a name="restrictions-on-collectible-assemblies"></a><span data-ttu-id="21619-133">収集可能なアセンブリに対する制限</span><span class="sxs-lookup"><span data-stu-id="21619-133">Restrictions on collectible assemblies</span></span>

<span data-ttu-id="21619-134">収集可能なアセンブリには、次の制限があります。</span><span class="sxs-lookup"><span data-stu-id="21619-134">The following restrictions apply to collectible assemblies:</span></span> 

- <span data-ttu-id="21619-135">**静的参照** </span><span class="sxs-lookup"><span data-stu-id="21619-135">**Static references** </span></span>  
  <span data-ttu-id="21619-136">通常の動的アセンブリ内の型では、収集可能なアセンブリで定義されている型への静的参照を使用できません。</span><span class="sxs-lookup"><span data-stu-id="21619-136">Types in an ordinary dynamic assembly cannot have static references to types that are defined in a collectible assembly.</span></span> <span data-ttu-id="21619-137">たとえば、収集可能なアセンブリ内の型を継承する通常の型を定義すると、<xref:System.NotSupportedException> 例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="21619-137">For example, if you define an ordinary type that inherits from a type in a collectible assembly, a <xref:System.NotSupportedException> exception is thrown.</span></span> <span data-ttu-id="21619-138">収集可能なアセンブリ内の型では、別の収集可能なアセンブリ内の型への静的参照を使用できますが、この場合は、参照アセンブリの有効期間が参照元アセンブリの有効期間に延長されます。</span><span class="sxs-lookup"><span data-stu-id="21619-138">A type in a collectible assembly can have static references to a type in another collectible assembly, but this extends the lifetime of the referenced assembly to the lifetime of the referencing assembly.</span></span>

- <span data-ttu-id="21619-139">**COM 相互運用** </span><span class="sxs-lookup"><span data-stu-id="21619-139">**COM interop** </span></span>  
   <span data-ttu-id="21619-140">収集可能なアセンブリ内では COM インターフェイスを定義できません。また、収集可能なアセンブリ内の型のインスタンスを COM オブジェクトに変換することもできません。</span><span class="sxs-lookup"><span data-stu-id="21619-140">No COM interfaces can be defined within a collectible assembly, and no instances of types within a collectible assembly can be converted into COM objects.</span></span> <span data-ttu-id="21619-141">収集可能なアセンブリ内の型は、COM 呼び出し可能ラッパー (CCW) またはランタイム呼び出し可能ラッパー (RCW) として機能できません。</span><span class="sxs-lookup"><span data-stu-id="21619-141">A type in a collectible assembly cannot serve as a COM callable wrapper (CCW) or runtime callable wrapper (RCW).</span></span> <span data-ttu-id="21619-142">ただし、収集可能なアセンブリ内の型では、COM インターフェイスを実装するオブジェクトを使用できます。</span><span class="sxs-lookup"><span data-stu-id="21619-142">However, types in collectible assemblies can use objects that implement COM interfaces.</span></span>

- <span data-ttu-id="21619-143">**プラットフォーム呼び出し** </span><span class="sxs-lookup"><span data-stu-id="21619-143">**Platform invoke** </span></span>  
   <span data-ttu-id="21619-144"><xref:System.Runtime.InteropServices.DllImportAttribute> 属性を持つメソッドを収集可能なアセンブリ内で宣言しても、コンパイルはできません。</span><span class="sxs-lookup"><span data-stu-id="21619-144">Methods that have the <xref:System.Runtime.InteropServices.DllImportAttribute> attribute will not compile when they are declared in a collectible assembly.</span></span> <span data-ttu-id="21619-145"><xref:System.Reflection.Emit.OpCodes.Calli?displayProperty=nameWithType> 命令は、収集可能なアセンブリ内の型の実装では使用できません。このような型をアンマネージ コードにマーシャリングすることはできません。</span><span class="sxs-lookup"><span data-stu-id="21619-145">The <xref:System.Reflection.Emit.OpCodes.Calli?displayProperty=nameWithType> instruction cannot be used in the implementation of a type in a collectible assembly, and such types cannot be marshaled to unmanaged code.</span></span> <span data-ttu-id="21619-146">ただし、収集可能でないアセンブリ内で宣言されているエントリ ポイントを使用すれば、ネイティブ コードを呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="21619-146">However, you can call into native code by using an entry point that is declared in a non-collectible assembly.</span></span>
 
- <span data-ttu-id="21619-147">**マーシャリング** </span><span class="sxs-lookup"><span data-stu-id="21619-147">**Marshaling** </span></span>  
   <span data-ttu-id="21619-148">収集可能なアセンブリで定義されているオブジェクト (特にデリゲート) はマーシャリングできません。</span><span class="sxs-lookup"><span data-stu-id="21619-148">Objects (in particular, delegates) that are defined in collectible assemblies cannot be marshaled.</span></span> <span data-ttu-id="21619-149">この制限は、一時的に生成されるすべての型にあります。</span><span class="sxs-lookup"><span data-stu-id="21619-149">This is a restriction on all transient emitted types.</span></span>

- <span data-ttu-id="21619-150">**アセンブリの読み込み** </span><span class="sxs-lookup"><span data-stu-id="21619-150">**Assembly loading** </span></span>  
   <span data-ttu-id="21619-151">収集可能なアセンブリを読み込むためにサポートされる機構は、リフレクション出力のみです。</span><span class="sxs-lookup"><span data-stu-id="21619-151">Reflection emit is the only mechanism that is supported for loading collectible assemblies.</span></span> <span data-ttu-id="21619-152">それ以外の形式のアセンブリ読み込みによってロードされたアセンブリは、アンロードできません。</span><span class="sxs-lookup"><span data-stu-id="21619-152">Assemblies that are loaded by using any other form of assembly loading cannot be unloaded.</span></span>
 
- <span data-ttu-id="21619-153">**コンテキスト バインド オブジェクト**  </span><span class="sxs-lookup"><span data-stu-id="21619-153">**Context-bound objects**  </span></span>  
   <span data-ttu-id="21619-154">コンテキストの静的変数はサポートされません。</span><span class="sxs-lookup"><span data-stu-id="21619-154">Context-static variables are not supported.</span></span> <span data-ttu-id="21619-155">収集可能なアセンブリ内の型は、<xref:System.ContextBoundObject> を拡張できません。</span><span class="sxs-lookup"><span data-stu-id="21619-155">Types in a collectible assembly cannot extend <xref:System.ContextBoundObject>.</span></span> <span data-ttu-id="21619-156">ただし、別の場所で定義されているコンテキスト バインド オブジェクトを、収集可能なアセンブリのコードで使用することはできます。</span><span class="sxs-lookup"><span data-stu-id="21619-156">However, code in collectible assemblies can use context-bound objects that are defined elsewhere.</span></span>

- <span data-ttu-id="21619-157">**スレッドの静的データ**     </span><span class="sxs-lookup"><span data-stu-id="21619-157">**Thread-static data**     </span></span>  
   <span data-ttu-id="21619-158">スレッドの静的変数はサポートされません。</span><span class="sxs-lookup"><span data-stu-id="21619-158">Thread-static variables are not supported.</span></span>

## <a name="see-also"></a><span data-ttu-id="21619-159">関連項目</span><span class="sxs-lookup"><span data-stu-id="21619-159">See also</span></span>

[<span data-ttu-id="21619-160">動的メソッドおよびアセンブリの出力</span><span class="sxs-lookup"><span data-stu-id="21619-160">Emitting Dynamic Methods and Assemblies</span></span>](emitting-dynamic-methods-and-assemblies.md)
