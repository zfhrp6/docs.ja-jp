---
title: "Game1 クラスの作成"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 47932ce3-2ba5-476f-a26b-3ddfd5226f27
caps.latest.revision: 8
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 9c6d0bdfd21f431ae6da38e3868386f91d5b725b
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="creating-the-game1-class"></a><span data-ttu-id="1fdec-102">Game1 クラスの作成</span><span class="sxs-lookup"><span data-stu-id="1fdec-102">Creating the Game1 Class</span></span>
<span data-ttu-id="1fdec-103">すべての Microsoft XNA プロジェクトと同様、Game1 クラスは [Microsoft.Xna.Framework.Game](http://msdn.microsoft.com/library/microsoft.xna.framework.game.aspx) クラスから派生しています。このクラスでは、XNA ゲーム用に、基本的なグラフィックス デバイスの初期化、ゲーム ロジックの提供、およびコードのレンダリングを行います。</span><span class="sxs-lookup"><span data-stu-id="1fdec-103">As with all Microsoft XNA projects, the Game1 class derives from the [Microsoft.Xna.Framework.Game](http://msdn.microsoft.com/library/microsoft.xna.framework.game.aspx) class, which provides basic graphics device initialization, game logic, and rendering code for XNA games.</span></span> <span data-ttu-id="1fdec-104">ほとんどの作業は GamePiece クラスと GamePieceCollection クラスで実行されるため、Game1 クラスは非常に簡潔になっています。</span><span class="sxs-lookup"><span data-stu-id="1fdec-104">The Game1 class is fairly simple because most of the work in done in the GamePiece and GamePieceCollection classes.</span></span>  
  
## <a name="creating-the-code"></a><span data-ttu-id="1fdec-105">コードの作成</span><span class="sxs-lookup"><span data-stu-id="1fdec-105">Creating the Code</span></span>  
 <span data-ttu-id="1fdec-106">クラスのプライベート メンバーはゲーム ピースを格納する **GamePieceCollection** オブジェクト、[GraphicsDeviceManager](http://msdn.microsoft.com/library/microsoft.xna.framework.graphicsdevicemanager.aspx) オブジェクト、ゲーム ピースのレンダリングに使用される [SpriteBatch](http://msdn.microsoft.com/library/microsoft.xna.framework.graphics.spritebatch.aspx) オブジェクトで構成されます。</span><span class="sxs-lookup"><span data-stu-id="1fdec-106">The private members for the class consist of a **GamePieceCollection** object to hold the game pieces, a [GraphicsDeviceManager](http://msdn.microsoft.com/library/microsoft.xna.framework.graphicsdevicemanager.aspx) object, and a [SpriteBatch](http://msdn.microsoft.com/library/microsoft.xna.framework.graphics.spritebatch.aspx) object used to render game pieces.</span></span>  
  
 <span data-ttu-id="1fdec-107">[!code-csharp[ManipulationXNA#_Game1_PrivateMembers](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/game1.cs#_game1_privatemembers)]</span><span class="sxs-lookup"><span data-stu-id="1fdec-107">[!code-csharp[ManipulationXNA#_Game1_PrivateMembers](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/game1.cs#_game1_privatemembers)]</span></span>  
  
 <span data-ttu-id="1fdec-108">ゲームの初期化中にこれらのオブジェクトはインスタンス化されます。</span><span class="sxs-lookup"><span data-stu-id="1fdec-108">During game initialization, these objects are instantiated.</span></span>  
  
 <span data-ttu-id="1fdec-109">[!code-csharp[ManipulationXNA#_Game1_ConstructorInitialize](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/game1.cs#_game1_constructorinitialize)]</span><span class="sxs-lookup"><span data-stu-id="1fdec-109">[!code-csharp[ManipulationXNA#_Game1_ConstructorInitialize](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/game1.cs#_game1_constructorinitialize)]</span></span>  
  
 <span data-ttu-id="1fdec-110">[LoadContent](http://msdn.microsoft.com/library/microsoft.xna.framework.game.loadcontent.aspx) メソッドが呼び出されると、ゲーム ピースが作成され、**GamePieceCollection** オブジェクトに割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="1fdec-110">When the [LoadContent](http://msdn.microsoft.com/library/microsoft.xna.framework.game.loadcontent.aspx) method is called, the game pieces are created and assigned to the **GamePieceCollection** object.</span></span> <span data-ttu-id="1fdec-111">ゲーム ピースには、次の 2 種類があります。</span><span class="sxs-lookup"><span data-stu-id="1fdec-111">There are two types of game pieces.</span></span> <span data-ttu-id="1fdec-112">ピースのスケール ファクターは、小さいピースや大きいピースが存在するようにわずかに変更されます。</span><span class="sxs-lookup"><span data-stu-id="1fdec-112">The scale factor for the pieces is changed slightly so that there are some smaller and some larger pieces.</span></span>  
  
 <span data-ttu-id="1fdec-113">[!code-csharp[ManipulationXNA#_Game1_LoadContent](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/game1.cs#_game1_loadcontent)]</span><span class="sxs-lookup"><span data-stu-id="1fdec-113">[!code-csharp[ManipulationXNA#_Game1_LoadContent](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/game1.cs#_game1_loadcontent)]</span></span>  
  
 <span data-ttu-id="1fdec-114">[Update](http://msdn.microsoft.com/library/microsoft.xna.framework.game.update.aspx) メソッドは、ゲームの実行中に XNA フレームワークによって繰り返し呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="1fdec-114">The [Update](http://msdn.microsoft.com/library/microsoft.xna.framework.game.update.aspx) method is called repeatedly by the XNA Framework while the game is running.</span></span> <span data-ttu-id="1fdec-115">[Update](http://msdn.microsoft.com/library/microsoft.xna.framework.game.update.aspx) メソッドは、ゲーム ピースのコレクションで **ProcessInertia** メソッドと **UpdateFromMouse** メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="1fdec-115">The [Update](http://msdn.microsoft.com/library/microsoft.xna.framework.game.update.aspx) method calls the **ProcessInertia** and the **UpdateFromMouse** methods on the game piece collection.</span></span> <span data-ttu-id="1fdec-116">これらのメソッドの説明は、「[GamePieceCollection クラスの作成](../../../docs/framework/common-client-technologies/creating-the-gamepiececollection-class.md)」にあります。</span><span class="sxs-lookup"><span data-stu-id="1fdec-116">These methods are described in [Creating the GamePieceCollection Class](../../../docs/framework/common-client-technologies/creating-the-gamepiececollection-class.md).</span></span>  
  
 <span data-ttu-id="1fdec-117">[!code-csharp[ManipulationXNA#_Game1_UpdateGame](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/game1.cs#_game1_updategame)]</span><span class="sxs-lookup"><span data-stu-id="1fdec-117">[!code-csharp[ManipulationXNA#_Game1_UpdateGame](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/game1.cs#_game1_updategame)]</span></span>  
  
 <span data-ttu-id="1fdec-118">[Draw](http://msdn.microsoft.com/library/microsoft.xna.framework.game.draw.aspx) メソッドも、ゲームの実行中に XNA フレームワークによって繰り返し呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="1fdec-118">The [Draw](http://msdn.microsoft.com/library/microsoft.xna.framework.game.draw.aspx) method is also called repeatedly by the XNA Framework while the game is running.</span></span> <span data-ttu-id="1fdec-119">[Draw](http://msdn.microsoft.com/library/microsoft.xna.framework.game.draw.aspx) メソッドは、**GamePieceCollection** オブジェクトの **Draw** メソッドを呼び出すことで、ゲーム ピースのレンダリングを実行します。</span><span class="sxs-lookup"><span data-stu-id="1fdec-119">The [Draw](http://msdn.microsoft.com/library/microsoft.xna.framework.game.draw.aspx) method performs the rendering of game pieces by calling the **Draw** method of the **GamePieceCollection** object.</span></span> <span data-ttu-id="1fdec-120">これらのメソッドの説明は、「[GamePieceCollection クラスの作成](../../../docs/framework/common-client-technologies/creating-the-gamepiececollection-class.md)」にあります。</span><span class="sxs-lookup"><span data-stu-id="1fdec-120">This method is described in[Creating the GamePieceCollection Class](../../../docs/framework/common-client-technologies/creating-the-gamepiececollection-class.md).</span></span>  
  
 <span data-ttu-id="1fdec-121">[!code-csharp[ManipulationXNA#_Game1_DrawGame](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/game1.cs#_game1_drawgame)]</span><span class="sxs-lookup"><span data-stu-id="1fdec-121">[!code-csharp[ManipulationXNA#_Game1_DrawGame](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/game1.cs#_game1_drawgame)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1fdec-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="1fdec-122">See Also</span></span>  
 <span data-ttu-id="1fdec-123">[操作と慣性](../../../docs/framework/common-client-technologies/manipulations-and-inertia.md) </span><span class="sxs-lookup"><span data-stu-id="1fdec-123">[Manipulations and Inertia](../../../docs/framework/common-client-technologies/manipulations-and-inertia.md) </span></span>  
 <span data-ttu-id="1fdec-124">[XNA アプリケーションでの操作と慣性の使用](../../../docs/framework/common-client-technologies/use-manipulations-and-inertia-in-an-xna-application.md) </span><span class="sxs-lookup"><span data-stu-id="1fdec-124">[Using Manipulations and Inertia in an XNA Application](../../../docs/framework/common-client-technologies/use-manipulations-and-inertia-in-an-xna-application.md) </span></span>  
 <span data-ttu-id="1fdec-125">[GamePiece クラスの作成](../../../docs/framework/common-client-technologies/creating-the-gamepiece-class.md) </span><span class="sxs-lookup"><span data-stu-id="1fdec-125">[Creating the GamePiece Class](../../../docs/framework/common-client-technologies/creating-the-gamepiece-class.md) </span></span>  
 <span data-ttu-id="1fdec-126">[GamePieceCollection クラスの作成](../../../docs/framework/common-client-technologies/creating-the-gamepiececollection-class.md) </span><span class="sxs-lookup"><span data-stu-id="1fdec-126">[Creating the GamePieceCollection Class](../../../docs/framework/common-client-technologies/creating-the-gamepiececollection-class.md) </span></span>  
 [<span data-ttu-id="1fdec-127">完全なコードの一覧</span><span class="sxs-lookup"><span data-stu-id="1fdec-127">Full Code Listings</span></span>](../../../docs/framework/common-client-technologies/full-code-listings.md)

