---
title: "方法: プライマリ相互運用機能アセンブリを登録する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- registering primary interop assemblies
- primary interop assemblies, registering
ms.assetid: 4b2fcf8a-429d-43ce-8334-e026040be8bb
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 1b72a24f349237aa35ccae295e9e552facc21ddd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-register-primary-interop-assemblies"></a><span data-ttu-id="33fb0-102">方法: プライマリ相互運用機能アセンブリを登録する</span><span class="sxs-lookup"><span data-stu-id="33fb0-102">How to: Register Primary Interop Assemblies</span></span>
<span data-ttu-id="33fb0-103">クラスは、COM 相互運用でのみマーシャリングすることができ、常にインターフェイスとしてマーシャリングされます。</span><span class="sxs-lookup"><span data-stu-id="33fb0-103">Classes can be marshaled only by COM interop and are always marshaled as interfaces.</span></span> <span data-ttu-id="33fb0-104">場合によっては、クラスをマーシャリングするために使用されるインターフェイスが、クラス インターフェイスと呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="33fb0-104">In some cases the interface used to marshal the class is known as the class interface.</span></span> <span data-ttu-id="33fb0-105">クラス インターフェイスを任意のインターフェイスでオーバーライドする方法の詳細については、「[COM 呼び出し可能ラッパー](../../../docs/framework/interop/com-callable-wrapper.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="33fb0-105">For information about overriding the class interface with an interface of your choice, see [COM Callable Wrapper](../../../docs/framework/interop/com-callable-wrapper.md).</span></span>  
  
 <span data-ttu-id="33fb0-106">.NET Framework アプリケーションから COM の型を使用するすべての開発者は相互運用機能アセンブリを生成できますが、そのようにすると問題が発生します。</span><span class="sxs-lookup"><span data-stu-id="33fb0-106">Although any developer who wants to use COM types from a .NET Framework application can generate an interop assembly, doing so creates a problem.</span></span> <span data-ttu-id="33fb0-107">開発者が COM タイプ ライブラリをインポートして署名するたびに、その開発者は、別の開発者によってインポートされて署名されたものとは互換性のない一意の型のセットを作成することになります。</span><span class="sxs-lookup"><span data-stu-id="33fb0-107">Each time a developer imports and signs a COM type library, that developer creates a set of unique types that are incompatible with those imported and signed by another developer.</span></span> <span data-ttu-id="33fb0-108">この型の非互換性の問題を解決する方法は、各開発者が、ベンダーによって提供されて署名されたプライマリ相互運用機能アセンブリを取得することです。</span><span class="sxs-lookup"><span data-stu-id="33fb0-108">The solution to this type incompatibility problem is for each developer to obtain the vendor-supplied and signed primary interop assembly.</span></span>  
  
 <span data-ttu-id="33fb0-109">サードパーティの COM 型を他のアプリケーションに公開する予定の場合は、それが定義するタイプ ライブラリと同じ発行元によって提供されるプライマリ相互運用機能アセンブリを常に使用してください。</span><span class="sxs-lookup"><span data-stu-id="33fb0-109">If you plan to expose third-party COM types to other applications, always use the primary interop assembly provided by the same publisher as the type library it defines.</span></span> <span data-ttu-id="33fb0-110">保証された型の互換性を提供することに加えて、多くの場合、プライマリ相互運用機能アセンブリは相互運用性を強化するためにベンダーによってカスタマイズされます。</span><span class="sxs-lookup"><span data-stu-id="33fb0-110">In addition to providing guaranteed type compatibility, primary interop assemblies are often customized by the vendor to enhance interoperability.</span></span>  
  
 <span data-ttu-id="33fb0-111">サードパーティの COM 型を公開する予定がない場合でも、プライマリ相互運用機能アセンブリを使用することで、COM コンポーネントとの相互運用のタスクを容易に実行できます。</span><span class="sxs-lookup"><span data-stu-id="33fb0-111">Even if you do not plan to expose third-party COM types, using the primary interop assembly can ease the task of interoperating with COM components.</span></span> <span data-ttu-id="33fb0-112">ただし、この方法では、プライマリ相互運用機能アセンブリで定義された型に対してベンダーが加える可能性のある変更から隔離されることはありません。</span><span class="sxs-lookup"><span data-stu-id="33fb0-112">However, this strategy provides no insulation from changes a vendor might make to types defined in a primary interop assembly.</span></span> <span data-ttu-id="33fb0-113">使用するアプリケーションでそのような隔離が必要な場合は、プライマリ相互運用機能アセンブリを使用する代わりに独自の相互運用アセンブリを生成してください。</span><span class="sxs-lookup"><span data-stu-id="33fb0-113">When your application requires such insulation, generate your own interop assembly instead of using the primary interop assembly.</span></span>  
  
 <span data-ttu-id="33fb0-114">取得したすべてのプライマリ相互運用機能アセンブリを開発コンピューターに登録してからでなければ、[!INCLUDE[vsprvsext](../../../includes/vsprvsext-md.md)] でそれらを参照できません。</span><span class="sxs-lookup"><span data-stu-id="33fb0-114">You must register all acquired primary interop assemblies on your development computer before you can reference them with [!INCLUDE[vsprvsext](../../../includes/vsprvsext-md.md)].</span></span> <span data-ttu-id="33fb0-115">Visual Studio は、初めて COM タイプ ライブラリから型を参照するときに、プライマリ相互運用機能アセンブリを検索して使用します。</span><span class="sxs-lookup"><span data-stu-id="33fb0-115">Visual Studio looks for and uses a primary interop assembly the first time that you reference a type from a COM type library.</span></span> <span data-ttu-id="33fb0-116">Visual Studio は、タイプ ライブラリに関連付けられているプライマリ相互運用機能アセンブリが見つからない場合、それを取得するように求めるプロンプトを出すか、または相互運用機能アセンブリを代わりに作成することを申し出ます。</span><span class="sxs-lookup"><span data-stu-id="33fb0-116">If Visual Studio cannot locate the primary interop assembly associated with the type library, it prompts you to acquire it or offers to create an interop assembly instead.</span></span> <span data-ttu-id="33fb0-117">同じように、[タイプ ライブラリ インポーター (Tlbimp.exe)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md) も、レジストリを使用してプライマリ相互運用機能アセンブリを見つけます。</span><span class="sxs-lookup"><span data-stu-id="33fb0-117">Likewise, the [Type Library Importer (Tlbimp.exe)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md) also uses the registry to locate primary interop assemblies.</span></span>  
  
 <span data-ttu-id="33fb0-118">Visual Studio を使用する予定がない限り、プライマリ相互運用機能アセンブリを登録する必要はありませんが、登録には次の 2 つの利点があります。</span><span class="sxs-lookup"><span data-stu-id="33fb0-118">Although it is not necessary to register primary interop assemblies unless you plan to use Visual Studio, registration provides two advantages:</span></span>  
  
-   <span data-ttu-id="33fb0-119">登録されているプライマリ相互運用機能アセンブリは、元のタイプ ライブラリのレジストリ キーの下で明白にマークされます。</span><span class="sxs-lookup"><span data-stu-id="33fb0-119">A registered primary interop assembly is clearly marked under the registry key of the original type library.</span></span> <span data-ttu-id="33fb0-120">登録は、コンピューター上のプライマリ相互運用機能アセンブリを検索するための最善の方法です。</span><span class="sxs-lookup"><span data-stu-id="33fb0-120">Registration is the best way for you to locate a primary interop assembly on your computer.</span></span>  
  
-   <span data-ttu-id="33fb0-121">将来のいつか、Visual Studio を使用して登録されていないプライマリ相互運用機能アセンブリのある型を参照する場合に、間違えて新しい相互運用機能アセンブリを生成して使用してしまうことを回避できます。</span><span class="sxs-lookup"><span data-stu-id="33fb0-121">You can avoid accidentally generating and using a new interop assembly if, at some time in the future, you do use Visual Studio to reference a type for which you have an unregistered primary interop assembly.</span></span>  
  
 <span data-ttu-id="33fb0-122">[アセンブリ登録ツール (Regasm.exe)](../../../docs/framework/tools/regasm-exe-assembly-registration-tool.md) を使用して、プライマリ相互運用機能アセンブリを登録します。</span><span class="sxs-lookup"><span data-stu-id="33fb0-122">Use the [Assembly Registration Tool (Regasm.exe)](../../../docs/framework/tools/regasm-exe-assembly-registration-tool.md) to register a primary interop assembly.</span></span>  
  
### <a name="to-register-a-primary-interop-assembly"></a><span data-ttu-id="33fb0-123">プライマリ相互運用機能アセンブリを登録する方法</span><span class="sxs-lookup"><span data-stu-id="33fb0-123">To register a primary interop assembly</span></span>  
  
1.  <span data-ttu-id="33fb0-124">コマンド プロンプトで、次のコマンドを入力します。</span><span class="sxs-lookup"><span data-stu-id="33fb0-124">At the command prompt, type:</span></span>  
  
     <span data-ttu-id="33fb0-125">**regasm** *assemblyname*</span><span class="sxs-lookup"><span data-stu-id="33fb0-125">**regasm** *assemblyname*</span></span>  
  
     <span data-ttu-id="33fb0-126">このコマンドで、*assemblyname* は登録されているアセンブリのファイル名です。</span><span class="sxs-lookup"><span data-stu-id="33fb0-126">In this command, *assemblyname* is the file name of the assembly that is registered.</span></span> <span data-ttu-id="33fb0-127">Regasm.exe は、元のタイプ ライブラリと同じレジストリ キーの下に、プライマリ相互運用機能アセンブリの項目を追加します。</span><span class="sxs-lookup"><span data-stu-id="33fb0-127">Regasm.exe adds an entry for the primary interop assembly under the same registry key as the original type library.</span></span>  
  
## <a name="example"></a><span data-ttu-id="33fb0-128">例</span><span class="sxs-lookup"><span data-stu-id="33fb0-128">Example</span></span>  
 <span data-ttu-id="33fb0-129">次の例は、`CompanyA.UtilLib.dll` プライマリ相互運用機能アセンブリを登録します。</span><span class="sxs-lookup"><span data-stu-id="33fb0-129">The following example registers the `CompanyA.UtilLib.dll` primary interop assembly.</span></span>  
  
```  
regasm CompanyA.UtilLib.dll  
```  
  
## <a name="see-also"></a><span data-ttu-id="33fb0-130">関連項目</span><span class="sxs-lookup"><span data-stu-id="33fb0-130">See Also</span></span>  
 [<span data-ttu-id="33fb0-131">プライマリ相互運用機能アセンブリを使ったプログラミング</span><span class="sxs-lookup"><span data-stu-id="33fb0-131">Programming with Primary Interop Assemblies</span></span>](http://msdn.microsoft.com/en-us/306fa1d6-0703-4004-9e93-d0a57f1be81e)  
 [<span data-ttu-id="33fb0-132">プライマリ相互運用機能アセンブリの検索</span><span class="sxs-lookup"><span data-stu-id="33fb0-132">Locating Primary Interop Assemblies</span></span>](http://msdn.microsoft.com/en-us/d6768e4b-cd80-414d-a4f8-05d979eb393b)  
 [<span data-ttu-id="33fb0-133">プライマリ相互運用機能アセンブリの再配布</span><span class="sxs-lookup"><span data-stu-id="33fb0-133">Redistributing Primary Interop Assemblies</span></span>](http://msdn.microsoft.com/en-us/e76384f0-d631-474c-bdbd-13884cba0265)
