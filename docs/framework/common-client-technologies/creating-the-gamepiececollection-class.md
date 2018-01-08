---
title: "GamePieceCollection クラスの作成"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e4b037ee-1201-4a55-b198-0d6532ed6f35
caps.latest.revision: "8"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8f000c1eed27acc16d158cb893cba876ea016277
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="creating-the-gamepiececollection-class"></a><span data-ttu-id="a94a5-102">GamePieceCollection クラスの作成</span><span class="sxs-lookup"><span data-stu-id="a94a5-102">Creating the GamePieceCollection Class</span></span>
<span data-ttu-id="a94a5-103">**GamePieceCollection** クラスは、汎用の List クラスから派生し、複数の **GamePiece** オブジェクトをより簡単に管理するメソッドを導入します。</span><span class="sxs-lookup"><span data-stu-id="a94a5-103">The **GamePieceCollection** class derives from the generic List class, and introduces methods to more easily manage multiple **GamePiece** objects.</span></span>  
  
## <a name="creating-the-code"></a><span data-ttu-id="a94a5-104">コードの作成</span><span class="sxs-lookup"><span data-stu-id="a94a5-104">Creating the Code</span></span>  
 <span data-ttu-id="a94a5-105">**GamePieceCollection** クラスのコンストラクターは、プライベート メンバー *capturedIndex* を初期化します。</span><span class="sxs-lookup"><span data-stu-id="a94a5-105">The constructor of the **GamePieceCollection** class initializes the private member *capturedIndex*.</span></span> <span data-ttu-id="a94a5-106">このフィールドは、現在どのゲーム ピースにマウス キャプチャがあるかを追跡するために使用します。</span><span class="sxs-lookup"><span data-stu-id="a94a5-106">This field is used to track which of the game pieces currently has the mouse capture.</span></span>  
  
 [!code-csharp[ManipulationXNA#_GamePieceCollection_PrivateMembersAndConstructor](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/gamepiececollection.cs#_gamepiececollection_privatemembersandconstructor)]  
  
 <span data-ttu-id="a94a5-107">**ProcessInertia** メソッドと **Draw** メソッドは、コレクションのすべてのゲーム ピースを列挙し、各 **GamePiece** オブジェクトのそれぞれのメソッドで呼び出すことで、ゲームの [Game.Update](http://msdn.microsoft.com/library/microsoft.xna.framework.game.update.aspx) メソッドと [Game.Draw](http://msdn.microsoft.com/library/microsoft.xna.framework.game.draw.aspx) メソッドに必要なコードを簡素化します。</span><span class="sxs-lookup"><span data-stu-id="a94a5-107">The **ProcessInertia** and the **Draw** methods simplify the code needed in the game [Game.Update](http://msdn.microsoft.com/library/microsoft.xna.framework.game.update.aspx) and [Game.Draw](http://msdn.microsoft.com/library/microsoft.xna.framework.game.draw.aspx) methods by enumerating all of the game pieces in the collection and calling the respective method on each **GamePiece** object.</span></span>  
  
 [!code-csharp[ManipulationXNA#_GamePieceCollection_ProcessInertiaAndDraw](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/gamepiececollection.cs#_gamepiececollection_processinertiaanddraw)]  
  
 <span data-ttu-id="a94a5-108">**UpdateFromMouse** メソッドもゲームの更新中に呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="a94a5-108">The **UpdateFromMouse** method is also called during game update.</span></span> <span data-ttu-id="a94a5-109">最初に現在のキャプチャ (もしあれば) が有効なままであるかどうかを確認すると、1 つのゲーム ピースのみがマウス キャプチャするようになります。</span><span class="sxs-lookup"><span data-stu-id="a94a5-109">It enables only one game piece to have the mouse capture by first checking to see if the current capture (if any) is still in effect.</span></span> <span data-ttu-id="a94a5-110">有効の場合、他のピースはキャプチャの確認ができません。</span><span class="sxs-lookup"><span data-stu-id="a94a5-110">If so, no other piece is allowed to check for capture.</span></span>  
  
 <span data-ttu-id="a94a5-111">キャプチャがあるピースがない場合、**UpdateFromMouse** メソッドが最後から最初へとゲーム ピースを列挙し、対象のピースがマウス キャプチャを報告するかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="a94a5-111">If no piece currently has the capture, the **UpdateFromMouse** method enumerates each game piece from last to first, and checks to see if that piece reports a mouse capture.</span></span> <span data-ttu-id="a94a5-112">報告する場合、対象のピースは現在キャプチャされているピースになり、後続の処理は実行されません。</span><span class="sxs-lookup"><span data-stu-id="a94a5-112">If so, that piece becomes the current captured piece, and no further processing takes place.</span></span> <span data-ttu-id="a94a5-113">**UpdateFromMouse** メソッドは、先にコレクションの最後の項目を確認します。そうすることで、2 つのピースが重なっている場合、Z オーダーが高いピースがキャプチャを取得します。</span><span class="sxs-lookup"><span data-stu-id="a94a5-113">The **UpdateFromMouse** method checks the last item in the collection first so that if two pieces are overlapped, the one with the higher Z-order will obtain the capture.</span></span> <span data-ttu-id="a94a5-114">Z オーダーは明示的ではなく、変更もできません。Z オーダーは、ゲーム ピースがコレクションに追加された順序で管理されます。</span><span class="sxs-lookup"><span data-stu-id="a94a5-114">Z-order is not explicit nor changeable; it is governed simply by the order in which game pieces are added to the collection.</span></span>  
  
 [!code-csharp[ManipulationXNA#_GamePieceCollection_UpdateFromMouse](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/gamepiececollection.cs#_gamepiececollection_updatefrommouse)]  
  
## <a name="see-also"></a><span data-ttu-id="a94a5-115">参照</span><span class="sxs-lookup"><span data-stu-id="a94a5-115">See Also</span></span>  
 [<span data-ttu-id="a94a5-116">操作と慣性</span><span class="sxs-lookup"><span data-stu-id="a94a5-116">Manipulations and Inertia</span></span>](../../../docs/framework/common-client-technologies/manipulations-and-inertia.md)  
 [<span data-ttu-id="a94a5-117">XNA アプリケーションでの操作と慣性の使用</span><span class="sxs-lookup"><span data-stu-id="a94a5-117">Using Manipulations and Inertia in an XNA Application</span></span>](../../../docs/framework/common-client-technologies/use-manipulations-and-inertia-in-an-xna-application.md)  
 [<span data-ttu-id="a94a5-118">GamePiece クラスの作成</span><span class="sxs-lookup"><span data-stu-id="a94a5-118">Creating the GamePiece Class</span></span>](../../../docs/framework/common-client-technologies/creating-the-gamepiece-class.md)  
 [<span data-ttu-id="a94a5-119">Game1 クラスの作成</span><span class="sxs-lookup"><span data-stu-id="a94a5-119">Creating the Game1 Class</span></span>](../../../docs/framework/common-client-technologies/creating-the-game1-class.md)  
 [<span data-ttu-id="a94a5-120">完全なコードの一覧</span><span class="sxs-lookup"><span data-stu-id="a94a5-120">Full Code Listings</span></span>](../../../docs/framework/common-client-technologies/full-code-listings.md)
