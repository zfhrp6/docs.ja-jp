---
title: COM 用のアセンブリのパッケージ化
ms.date: 03/30/2017
ms.prod: .net-framework
ms.technology:
- dotnet-clr
ms.topic: article
helpviewer_keywords:
- exposing .NET Framework components to COM
- COM interop, packaging assemblies
- packaging assemblies for COM
- Tlbexp.exe
- TypeLibConverter class
- .NET Services Installation tool
- Assembly Registration tool
- Type Library Exporter
- Reqsvcs.exe
- interoperation with unmanaged code, exposing .NET Framework components
- interoperation with unmanaged code, packaging assemblies
- COM interop, exposing COM components
- Reqasm.exe
ms.assetid: 39dc55aa-f2a1-4093-87bb-f1c0edb6e761
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 5c1e3ee38f98eae46c09ec2175f3c9af01288bd2
ms.sourcegitcommit: 9a4fe1a1c37b26532654b4bbe22d702237950009
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="packaging-an-assembly-for-com"></a><span data-ttu-id="ae364-102">COM 用のアセンブリのパッケージ化</span><span class="sxs-lookup"><span data-stu-id="ae364-102">Packaging an Assembly for COM</span></span>
<span data-ttu-id="ae364-103">COM 開発者がアプリケーションに組み込むときに役立つ、マネージ型に関する情報を次に示します。</span><span class="sxs-lookup"><span data-stu-id="ae364-103">COM developers can benefit from the following information about the managed types they plan to incorporate in their application:</span></span>  
  
-   <span data-ttu-id="ae364-104">COM アプリケーションで使用できる型の一覧</span><span class="sxs-lookup"><span data-stu-id="ae364-104">A list of types that COM applications can consume</span></span>  
  
     <span data-ttu-id="ae364-105">マネージ型には、COM から参照できない型、参照可能だが作成できない型、および参照と作成の両方が可能な型があります。</span><span class="sxs-lookup"><span data-stu-id="ae364-105">Some managed types are invisible to COM; some are visible but not creatable; and some are both visible and creatable.</span></span> <span data-ttu-id="ae364-106">アセンブリは、参照できない型、参照できる型、作成できない型、作成できる型を任意に組み合わせて構成できます。</span><span class="sxs-lookup"><span data-stu-id="ae364-106">An assembly can comprise any combination of invisible, visible, not creatable, and creatable types.</span></span> <span data-ttu-id="ae364-107">完全を期すために、COM に公開するアセンブリ内の型を識別する必要があります。特に COM に公開するアセンブリ内の型が .NET Framework に公開されている型のサブセットである場合に型の識別が必要になります。</span><span class="sxs-lookup"><span data-stu-id="ae364-107">For completeness, identify the types in an assembly that you intend to expose to COM, especially when those types are a subset of the types exposed to the .NET Framework.</span></span>  
  
     <span data-ttu-id="ae364-108">追加情報については、「[相互運用のための .NET 型の要件](qualifying-net-types-for-interoperation.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ae364-108">For additional information, see [Qualifying .NET Types for Interoperation](qualifying-net-types-for-interoperation.md).</span></span>  
  
-   <span data-ttu-id="ae364-109">バージョン管理に関する注意事項</span><span class="sxs-lookup"><span data-stu-id="ae364-109">Versioning instructions</span></span>  
  
     <span data-ttu-id="ae364-110">クラス インターフェイス (COM 相互運用機能により生成されたインターフェイス) を実装したマネージ クラスには、バージョン管理に関する制約が生じる場合があります。</span><span class="sxs-lookup"><span data-stu-id="ae364-110">Managed classes that implement the class interface (a COM interop-generated interface) are subject to versioning restrictions.</span></span>  
  
     <span data-ttu-id="ae364-111">クラス インターフェイスの使用に関するガイドラインについては、次を参照してください。[クラス インターフェイスの概要](com-callable-wrapper.md#introducing-the-class-interface)です。</span><span class="sxs-lookup"><span data-stu-id="ae364-111">For guidelines on using the class interface, see [Introducing the class interface](com-callable-wrapper.md#introducing-the-class-interface).</span></span>  
  
-   <span data-ttu-id="ae364-112">配置に関する注意事項</span><span class="sxs-lookup"><span data-stu-id="ae364-112">Deployment instructions</span></span>  
  
     <span data-ttu-id="ae364-113">発行者により署名された厳密な名前のアセンブリは、グローバル アセンブリ キャッシュにインストールできます。</span><span class="sxs-lookup"><span data-stu-id="ae364-113">Strong-named assemblies that are signed by a publisher can be installed into the global assembly cache.</span></span> <span data-ttu-id="ae364-114">署名のないアセンブリは、プライベート アセンブリとしてユーザーのコンピューターにインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="ae364-114">Unsigned assemblies must be installed on the user's machine as private assemblies.</span></span>  
  
     <span data-ttu-id="ae364-115">詳細については、「[アセンブリのセキュリティに関する考慮事項](../app-domains/assembly-security-considerations.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ae364-115">For additional information, see [Assembly Security Considerations](../app-domains/assembly-security-considerations.md).</span></span>  
  
-   <span data-ttu-id="ae364-116">タイプ ライブラリのインクルード</span><span class="sxs-lookup"><span data-stu-id="ae364-116">Type library inclusion</span></span>  
  
     <span data-ttu-id="ae364-117">大部分の型は、COM アプリケーションで処理されるときにタイプ ライブラリが必要です。</span><span class="sxs-lookup"><span data-stu-id="ae364-117">Most types require a type library when consumed by a COM application.</span></span> <span data-ttu-id="ae364-118">タイプ ライブラリの生成は、自分で行うことも、COM 開発者に任せることもできます。</span><span class="sxs-lookup"><span data-stu-id="ae364-118">You can generate a type library or have COM developers perform this task.</span></span> <span data-ttu-id="ae364-119">[!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] には、タイプ ライブラリを生成するために次のオプションが用意されています。</span><span class="sxs-lookup"><span data-stu-id="ae364-119">The [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] provides the following options for generating a type library:</span></span>  
  
    -   [<span data-ttu-id="ae364-120">タイプ ライブラリ エクスポーター</span><span class="sxs-lookup"><span data-stu-id="ae364-120">Type Library Exporter</span></span>](#cpconpackagingassemblyforcomanchor1)  
  
    -   [<span data-ttu-id="ae364-121">TypeLibConverter クラス</span><span class="sxs-lookup"><span data-stu-id="ae364-121">TypeLibConverter Class</span></span>](#cpconpackagingassemblyforcomanchor2)  
  
    -   [<span data-ttu-id="ae364-122">アセンブリ登録ツール</span><span class="sxs-lookup"><span data-stu-id="ae364-122">Assembly Registration Tool</span></span>](#cpconpackagingassemblyforcomanchor3)  
  
    -   [<span data-ttu-id="ae364-123">.NET サービス インストール ツール</span><span class="sxs-lookup"><span data-stu-id="ae364-123">.NET Services Installation Tool</span></span>](#cpconpackagingassemblyforcomanchor4)  
  
     <span data-ttu-id="ae364-124">どの機構を選択した場合でも、提供するアセンブリ内で定義されたパブリック型だけが、生成されるタイプ ライブラリに含まれます。</span><span class="sxs-lookup"><span data-stu-id="ae364-124">Regardless of the mechanism you choose, only public types defined in the assembly you supply are included in the generated type library.</span></span>  
  
     <span data-ttu-id="ae364-125">タイプ ライブラリは、個別のファイルとしてパッケージ化することも、.NET ベースのアプリケーションに Win32 リソースとして埋め込むこともできます。</span><span class="sxs-lookup"><span data-stu-id="ae364-125">You can package a type library as a separate file or embed it as Win32 resource file within a .NET-based application.</span></span> <span data-ttu-id="ae364-126">Microsoft Visual Basic 6.0 ではこの作業は自動的に実行されますが、[!INCLUDE[vbprvbext](../../../includes/vbprvbext-md.md)] を使用する場合は、手動でタイプ ライブラリを埋め込む必要があります。</span><span class="sxs-lookup"><span data-stu-id="ae364-126">Microsoft Visual Basic 6.0 performed this task for you automatically; however, when using [!INCLUDE[vbprvbext](../../../includes/vbprvbext-md.md)], you must embed your type library manually.</span></span> <span data-ttu-id="ae364-127">手順については、「[How to: Embed Type Libraries as Win32 Resources in .NET-Based Applications](https://msdn.microsoft.com/library/c97b4b8c-2ab7-4ac7-8fc8-0ba5c5d59c44(v=vs.100))」(方法: タイプ ライブラリを Win32 リソースとして .NET ベースのアプリケーションに埋め込む) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ae364-127">For instructions, see [How to: Embed Type Libraries as Win32 Resources in .NET-Based Applications](https://msdn.microsoft.com/library/c97b4b8c-2ab7-4ac7-8fc8-0ba5c5d59c44(v=vs.100)).</span></span>  
  
<a name="cpconpackagingassemblyforcomanchor1"></a>   
## <a name="type-library-exporter"></a><span data-ttu-id="ae364-128">タイプ ライブラリ エクスポーター</span><span class="sxs-lookup"><span data-stu-id="ae364-128">Type Library Exporter</span></span>  
 <span data-ttu-id="ae364-129">[タイプ ライブラリ エクスポーター (Tlbexp.exe)](../tools/tlbexp-exe-type-library-exporter.md) は、アセンブリに含まれているクラスおよびインターフェイスを COM タイプ ライブラリに変換するコマンド ライン ツールです。</span><span class="sxs-lookup"><span data-stu-id="ae364-129">The [Type Library Exporter (Tlbexp.exe)](../tools/tlbexp-exe-type-library-exporter.md) is a command-line tool that converts the classes and interfaces contained in an assembly to a COM type library.</span></span> <span data-ttu-id="ae364-130">クラスの型情報が利用可能になると、COM クライアントは .NET クラスのインスタンスを生成し、COM オブジェクトの場合と同じ方法でインスタンスのメソッドを呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="ae364-130">Once the type information of the class is available, COM clients can create an instance of the .NET class and call the methods of the instance, just as if it were a COM object.</span></span> <span data-ttu-id="ae364-131">Tlbexp.exe により、一度に 1 つのアセンブリ全体が変換されます。</span><span class="sxs-lookup"><span data-stu-id="ae364-131">Tlbexp.exe converts an entire assembly at one time.</span></span> <span data-ttu-id="ae364-132">Tlbexp.exe を使用しても、アセンブリで定義されている型のサブセットに関する型情報は生成できません。</span><span class="sxs-lookup"><span data-stu-id="ae364-132">You cannot use Tlbexp.exe to generate type information for a subset of the types defined in an assembly.</span></span>  
  
<a name="cpconpackagingassemblyforcomanchor2"></a>   
## <a name="typelibconverter-class"></a><span data-ttu-id="ae364-133">TypeLibConverter クラス</span><span class="sxs-lookup"><span data-stu-id="ae364-133">TypeLibConverter Class</span></span>  
 <span data-ttu-id="ae364-134">**System.Runtime.Interop** 名前空間にある <xref:System.Runtime.InteropServices.TypeLibConverter> クラスは、アセンブリに含まれているクラスおよびインターフェイスを COM タイプ ライブラリに変換します。</span><span class="sxs-lookup"><span data-stu-id="ae364-134">The <xref:System.Runtime.InteropServices.TypeLibConverter> class, located in the **System.Runtime.Interop** namespace, converts the classes and interfaces contained in an assembly to a COM type library.</span></span> <span data-ttu-id="ae364-135">この API は、前のセクションで説明したタイプ ライブラリ エクスポーターと同じ型情報を生成します。</span><span class="sxs-lookup"><span data-stu-id="ae364-135">This API produces the same type information as the Type Library Exporter, described in the previous section.</span></span>  
  
 <span data-ttu-id="ae364-136">**TypeLibConverter クラス**は、<xref:System.Runtime.InteropServices.ITypeLibConverter> を実装しています。</span><span class="sxs-lookup"><span data-stu-id="ae364-136">The **TypeLibConverter class** implements the <xref:System.Runtime.InteropServices.ITypeLibConverter>.</span></span>  
  
<a name="cpconpackagingassemblyforcomanchor3"></a>   
## <a name="assembly-registration-tool"></a><span data-ttu-id="ae364-137">アセンブリ登録ツール</span><span class="sxs-lookup"><span data-stu-id="ae364-137">Assembly Registration Tool</span></span>  
 <span data-ttu-id="ae364-138">[アセンブリ登録ツール (Regasm.exe)](../tools/regasm-exe-assembly-registration-tool.md) は、**/tlb:** オプションを適用すると、タイプ ライブラリを生成および登録できます。</span><span class="sxs-lookup"><span data-stu-id="ae364-138">The [Assembly Registration Tool (Regasm.exe)](../tools/regasm-exe-assembly-registration-tool.md) can generate and register a type library when you apply the **/tlb:** option.</span></span> <span data-ttu-id="ae364-139">COM クライアントでは、タイプ ライブラリを Windows のレジストリにインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="ae364-139">COM clients require that type libraries be installed in the Windows registry.</span></span> <span data-ttu-id="ae364-140">このオプションを適用しない場合、Regasm.exe はアセンブリの型だけを登録し、タイプ ライブラリは登録しません。</span><span class="sxs-lookup"><span data-stu-id="ae364-140">Without this option, Regasm.exe only registers the types in an assembly, not the type library.</span></span> <span data-ttu-id="ae364-141">アセンブリの型を登録することと、タイプ ライブラリを登録することは、まったく別の作業です。</span><span class="sxs-lookup"><span data-stu-id="ae364-141">Registering the types in an assembly and registering the type library are distinct activities.</span></span>  
  
<a name="cpconpackagingassemblyforcomanchor4"></a>   
## <a name="net-services-installation-tool"></a><span data-ttu-id="ae364-142">.NET サービス インストール ツール</span><span class="sxs-lookup"><span data-stu-id="ae364-142">.NET Services Installation Tool</span></span>  
 <span data-ttu-id="ae364-143">[.NET サービス インストール ツール (Regsvcs.exe)](../tools/regsvcs-exe-net-services-installation-tool.md) は、Windows 2000 コンポーネント サービスにマネージ クラスを追加したり、1 つのツール内の複数のタスクを統合したりします。</span><span class="sxs-lookup"><span data-stu-id="ae364-143">The [.NET Services Installation Tool (Regsvcs.exe)](../tools/regsvcs-exe-net-services-installation-tool.md) adds managed classes to Windows 2000 Component Services and combines several tasks within a single tool.</span></span> <span data-ttu-id="ae364-144">Regsvcs.exe は、アセンブリの読み込みおよび登録だけでなく、タイプ ライブラリの生成、登録、および既存の COM+ 1.0 アプリケーションへのインストールができます。</span><span class="sxs-lookup"><span data-stu-id="ae364-144">In addition to loading and registering an assembly, Regsvcs.exe can generate, register, and install the type library into an existing COM+ 1.0 application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae364-145">関連項目</span><span class="sxs-lookup"><span data-stu-id="ae364-145">See Also</span></span>  
 <xref:System.Runtime.InteropServices.TypeLibConverter>  
 <xref:System.Runtime.InteropServices.ITypeLibConverter>  
 [<span data-ttu-id="ae364-146">COM への .NET Framework コンポーネントの公開</span><span class="sxs-lookup"><span data-stu-id="ae364-146">Exposing .NET Framework Components to COM</span></span>](exposing-dotnet-components-to-com.md)  
 [<span data-ttu-id="ae364-147">要件 (相互運用のための .NET 型の)</span><span class="sxs-lookup"><span data-stu-id="ae364-147">Qualifying .NET Types for Interoperation</span></span>](qualifying-net-types-for-interoperation.md)  
 [<span data-ttu-id="ae364-148">クラス インターフェイスの概要</span><span class="sxs-lookup"><span data-stu-id="ae364-148">Introducing the class interface</span></span>](com-callable-wrapper.md#introducing-the-class-interface)  
 [<span data-ttu-id="ae364-149">アセンブリのセキュリティに関する考慮事項</span><span class="sxs-lookup"><span data-stu-id="ae364-149">Assembly Security Considerations</span></span>](../app-domains/assembly-security-considerations.md)  
 [<span data-ttu-id="ae364-150">Tlbexp.exe (タイプ ライブラリ エクスポーター)</span><span class="sxs-lookup"><span data-stu-id="ae364-150">Tlbexp.exe (Type Library Exporter)</span></span>](../tools/tlbexp-exe-type-library-exporter.md)  
 [<span data-ttu-id="ae364-151">COM へのアセンブリの登録</span><span class="sxs-lookup"><span data-stu-id="ae364-151">Registering Assemblies with COM</span></span>](registering-assemblies-with-com.md)  
 <span data-ttu-id="ae364-152">[方法: タイプ ライブラリを Win32 リソースとしてアプリケーションに埋め込む](https://msdn.microsoft.com/library/c97b4b8c-2ab7-4ac7-8fc8-0ba5c5d59c44(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="ae364-152">[How to: Embed Type Libraries as Win32 Resources in Applications](https://msdn.microsoft.com/library/c97b4b8c-2ab7-4ac7-8fc8-0ba5c5d59c44(v=vs.100))</span></span>
