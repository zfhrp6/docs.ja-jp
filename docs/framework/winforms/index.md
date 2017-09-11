---
title: "Windows フォーム | Microsoft ドキュメント"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- jsharp
helpviewer_keywords:
- Windows Forms
- user interface
- user interface, forms
ms.assetid: 627df1e9-b254-41af-bbac-9a4f02810c54
caps.latest.revision: 25
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.translationtype: Human Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 0b682d47c2f5d8f1011f2d026ccd6bdf5a7f4fa2
ms.contentlocale: ja-jp
ms.lasthandoff: 05/02/2017

---
# <a name="windows-forms"></a><span data-ttu-id="71583-102">Windows フォーム</span><span class="sxs-lookup"><span data-stu-id="71583-102">Windows Forms</span></span>
<span data-ttu-id="71583-103">フォームはアプリケーションの基本単位であるため、機能とデザインにある程度の配慮を与えることが重要です。</span><span class="sxs-lookup"><span data-stu-id="71583-103">As forms are the base unit of your application, it is essential that you give some thought to their function and design.</span></span> <span data-ttu-id="71583-104">フォームは、最終的には開発者がユーザー インターフェイスを作成するコントロールとデータを操作するコードを拡張する白紙状態です。</span><span class="sxs-lookup"><span data-stu-id="71583-104">A form is ultimately a blank slate that you, as a developer, enhance with controls to create a user interface and with code to manipulate data.</span></span> <span data-ttu-id="71583-105">そのために、[!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] はコード作成を支援する統合開発環境 (IDE) や、[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] を使用して作成された豊富なコントロール セットを提供します。</span><span class="sxs-lookup"><span data-stu-id="71583-105">To that end, [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] provides you with an integrated development environment (IDE) to aid in writing code, as well as a rich control set written with the [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)].</span></span> <span data-ttu-id="71583-106">これらのコントロールの機能をコードに補完することにより、必要なソリューションを簡単に素早く開発できます。</span><span class="sxs-lookup"><span data-stu-id="71583-106">By complementing the functionality of these controls with your code, you can easily and quickly develop the solutions you need.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="71583-107">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="71583-107">In This Section</span></span>  
 [<span data-ttu-id="71583-108">Windows フォームについて</span><span class="sxs-lookup"><span data-stu-id="71583-108">Getting Started with Windows Forms</span></span>](../../../docs/framework/winforms/getting-started-with-windows-forms.md)  
 <span data-ttu-id="71583-109">データの表示、ユーザー入力の処理、アプリケーションの簡単で堅牢なセキュリティを使用した配置のために、Windows フォームの機能を利用する方法に関するトピックへのリンクを提供します。</span><span class="sxs-lookup"><span data-stu-id="71583-109">Provides links to topics about how to harness the power of Windows Forms to display data, handle user input, and deploy your applications easily and with more robust security.</span></span>  
  
 [<span data-ttu-id="71583-110">Windows フォーム アプリケーションの拡張</span><span class="sxs-lookup"><span data-stu-id="71583-110">Enhancing Windows Forms Applications</span></span>](../../../docs/framework/winforms/advanced/index.md)  
 <span data-ttu-id="71583-111">Windows フォームでのさまざまな機能を拡張する方法に関するトピックへのリンクを提供します。</span><span class="sxs-lookup"><span data-stu-id="71583-111">Provides links to topics about how to enhance your Windows Forms with a variety of features.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="71583-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="71583-112">Related Sections</span></span>  
 [<span data-ttu-id="71583-113">Windows フォーム コントロール</span><span class="sxs-lookup"><span data-stu-id="71583-113">Windows Forms Controls</span></span>](../../../docs/framework/winforms/controls/index.md)  
 <span data-ttu-id="71583-114">Windows フォーム コントロールの説明および、その実装方法について説明するトピックへのリンクが含まれます。</span><span class="sxs-lookup"><span data-stu-id="71583-114">Contains links to topics that describe Windows Forms controls and show how to implement them.</span></span>  
  
 [<span data-ttu-id="71583-115">Windows フォームでのデータ バインディング</span><span class="sxs-lookup"><span data-stu-id="71583-115">Windows Forms Data Binding</span></span>](../../../docs/framework/winforms/windows-forms-data-binding.md)  
 <span data-ttu-id="71583-116">Windows フォームのデータ バインディング アーキテクチャについて説明するトピックへのリンクが含まれます。</span><span class="sxs-lookup"><span data-stu-id="71583-116">Contains links to topics that describe the Windows Forms data-binding architecture.</span></span>  
  
 [<span data-ttu-id="71583-117">グラフィックスの概要</span><span class="sxs-lookup"><span data-stu-id="71583-117">Graphics Overview</span></span>](../../../docs/framework/winforms/advanced/graphics-overview-windows-forms.md)  
 <span data-ttu-id="71583-118">Windows のグラフィック デザイン インターフェイスの高度な実装を使用して、オブジェクトとして、グラフィックスを作成、テキストを描画、および、画像を操作する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="71583-118">Discusses how to create graphics, draw text, and manipulate graphical images as objects using the advanced implementation of the Windows graphics design interface.</span></span>  
  
 [<span data-ttu-id="71583-119">ClickOnce のセキュリティと配置</span><span class="sxs-lookup"><span data-stu-id="71583-119">ClickOnce Security and Deployment</span></span>](http://msdn.microsoft.com/library/abab6d34-c3c2-45c1-a8b6-43c7d3131e7a)  
 <span data-ttu-id="71583-120">ClickOnce 配置の基本原則について説明します。</span><span class="sxs-lookup"><span data-stu-id="71583-120">Discusses the principles of ClickOnce deployment.</span></span>  
  
 [<span data-ttu-id="71583-121">Windows フォームと MFC のプログラミング上の違い</span><span class="sxs-lookup"><span data-stu-id="71583-121">Windows Forms/MFC Programming Differences</span></span>](http://msdn.microsoft.com/library/f3bfcf45-cfd4-45a4-8cde-5f4dbb18ee51)  
 <span data-ttu-id="71583-122">MFC アプリケーションと Windows フォームの違いについて説明します。</span><span class="sxs-lookup"><span data-stu-id="71583-122">Discusses the differences between MFC applications and Windows Forms.</span></span>  
  
 [<span data-ttu-id="71583-123">Visual Studio でのデータへのアクセス</span><span class="sxs-lookup"><span data-stu-id="71583-123">Accessing data in Visual Studio</span></span>](http://msdn.microsoft.com/library/9812a6d5-23d2-4427-8b98-70a2abfec3bc)  
 <span data-ttu-id="71583-124">アプリケーションにデータ アクセス機能を取り込む方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="71583-124">Discusses incorporating data access functionality into your applications.</span></span>  
  
 [<span data-ttu-id="71583-125">Windows フォーム アプリケーション</span><span class="sxs-lookup"><span data-stu-id="71583-125">Windows Forms Applications</span></span>](http://msdn.microsoft.com/library/7092ee7f-8378-4def-aef8-1695bd97cf14)  
 <span data-ttu-id="71583-126">Windows アプリケーション プロジェクト テンプレートを使用して作成されたアプリケーションのデバッグのプロセス、およびデバッグ構成とリリース構成を変更する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="71583-126">Discusses the process of debugging applications created with the Windows Application project template, as well as how to change the Debug and Release configurations.</span></span>  
  
 [<span data-ttu-id="71583-127">アプリケーション、サービス、およびコンポーネントの配置</span><span class="sxs-lookup"><span data-stu-id="71583-127">Deploying Applications, Services, and Components</span></span>](https://msdn.microsoft.com/library/wtzawcsz)  
 <span data-ttu-id="71583-128">完成したアプリケーションやコンポーネントを他のコンピューターにインストールできるように配布するためのプロセスについて説明します。</span><span class="sxs-lookup"><span data-stu-id="71583-128">Describes the process by which you distribute a finished application or component to be installed on other computers.</span></span>  
  
 [<span data-ttu-id="71583-129">コンソール アプリケーションの構築</span><span class="sxs-lookup"><span data-stu-id="71583-129">Building Console Applications</span></span>](../../../docs/standard/building-console-apps.md)  
 <span data-ttu-id="71583-130"><xref:System.Console> クラスを使用したコンソール アプリケーションの作成の基本について説明します。</span><span class="sxs-lookup"><span data-stu-id="71583-130">Describes the basics of creating a console application using the <xref:System.Console> class.</span></span>
