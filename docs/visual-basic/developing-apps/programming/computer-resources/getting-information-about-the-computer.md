---
title: "方法: コンピューターについての情報の取得 (Visual Basic)"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- My.Computer.Info object, tasks
ms.assetid: 13c145bc-5c85-4fea-a5dd-2ca8681a0252
caps.latest.revision: 16
author: dotnet-bot
ms.author: dotnetcontent
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
ms.openlocfilehash: 8dee43f87a7a09f9b5cd77d5df5c2d0d8c6d4062
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="getting-information-about-the-computer-visual-basic"></a><span data-ttu-id="c4af4-102">方法: コンピューターについての情報の取得 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c4af4-102">Getting Information about the Computer (Visual Basic)</span></span>
<span data-ttu-id="c4af4-103">`My.Computer.Info` オブジェクトは、コンピューターのメモリ、読み込まれたアセンブリ名、オペレーティング システムに関する情報を取得するためのプロパティを提供します。</span><span class="sxs-lookup"><span data-stu-id="c4af4-103">The `My.Computer.Info` object provides properties for getting information about the computer's memory, loaded assemblies, name, and operating system.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c4af4-104">コメント</span><span class="sxs-lookup"><span data-stu-id="c4af4-104">Remarks</span></span>  
 <span data-ttu-id="c4af4-105">この表は `My.Computer.Info` オブジェクトでよく処理されるタスクを一覧にしたものであり、各タスクの実行方法を実演するトピックにここからアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="c4af4-105">This table lists tasks commonly accomplished through the `My.Computer.Info` object and points to topics demonstrating how to perform each.</span></span>  
  
|<span data-ttu-id="c4af4-106">目的</span><span class="sxs-lookup"><span data-stu-id="c4af4-106">To</span></span>|<span data-ttu-id="c4af4-107">参照トピック</span><span class="sxs-lookup"><span data-stu-id="c4af4-107">See</span></span>|  
|---|---|   
|<span data-ttu-id="c4af4-108">アプリケーションがインストールされているコンピューターで使用できる仮想アドレス領域の量を確認する</span><span class="sxs-lookup"><span data-stu-id="c4af4-108">Determine how much virtual address space is available for the computer on which the application is installed</span></span>|<xref:Microsoft.VisualBasic.Devices.ComputerInfo.TotalVirtualMemory%2A>|  
|<span data-ttu-id="c4af4-109">アプリケーションを実行しているコンピューターのプラットフォームの種類を確認する</span><span class="sxs-lookup"><span data-stu-id="c4af4-109">Determine the platform type of the computer on which the application is running</span></span>|<xref:Microsoft.VisualBasic.Devices.ComputerInfo.OSPlatform%2A>|  
|<span data-ttu-id="c4af4-110">アプリケーションを実行しているコンピューターのオペレーティング システムの種類を確認する</span><span class="sxs-lookup"><span data-stu-id="c4af4-110">Determine the operating system of the computer on which the application is running</span></span>|<xref:Microsoft.VisualBasic.Devices.ComputerInfo.OSFullName%2A>|  
|<span data-ttu-id="c4af4-111">アプリケーションを実行しているコンピューターにインストールされているサービス パックを確認する</span><span class="sxs-lookup"><span data-stu-id="c4af4-111">Determine what service packs have been installed on the computer on which the application is running</span></span>|<xref:Microsoft.VisualBasic.Devices.ComputerInfo.OSVersion%2A>|  
|<span data-ttu-id="c4af4-112">アプリケーションを実行しているコンピューターにインストールされている `UICulture` を確認する</span><span class="sxs-lookup"><span data-stu-id="c4af4-112">Determine the installed `UICulture` on the computer on which the application is running.</span></span>|<xref:Microsoft.VisualBasic.Devices.ComputerInfo.InstalledUICulture%2A>|  
  
## <a name="see-also"></a><span data-ttu-id="c4af4-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="c4af4-113">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Devices.ServerComputer.Info%2A>

