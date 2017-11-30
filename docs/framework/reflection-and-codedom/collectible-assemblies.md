---
title: "回収可能アセンブリの動的な型の生成"
description: 
ms.date: 08/29/2017
ms.prod: .net
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- reflection, dynamic assembly
- assemblies, collectible
- collectible assemblies, retrieving
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2c9a613f4cc13c3e4189a59ace2e05d01d1bcb4f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="collectible-assemblies-for-dynamic-type-generation"></a><span data-ttu-id="839d8-102">回収可能アセンブリの動的な型の生成</span><span class="sxs-lookup"><span data-stu-id="839d8-102">Collectible assemblies for dynamic type generation</span></span>

<span data-ttu-id="839d8-103">*回収可能アセンブリ*動的アセンブリが作成されたアプリケーション ドメインをアンロードせずアンロードできます。</span><span class="sxs-lookup"><span data-stu-id="839d8-103">*Collectible assemblies* are dynamic assemblies that can be unloaded without unloading the application domain in which they were created.</span></span> <span data-ttu-id="839d8-104">回収可能アセンブリとが含まれている型で使用される、すべてのマネージ コードとアンマネージ メモリが再利用できることができます。</span><span class="sxs-lookup"><span data-stu-id="839d8-104">All managed and unmanaged memory used by a collectible assembly and the types it contains can be reclaimed.</span></span> <span data-ttu-id="839d8-105">アセンブリ名などの情報は、内部テーブルから削除されます。</span><span class="sxs-lookup"><span data-stu-id="839d8-105">Information such as the assembly name is removed from internal tables.</span></span>

<span data-ttu-id="839d8-106">アンロードを有効にするには、<xref:System.Reflection.Emit.AssemblyBuilderAccess.RunAndCollect?displayProperty=nameWithType>動的アセンブリを作成するときにフラグを設定します。</span><span class="sxs-lookup"><span data-stu-id="839d8-106">To enable unloading, use the <xref:System.Reflection.Emit.AssemblyBuilderAccess.RunAndCollect?displayProperty=nameWithType> flag when you create a dynamic assembly.</span></span> <span data-ttu-id="839d8-107">アセンブリが一時的な (つまり、保存できません) で説明されている制限事項が適用、[回収可能アセンブリに関する制限事項](#restrictions-on-collectible-assemblies)セクションです。</span><span class="sxs-lookup"><span data-stu-id="839d8-107">The assembly is transient (that is, it cannot be saved) and is subject to limitations described in the [Restrictions on Collectible Assemblies](#restrictions-on-collectible-assemblies) section.</span></span> <span data-ttu-id="839d8-108">共通言語ランタイム (CLR) は、アセンブリに関連付けられているすべてのオブジェクトを解放するときに自動的に回収可能アセンブリをアンロードします。</span><span class="sxs-lookup"><span data-stu-id="839d8-108">The common language runtime (CLR) unloads a collectible assembly automatically when you release all objects associated with the assembly.</span></span> <span data-ttu-id="839d8-109">その他のすべての点で回収可能アセンブリが作成され、他の動的アセンブリと同じ方法で使用します。</span><span class="sxs-lookup"><span data-stu-id="839d8-109">In all other respects, collectible assemblies are created and used in the same way as other dynamic assemblies.</span></span>

## <a name="lifetime-of-collectible-assemblies"></a><span data-ttu-id="839d8-110">回収可能アセンブリの有効期間</span><span class="sxs-lookup"><span data-stu-id="839d8-110">Lifetime of collectible assemblies</span></span>

<span data-ttu-id="839d8-111">回収可能アセンブリの有効期間への参照が含まれている型やこれらの型から作成されるオブジェクトの存在によって制御されます。</span><span class="sxs-lookup"><span data-stu-id="839d8-111">The lifetime of a collectible assembly is controlled by the existence of references to the types it contains and the objects that are created from those types.</span></span> <span data-ttu-id="839d8-112">次の 1 つ以上存在する限り、共通言語ランタイムがアセンブリをアンロードしません (`T`アセンブリで定義されている型である)。</span><span class="sxs-lookup"><span data-stu-id="839d8-112">The common language runtime does not unload an assembly as long as one or more of the following exist (`T` is any type that is defined in the assembly):</span></span> 

- <span data-ttu-id="839d8-113">`T` のインスタンス。</span><span class="sxs-lookup"><span data-stu-id="839d8-113">An instance of `T`.</span></span>

- <span data-ttu-id="839d8-114">インスタンスの配列の`T`します。</span><span class="sxs-lookup"><span data-stu-id="839d8-114">An instance of an array of `T`.</span></span>
 
- <span data-ttu-id="839d8-115">持つジェネリック型のインスタンス`T`として、型引数のいずれか。</span><span class="sxs-lookup"><span data-stu-id="839d8-115">An instance of a generic type that has `T` as one of its type arguments.</span></span> <span data-ttu-id="839d8-116">ジェネリック コレクションが含まれます`T`場合でも、そのコレクションが空です。</span><span class="sxs-lookup"><span data-stu-id="839d8-116">This includes generic collections of `T`, even if that collection is empty.</span></span>

- <span data-ttu-id="839d8-117">インスタンス<xref:System.Type>または<xref:System.Reflection.Emit.TypeBuilder>を表す`T`です。</span><span class="sxs-lookup"><span data-stu-id="839d8-117">An instance of <xref:System.Type> or <xref:System.Reflection.Emit.TypeBuilder> that represents `T`.</span></span> 

   > [!IMPORTANT]
   > <span data-ttu-id="839d8-118">アセンブリの部分を表すすべてのオブジェクトを解放する必要があります。</span><span class="sxs-lookup"><span data-stu-id="839d8-118">You must release all objects that represent parts of the assembly.</span></span> <span data-ttu-id="839d8-119"><xref:System.Reflection.Emit.ModuleBuilder>を定義する`T`への参照を保持、 <xref:System.Reflection.Emit.TypeBuilder>、および<xref:System.Reflection.Emit.AssemblyBuilder>オブジェクトへの参照を保持する、<xref:System.Reflection.Emit.ModuleBuilder>ので、これらのオブジェクトへの参照を解放する必要があります。</span><span class="sxs-lookup"><span data-stu-id="839d8-119">The <xref:System.Reflection.Emit.ModuleBuilder> that defines `T` keeps a reference to the <xref:System.Reflection.Emit.TypeBuilder>, and the <xref:System.Reflection.Emit.AssemblyBuilder> object keeps a reference to the <xref:System.Reflection.Emit.ModuleBuilder>, so references to these objects must be released.</span></span> <span data-ttu-id="839d8-120">存在も、<xref:System.Reflection.Emit.LocalBuilder>または<xref:System.Reflection.Emit.ILGenerator>の作成に使用される`T`アンロードできなくなります。</span><span class="sxs-lookup"><span data-stu-id="839d8-120">Even the existence of a <xref:System.Reflection.Emit.LocalBuilder> or an <xref:System.Reflection.Emit.ILGenerator> used in the construction of `T` prevents unloading.</span></span>

- <span data-ttu-id="839d8-121">参照を静的`T`動的に定義された別の種類によって`T1`コードを実行して到達可能です。</span><span class="sxs-lookup"><span data-stu-id="839d8-121">A static reference to `T` by another dynamically defined type `T1` that is still reachable by executing code.</span></span> <span data-ttu-id="839d8-122">たとえば、`T1`から導き出さ`T`、または`T`のメソッドのパラメーターの型である可能性があります`T1`です。</span><span class="sxs-lookup"><span data-stu-id="839d8-122">For example, `T1` might derive from `T`, or `T` might be the type of a parameter in a method of `T1`.</span></span>
 
- <span data-ttu-id="839d8-123">A **ByRef**に属している静的フィールドを`T`です。</span><span class="sxs-lookup"><span data-stu-id="839d8-123">A **ByRef** to a static field that belongs to `T`.</span></span>

- <span data-ttu-id="839d8-124">A <xref:System.RuntimeTypeHandle>、 <xref:System.RuntimeFieldHandle>、または<xref:System.RuntimeMethodHandle>を参照する`T`またはのコンポーネントに`T`です。</span><span class="sxs-lookup"><span data-stu-id="839d8-124">A <xref:System.RuntimeTypeHandle>, <xref:System.RuntimeFieldHandle>, or <xref:System.RuntimeMethodHandle> that refers to `T` or to a component of `T`.</span></span>

- <span data-ttu-id="839d8-125">インスタンスが使用可能なない直接リフレクション オブジェクトまたはアクセスに直接、<xref:System.Type>を表すオブジェクト`T`です。</span><span class="sxs-lookup"><span data-stu-id="839d8-125">An instance of any reflection object that could be used indirectly or directly to access the <xref:System.Type> object that represents `T`.</span></span> <span data-ttu-id="839d8-126">たとえば、<xref:System.Type>オブジェクトに対する`T`要素型が配列型から取得できます`T`、またはを持つジェネリック型から`T`型引数として。</span><span class="sxs-lookup"><span data-stu-id="839d8-126">For example, the <xref:System.Type> object for `T` can be obtained from an array type whose element type is `T`, or from a generic type that has `T` as a type argument.</span></span> 

- <span data-ttu-id="839d8-127">メソッド`M`任意のスレッドのコール スタックに場所`M`のメソッドは、`T`またはアセンブリで定義されているモジュール レベル メソッドです。</span><span class="sxs-lookup"><span data-stu-id="839d8-127">A method `M` on the call stack of any thread, where `M` is a method of `T` or a module-level method that is defined in the assembly.</span></span>

- <span data-ttu-id="839d8-128">アセンブリのモジュールで定義されている静的メソッドへのデリゲート。</span><span class="sxs-lookup"><span data-stu-id="839d8-128">A delegate to a static method that is defined in a module of the assembly.</span></span>

<span data-ttu-id="839d8-129">この一覧から 1 つの項目は、1 つだけの型またはアセンブリ内の 1 つのメソッドが、しかない場合、ランタイムは、アセンブリをアンロードできません。</span><span class="sxs-lookup"><span data-stu-id="839d8-129">If only one item from this list exists for only one type or one method in the assembly, the runtime cannot unload the assembly.</span></span>

> [!NOTE]
> <span data-ttu-id="839d8-130">ランタイムが実際にアンロードしないアセンブリ リスト内のすべての項目に対してファイナライザーが実行されるまでです。</span><span class="sxs-lookup"><span data-stu-id="839d8-130">The runtime does not actually unload the assembly until finalizers have run for all items in the list.</span></span>

<span data-ttu-id="839d8-131">追跡の有効期間の目的では、構築されたジェネリック型などの入力`List<int>`(C# の場合) または`List(Of Integer)`(Visual Basic で) を作成されで使用される回収可能アセンブリの生成をされていると見なされます、アセンブリのいずれかを定義します。ジェネリックを含む定義を入力するか、型引数のいずれかの定義を含むアセンブリにします。</span><span class="sxs-lookup"><span data-stu-id="839d8-131">For purposes of tracking lifetime, a constructed generic type such as `List<int>` (in C#) or `List(Of Integer)` (in Visual Basic) that is created and used in the generation of a collectible assembly is considered to have been defined either in the assembly that contains the generic type definition or in an assembly that contains the definition of one of its type arguments.</span></span> <span data-ttu-id="839d8-132">使用される正確なアセンブリは、実装の詳細と件名を変更します。</span><span class="sxs-lookup"><span data-stu-id="839d8-132">The exact assembly that is used is an implementation detail and subject to change.</span></span>
 
## <a name="restrictions-on-collectible-assemblies"></a><span data-ttu-id="839d8-133">回収可能アセンブリに関する制限事項</span><span class="sxs-lookup"><span data-stu-id="839d8-133">Restrictions on collectible assemblies</span></span>

<span data-ttu-id="839d8-134">回収可能アセンブリには次の制限が適用されます。</span><span class="sxs-lookup"><span data-stu-id="839d8-134">The following restrictions apply to collectible assemblies:</span></span> 

- <span data-ttu-id="839d8-135">**静的参照** </span><span class="sxs-lookup"><span data-stu-id="839d8-135">**Static references** </span></span>  
  <span data-ttu-id="839d8-136">通常の動的アセンブリ内の型は、回収可能アセンブリで定義されている型への静的参照を持つことはできません。</span><span class="sxs-lookup"><span data-stu-id="839d8-136">Types in an ordinary dynamic assembly cannot have static references to types that are defined in a collectible assembly.</span></span> <span data-ttu-id="839d8-137">たとえば、回収可能アセンブリ内の型から継承する通常の型を定義する場合、<xref:System.NotSupportedException>例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="839d8-137">For example, if you define an ordinary type that inherits from a type in a collectible assembly, a <xref:System.NotSupportedException> exception is thrown.</span></span> <span data-ttu-id="839d8-138">回収可能アセンブリ内の型は、別の回収可能アセンブリ、型への静的参照を持つことができますが、これは、参照されたアセンブリを参照しているアセンブリの有効期間の有効期間を拡張します。</span><span class="sxs-lookup"><span data-stu-id="839d8-138">A type in a collectible assembly can have static references to a type in another collectible assembly, but this extends the lifetime of the referenced assembly to the lifetime of the referencing assembly.</span></span>

- <span data-ttu-id="839d8-139">**COM 相互運用機能** </span><span class="sxs-lookup"><span data-stu-id="839d8-139">**COM interop** </span></span>  
   <span data-ttu-id="839d8-140">回収可能アセンブリ内でない COM インターフェイスを定義することができ、COM オブジェクトに回収可能アセンブリ内の型のインスタンスを変換することができます。</span><span class="sxs-lookup"><span data-stu-id="839d8-140">No COM interfaces can be defined within a collectible assembly, and no instances of types within a collectible assembly can be converted into COM objects.</span></span> <span data-ttu-id="839d8-141">回収可能アセンブリ内の型は、COM 呼び出し可能ラッパー (CCW) またはランタイム呼び出し可能ラッパー (RCW) として使用できません。</span><span class="sxs-lookup"><span data-stu-id="839d8-141">A type in a collectible assembly cannot serve as a COM callable wrapper (CCW) or runtime callable wrapper (RCW).</span></span> <span data-ttu-id="839d8-142">ただし、回収可能アセンブリ内の型は COM インターフェイスを実装するオブジェクトを使用できます。</span><span class="sxs-lookup"><span data-stu-id="839d8-142">However, types in collectible assemblies can use objects that implement COM interfaces.</span></span>

- <span data-ttu-id="839d8-143">**プラットフォーム呼び出し** </span><span class="sxs-lookup"><span data-stu-id="839d8-143">**Platform invoke** </span></span>  
   <span data-ttu-id="839d8-144">持つメソッドを<xref:System.Runtime.InteropServices.DllImportAttribute>回収可能アセンブリ内で宣言されているときに、属性はコンパイルされません。</span><span class="sxs-lookup"><span data-stu-id="839d8-144">Methods that have the <xref:System.Runtime.InteropServices.DllImportAttribute> attribute will not compile when they are declared in a collectible assembly.</span></span> <span data-ttu-id="839d8-145"><xref:System.Reflection.Emit.OpCodes.Calli?displayProperty=nameWithType>命令は、回収可能アセンブリ内の型の実装で使用することはできませんし、このような型は、アンマネージ コードにマーシャ リングすることはできません。</span><span class="sxs-lookup"><span data-stu-id="839d8-145">The <xref:System.Reflection.Emit.OpCodes.Calli?displayProperty=nameWithType> instruction cannot be used in the implementation of a type in a collectible assembly, and such types cannot be marshaled to unmanaged code.</span></span> <span data-ttu-id="839d8-146">ただし、非回収可能アセンブリで宣言されているエントリ ポイントを使用してネイティブ コードを呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="839d8-146">However, you can call into native code by using an entry point that is declared in a non-collectible assembly.</span></span>
 
- <span data-ttu-id="839d8-147">**マーシャ リング** </span><span class="sxs-lookup"><span data-stu-id="839d8-147">**Marshaling** </span></span>  
   <span data-ttu-id="839d8-148">回収可能アセンブリで定義されている (特に、デリゲートは) 内のオブジェクトをマーシャ リングすることはできません。</span><span class="sxs-lookup"><span data-stu-id="839d8-148">Objects (in particular, delegates) that are defined in collectible assemblies cannot be marshaled.</span></span> <span data-ttu-id="839d8-149">これは、すべての一時的な生成型に制限します。</span><span class="sxs-lookup"><span data-stu-id="839d8-149">This is a restriction on all transient emitted types.</span></span>

- <span data-ttu-id="839d8-150">**アセンブリの読み込み** </span><span class="sxs-lookup"><span data-stu-id="839d8-150">**Assembly loading** </span></span>  
   <span data-ttu-id="839d8-151">リフレクション出力は、回収可能アセンブリを読み込むためのサポートされている唯一のメカニズムです。</span><span class="sxs-lookup"><span data-stu-id="839d8-151">Reflection emit is the only mechanism that is supported for loading collectible assemblies.</span></span> <span data-ttu-id="839d8-152">アセンブリの読み込みの他の形式を使用して、読み込まれたアセンブリをアンロードすることはできません。</span><span class="sxs-lookup"><span data-stu-id="839d8-152">Assemblies that are loaded by using any other form of assembly loading cannot be unloaded.</span></span>
 
- <span data-ttu-id="839d8-153">**コンテキスト バインド オブジェクト**  </span><span class="sxs-lookup"><span data-stu-id="839d8-153">**Context-bound objects**  </span></span>  
   <span data-ttu-id="839d8-154">コンテキストの静的変数はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="839d8-154">Context-static variables are not supported.</span></span> <span data-ttu-id="839d8-155">回収可能アセンブリで型を拡張することはできません<xref:System.ContextBoundObject>です。</span><span class="sxs-lookup"><span data-stu-id="839d8-155">Types in a collectible assembly cannot extend <xref:System.ContextBoundObject>.</span></span> <span data-ttu-id="839d8-156">ただし、回収可能アセンブリのコードは他の場所で定義されているコンテキスト バインド オブジェクトを使用できます。</span><span class="sxs-lookup"><span data-stu-id="839d8-156">However, code in collectible assemblies can use context-bound objects that are defined elsewhere.</span></span>

- <span data-ttu-id="839d8-157">**スレッドの静的データ**     </span><span class="sxs-lookup"><span data-stu-id="839d8-157">**Thread-static data**     </span></span>  
   <span data-ttu-id="839d8-158">スレッドの静的変数はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="839d8-158">Thread-static variables are not supported.</span></span>

## <a name="see-also"></a><span data-ttu-id="839d8-159">関連項目</span><span class="sxs-lookup"><span data-stu-id="839d8-159">See also</span></span>

[<span data-ttu-id="839d8-160">動的メソッドおよびアセンブリの出力</span><span class="sxs-lookup"><span data-stu-id="839d8-160">Emitting Dynamic Methods and Assemblies</span></span>](emitting-dynamic-methods-and-assemblies.md)
