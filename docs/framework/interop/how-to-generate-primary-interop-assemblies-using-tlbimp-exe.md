---
title: "方法: Tlbimp.exe を使用してプライマリ相互運用機能アセンブリを生成する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- primary interop assemblies, generating
- Tlbimp.exe
- Type Library Importer
ms.assetid: 5419011c-6e57-40f6-8c65-386db8f7a651
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: bdf39da2a597d75479a2a3ed3d60132a0f7e7def
ms.sourcegitcommit: d95a91d685565f4d95c8773b558752864a6a3d7e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2018
---
# <a name="how-to-generate-primary-interop-assemblies-using-tlbimpexe"></a><span data-ttu-id="71ed3-102">方法: Tlbimp.exe を使用してプライマリ相互運用機能アセンブリを生成する</span><span class="sxs-lookup"><span data-stu-id="71ed3-102">How to: Generate Primary Interop Assemblies Using Tlbimp.exe</span></span>
<span data-ttu-id="71ed3-103">プライマリ相互運用機能アセンブリを生成するには、次の 2 つの方法があります。</span><span class="sxs-lookup"><span data-stu-id="71ed3-103">There are two ways to generate a primary interop assembly:</span></span>  
  
-   <span data-ttu-id="71ed3-104">[!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] によって提供される[タイプ ライブラリ インポーター (Tlbimp.exe)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md) を使用します。</span><span class="sxs-lookup"><span data-stu-id="71ed3-104">Using the [Type Library Importer (Tlbimp.exe)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md) provided by the [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)].</span></span>  
  
     <span data-ttu-id="71ed3-105">プライマリ相互運用機能アセンブリを生成する最も簡単な方法は、[Tlbimp.exe (タイプ ライブラリ インポーター)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md) を使用することです。</span><span class="sxs-lookup"><span data-stu-id="71ed3-105">The most straightforward way to produce primary interop assemblies is to use the [Tlbimp.exe (Type Library Importer)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md).</span></span> <span data-ttu-id="71ed3-106">Tlbimp.exe は、次の保護機能を提供します。</span><span class="sxs-lookup"><span data-stu-id="71ed3-106">Tlbimp.exe provides the following safeguards:</span></span>  
  
    -   <span data-ttu-id="71ed3-107">新規の相互運用機能アセンブリを作成するときには、その前に登録されている他のプライマリ相互運用機能アセンブリを調べて、入れ子になったタイプ ライブラリの参照がないかを確認してください。</span><span class="sxs-lookup"><span data-stu-id="71ed3-107">Checks for other registered primary interop assemblies before creating new interop assemblies for any nested type library references.</span></span>  
  
    -   <span data-ttu-id="71ed3-108">プライマリ相互運用機能アセンブリに厳密な名前が付くようにコンテナー名やファイル名を指定しない場合は、プライマリ相互運用機能アセンブリの生成に失敗します。</span><span class="sxs-lookup"><span data-stu-id="71ed3-108">Fails to emit the primary interop assembly if you do not specify either the container or file name to give the primary interop assembly a strong name.</span></span>  
  
    -   <span data-ttu-id="71ed3-109">依存アセンブリへの参照を省略した場合は、プライマリ相互運用機能アセンブリの生成に失敗します。</span><span class="sxs-lookup"><span data-stu-id="71ed3-109">Fails to emit a primary interop assembly if you omit references to dependent assemblies.</span></span>  
  
    -   <span data-ttu-id="71ed3-110">プライマリ相互運用機能アセンブリではない依存アセンブリへの参照を追加した場合は、プライマリ相互運用機能アセンブリの生成に失敗します。</span><span class="sxs-lookup"><span data-stu-id="71ed3-110">Fails to emit a primary interop assembly if you add references to dependent assemblies that are not primary interop assemblies.</span></span>  
  
-   <span data-ttu-id="71ed3-111">C# などの共通言語仕様 (CLS) に準拠した言語を使用して、ソース コードで手動によりプライマリ相互運用機能アセンブリを作成します。</span><span class="sxs-lookup"><span data-stu-id="71ed3-111">Creating primary interop assemblies manually in source code by using a language that is compliant with the Common Language Specification (CLS), such as C#.</span></span> <span data-ttu-id="71ed3-112">この方法は、タイプ ライブラリが使用できない場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="71ed3-112">This approach is useful when a type library is unavailable.</span></span>  
  
 <span data-ttu-id="71ed3-113">厳密な名前でアセンブリに署名するには、暗号キー ペアが必要です。</span><span class="sxs-lookup"><span data-stu-id="71ed3-113">You must have a cryptographic key pair to sign the assembly with a strong name.</span></span> <span data-ttu-id="71ed3-114">詳細については、「[キー ペアを作成する](../../../docs/framework/app-domains/how-to-create-a-public-private-key-pair.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="71ed3-114">For details, see [Creating A Key Pair](../../../docs/framework/app-domains/how-to-create-a-public-private-key-pair.md).</span></span>  
  
### <a name="to-generate-a-primary-interop-assembly-using-tlbimpexe"></a><span data-ttu-id="71ed3-115">Tlbimp.exe を使用してプライマリ相互運用機能アセンブリを生成する方法</span><span class="sxs-lookup"><span data-stu-id="71ed3-115">To generate a primary interop assembly using Tlbimp.exe</span></span>  
  
1.  <span data-ttu-id="71ed3-116">コマンド プロンプトで、次のコマンドを入力します。</span><span class="sxs-lookup"><span data-stu-id="71ed3-116">At the command prompt, type:</span></span>  
  
     <span data-ttu-id="71ed3-117">**tlbimp** *tlbfile*  **/primary /keyfile:** *filename* **/out:** *assemblyname*</span><span class="sxs-lookup"><span data-stu-id="71ed3-117">**tlbimp** *tlbfile*  **/primary /keyfile:** *filename* **/out:** *assemblyname*</span></span>  
  
     <span data-ttu-id="71ed3-118">このコマンドの *tlbfile* は COM タイプ ライブラリを含むファイル、*filename* はキー ペアを含むコンテナーまたはファイルの名前、*assemblyname* は厳密な名前で署名するアセンブリの名前です。</span><span class="sxs-lookup"><span data-stu-id="71ed3-118">In this command, *tlbfile* is the file containing the COM type library, *filename* is the name of the container or file that contains the key pair, and *assemblyname* is the name of the assembly to sign with a strong name.</span></span>  
  
 <span data-ttu-id="71ed3-119">プライマリ相互運用機能アセンブリは、他のプライマリ相互運用機能アセンブリのみを参照できます。</span><span class="sxs-lookup"><span data-stu-id="71ed3-119">Primary interop assemblies can reference only other primary interop assemblies.</span></span> <span data-ttu-id="71ed3-120">アセンブリがサードパーティの COM タイプ ライブラリからタイプを参照する場合、プライマリ相互運用機能アセンブリを生成する前に、発行者からプライマリ相互運用機能アセンブリを取得する必要があります。</span><span class="sxs-lookup"><span data-stu-id="71ed3-120">If your assembly references types from a third-party COM type library, you must obtain a primary interop assembly from the publisher before you can generate your primary interop assembly.</span></span> <span data-ttu-id="71ed3-121">発行者である場合は、参照元のプライマリ相互運用機能アセンブリを生成する前に、依存タイプ ライブラリのプライマリ相互運用機能アセンブリを生成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="71ed3-121">If you are the publisher, you must generate a primary interop assembly for the dependent type library before generating the referencing primary interop assembly.</span></span>  
  
 <span data-ttu-id="71ed3-122">元のタイプ ライブラリとは異なるバージョン番号の依存プライマリ相互運用機能アセンブリは、現在のディレクトリにインストールされている場合、検出できません。</span><span class="sxs-lookup"><span data-stu-id="71ed3-122">A dependent primary interop assembly with a version number that differs from that of the original type library is not discoverable when installed in the current directory.</span></span> <span data-ttu-id="71ed3-123">依存プライマリ相互運用機能アセンブリを Windows レジストリに登録するか、または **/reference** オプションを使用して、Tlbimp.exe が依存 DLL を検出できるようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="71ed3-123">You must either register the dependent primary interop assembly in the Windows registry or use the **/reference** option to be sure that Tlbimp.exe finds the dependent DLL.</span></span>  
  
 <span data-ttu-id="71ed3-124">複数のバージョンのタイプ ライブラリをラップすることもできます。</span><span class="sxs-lookup"><span data-stu-id="71ed3-124">You can also wrap multiple versions of a type library.</span></span> <span data-ttu-id="71ed3-125">その方法については、「[方法: 複数のバージョンのタイプ ライブラリをラップする](https://msdn.microsoft.com/library/79eefe04-a770-4bc3-8ea2-e90ddb8ec31f(v=vs.100))」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="71ed3-125">For instructions, see [How to: Wrap Multiple Versions of Type Libraries](https://msdn.microsoft.com/library/79eefe04-a770-4bc3-8ea2-e90ddb8ec31f(v=vs.100)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="71ed3-126">例</span><span class="sxs-lookup"><span data-stu-id="71ed3-126">Example</span></span>  
 <span data-ttu-id="71ed3-127">次の例は、COM タイプ ライブラリ `LibUtil.tlb` をインポートし、アセンブリ `LibUtil.dll` にキー ファイル `CompanyA.snk` を使用して厳密な名前で署名します。</span><span class="sxs-lookup"><span data-stu-id="71ed3-127">The following example imports the COM type library `LibUtil.tlb` and signs the assembly `LibUtil.dll` with a strong name using the key file `CompanyA.snk`.</span></span> <span data-ttu-id="71ed3-128">この例では、特定の名前空間名を省略することにより、既定の名前空間 `LibUtil` を生成します。</span><span class="sxs-lookup"><span data-stu-id="71ed3-128">By omitting a specific namespace name, this example produces the default namespace, `LibUtil`.</span></span>  
  
```  
tlbimp LibUtil.tlb /primary /keyfile:CompanyA.snk /out:LibUtil.dll  
```  
  
 <span data-ttu-id="71ed3-129">名前を (*VendorName*.*LibraryName* の名前付けガイドラインを使用して) より分かりやすくするために、次の例では既定のアセンブリ ファイル名と名前空間名をオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="71ed3-129">For a more descriptive name (using the *VendorName*.*LibraryName* naming guideline), the following example overrides the default assembly file name and namespace name.</span></span>  
  
```  
tlbimp LibUtil.tlb /primary /keyfile:CompanyA.snk /namespace:CompanyA.LibUtil /out:CompanyA.LibUtil.dll  
```  
  
 <span data-ttu-id="71ed3-130">次の例では、`CompanyA.LibUtil.dll` を参照する `MyLib.tlb` をインポートし、アセンブリ `CompanyB.MyLib.dll` にキー ファイル `CompanyB.snk` を使用して厳密な名前で署名します。</span><span class="sxs-lookup"><span data-stu-id="71ed3-130">The following example imports `MyLib.tlb`, which references `CompanyA.LibUtil.dll`, and signs the assembly `CompanyB.MyLib.dll` with a strong name using the key file `CompanyB.snk`.</span></span> <span data-ttu-id="71ed3-131">名前空間 `CompanyB.MyLib` は、既定の名前空間名をオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="71ed3-131">The namespace, `CompanyB.MyLib`, overrides the default namespace name.</span></span>  
  
```  
tlbimp MyLib.tlb /primary /keyfile:CompanyB.snk /namespace:CompanyB.MyLib /reference:CompanyA.LibUtil.dll /out:CompanyB.MyLib.dll  
```  
  
## <a name="see-also"></a><span data-ttu-id="71ed3-132">参照</span><span class="sxs-lookup"><span data-stu-id="71ed3-132">See Also</span></span>  
 [<span data-ttu-id="71ed3-133">方法: プライマリ相互運用機能アセンブリを登録する</span><span class="sxs-lookup"><span data-stu-id="71ed3-133">How to: Register Primary Interop Assemblies</span></span>](../../../docs/framework/interop/how-to-register-primary-interop-assemblies.md)
