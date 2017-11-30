---
title: "方法: どの .NET Framework のセキュリティ更新プログラムと修正プログラムがインストールされている確認"
description: "どの .NET Framework のセキュリティ更新プログラムと修正プログラムがコンピューターにインストールされているを確認する方法を説明します。"
ms.date: 11/21/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- updates, determining for .NET Framework
- .NET Framework, determining updates
ms.assetid: 53c7b5f7-d47a-402a-b194-7244a696a88b
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: c35705470a8e1b553eca2ca0c68d3b8b9b3f6fa6
ms.sourcegitcommit: a3ba258f7a8cab5c6d19a3743dd95e904ecebc44
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/27/2017
---
# <a name="how-to-determine-which-net-framework-security-updates-and-hotfixes-are-installed"></a><span data-ttu-id="d6e6a-103">方法: どの .NET Framework のセキュリティ更新プログラムと修正プログラムがインストールされている確認</span><span class="sxs-lookup"><span data-stu-id="d6e6a-103">How to: Determine which .NET Framework security updates and hotfixes are installed</span></span>

<span data-ttu-id="d6e6a-104">ここで説明する .NET Framework のセキュリティ更新プログラムを確認する方法と修正プログラムがコンピューターにインストールされています。</span><span class="sxs-lookup"><span data-stu-id="d6e6a-104">This article shows you how to find out which .NET Framework security updates and hotfixes are installed on a computer.</span></span>

> [!NOTE]
> <span data-ttu-id="d6e6a-105">この記事で示したすべての手法では、管理者特権を持つアカウントが必要です。</span><span class="sxs-lookup"><span data-stu-id="d6e6a-105">All the techniques shown in this article require an account with administrative privileges.</span></span>

## <a name="to-find-installed-updates-using-the-registry"></a><span data-ttu-id="d6e6a-106">インストールされたレジストリを使用して更新プログラムを検索するには</span><span class="sxs-lookup"><span data-stu-id="d6e6a-106">To find installed updates using the registry</span></span>

<span data-ttu-id="d6e6a-107">インストールされているセキュリティ更新プログラムと修正プログラムをコンピューターにインストールされている .NET Framework のバージョンごとには、Windows レジストリに一覧表示されます。</span><span class="sxs-lookup"><span data-stu-id="d6e6a-107">The installed security updates and hotfixes for each version of the .NET Framework installed on a computer are listed in the Windows registry.</span></span> <span data-ttu-id="d6e6a-108">レジストリ エディターを使用することができます (*regedit.exe*) プログラムをこの情報を表示します。</span><span class="sxs-lookup"><span data-stu-id="d6e6a-108">You can use the Registry Editor (*regedit.exe*) program to view this information.</span></span>

1. <span data-ttu-id="d6e6a-109">プログラム **regedit.exe** を開きます。</span><span class="sxs-lookup"><span data-stu-id="d6e6a-109">Open the program **regedit.exe**.</span></span> <span data-ttu-id="d6e6a-110">Windows 8 およびそれ以降のバージョンを右クリックして**開始** ![Windows ロゴ](../get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo")選択してから、**実行**です。</span><span class="sxs-lookup"><span data-stu-id="d6e6a-110">In Windows 8 and later versions, right-click **Start** ![Windows logo](../get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo"), then select **Run**.</span></span> <span data-ttu-id="d6e6a-111">**開く**ボックスに、入力**regedit**選択**[ok]**です。</span><span class="sxs-lookup"><span data-stu-id="d6e6a-111">In the **Open** box, enter **regedit** and select **OK**.</span></span>

2. <span data-ttu-id="d6e6a-112">レジストリ エディターで、次のサブキーを開きます。</span><span class="sxs-lookup"><span data-stu-id="d6e6a-112">In the Registry Editor, open the following subkey:</span></span>

     `HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Updates`

     <span data-ttu-id="d6e6a-113">インストールされている更新プログラムは、適用された .NET Framework バージョンを識別するサブキーの下に一覧表示されています。</span><span class="sxs-lookup"><span data-stu-id="d6e6a-113">The installed updates are listed under subkeys that identify the .NET Framework version they apply to.</span></span> <span data-ttu-id="d6e6a-114">各更新プログラムは、サポート技術情報の (KB) 番号で識別されます。</span><span class="sxs-lookup"><span data-stu-id="d6e6a-114">Each update is identified by a Knowledge Base (KB) number.</span></span>

<span data-ttu-id="d6e6a-115">レジストリ エディターでは、各バージョンの .NET Framework バージョンとインストールされている更新プログラムが別々のサブキーに格納されます。</span><span class="sxs-lookup"><span data-stu-id="d6e6a-115">In the Registry Editor, the .NET Framework versions and installed updates for each version are stored in different subkeys.</span></span> <span data-ttu-id="d6e6a-116">インストールされているバージョン番号を検出する方法については、次を参照してください。[する方法: .NET Framework バージョンがインストールされている確認](../../../docs/framework/migration-guide/how-to-determine-which-versions-are-installed.md)です。</span><span class="sxs-lookup"><span data-stu-id="d6e6a-116">For information about detecting the installed version numbers, see [How to: Determine which .NET Framework versions are installed](../../../docs/framework/migration-guide/how-to-determine-which-versions-are-installed.md).</span></span>

## <a name="to-find-installed-updates-by-querying-the-registry-in-code"></a><span data-ttu-id="d6e6a-117">コードでレジストリを照会することによってインストールされた更新プログラムを検索するには</span><span class="sxs-lookup"><span data-stu-id="d6e6a-117">To find installed updates by querying the registry in code</span></span>

<span data-ttu-id="d6e6a-118">次の例は、プログラムによって、.NET Framework のセキュリティ更新プログラムと、コンピューターにインストールされている修正プログラムを決定します。</span><span class="sxs-lookup"><span data-stu-id="d6e6a-118">The following example programmatically determines the .NET Framework security updates and hotfixes that are installed on a computer:</span></span>

[!code-csharp[ListUpdates](../../../samples/snippets/csharp/VS_Snippets_CLR/listupdates/cs/program.cs)]
[!code-vb[ListUpdates](../../../samples/snippets/visualbasic/VS_Snippets_CLR/listupdates/vb/program.vb)]

<span data-ttu-id="d6e6a-119">この例には、次のいずれかのような出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="d6e6a-119">The example produces an output that's similar to the following one:</span></span>

```console
Microsoft .NET Framework 4 Client Profile
  KB2468871
  KB2468871v2
  KB2478063
  KB2533523
  KB2544514
  KB2600211
  KB2600217
Microsoft .NET Framework 4 Extended
  KB2468871
  KB2468871v2
  KB2478063
  KB2533523
  KB2544514
  KB2600211
  KB2600217
```

## <a name="to-find-installed-updates-by-querying-the-registry-in-powershell"></a><span data-ttu-id="d6e6a-120">PowerShell でレジストリを照会してインストールされた更新プログラムを検索するには</span><span class="sxs-lookup"><span data-stu-id="d6e6a-120">To find installed updates by querying the registry in PowerShell</span></span>

<span data-ttu-id="d6e6a-121">次の例では、.NET Framework のセキュリティ更新プログラムと PowerShell を使用してコンピューターにインストールされている修正プログラムを確認する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="d6e6a-121">The following example shows how to determine the .NET Framework security updates and hotfixes that are installed on a computer using PowerShell:</span></span>

```powershell
 Get-ChildItem "HKLM:SOFTWARE\Wow6432Node\Microsoft\Updates\*" -Recurse | Where-Object {$_.name -like
 "*.NET Framework*"}
```

<span data-ttu-id="d6e6a-122">この例には、次のいずれかのような出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="d6e6a-122">The example produces an output that's similar to the following one:</span></span>

```console
    Hive: HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Updates\Microsoft .NET Framework 4 Client Profile


Name                           Property
----                           --------
KB2468871                      ThisVersionInstalled : Y
KB2468871v2                    ThisVersionInstalled : Y
KB2478063                      ThisVersionInstalled : Y
KB2533523                      ThisVersionInstalled : Y
KB2544514                      ThisVersionInstalled : Y
KB2600211                      ThisVersionInstalled : Y
KB2600217                      ThisVersionInstalled : Y


    Hive: HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Updates\Microsoft .NET Framework 4 Extended


Name                           Property
----                           --------
KB2468871                      ThisVersionInstalled : Y
KB2468871v2                    ThisVersionInstalled : Y
KB2478063                      ThisVersionInstalled : Y
KB2533523                      ThisVersionInstalled : Y
KB2544514                      ThisVersionInstalled : Y
KB2600211                      ThisVersionInstalled : Y
KB2600217                      ThisVersionInstalled : Y
```

## <a name="see-also"></a><span data-ttu-id="d6e6a-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="d6e6a-123">See also</span></span>

[<span data-ttu-id="d6e6a-124">方法: .NET Framework バージョンがインストールされている確認</span><span class="sxs-lookup"><span data-stu-id="d6e6a-124">How to: Determine which .NET Framework versions are installed</span></span>](../../../docs/framework/migration-guide/how-to-determine-which-versions-are-installed.md)  
[<span data-ttu-id="d6e6a-125">開発者にとっての .NET Framework をインストールします。</span><span class="sxs-lookup"><span data-stu-id="d6e6a-125">Install the .NET Framework for developers</span></span>](../../../docs/framework/install/guide-for-developers.md)  
[<span data-ttu-id="d6e6a-126">バージョンおよび依存関係</span><span class="sxs-lookup"><span data-stu-id="d6e6a-126">Versions and dependencies</span></span>](../../../docs/framework/migration-guide/versions-and-dependencies.md)
