---
title: "方法 : インストールされている .NET Framework の更新プログラムを確認する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- updates, determining for .NET Framework
- .NET Framework, determining updates
ms.assetid: 53c7b5f7-d47a-402a-b194-7244a696a88b
caps.latest.revision: "6"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: ba734dd3a9585b52b96cb2d27743da6190961126
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-determine-which-net-framework-updates-are-installed"></a><span data-ttu-id="8e3d8-102">方法 : インストールされている .NET Framework の更新プログラムを確認する</span><span class="sxs-lookup"><span data-stu-id="8e3d8-102">How to: Determine Which .NET Framework Updates Are Installed</span></span>
<span data-ttu-id="8e3d8-103">コンピューターにインストールされている .NET Framework のバージョンごとのインストール済みの更新プログラムは、Windows レジストリに一覧表示されます。</span><span class="sxs-lookup"><span data-stu-id="8e3d8-103">The installed updates for each version of the .NET Framework installed on a computer are listed in the Windows registry.</span></span> <span data-ttu-id="8e3d8-104">レジストリ エディター (regedit.exe) を使用して、この情報を表示することができます。</span><span class="sxs-lookup"><span data-stu-id="8e3d8-104">You can use the Registry Editor (regedit.exe) to view this information.</span></span>  
  
 <span data-ttu-id="8e3d8-105">レジストリ エディターでは、各バージョンの .NET Framework バージョンとインストールされている更新プログラムが別々のサブキーに格納されます。</span><span class="sxs-lookup"><span data-stu-id="8e3d8-105">In the Registry Editor, the .NET Framework versions and installed updates for each version are stored in different subkeys.</span></span> <span data-ttu-id="8e3d8-106">インストールされているバージョン番号を検出する方法については、「[方法: インストールされている .NET Framework バージョンを確認する](../../../docs/framework/migration-guide/how-to-determine-which-versions-are-installed.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8e3d8-106">For information about detecting the installed version numbers, see [How to: Determine Which .NET Framework Versions Are Installed](../../../docs/framework/migration-guide/how-to-determine-which-versions-are-installed.md).</span></span> <span data-ttu-id="8e3d8-107">.NET Framework のインストールの詳細については、「[開発者向けの .NET Framework のインストール](../../../docs/framework/install/guide-for-developers.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8e3d8-107">For information about installing the .NET Framework, see [Install the .NET Framework for developers](../../../docs/framework/install/guide-for-developers.md).</span></span>  
  
### <a name="to-find-installed-updates"></a><span data-ttu-id="8e3d8-108">インストールされている更新プログラムを確認するには</span><span class="sxs-lookup"><span data-stu-id="8e3d8-108">To find installed updates</span></span>  
  
1.  <span data-ttu-id="8e3d8-109">プログラム **regedit.exe** を開きます。</span><span class="sxs-lookup"><span data-stu-id="8e3d8-109">Open the program **regedit.exe**.</span></span> <span data-ttu-id="8e3d8-110">Windows 8 以降の場合、スタート画面を開き、名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="8e3d8-110">In Windows 8 and higher open the Start screen and type the name.</span></span> <span data-ttu-id="8e3d8-111">それより前のバージョンの Windows では、**[スタート]** メニューの **[ファイル名を指定して実行]** を選択し、**[開く]** ボックスに **regedit.exe** と入力します。</span><span class="sxs-lookup"><span data-stu-id="8e3d8-111">In earlier versions of Windows, on the **Start** menu, choose **Run** and then, in the **Open** box, enter **regedit.exe**.</span></span>  
  
     <span data-ttu-id="8e3d8-112">regedit.exe を実行するには、管理特権が必要です。</span><span class="sxs-lookup"><span data-stu-id="8e3d8-112">You must have administrative credentials to run regedit.exe.</span></span>  
  
2.  <span data-ttu-id="8e3d8-113">レジストリ エディターで、次のサブキーを開きます。</span><span class="sxs-lookup"><span data-stu-id="8e3d8-113">In the Registry Editor, open the following subkey:</span></span>  
  
     <span data-ttu-id="8e3d8-114">HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Updates</span><span class="sxs-lookup"><span data-stu-id="8e3d8-114">HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Updates</span></span>  
  
     <span data-ttu-id="8e3d8-115">インストールされている更新プログラムは、適用された .NET Framework バージョンを識別するサブキーの下に一覧表示されています。</span><span class="sxs-lookup"><span data-stu-id="8e3d8-115">The installed updates are listed under subkeys that identify the .NET Framework version they apply to.</span></span> <span data-ttu-id="8e3d8-116">各更新プログラムは、サポート技術情報の (KB) 番号で識別されます。</span><span class="sxs-lookup"><span data-stu-id="8e3d8-116">Each update is identified by a Knowledge Base (KB) number.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8e3d8-117">例</span><span class="sxs-lookup"><span data-stu-id="8e3d8-117">Example</span></span>  
 <span data-ttu-id="8e3d8-118">次のコードは、プログラミングによってコンピューターにインストールされている .NET Framework の更新プログラムを判断します。</span><span class="sxs-lookup"><span data-stu-id="8e3d8-118">The following code programmatically determines the .NET Framework updates that are installed on a computer.</span></span> <span data-ttu-id="8e3d8-119">この例を実行するには、管理特権が必要です。</span><span class="sxs-lookup"><span data-stu-id="8e3d8-119">You must have administrative credentials to run this example.</span></span>  
  
 [!code-csharp[ListUpdates#1](../../../samples/snippets/csharp/VS_Snippets_CLR/listupdates/cs/program.cs#1)]
 [!code-vb[ListUpdates#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/listupdates/vb/program.vb#1)]  
  
 <span data-ttu-id="8e3d8-120">この例では次のような出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="8e3d8-120">The example produces output that's similar to the following:</span></span>  
  
```  
Microsoft .NET Framework 3.5 SP1  
  KB953595  Hotfix for Microsoft .NET Framework 3.5 SP1 (KB953595)  
  SP1  
    KB2657424  Security Update for Microsoft .NET Framework 3.5 SP1 (KB2657424)  
    KB958484  Hotfix for Microsoft .NET Framework 3.5 SP1 (KB958484)  
    KB963707  Update for Microsoft .NET Framework 3.5 SP1 (KB963707)  
Microsoft .NET Framework 4 Client Profile  
  KB2160841  Security Update for Microsoft .NET Framework 4 Client Profile (KB2160841)  
  KB2446708  Security Update for Microsoft .NET Framework 4 Client Profile (KB2446708)  
  KB2468871  Update for Microsoft .NET Framework 4 Client Profile (KB2468871)  
  KB2478663  Security Update for Microsoft .NET Framework 4 Client Profile (KB2478663)  
  KB2518870  Security Update for Microsoft .NET Framework 4 Client Profile (KB2518870)  
  KB2533523  Update for Microsoft .NET Framework 4 Client Profile (KB2533523)  
  KB2539636  Security Update for Microsoft .NET Framework 4 Client Profile (KB2539636)  
  KB2572078  Security Update for Microsoft .NET Framework 4 Client Profile (KB2572078)  
  KB2633870  Security Update for Microsoft .NET Framework 4 Client Profile (KB2633870)  
  KB2656351  Security Update for Microsoft .NET Framework 4 Client Profile (KB2656351)  
Microsoft .NET Framework 4 Extended  
  KB2416472  Security Update for Microsoft .NET Framework 4 Extended (KB2416472)  
  KB2468871  Update for Microsoft .NET Framework 4 Extended (KB2468871)  
  KB2487367  Security Update for Microsoft .NET Framework 4 Extended (KB2487367)  
  KB2533523  Update for Microsoft .NET Framework 4 Extended (KB2533523)  
  KB2656351  Security Update for Microsoft .NET Framework 4 Extended (KB2656351)  
```  
  
## <a name="see-also"></a><span data-ttu-id="8e3d8-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="8e3d8-121">See also</span></span>

<span data-ttu-id="8e3d8-122">[方法 : インストールされている .NET Framework バージョンを確認する](../../../docs/framework/migration-guide/how-to-determine-which-versions-are-installed.md) </span><span class="sxs-lookup"><span data-stu-id="8e3d8-122">[How to: Determine Which .NET Framework Versions Are Installed](../../../docs/framework/migration-guide/how-to-determine-which-versions-are-installed.md) </span></span>  
<span data-ttu-id="8e3d8-123">[.NET Framework のインストール](../../../docs/framework/install/guide-for-developers.md) </span><span class="sxs-lookup"><span data-stu-id="8e3d8-123">[Installing the .NET Framework](../../../docs/framework/install/guide-for-developers.md) </span></span>  
[<span data-ttu-id="8e3d8-124">バージョンおよび依存関係</span><span class="sxs-lookup"><span data-stu-id="8e3d8-124">Versions and Dependencies</span></span>](../../../docs/framework/migration-guide/versions-and-dependencies.md)
