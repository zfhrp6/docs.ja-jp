---
title: '方法 : グローバル アセンブリ キャッシュからアセンブリを削除する'
ms.date: 03/30/2017
helpviewer_keywords:
- assemblies [.NET Framework], global assembly cache
- Gacutil.exe
- global assembly cache, removing assemblies
- strong-named assemblies, global assembly cache
- removing assemblies from global assembly cache
- deleting assemblies in global assembly cache
- Global Assembly Cache tool
- GAC (global assembly cache), removing assemblies
ms.assetid: acdcc588-b458-436d-876c-726de68244c1
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6c5f47f4c33f725377281146bef0a37dbd3f774c
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="how-to-remove-an-assembly-from-the-global-assembly-cache"></a><span data-ttu-id="05f3c-102">方法 : グローバル アセンブリ キャッシュからアセンブリを削除する</span><span class="sxs-lookup"><span data-stu-id="05f3c-102">How to: Remove an Assembly from the Global Assembly Cache</span></span>
<span data-ttu-id="05f3c-103">グローバル アセンブリ キャッシュ (GAC) からアセンブリを削除するには、次の 2 つの方法があります。</span><span class="sxs-lookup"><span data-stu-id="05f3c-103">There are two ways to remove an assembly from the global assembly cache (GAC):</span></span>  
  
-   <span data-ttu-id="05f3c-104">[グローバル アセンブリ キャッシュ ツール (Gacutil.exe)](../../../docs/framework/tools/gacutil-exe-gac-tool.md) を使用する方法。</span><span class="sxs-lookup"><span data-stu-id="05f3c-104">By using the [Global Assembly Cache tool (Gacutil.exe)](../../../docs/framework/tools/gacutil-exe-gac-tool.md).</span></span> <span data-ttu-id="05f3c-105">このオプションを使用すると、開発およびテスト時に GAC に配置したアセンブリをアンインストールできます。</span><span class="sxs-lookup"><span data-stu-id="05f3c-105">You can use this option to uninstall assemblies that you've placed in the GAC during development and testing.</span></span>  
  
-   <span data-ttu-id="05f3c-106">[Windows インストーラー](http://msdn.microsoft.com/library/windows/desktop/cc185688.aspx)を使用する方法。</span><span class="sxs-lookup"><span data-stu-id="05f3c-106">By using [Windows Installer](http://msdn.microsoft.com/library/windows/desktop/cc185688.aspx).</span></span> <span data-ttu-id="05f3c-107">インストール パッケージをテストするとき、そして実稼働システムのために、アセンブリをアンインストールするにはこのオプションを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="05f3c-107">You should use this option to uninstall assemblies when testing installation packages and for production systems.</span></span>  
  
### <a name="removing-an-assembly-with-gacutilexe"></a><span data-ttu-id="05f3c-108">Gacutil.exe によるアセンブリの削除</span><span class="sxs-lookup"><span data-stu-id="05f3c-108">Removing an assembly with Gacutil.exe</span></span>  
  
1.  <span data-ttu-id="05f3c-109">コマンド プロンプトに次のコマンドを入力します。</span><span class="sxs-lookup"><span data-stu-id="05f3c-109">At the command prompt, type the following command:</span></span>  
  
     <span data-ttu-id="05f3c-110">**gacutil –u** \<*assembly name*></span><span class="sxs-lookup"><span data-stu-id="05f3c-110">**gacutil –u** \<*assembly name*></span></span>  
  
     <span data-ttu-id="05f3c-111">このコマンドで、*assembly name* はグローバル アセンブリ キャッシュから削除するアセンブリの名前です。</span><span class="sxs-lookup"><span data-stu-id="05f3c-111">In this command, *assembly name* is the name of the assembly to remove from the global assembly cache.</span></span>  
  
    > [!WARNING]
    >  <span data-ttu-id="05f3c-112">アセンブリが一部のアプリケーションで引き続き必要となる可能性があるので、Gacutil.exe を使用して実稼働システムのアセンブリを削除しないでください。</span><span class="sxs-lookup"><span data-stu-id="05f3c-112">You should not use Gacutil.exe to remove assemblies on production systems because of the possibility that the assembly may still be required by some application.</span></span> <span data-ttu-id="05f3c-113">代わりに、GAC にインストールされる各アセンブリの参照カウントを保持する Windows インストーラーを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="05f3c-113">Instead, you should use the Windows Installer, which maintains a reference count for each assembly it installs in the GAC.</span></span>  
  
 <span data-ttu-id="05f3c-114">次の例では、`hello.dll` という名前のアセンブリが、グローバル アセンブリ キャッシュから削除されます。</span><span class="sxs-lookup"><span data-stu-id="05f3c-114">The following example removes an assembly named `hello.dll` from the global assembly cache.</span></span>  
  
```  
gacutil -u hello  
```  
  
### <a name="removing-an-assembly-with-windows-installer"></a><span data-ttu-id="05f3c-115">Windows インストーラーでアセンブリを削除する</span><span class="sxs-lookup"><span data-stu-id="05f3c-115">Removing an assembly with Windows Installer</span></span>  
  
1.  <span data-ttu-id="05f3c-116">**コントロール パネル**の**プログラムと機能**アプリで、アンインストールするアプリを選択します。</span><span class="sxs-lookup"><span data-stu-id="05f3c-116">From the **Programs and Features** app in **Control Panel**, select the app that you want to uninstall.</span></span> <span data-ttu-id="05f3c-117">インストール パッケージが GAC にアセンブリを配置した場合、それらが別のアプリケーションによって使用されないときは、Windows インストーラーはそれらを削除します。</span><span class="sxs-lookup"><span data-stu-id="05f3c-117">If the installation package placed assemblies in the GAC, Windows Installer will remove them if they are not used by another application.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="05f3c-118">Windows インストーラーは、GAC にインストールされたアセンブリの参照カウントを保持します。</span><span class="sxs-lookup"><span data-stu-id="05f3c-118">Windows Installer maintains a reference count for assemblies installed in the GAC.</span></span> <span data-ttu-id="05f3c-119">アセンブリの参照カウントがゼロになる場合 (それが Windows インストーラー パッケージによってインストールされたアプリケーションによって使用されないことを示す) にのみ、アセンブリが GAC から削除されます。</span><span class="sxs-lookup"><span data-stu-id="05f3c-119">An assembly is removed from the GAC only when its reference count reaches zero, which indicates that it is not used by any application installed by a Windows Installer package.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05f3c-120">参照</span><span class="sxs-lookup"><span data-stu-id="05f3c-120">See Also</span></span>  
 [<span data-ttu-id="05f3c-121">アセンブリとグローバル アセンブリ キャッシュの使用</span><span class="sxs-lookup"><span data-stu-id="05f3c-121">Working with Assemblies and the Global Assembly Cache</span></span>](../../../docs/framework/app-domains/working-with-assemblies-and-the-gac.md)  
 [<span data-ttu-id="05f3c-122">方法: グローバル アセンブリ キャッシュにアセンブリをインストールする</span><span class="sxs-lookup"><span data-stu-id="05f3c-122">How to: Install an Assembly into the Global Assembly Cache</span></span>](../../../docs/framework/app-domains/how-to-install-an-assembly-into-the-gac.md)  
 [<span data-ttu-id="05f3c-123">Gacutil.exe (グローバル アセンブリ キャッシュ ツール)</span><span class="sxs-lookup"><span data-stu-id="05f3c-123">Gacutil.exe (Global Assembly Cache Tool)</span></span>](../../../docs/framework/tools/gacutil-exe-gac-tool.md)
