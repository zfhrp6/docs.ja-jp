---
title: "GamePieceCollection クラスの作成"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e4b037ee-1201-4a55-b198-0d6532ed6f35
caps.latest.revision: 8
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: b74702d71113c3a9dac654971e7d02f97016218b
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="creating-the-gamepiececollection-class"></a><span data-ttu-id="71c98-102">GamePieceCollection クラスの作成</span><span class="sxs-lookup"><span data-stu-id="71c98-102">Creating the GamePieceCollection Class</span></span>
<span data-ttu-id="71c98-103">**GamePieceCollection** クラスは、汎用の List クラスから派生し、複数の **GamePiece** オブジェクトをより簡単に管理するメソッドを導入します。</span><span class="sxs-lookup"><span data-stu-id="71c98-103">The **GamePieceCollection** class derives from the generic List class, and introduces methods to more easily manage multiple **GamePiece** objects.</span></span>  
  
## <a name="creating-the-code"></a><span data-ttu-id="71c98-104">コードの作成</span><span class="sxs-lookup"><span data-stu-id="71c98-104">Creating the Code</span></span>  
 <span data-ttu-id="71c98-105">**GamePieceCollection** クラスのコンストラクターは、プライベート メンバー *capturedIndex* を初期化します。</span><span class="sxs-lookup"><span data-stu-id="71c98-105">The constructor of the **GamePieceCollection** class initializes the private member *capturedIndex*.</span></span> <span data-ttu-id="71c98-106">このフィールドは、現在どのゲーム ピースにマウス キャプチャがあるかを追跡するために使用します。</span><span class="sxs-lookup"><span data-stu-id="71c98-106">This field is used to track which of the game pieces currently has the mouse capture.</span></span>  
  
 <span data-ttu-id="71c98-107">[!code-csharp[ManipulationXNA#_GamePieceCollection_PrivateMembersAndConstructor](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/gamepiececollection.cs#_gamepiececollection_privatemembersandconstructor)]</span><span class="sxs-lookup"><span data-stu-id="71c98-107">[!code-csharp[ManipulationXNA#_GamePieceCollection_PrivateMembersAndConstructor](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/gamepiececollection.cs#_gamepiececollection_privatemembersandconstructor)]</span></span>  
  
 <span data-ttu-id="71c98-108">**ProcessInertia** メソッドと **Draw** メソッドは、コレクションのすべてのゲーム ピースを列挙し、各 **GamePiece** オブジェクトのそれぞれのメソッドで呼び出すことで、ゲームの [Game.Update](http://msdn.microsoft.com/library/microsoft.xna.framework.game.update.aspx) メソッドと [Game.Draw](http://msdn.microsoft.com/library/microsoft.xna.framework.game.draw.aspx) メソッドに必要なコードを簡素化します。</span><span class="sxs-lookup"><span data-stu-id="71c98-108">The **ProcessInertia** and the **Draw** methods simplify the code needed in the game [Game.Update](http://msdn.microsoft.com/library/microsoft.xna.framework.game.update.aspx) and [Game.Draw](http://msdn.microsoft.com/library/microsoft.xna.framework.game.draw.aspx) methods by enumerating all of the game pieces in the collection and calling the respective method on each **GamePiece** object.</span></span>  
  
 <span data-ttu-id="71c98-109">[!code-csharp[ManipulationXNA#_GamePieceCollection_ProcessInertiaAndDraw](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/gamepiececollection.cs#_gamepiececollection_processinertiaanddraw)]</span><span class="sxs-lookup"><span data-stu-id="71c98-109">[!code-csharp[ManipulationXNA#_GamePieceCollection_ProcessInertiaAndDraw](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/gamepiececollection.cs#_gamepiececollection_processinertiaanddraw)]</span></span>  
  
 <span data-ttu-id="71c98-110">**UpdateFromMouse** メソッドもゲームの更新中に呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="71c98-110">The **UpdateFromMouse** method is also called during game update.</span></span> <span data-ttu-id="71c98-111">最初に現在のキャプチャ (もしあれば) が有効なままであるかどうかを確認すると、1 つのゲーム ピースのみがマウス キャプチャするようになります。</span><span class="sxs-lookup"><span data-stu-id="71c98-111">It enables only one game piece to have the mouse capture by first checking to see if the current capture (if any) is still in effect.</span></span> <span data-ttu-id="71c98-112">有効の場合、他のピースはキャプチャの確認ができません。</span><span class="sxs-lookup"><span data-stu-id="71c98-112">If so, no other piece is allowed to check for capture.</span></span>  
  
 <span data-ttu-id="71c98-113">キャプチャがあるピースがない場合、**UpdateFromMouse** メソッドが最後から最初へとゲーム ピースを列挙し、対象のピースがマウス キャプチャを報告するかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="71c98-113">If no piece currently has the capture, the **UpdateFromMouse** method enumerates each game piece from last to first, and checks to see if that piece reports a mouse capture.</span></span> <span data-ttu-id="71c98-114">報告する場合、対象のピースは現在キャプチャされているピースになり、後続の処理は実行されません。</span><span class="sxs-lookup"><span data-stu-id="71c98-114">If so, that piece becomes the current captured piece, and no further processing takes place.</span></span> <span data-ttu-id="71c98-115">**UpdateFromMouse** メソッドは、先にコレクションの最後の項目を確認します。そうすることで、2 つのピースが重なっている場合、Z オーダーが高いピースがキャプチャを取得します。</span><span class="sxs-lookup"><span data-stu-id="71c98-115">The **UpdateFromMouse** method checks the last item in the collection first so that if two pieces are overlapped, the one with the higher Z-order will obtain the capture.</span></span> <span data-ttu-id="71c98-116">Z オーダーは明示的ではなく、変更もできません。Z オーダーは、ゲーム ピースがコレクションに追加された順序で管理されます。</span><span class="sxs-lookup"><span data-stu-id="71c98-116">Z-order is not explicit nor changeable; it is governed simply by the order in which game pieces are added to the collection.</span></span>  
  
 <span data-ttu-id="71c98-117">[!code-csharp[ManipulationXNA#_GamePieceCollection_UpdateFromMouse](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/gamepiececollection.cs#_gamepiececollection_updatefrommouse)]</span><span class="sxs-lookup"><span data-stu-id="71c98-117">[!code-csharp[ManipulationXNA#_GamePieceCollection_UpdateFromMouse](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/gamepiececollection.cs#_gamepiececollection_updatefrommouse)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71c98-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="71c98-118">See Also</span></span>  
 <span data-ttu-id="71c98-119">[操作と慣性](../../../docs/framework/common-client-technologies/manipulations-and-inertia.md) </span><span class="sxs-lookup"><span data-stu-id="71c98-119">[Manipulations and Inertia](../../../docs/framework/common-client-technologies/manipulations-and-inertia.md) </span></span>  
 <span data-ttu-id="71c98-120">[XNA アプリケーションでの操作と慣性の使用](../../../docs/framework/common-client-technologies/use-manipulations-and-inertia-in-an-xna-application.md) </span><span class="sxs-lookup"><span data-stu-id="71c98-120">[Using Manipulations and Inertia in an XNA Application](../../../docs/framework/common-client-technologies/use-manipulations-and-inertia-in-an-xna-application.md) </span></span>  
 <span data-ttu-id="71c98-121">[GamePiece クラスの作成](../../../docs/framework/common-client-technologies/creating-the-gamepiece-class.md) </span><span class="sxs-lookup"><span data-stu-id="71c98-121">[Creating the GamePiece Class](../../../docs/framework/common-client-technologies/creating-the-gamepiece-class.md) </span></span>  
 <span data-ttu-id="71c98-122">[Game1 クラスの作成](../../../docs/framework/common-client-technologies/creating-the-game1-class.md) </span><span class="sxs-lookup"><span data-stu-id="71c98-122">[Creating the Game1 Class](../../../docs/framework/common-client-technologies/creating-the-game1-class.md) </span></span>  
 [<span data-ttu-id="71c98-123">完全なコードの一覧</span><span class="sxs-lookup"><span data-stu-id="71c98-123">Full Code Listings</span></span>](../../../docs/framework/common-client-technologies/full-code-listings.md)

