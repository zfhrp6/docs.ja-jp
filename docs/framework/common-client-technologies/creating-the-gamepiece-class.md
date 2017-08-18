---
title: "GamePiece クラスの作成"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 37a27a86-ac1c-47be-b477-cb4b819459d3
caps.latest.revision: 9
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 7ac9884766812cd635b5a70c028cf15c19838511
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="creating-the-gamepiece-class"></a>GamePiece クラスの作成
**GamePiece** クラスは、Microsoft XNA ゲーム ピースのイメージの読み込み、ゲーム ピースに関係するマウスの状態の追跡、マウスのキャプチャ、操作と慣性の処理の実行、およびゲーム ピースがビュー ポートの限度に達したときの跳ね返り機能の提供に必要な機能をすべてカプセル化します。  
  
## <a name="private-members"></a>プライベート メンバー  
 **GamePiece** クラスの上部で、いくつかのプライベート メンバーが宣言されます。  
  
 [!code-csharp[ManipulationXNA#_GamePiece_PrivateMembers](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/gamepiece.cs#_gamepiece_privatemembers)]  
  
## <a name="public-properties"></a>パブリック プロパティ  
 これらの 3 つのプライベート メンバーは、パブリック プロパティを介して公開されます。 **Scale** と **PieceColor** プロパティを使用すると、アプリケーションはピースのサイズと色をそれぞれ指定することができます。 **Bounds** プロパティを公開すると、あるピースが別のピースを重ねて配置する場合など、あるピース自体をレンダリングするために別のピースの境界を使用できるようになります。 次のコードは、パブリック プロパティの宣言を示します。  
  
 [!code-csharp[ManipulationXNA#_GamePiece_PublicProperties](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/gamepiece.cs#_gamepiece_publicproperties)]  
  
## <a name="class-constructor"></a>クラスのコンストラクター  
 **GamePiece** クラスのコンストラクターは、次のパラメーターを受け入れます。  
  
-   [SpriteBatch](http://msdn.microsoft.com/library/microsoft.xna.framework.graphics.spritebatch.aspx) 型。 ここで渡される参照は、プライベート メンバー `spriteBatch` に割り当てられ、ゲーム ピースが自身をレンダリングするときに [SpriteBatch.Draw](http://msdn.microsoft.com/library/microsoft.xna.framework.graphics.spritebatch.draw.aspx) メソッドにアクセスするために使用されます。 さらに、[GraphicsDevice](http://msdn.microsoft.com/library/microsoft.xna.framework.graphics.spritebatch.graphicsdevice.aspx) プロパティは、ゲーム ピースに関連付けられた [Texture](http://msdn.microsoft.com/library/microsoft.xna.framework.graphics.texture.aspx) オブジェクトの作成や、ゲーム ピースがウィンドウの境界に達したことを検知してピースが跳ね返るようにするための、ビュー ポートのサイズの取得にも使用されます。  
  
-   ゲーム ピースに使用するイメージのファイル名を指定する文字列。  
  
 また、コンストラクターは、<xref:System.Windows.Input.Manipulations.ManipulationProcessor2D> オブジェクトと <xref:System.Windows.Input.Manipulations.InertiaProcessor2D> オブジェクトを作成し、それらのイベントのイベント ハンドラーを確立します。  
  
 次のコードは、**GamePiece** クラスのコンストラクターを示します。  
  
 [!code-csharp[ManipulationXNA#_GamePiece_Constructor](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/gamepiece.cs#_gamepiece_constructor)]  
  
## <a name="capturing-mouse-input"></a>マウスの入力のキャプチャ  
 **UpdateFromMouse** メソッドは、マウスがゲーム ピースの境界内にある間にマウス ボタンが押されたときに検出するとともに、マウス ボタンが離されたときに検出する役割を務めます。  
  
 (マウスがピースの境界内にある間に) マウスの左ボタンを押すと、このメソッドはフラグを設定して、ゲーム ピースがマウスをキャプチャして、操作の処理を開始することを示します。  
  
 操作の処理は、<xref:System.Windows.Input.Manipulations.Manipulator2D> オブジェクトの配列を作成し、それを <xref:System.Windows.Input.Manipulations.ManipulationProcessor2D> オブジェクトに渡して開始します。 これにより、操作プロセッサがマニピュレーター (この場合は 1 つのマニピュレーター) を評価し、操作イベントを発生させます。  
  
 さらに、ドラッグが発生するポイントが保存されます。 これは後の <xref:System.Windows.Input.Manipulations.ManipulationProcessor2D.Delta> イベントのときに、ゲーム ピースがドラッグ ポイントの背後の線に向かって移動するようにデルタ変換値を調整するために使用します。  
  
 最後に、このメソッドは、マウスのキャプチャの状態を返します。 これにより、[GamePieceCollection](../../../docs/framework/common-client-technologies/creating-the-gamepiececollection-class.md) オブジェクトは、複数のゲーム ピースがある場合にキャプチャを管理できるようになります。  
  
 次のコードは、**UpdateFromMouse** メソッドを示しています。  
  
 [!code-csharp[ManipulationXNA#_GamePiece_UpdateFromMouse](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/gamepiece.cs#_gamepiece_updatefrommouse)]  
  
## <a name="processing-manipulations"></a>操作の処理  
 操作の開始時に、<xref:System.Windows.Input.Manipulations.ManipulationProcessor2D.Started> イベントが発生します。 このイベントのハンドラーは、慣性の処理が発生している場合は停止し、*processInertia* フラグを `false` に設定します。  
  
 [!code-csharp[ManipulationXNA#_GamePiece_OnManipulationStarted](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/gamepiece.cs#_gamepiece_onmanipulationstarted)]  
  
 操作に関連している値が変化するため、<xref:System.Windows.Input.Manipulations.ManipulationProcessor2D.Delta> イベントが発生します。 このイベントのハンドラーは、ゲーム ピースの位置と回転の値を変更するイベント引数に渡されるデルタ値を使用します。  
  
 [!code-csharp[ManipulationXNA#_GamePiece_OnManipulationDelta](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/gamepiece.cs#_gamepiece_onmanipulationdelta)]  
  
 操作に関連するすべてのマニピュレーター (この場合は 1 つのマニピュレーター) が削除されると、操作プロセッサは <xref:System.Windows.Input.Manipulations.ManipulationProcessor2D.Completed> イベントを生成します。 このイベントのハンドラーは、慣性プロセッサの初期速度をイベント引数によって報告された初期速度に設定して慣性の処理を開始するとともに、*processInertia* フラグを `true` に設定します。  
  
 [!code-csharp[ManipulationXNA#_GamePiece_OnManipulationCompleted](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/gamepiece.cs#_gamepiece_onmanipulationcompleted)]  
  
## <a name="processing-inertia"></a>慣性の処理  
 慣性の処理では、角速度と直線速度、位置 (変換) 座標、および回転の新しい値を推定します。<xref:System.Windows.Input.Manipulations.InertiaProcessor2D.Delta> イベントが発生します。 このイベントのハンドラーは、ゲーム ピースの位置と回転を変更するイベント引数に渡されるデルタ値を使用します。  
  
 新しい座標によって、ゲーム ピースがビュー ポートの境界を越えてしまった場合、慣性の処理の速度が元に戻ります。 これにより、ゲーム ピースが接したビュー ポートの境界から跳ね返ります。  
  
 推定が実行している間は、<xref:System.Windows.Input.Manipulations.InertiaProcessor2D> オブジェクトのプロパティを変更できません。 そのため、X または Y の速度を元に戻す場合、イベント ハンドラーは、最初に <xref:System.Windows.Input.Manipulations.InertiaProcessor2D.Complete%2A> メソッドを呼び出して慣性を停止します。 続いて、新しい初期速度値を、(スポンジ動作向けに調整された) 現在の速度値に割り当てます。また、*processInertia* フラグを `true` に設定します。  
  
 次のコードは、<xref:System.Windows.Input.Manipulations.InertiaProcessor2D.Delta> イベントのイベント ハンドラーを示しています。  
  
 [!code-csharp[ManipulationXNA#_GamePiece_OnInertiaDelta](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/gamepiece.cs#_gamepiece_oninertiadelta)]  
  
 慣性の処理が完了すると、慣性プロセッサは <xref:System.Windows.Input.Manipulations.InertiaProcessor2D.Completed> イベントを発生させます。 このイベントのハンドラーは、*processInertia* フラグを `false` に設定します。  
  
 [!code-csharp[ManipulationXNA#_GamePiece_OnInertiaCompleted](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/gamepiece.cs#_gamepiece_oninertiacompleted)]  
  
 これまでに提示したロジックで、実際に慣性の推定が発生するものはありません。 これは、**ProcessInertia** メソッドで実現されます。 このメソッドは、ゲームの更新ループ ([Game.Update](http://msdn.microsoft.com/library/microsoft.xna.framework.game.update.aspx) メソッド) から繰り返し呼び出され、*processInertia* フラグが `true` に設定されていることを確認します。設定されている場合は <xref:System.Windows.Input.Manipulations.InertiaProcessor2D.Process%2A> メソッドを呼び出します。 このメソッドを呼び出すと、推定が発生して、<xref:System.Windows.Input.Manipulations.InertiaProcessor2D.Delta> イベントが発生します。  
  
 [!code-csharp[ManipulationXNA#_GamePiece_ProcessInertia](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/gamepiece.cs#_gamepiece_processinertia)]  
  
 いずれかの描画メソッドのオーバーロードが呼び出されるまで、ゲーム ピースは実際に表示されません。 このメソッドの最初のオーバー ロードは、ゲームの描画ループから繰り返し呼び出されます ([Game.Draw](http://msdn.microsoft.com/library/microsoft.xna.framework.game.draw.aspx) メソッド)。 これにより、現在の位置、回転、およびスケール ファクターでゲーム ピースが表示されます。  
  
 [!code-csharp[ManipulationXNA#_GamePiece_Draw](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/gamepiece.cs#_gamepiece_draw)]  
  
## <a name="additional-properties"></a>その他のプロパティ  
 **GamePiece** クラスによって 3 つのプライベート プロパティが使用されます。  
  
1.  **Timestamp** – 操作と慣性プロセッサが使用するタイムスタンプ値を取得します。  
  
2.  **X** – ゲーム ピースの X 座標を取得または設定します。 設定すると、ヒット テストや、操作プロセッサのピボット位置に使用する境界を調整します。  
  
3.  **Y** – ゲーム ピースの Y 座標を取得または設定します。 設定すると、ヒット テストや、操作プロセッサのピボット位置に使用する境界を調整します。  
  
 [!code-csharp[ManipulationXNA#_GamePiece_PrivateProperties](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/gamepiece.cs#_gamepiece_privateproperties)]  
  
## <a name="see-also"></a>関連項目  
 [操作と慣性](../../../docs/framework/common-client-technologies/manipulations-and-inertia.md)   
 [XNA アプリケーションでの操作と慣性の使用](../../../docs/framework/common-client-technologies/use-manipulations-and-inertia-in-an-xna-application.md)   
 [GamePieceCollection クラスの作成](../../../docs/framework/common-client-technologies/creating-the-gamepiececollection-class.md)   
 [Game1 クラスの作成](../../../docs/framework/common-client-technologies/creating-the-game1-class.md)

