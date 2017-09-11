---
title: "相互運用性の概要 (C# プログラミング ガイド)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- COM interop
- C# language, interoperability
- C++ Interop
- interoperability, about interoperability
- platform invoke
ms.assetid: c025b2e0-2357-4c27-8461-118f0090aeff
caps.latest.revision: 43
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: c817dcd9073a5a1d4aeee558bf53d50566bbb472
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="interoperability-overview-c-programming-guide"></a><span data-ttu-id="009a7-102">相互運用性の概要 (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="009a7-102">Interoperability Overview (C# Programming Guide)</span></span>
<span data-ttu-id="009a7-103">C# マネージ コードとアンマネージ コード間で相互運用を可能にする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="009a7-103">The topic describes methods to enable interoperability between C# managed code and unmanaged code.</span></span>  
  
## <a name="platform-invoke"></a><span data-ttu-id="009a7-104">プラットフォーム呼び出し</span><span class="sxs-lookup"><span data-stu-id="009a7-104">Platform Invoke</span></span>  
 <span data-ttu-id="009a7-105">"*プラットフォーム呼び出し*" とは、Microsoft Win32 API にあるような、ダイナミックリンク ライブラリ (DLL) で実装されているアンマネージ関数をマネージ コードで呼び出すことを可能にするサービスです。</span><span class="sxs-lookup"><span data-stu-id="009a7-105">*Platform invoke* is a service that enables managed code to call unmanaged functions that are implemented in dynamic link libraries (DLLs), such as those in the Microsoft Win32 API.</span></span> <span data-ttu-id="009a7-106">これはエクスポートされた関数を見つけて呼び出し、必要に応じて相互運用の境界を越えて、その引数 (整数、文字列、配列、構造体、その他) をマーシャリングします。</span><span class="sxs-lookup"><span data-stu-id="009a7-106">It locates and invokes an exported function and marshals its arguments (integers, strings, arrays, structures, and so on) across the interoperation boundary as needed.</span></span>  
  
 <span data-ttu-id="009a7-107">詳細については、「[アンマネージ DLL 関数の処理](../../../framework/interop/consuming-unmanaged-dll-functions.md)」と「[方法: プラットフォーム呼び出しを使用して Wave ファイルを再生する](../../../csharp/programming-guide/interop/how-to-use-platform-invoke-to-play-a-wave-file.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="009a7-107">For more information, see [Consuming Unmanaged DLL Functions](../../../framework/interop/consuming-unmanaged-dll-functions.md) and [How to: Use Platform Invoke to Play a Wave File](../../../csharp/programming-guide/interop/how-to-use-platform-invoke-to-play-a-wave-file.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="009a7-108">[共通言語ランタイム](../../../standard/clr.md) (CLR) が、システム リソースへのアクセスを管理します。</span><span class="sxs-lookup"><span data-stu-id="009a7-108">The [Common Language Runtime](../../../standard/clr.md) (CLR) manages access to system resources.</span></span> <span data-ttu-id="009a7-109">CLR の外部のアンマネージ コードを呼び出すと、このセキュリティ メカニズムがバイパスされるため、セキュリティ リスクが生じます。</span><span class="sxs-lookup"><span data-stu-id="009a7-109">Calling unmanaged code that is outside the CLR bypasses this security mechanism, and therefore presents a security risk.</span></span> <span data-ttu-id="009a7-110">たとえば、アンマネージ コードがアンマネージ コード内のリソースを直接呼び出した場合、CLR のセキュリティ機構がバイパスされます。</span><span class="sxs-lookup"><span data-stu-id="009a7-110">For example, unmanaged code might call resources in unmanaged code directly, bypassing CLR security mechanisms.</span></span> <span data-ttu-id="009a7-111">詳細については、[.NET Framework セキュリティ](http://go.microsoft.com/fwlink/?LinkId=37122)に関する記事を参照してください。</span><span class="sxs-lookup"><span data-stu-id="009a7-111">For more information, see [.NET Framework Security](http://go.microsoft.com/fwlink/?LinkId=37122).</span></span>  
  
## <a name="c-interop"></a><span data-ttu-id="009a7-112">C++ Interop</span><span class="sxs-lookup"><span data-stu-id="009a7-112">C++ Interop</span></span>  
 <span data-ttu-id="009a7-113">It Just Works (IJW) とも呼ばれる C++ interop を使用してネイティブ C++ クラスをラップすると、このクラスを C# またはその他の .NET Framework 言語で作成されたコードで使用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="009a7-113">You can use C++ interop, also known as It Just Works (IJW), to wrap a native C++ class so that it can be consumed by code that is authored in C# or another .NET Framework language.</span></span> <span data-ttu-id="009a7-114">これを行うには、C++ コードを記述して、ネイティブ DLL または COM コンポーネントをラップします。</span><span class="sxs-lookup"><span data-stu-id="009a7-114">To do this, you write C++ code to wrap a native DLL or COM component.</span></span> <span data-ttu-id="009a7-115">他の .NET Framework 言語とは異なり、[!INCLUDE[vcprvc](~/includes/vcprvc-md.md)] には相互運用性サポートが備えられています。これにより、マネージ コードとアンマネージ コードは同じアプリケーション内、また同じファイルでも共存できるようになります。</span><span class="sxs-lookup"><span data-stu-id="009a7-115">Unlike other .NET Framework languages, [!INCLUDE[vcprvc](~/includes/vcprvc-md.md)] has interoperability support that enables managed and unmanaged code to be located in the same application and even in the same file.</span></span> <span data-ttu-id="009a7-116">C++ コードは、マネージ アセンブリを生成する **/clr** コンパイラ スイッチを使用して構築できます。</span><span class="sxs-lookup"><span data-stu-id="009a7-116">You then build the C++ code by using the **/clr** compiler switch to produce a managed assembly.</span></span> <span data-ttu-id="009a7-117">最後に、C# プロジェクトのアセンブリへの参照を追加し、他のマネージ クラスを使用するときと同じように、ラップされたオブジェクトを使用します。</span><span class="sxs-lookup"><span data-stu-id="009a7-117">Finally, you add a reference to the assembly in your C# project and use the wrapped objects just as you would use other managed classes.</span></span>  
  
## <a name="exposing-com-components-to-c"></a><span data-ttu-id="009a7-118">C# への COM コンポーネントの公開</span><span class="sxs-lookup"><span data-stu-id="009a7-118">Exposing COM Components to C#</span></span>  
 <span data-ttu-id="009a7-119">C# プロジェクトから COM コンポーネントを使用することができます。</span><span class="sxs-lookup"><span data-stu-id="009a7-119">You can consume a COM component from a C# project.</span></span> <span data-ttu-id="009a7-120">一般的な手順は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="009a7-120">The general steps are as follows:</span></span>  
  
1.  <span data-ttu-id="009a7-121">使用する COM コンポーネントを探して登録します。</span><span class="sxs-lookup"><span data-stu-id="009a7-121">Locate a COM component to use and register it.</span></span> <span data-ttu-id="009a7-122">regsvr32.exe を使用して、COM DLL の登録または登録解除を行います。</span><span class="sxs-lookup"><span data-stu-id="009a7-122">Use regsvr32.exe to register or un–register a COM DLL.</span></span>  
  
2.  <span data-ttu-id="009a7-123">プロジェクトに、COM コンポーネントまたはタイプ ライブラリへの参照を追加します。</span><span class="sxs-lookup"><span data-stu-id="009a7-123">Add to the project a reference to the COM component or type library.</span></span>  
  
     <span data-ttu-id="009a7-124">参照を追加する際、[!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] は [Tlbimp.exe (Type Library Importer)](http://msdn.microsoft.com/library/ec0a8d63-11b3-4acd-b398-da1e37e97382) を使用します。これにより、タイプ ライブラリを入力として取得し、.NET Framework 相互運用アセンブリを出力します。</span><span class="sxs-lookup"><span data-stu-id="009a7-124">When you add the reference, [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] uses the [Tlbimp.exe (Type Library Importer)](http://msdn.microsoft.com/library/ec0a8d63-11b3-4acd-b398-da1e37e97382), which takes a type library as input, to output a .NET Framework interop assembly.</span></span> <span data-ttu-id="009a7-125">このアセンブリは、ランタイム呼び出し可能ラッパー (RCW) とも呼ばれ、タイプ ライブラリ内の COM クラスとインターフェイスをラップする、マネージ クラスとインターフェイスを含みます。</span><span class="sxs-lookup"><span data-stu-id="009a7-125">The assembly, also named a runtime callable wrapper (RCW), contains managed classes and interfaces that wrap the COM classes and interfaces that are in the type library.</span></span> [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)]<span data-ttu-id="009a7-126"> は、生成されたアセンブリへの参照をプロジェクトに追加します。</span><span class="sxs-lookup"><span data-stu-id="009a7-126"> adds to the project a reference to the generated assembly.</span></span>  
  
3.  <span data-ttu-id="009a7-127">RCW で定義されているクラスのインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="009a7-127">Create an instance of a class that is defined in the RCW.</span></span> <span data-ttu-id="009a7-128">これにより、COM オブジェクトのインスタンスが作成されます。</span><span class="sxs-lookup"><span data-stu-id="009a7-128">This, in turn, creates an instance of the COM object.</span></span>  
  
4.  <span data-ttu-id="009a7-129">他のマネージ オブジェクトを使用するときと同様に、オブジェクトを使用します。</span><span class="sxs-lookup"><span data-stu-id="009a7-129">Use the object just as you use other managed objects.</span></span> <span data-ttu-id="009a7-130">オブジェクトがガベージ コレクションによって解放されるとき、COM オブジェクトのインスタンスもメモリから解放されます。</span><span class="sxs-lookup"><span data-stu-id="009a7-130">When the object is reclaimed by garbage collection, the instance of the COM object is also released from memory.</span></span>  
  
 <span data-ttu-id="009a7-131">詳細については、「[.NET Framework への COM コンポーネントの公開](http://msdn.microsoft.com/library/e78b14f1-e487-43cd-9c6d-1a07483f1730)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="009a7-131">For more information, see [Exposing COM Components to the .NET Framework](http://msdn.microsoft.com/library/e78b14f1-e487-43cd-9c6d-1a07483f1730).</span></span>  
  
## <a name="exposing-c-to-com"></a><span data-ttu-id="009a7-132">COM への C# の公開</span><span class="sxs-lookup"><span data-stu-id="009a7-132">Exposing C# to COM</span></span>  
 <span data-ttu-id="009a7-133">COM クライアントは、適切に公開されている C# 型を使用できます。</span><span class="sxs-lookup"><span data-stu-id="009a7-133">COM clients can consume C# types that have been correctly exposed.</span></span> <span data-ttu-id="009a7-134">C# 型を公開する基本的な手順は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="009a7-134">The basic steps to expose C# types are as follows:</span></span>  
  
1.  <span data-ttu-id="009a7-135">C# プロジェクトに相互運用属性を追加します。</span><span class="sxs-lookup"><span data-stu-id="009a7-135">Add interop attributes in the C# project.</span></span>  
  
     <span data-ttu-id="009a7-136">アセンブリ COM は、[!INCLUDE[csprcs](~/includes/csprcs-md.md)] プロジェクト プロパティを変更することで参照できるようになります。</span><span class="sxs-lookup"><span data-stu-id="009a7-136">You can make an assembly COM visible by modifying [!INCLUDE[csprcs](~/includes/csprcs-md.md)] project properties.</span></span> <span data-ttu-id="009a7-137">詳細については、「[[アセンブリ情報] ダイアログ ボックス](/visualstudio/ide/reference/assembly-information-dialog-box)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="009a7-137">For more information, see [Assembly Information Dialog Box](/visualstudio/ide/reference/assembly-information-dialog-box).</span></span>  
  
2.  <span data-ttu-id="009a7-138">COM タイプ ライブラリを生成し、COM の使用状況に登録します。</span><span class="sxs-lookup"><span data-stu-id="009a7-138">Generate a COM type library and register it for COM usage.</span></span>  
  
     <span data-ttu-id="009a7-139">[!INCLUDE[csprcs](~/includes/csprcs-md.md)] プロジェクト プロパティを変更して、C# アセンブリが COM 相互運用に自動的に登録されるようにできます。</span><span class="sxs-lookup"><span data-stu-id="009a7-139">You can modify [!INCLUDE[csprcs](~/includes/csprcs-md.md)] project properties to automatically register the C# assembly for COM interop.</span></span> [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)]<span data-ttu-id="009a7-140"> は `/tlb` コマンド ライン スイッチを使用して [Regasm.exe (Assembly Registration Tool)](http://msdn.microsoft.com/library/e190e342-36ef-4651-a0b4-0e8c2c0281cb) を使用します。これにより、マネージ アセンブリが入力として出力され、タイプ ライブラリを生成できます。</span><span class="sxs-lookup"><span data-stu-id="009a7-140"> uses the [Regasm.exe (Assembly Registration Tool)](http://msdn.microsoft.com/library/e190e342-36ef-4651-a0b4-0e8c2c0281cb), using the `/tlb` command-line switch, which takes a managed assembly as input, to generate a type library.</span></span> <span data-ttu-id="009a7-141">タイプ ライブラリは、アセンブリ内の `public` 型を記述し、レジストリ エントリを追加することで、COM クライアントがマネージ クラスを作成できるようにします。</span><span class="sxs-lookup"><span data-stu-id="009a7-141">This type library describes the `public` types in the assembly and adds registry entries so that COM clients can create managed classes.</span></span>  
  
 <span data-ttu-id="009a7-142">詳細については、「[COM への .NET Framework コンポーネントの公開](http://msdn.microsoft.com/library/e42a65f7-1e61-411f-b09a-aca1bbce24c6)」と「[COM クラスの例](../../../csharp/programming-guide/interop/example-com-class.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="009a7-142">For more information, see [Exposing .NET Framework Components to COM](http://msdn.microsoft.com/library/e42a65f7-1e61-411f-b09a-aca1bbce24c6) and [Example COM Class](../../../csharp/programming-guide/interop/example-com-class.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="009a7-143">関連項目</span><span class="sxs-lookup"><span data-stu-id="009a7-143">See Also</span></span>  
 <span data-ttu-id="009a7-144">[相互運用パフォーマンスの向上](http://go.microsoft.com/fwlink/?LinkId=99564) </span><span class="sxs-lookup"><span data-stu-id="009a7-144">[Improving Interop Performance](http://go.microsoft.com/fwlink/?LinkId=99564) </span></span>  
 <span data-ttu-id="009a7-145">[COM 相互運用の概要](http://go.microsoft.com/fwlink/?LinkId=112406) </span><span class="sxs-lookup"><span data-stu-id="009a7-145">[Introduction to COM Interop](http://go.microsoft.com/fwlink/?LinkId=112406) </span></span>  
 <span data-ttu-id="009a7-146">[マネージ コードとアンマネージ コード間でのマーシャリング](http://go.microsoft.com/fwlink/?LinkId=112398) </span><span class="sxs-lookup"><span data-stu-id="009a7-146">[Marshaling between Managed and Unmanaged Code](http://go.microsoft.com/fwlink/?LinkId=112398) </span></span>  
 <span data-ttu-id="009a7-147">[アンマネージ コードとの相互運用](https://msdn.microsoft.com/library/sd10k43k) </span><span class="sxs-lookup"><span data-stu-id="009a7-147">[Interoperating with Unmanaged Code](https://msdn.microsoft.com/library/sd10k43k) </span></span>  
 <span data-ttu-id="009a7-148">[高度な COM 相互運用性](http://msdn.microsoft.com/en-us/3ada36e5-2390-4d70-b490-6ad8de92f2fb) </span><span class="sxs-lookup"><span data-stu-id="009a7-148">[Advanced COM Interoperability](http://msdn.microsoft.com/en-us/3ada36e5-2390-4d70-b490-6ad8de92f2fb) </span></span>  
 [<span data-ttu-id="009a7-149">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="009a7-149">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)

