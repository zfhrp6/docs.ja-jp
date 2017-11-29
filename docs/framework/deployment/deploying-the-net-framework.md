---
title: ".NET Framework の配置"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- .NET Framework, deploying
- deployment [.NET Framework]
ms.assetid: 19df26c5-4008-461d-a7d7-18f4506312d2
caps.latest.revision: "2"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: b3a33b57ee7cf38e06195244023e8bb918dea02b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="deploying-the-net-framework"></a><span data-ttu-id="b4f1a-102">.NET Framework の配置</span><span class="sxs-lookup"><span data-stu-id="b4f1a-102">Deploying the .NET Framework</span></span>
<span data-ttu-id="b4f1a-103">.NET Framework ドキュメントのこのセクションでは、アプリケーションとともに .NET Framework をインストールする開発者、およびネットワーク上で .NET Framework を展開する管理者に対して情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="b4f1a-103">This section of the .NET Framework documentation provides information for developers who want to install the .NET Framework with their applications, and administrators who want to deploy the .NET Framework across a network.</span></span> <span data-ttu-id="b4f1a-104">また、アクティベーション、配置に伴う再起動の問題、.NET Framework のインストールの進捗を監視する方法についても説明します。</span><span class="sxs-lookup"><span data-stu-id="b4f1a-104">It also discusses activation and restart issues associated with deployment, and how to monitor the progress of your .NET Framework installation.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b4f1a-105">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="b4f1a-105">In This Section</span></span>  
 [<span data-ttu-id="b4f1a-106">配置ガイド (開発者向け)</span><span class="sxs-lookup"><span data-stu-id="b4f1a-106">Deployment Guide for Developers</span></span>](../../../docs/framework/deployment/deployment-guide-for-developers.md)  
 <span data-ttu-id="b4f1a-107">開発者による .NET Framework とアプリケーションのユーザーのコンピューターへのインストール方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="b4f1a-107">Explains how developers can install .NET Framework on their users' computers with their applications.</span></span>  
  
 [<span data-ttu-id="b4f1a-108">配置ガイド (管理者向け)</span><span class="sxs-lookup"><span data-stu-id="b4f1a-108">Deployment Guide for Administrators</span></span>](../../../docs/framework/deployment/guide-for-administrators.md)  
 <span data-ttu-id="b4f1a-109">System Center Configuration Manager (SCCM) を使用したシステム管理者による .NET Framework の配置方法と、ネットワーク全体でのシステムの依存関係について説明します。</span><span class="sxs-lookup"><span data-stu-id="b4f1a-109">Explains how a system administrator can deploy the .NET Framework and its system dependencies across a network by using System Center Configuration Manager (SCCM).</span></span>  
  
 [<span data-ttu-id="b4f1a-110">.NET Framework 4.5 のインストール中のシステム再起動の削減</span><span class="sxs-lookup"><span data-stu-id="b4f1a-110">Reducing System Restarts During .NET Framework 4.5 Installations</span></span>](../../../docs/framework/deployment/reducing-system-restarts.md)  
 <span data-ttu-id="b4f1a-111">再起動をできる限り回避する再起動マネージャーと、.NET Framework をインストールするアプリケーションがそれをどのように利用できるかを説明しています。</span><span class="sxs-lookup"><span data-stu-id="b4f1a-111">Describes the Restart Manager, which prevents reboots whenever possible, and explains how applications that install the .NET Framework can take advantage of it.</span></span>  
  
 [<span data-ttu-id="b4f1a-112">方法: .NET Framework 4.5 インストーラーの進行状況を表示する</span><span class="sxs-lookup"><span data-stu-id="b4f1a-112">How to: Get Progress from the .NET Framework 4.5 Installer</span></span>](../../../docs/framework/deployment/how-to-get-progress-from-the-dotnet-installer.md)  
 <span data-ttu-id="b4f1a-113">進行状況のビューを独自に表示する一方で、.NET Framework セットアップ プロセスをサイレントで起動および追跡する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="b4f1a-113">Describes how to silently launch and track the .NET Framework setup process while showing your own view of the setup progress.</span></span>  
  
 [<span data-ttu-id="b4f1a-114">.NET Framework 初期化エラー: ユーザー エクスペリエンスの管理</span><span class="sxs-lookup"><span data-stu-id="b4f1a-114">.NET Framework Initialization Errors: Managing the User Experience</span></span>](../../../docs/framework/deployment/initialization-errors-managing-the-user-experience.md)  
 <span data-ttu-id="b4f1a-115">ユーザーのコンピューターで無効な、またはインストールされていない CLR バージョンが .NET Framework アプリケーションで必要になると何が起きるか、そしてこのようなエラーの解決方法と、ユーザーに表示されるエラー メッセージの制御方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="b4f1a-115">Explains what happens when a .NET Framework application requires a CLR version that's invalid or not installed on the user's computer, how to resolve these errors, and how to control the error message displayed to the user.</span></span>  
  
 [<span data-ttu-id="b4f1a-116">方法: CLR のアクティブ化に関する問題をデバッグする</span><span class="sxs-lookup"><span data-stu-id="b4f1a-116">How to: Debug CLR Activation Issues</span></span>](../../../docs/framework/deployment/how-to-debug-clr-activation-issues.md)  
 <span data-ttu-id="b4f1a-117">正しいバージョンの CLR でアプリケーションを実行して発生した問題を解決するために、どのようにして CLR アクティベーション ログを表示し、デバッグするかを説明します。</span><span class="sxs-lookup"><span data-stu-id="b4f1a-117">Explains how you can view and debug CLR activation logs to resolve issues you may encounter in getting your application to run with the correct version of the CLR.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4f1a-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="b4f1a-118">See Also</span></span>  
 [<span data-ttu-id="b4f1a-119">開発ガイド</span><span class="sxs-lookup"><span data-stu-id="b4f1a-119">Development Guide</span></span>](../../../docs/framework/development-guide.md)
