---
title: "XNA アプリケーションでの操作と慣性の使用"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b7c18905-850c-4da4-8977-a074406a4263
caps.latest.revision: 7
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 7d623a8c2276811ae443a4d745faffeeb79ffc6f
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="using-manipulations-and-inertia-in-an-xna-application"></a><span data-ttu-id="281b0-102">XNA アプリケーションでの操作と慣性の使用</span><span class="sxs-lookup"><span data-stu-id="281b0-102">Using Manipulations and Inertia in an XNA Application</span></span>
<span data-ttu-id="281b0-103">この記事では、操作と慣性の処理を Microsoft XNA アプリケーションで使用して、ゲーム ピースの動きを制御する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="281b0-103">This article describes how you can use manipulations and inertia processing in a Microsoft XNA application to control the movement of game pieces.</span></span> <span data-ttu-id="281b0-104">この記事をお読みになる前に、「[操作と慣性の概要](../../../docs/framework/common-client-technologies/manipulations-and-inertia-overview.md)」トピックの内容、および基本的な XNA のプログラミングの概念についてよく理解してください。</span><span class="sxs-lookup"><span data-stu-id="281b0-104">Before you read this article, you should be familiar with the [Manipulations and Inertia Overview](../../../docs/framework/common-client-technologies/manipulations-and-inertia-overview.md) topic, and be familiar with basic XNA programming concepts.</span></span>  
  
 <span data-ttu-id="281b0-105">この記事で説明されているタスクを実行するには、XNA プロジェクトから <xref:System.Windows.Input.Manipulations> アセンブリを参照し、コンピューターに [XNA Game Studio](http://msdn.microsoft.com/library/bb200104.aspx) ([ダウンロード](http://www.microsoft.com/downloads/details.aspx?FamilyId=7D70D6ED-1EDD-4852-9883-9A33C0AD8FEE&displaylang=en)) をインストールして、プロジェクトから XNA アセンブリを参照できるようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="281b0-105">To perform the tasks described in this article, your XNA project must reference the <xref:System.Windows.Input.Manipulations> assembly, and you must have [XNA Game Studio](http://msdn.microsoft.com/library/bb200104.aspx) ([download](http://www.microsoft.com/downloads/details.aspx?FamilyId=7D70D6ED-1EDD-4852-9883-9A33C0AD8FEE&displaylang=en)) installed on your computer so that your project can reference the XNA assemblies.</span></span>  
  
## <a name="overview-of-functionality"></a><span data-ttu-id="281b0-106">機能の概要</span><span class="sxs-lookup"><span data-stu-id="281b0-106">Overview of Functionality</span></span>  
 <span data-ttu-id="281b0-107">この記事では、操作と慣性の処理を使用するゲーム ピースを表すカスタム クラスの作成方法を示します。</span><span class="sxs-lookup"><span data-stu-id="281b0-107">This article shows you how to create a custom class that represents a game piece that uses manipulation and inertia processing.</span></span> <span data-ttu-id="281b0-108">このクラスを使用すると、マウスでゲーム ピースをドラッグしてから放すことで、画面全体で操作できるようになります。</span><span class="sxs-lookup"><span data-stu-id="281b0-108">This class enables you to manipulate a game piece across the screen by dragging it with the mouse, and then releasing it.</span></span> <span data-ttu-id="281b0-109">ゲーム ピースを放すと、慣性の処理により、ゲーム ピースの移動速度が徐々に低下します。</span><span class="sxs-lookup"><span data-stu-id="281b0-109">Once released, inertia processing keeps the game piece moving as it gradually slows down.</span></span> <span data-ttu-id="281b0-110">直線運動と角運動の両方が行われます。</span><span class="sxs-lookup"><span data-stu-id="281b0-110">Movement is both linear and angular.</span></span>  
  
 <span data-ttu-id="281b0-111">![単純な操作と慣性のアプリケーション。](../../../docs/framework/common-client-technologies/media/ndp-gamexna.jpg "NDP_GameXna")</span><span class="sxs-lookup"><span data-stu-id="281b0-111">![A simple manipulations and inertia application.](../../../docs/framework/common-client-technologies/media/ndp-gamexna.jpg "NDP_GameXna")</span></span>  
  
 <span data-ttu-id="281b0-112">さらに、複数のゲーム ピースを管理するカスタム コレクションが作成されます。</span><span class="sxs-lookup"><span data-stu-id="281b0-112">In addition, a custom collection is created that manages multiple game pieces.</span></span> <span data-ttu-id="281b0-113">これにより、XNA Game クラスから必要とされる処理が簡略化します。</span><span class="sxs-lookup"><span data-stu-id="281b0-113">This simplifies the handling that is required from the XNA Game class.</span></span>  
  
 [<span data-ttu-id="281b0-114">GamePiece クラスの作成</span><span class="sxs-lookup"><span data-stu-id="281b0-114">Creating the GamePiece Class</span></span>](../../../docs/framework/common-client-technologies/creating-the-gamepiece-class.md)  
  
 [<span data-ttu-id="281b0-115">GamePieceCollection クラスの作成</span><span class="sxs-lookup"><span data-stu-id="281b0-115">Creating the GamePieceCollection Class</span></span>](../../../docs/framework/common-client-technologies/creating-the-gamepiececollection-class.md)  
  
 [<span data-ttu-id="281b0-116">Game1 クラスの作成</span><span class="sxs-lookup"><span data-stu-id="281b0-116">Creating the Game1 Class</span></span>](../../../docs/framework/common-client-technologies/creating-the-game1-class.md)  
  
 [<span data-ttu-id="281b0-117">完全なコードの一覧</span><span class="sxs-lookup"><span data-stu-id="281b0-117">Full Code Listings</span></span>](../../../docs/framework/common-client-technologies/full-code-listings.md)  
  
## <a name="see-also"></a><span data-ttu-id="281b0-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="281b0-118">See Also</span></span>  
 <span data-ttu-id="281b0-119"><xref:System.Windows.Input.Manipulations></span><span class="sxs-lookup"><span data-stu-id="281b0-119"><xref:System.Windows.Input.Manipulations></span></span>   
 [<span data-ttu-id="281b0-120">操作と慣性の概要</span><span class="sxs-lookup"><span data-stu-id="281b0-120">Manipulations and Inertia Overview</span></span>](../../../docs/framework/common-client-technologies/manipulations-and-inertia-overview.md)

