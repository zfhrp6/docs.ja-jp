---
title: COM へのアセンブリの登録
ms.date: 03/30/2017
ms.prod: .net-framework
ms.technology:
- dotnet-clr
ms.topic: article
helpviewer_keywords:
- COM interop, registering assemblies
- unregistering assemblies
- interoperation with unmanaged code, registering assemblies
- registering assemblies
ms.assetid: 87925795-a3ae-4833-b138-125413478551
caps.latest.revision: 11
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 3beaffdc0660055dd047f449388216ccfdd312cc
ms.sourcegitcommit: 9a4fe1a1c37b26532654b4bbe22d702237950009
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="registering-assemblies-with-com"></a><span data-ttu-id="9e5a0-102">COM へのアセンブリの登録</span><span class="sxs-lookup"><span data-stu-id="9e5a0-102">Registering Assemblies with COM</span></span>
<span data-ttu-id="9e5a0-103">[アセンブリ登録ツール (Regasm.exe)](../tools/regasm-exe-assembly-registration-tool.md) というコマンドライン ツールを実行して、COM で使うアセンブリを登録または登録解除できます。</span><span class="sxs-lookup"><span data-stu-id="9e5a0-103">You can run a command-line tool called the [Assembly Registration Tool (Regasm.exe)](../tools/regasm-exe-assembly-registration-tool.md) to register or unregister an assembly for use with COM.</span></span> <span data-ttu-id="9e5a0-104">Regasm.exe は、COM クライアントが .NET Framework のクラスを透過的に使うことができるように、クラスについての情報をシステム レジストリに追加します。</span><span class="sxs-lookup"><span data-stu-id="9e5a0-104">Regasm.exe adds information about the class to the system registry so COM clients can use the .NET Framework class transparently.</span></span> <span data-ttu-id="9e5a0-105"><xref:System.Runtime.InteropServices.RegistrationServices> クラスには、同等の機能が用意されています。</span><span class="sxs-lookup"><span data-stu-id="9e5a0-105">The <xref:System.Runtime.InteropServices.RegistrationServices> class provides the equivalent functionality.</span></span>  
  
 <span data-ttu-id="9e5a0-106">マネージ コンポーネントを COM クライアントからアクティブ化するには、先にマネージ コンポーネントを Windows レジストリに登録しておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="9e5a0-106">A managed component must be registered in the Windows registry before it can be activated from a COM client.</span></span> <span data-ttu-id="9e5a0-107">次の表では、Regasm.exe が通常、Windows レジストリに追加するキーを示します </span><span class="sxs-lookup"><span data-stu-id="9e5a0-107">The following table shows the keys that Regasm.exe typically adds to the Windows registry.</span></span> <span data-ttu-id="9e5a0-108">(000000 は実際の GUID の値を示します)。</span><span class="sxs-lookup"><span data-stu-id="9e5a0-108">(000000 indicates the actual GUID value.)</span></span>  
  
|<span data-ttu-id="9e5a0-109">GUID</span><span class="sxs-lookup"><span data-stu-id="9e5a0-109">GUID</span></span>|<span data-ttu-id="9e5a0-110">説明</span><span class="sxs-lookup"><span data-stu-id="9e5a0-110">Description</span></span>|<span data-ttu-id="9e5a0-111">レジストリ キー</span><span class="sxs-lookup"><span data-stu-id="9e5a0-111">Registry key</span></span>|  
|----------|-----------------|------------------|  
|<span data-ttu-id="9e5a0-112">CLSID</span><span class="sxs-lookup"><span data-stu-id="9e5a0-112">CLSID</span></span>|<span data-ttu-id="9e5a0-113">クラス識別子</span><span class="sxs-lookup"><span data-stu-id="9e5a0-113">Class identifier</span></span>|<span data-ttu-id="9e5a0-114">HKEY_CLASSES_ROOT\CLSID\\{000…000}</span><span class="sxs-lookup"><span data-stu-id="9e5a0-114">HKEY_CLASSES_ROOT\CLSID\\{000…000}</span></span>|  
|<span data-ttu-id="9e5a0-115">IID</span><span class="sxs-lookup"><span data-stu-id="9e5a0-115">IID</span></span>|<span data-ttu-id="9e5a0-116">インターフェイス識別子</span><span class="sxs-lookup"><span data-stu-id="9e5a0-116">Interface identifier</span></span>|<span data-ttu-id="9e5a0-117">HKEY_CLASSES_ROOT\Interface\\{000…000}</span><span class="sxs-lookup"><span data-stu-id="9e5a0-117">HKEY_CLASSES_ROOT\Interface\\{000…000}</span></span>|  
|<span data-ttu-id="9e5a0-118">LIBID</span><span class="sxs-lookup"><span data-stu-id="9e5a0-118">LIBID</span></span>|<span data-ttu-id="9e5a0-119">ライブラリ識別子</span><span class="sxs-lookup"><span data-stu-id="9e5a0-119">Library identifier</span></span>|<span data-ttu-id="9e5a0-120">HKEY_CLASSES_ROOT\TypeLib\\{000…000}</span><span class="sxs-lookup"><span data-stu-id="9e5a0-120">HKEY_CLASSES_ROOT\TypeLib\\{000…000}</span></span>|  
|<span data-ttu-id="9e5a0-121">ProgID</span><span class="sxs-lookup"><span data-stu-id="9e5a0-121">ProgID</span></span>|<span data-ttu-id="9e5a0-122">プログラム識別子</span><span class="sxs-lookup"><span data-stu-id="9e5a0-122">Programmatic identifier</span></span>|<span data-ttu-id="9e5a0-123">HKEY_CLASSES_ROOT\000…000</span><span class="sxs-lookup"><span data-stu-id="9e5a0-123">HKEY_CLASSES_ROOT\000…000</span></span>|  
  
 <span data-ttu-id="9e5a0-124">HKCR\CLSID\\{0000…0000} キーの下では、既定値がクラスの ProgID に設定され、Class と Assembly という 2 つの新しい名前付きの値が追加されます。</span><span class="sxs-lookup"><span data-stu-id="9e5a0-124">Under the HKCR\CLSID\\{0000…0000} key, the default value is set to the ProgID of the class, and two new named values, Class and Assembly, are added.</span></span> <span data-ttu-id="9e5a0-125">ランタイムは、レジストリから Assembly の値を読み取り、ランタイム アセンブリ リゾルバーに渡します。</span><span class="sxs-lookup"><span data-stu-id="9e5a0-125">The runtime reads the Assembly value from the registry and passes it on to the runtime assembly resolver.</span></span> <span data-ttu-id="9e5a0-126">アセンブリ リゾルバーは、名前やバージョン番号などのアセンブリの情報に基づいて、アセンブリの特定を試みます。</span><span class="sxs-lookup"><span data-stu-id="9e5a0-126">The assembly resolver attempts to locate the assembly, based on assembly information such as the name and version number.</span></span> <span data-ttu-id="9e5a0-127">アセンブリ リゾルバーがアセンブリを特定するには、アセンブリが次のいずれかの場所に存在する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9e5a0-127">For the assembly resolver to locate an assembly, the assembly has to be in one of the following locations:</span></span>  
  
-   <span data-ttu-id="9e5a0-128">グローバル アセンブリ キャッシュ (厳密な名前付きアセンブリである必要があります)。</span><span class="sxs-lookup"><span data-stu-id="9e5a0-128">The global assembly cache (must be a strong-named assembly).</span></span>  
  
-   <span data-ttu-id="9e5a0-129">アプリケーション ディレクトリ内。</span><span class="sxs-lookup"><span data-stu-id="9e5a0-129">In the application directory.</span></span> <span data-ttu-id="9e5a0-130">アプリケーション パスから読み込まれたアセンブリは、そのアプリケーションからのみアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="9e5a0-130">Assemblies loaded from the application path are only accessible from that application.</span></span>  
  
-   <span data-ttu-id="9e5a0-131">Regasm.exe に対する **/codebase** オプションで指定されたファイル パス上。</span><span class="sxs-lookup"><span data-stu-id="9e5a0-131">Along an file path specified with the **/codebase** option to Regasm.exe.</span></span>  
  
 <span data-ttu-id="9e5a0-132">Regasm.exe は、HKCR\CLSID\\{0000…0000} キーの下に InProcServer32 キーも作成します。</span><span class="sxs-lookup"><span data-stu-id="9e5a0-132">Regasm.exe also creates the InProcServer32 key under the HKCR\CLSID\\{0000…0000} key.</span></span> <span data-ttu-id="9e5a0-133">このキーの既定値は、共通言語ランタイム (Mscoree.dll) を初期化する DLL の名前に設定されます。</span><span class="sxs-lookup"><span data-stu-id="9e5a0-133">The default value for the key is set to the name of the DLL that initializes the common language runtime (Mscoree.dll).</span></span>  
  
## <a name="examining-registry-entries"></a><span data-ttu-id="9e5a0-134">レジストリ エントリを調べる</span><span class="sxs-lookup"><span data-stu-id="9e5a0-134">Examining Registry Entries</span></span>  
 <span data-ttu-id="9e5a0-135">COM 相互運用は、.NET Framework クラスのインスタンスを作成するための標準のクラス ファクトリの実装を提供します。</span><span class="sxs-lookup"><span data-stu-id="9e5a0-135">COM interop provides a standard class factory implementation to create an instance of any .NET Framework class.</span></span> <span data-ttu-id="9e5a0-136">クライアントは、他の COM コンポーネントと同様に、マネージ DLL で **DllGetClassObject** を呼び出してクラス ファクトリを取得し、オブジェクトを作成することができます。</span><span class="sxs-lookup"><span data-stu-id="9e5a0-136">Clients can call **DllGetClassObject** on the managed DLL to get a class factory and create objects, just as they would with any other COM component.</span></span>  
  
 <span data-ttu-id="9e5a0-137">`InprocServer32` サブキーには、従来の COM タイプ ライブラリの代わりに Mscoree.dll への参照が表示され、共通言語ランタイムがマネージ オブジェクトを作成することを示します。</span><span class="sxs-lookup"><span data-stu-id="9e5a0-137">For the `InprocServer32` subkey, a reference to Mscoree.dll appears in place of a traditional COM type library to indicate that the common language runtime creates the managed object.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e5a0-138">関連項目</span><span class="sxs-lookup"><span data-stu-id="9e5a0-138">See Also</span></span>  
 [<span data-ttu-id="9e5a0-139">COM への .NET Framework コンポーネントの公開</span><span class="sxs-lookup"><span data-stu-id="9e5a0-139">Exposing .NET Framework Components to COM</span></span>](exposing-dotnet-components-to-com.md)  
 [<span data-ttu-id="9e5a0-140">方法: COM から .NET 型を参照する</span><span class="sxs-lookup"><span data-stu-id="9e5a0-140">How to: Reference .NET Types from COM</span></span>](how-to-reference-net-types-from-com.md)  
 <span data-ttu-id="9e5a0-141">[.NET オブジェクトの呼び出し](https://msdn.microsoft.com/library/40c9626c-aea6-4bad-b8f0-c1de462efd33(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="9e5a0-141">[Calling a .NET Object](https://msdn.microsoft.com/library/40c9626c-aea6-4bad-b8f0-c1de462efd33(v=vs.100))</span></span>  
 <span data-ttu-id="9e5a0-142">[COM アクセスに対するアプリケーションの配置](https://msdn.microsoft.com/library/fb63564c-c1b9-4655-a094-a235625882ce(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="9e5a0-142">[Deploying an Application for COM Access](https://msdn.microsoft.com/library/fb63564c-c1b9-4655-a094-a235625882ce(v=vs.100))</span></span>
