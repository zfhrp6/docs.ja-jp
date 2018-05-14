---
title: 操作と慣性の概要
ms.date: 03/30/2017
ms.assetid: dd31b89b-eab6-45a1-8d0b-11e0eb84b234
ms.openlocfilehash: 7aec2756bfc3a7d4ccd394d54f19428d73b44fcb
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="manipulations-and-inertia-overview"></a>操作と慣性の概要
"*操作*" では、"*マニピュレーター*" を使用して、ユーザー インターフェイス (UI) 要素の移動、回転、サイズ変更を行えます。 マニピュレーターは、マウス、または (タッチ対応のシナリオの場合) スタイラスや指を意味します。  
  
 "*慣性*" は、要素上で摩擦力をシミュレートして、動いている UI 要素の実際の動作をエミュレートします。 これにより、要素は (直線運動と角運動の両方で) 徐々に動作の速度を遅らせてから停止します。 この記事では、.NET Framework の操作と慣性の概要を説明します。  
  
## <a name="manipulations"></a>操作  
 操作では、マニピュレーターのコレクションを複合オブジェクトとして扱います。 アプリケーションは、個々 のコンポーネントではなく複合オブジェクトへの変更を追跡できます。  
  
 次の図の画像を考えてください。 ユーザーは 2 つのマニピュレーターを使用して、画像の移動、回転、拡大/縮小を行えます。 各マニピュレーターへの変更は、他のマニピュレーターと一緒に解釈されます。  
  
 たとえば、画像に 2 つのマニピュレーター (1 および 2) があり、マニピュレーター 1 を +Y 方向 (下) に移動する場合、画像への変更はマニピュレーター 2 で何が発生するかによって変わります。 マニピュレーター 2 も +Y 方向 (下) に移動する場合、画像は +Y 方向に移動します。 しかし、マニピュレーター 2 が変更しない場合、または -Y 方向 (上) に移動する場合は、画像は小さくなるか回転します。  
  
 ![2 本の指で操作中の仮想写真。](../../../docs/framework/common-client-technologies/media/manipulation-resize.png "Manipulation_Resize")  
  
 2 つのマニピュレーターによって操作されている画像  
  
 操作の処理には、マニピュレーターのサブセットを監視し、個別にではなく一緒に動作するかのように解釈するフレームワークがあります。 複数の操作プロセッサのオブジェクトを同時に作成することができ、アプリケーションで UI 要素ごとに 1 つのオブジェクトが操作されます。 操作プロセッサには、[.NET イベント](http://msdn.microsoft.com/library/17sde2xt.aspx)を通じて、どの入力デバイスを観察するかが通知され、それは操作を報告します。  
  
 操作プロセッサには、操作する特定の要素に関する情報はありません。 アプリケーションは、アプリケーション固有の要素への変更を個別に適用します。 たとえば、アプリケーションは画像に変換を適用したり、新しい場所に、または新しいサイズや向きに再描画して表示したりします。  
  
 操作は 2 次元 (2-D) の[アフィン変換](http://msdn.microsoft.com/library/ms533810\(VS.85\).aspx)用に設計されています。 アフィン変換には、変換、回転、拡大/縮小などがあります。  
  
### <a name="parts-of-a-manipulation"></a>操作のパーツ  
 操作は、<xref:System.Windows.Input.Manipulations.Manipulator2D> オブジェクトのコレクションです。 この集約的な操作は、最初の場所と楕円で表されます。 最初の場所は、要素を操作しているすべてのマニピュレーターの平均位置です。 楕円は、始点から各 <xref:System.Windows.Input.Manipulations.Manipulator2D> オブジェクトまでの平均距離である半径です。  
  
 ![操作の一部。] (../../../docs/framework/common-client-technologies/media/manipulation-definition.png "Manipulation_Definition")  
  
 2 つのマニピュレーター (1 と 2)、始点、および楕円によって操作を指定します。  
  
 マニピュレーターは UI 要素に対して追加、移動、または削除を行い、アプリケーションは <xref:System.Windows.Input.Manipulations.ManipulationProcessor2D.ProcessManipulators%2A> メソッドを呼び出して <xref:System.Windows.Input.Manipulations.ManipulationProcessor2D> オブジェクトを更新します。 最初に操作が開始するとき、 <xref:System.Windows.Input.Manipulations.ManipulationProcessor2D.Started> イベントが発生します。  
  
> [!NOTE]
>  操作の処理は、フレームベースの環境の更新で使用すると、より効率的です。 Microsoft XNA アプリケーションで操作の処理を使用する場合は問題ありません。これは、XNA フレームワークが [Game.Update](http://msdn.microsoft.com/library/microsoft.xna.framework.game.update.aspx) メソッドを使用してフレームベースの更新を行っているためです。 別の環境 (WinForms など) では、操作を収集し、定期的にバッチとして <xref:System.Windows.Input.Manipulations.ManipulationProcessor2D.ProcessManipulators%2A> メソッドに送信するために、独自のフレームベースのロジックを用意する必要がある場合があります。  
  
 マニピュレーターの数またはその場所が変化すると、<xref:System.Windows.Input.Manipulations.ManipulationProcessor2D.Delta> イベントが発生します。 <xref:System.Windows.Input.Manipulations.ManipulationProcessor2D.Delta> イベント ハンドラーに渡される <xref:System.Windows.Input.Manipulations.Manipulation2DDeltaEventArgs> オブジェクトのプロパティでは、始点、スケール、回転、および最後のイベント以降に発生した変換の変化を指定します。 マニピュレーターが移動したときや、マニピュレーターが追加または削除されたときには、操作の始点が変化します。 変換値では、操作での X 方向および Y 方向の移動量を指定します。  
  
 新しい値を使用して、アプリケーションは UI 要素を再描画します。  
  
 ![連絡先 A を右側に移動した後の操作。](../../../docs/framework/common-client-technologies/media/manipulation-changed.png "Manipulation_Changed")  
  
 マニピュレーター 1 が移動して始点を変化させる  
  
 操作に関連付けられている最後のマニピュレーターが <xref:System.Windows.Input.Manipulations.ManipulationProcessor2D> オブジェクトから削除されると、<xref:System.Windows.Input.Manipulations.ManipulationProcessor2D.Completed> イベントが発生します。  
  
### <a name="the-manipulation-processing-model"></a>操作の処理モデル  
 操作プロセッサは、直接使用モデルを使用します。 この単純なモデルでは、アプリケーションは操作プロセッサに入力イベントの詳細を渡す必要があります。 入力イベントは、マウス デバイス、スタイラス、指など、任意の入力プリミティブによって発生することがあります。 このプロセスでは、直接フィルター処理メカニズムと単純な使用モデルを提供しているため、アプリケーションは、必要なときに入力イベントをバッチ処理することができます。  
  
 アプリケーションが操作の処理に入力プリミティブを含めるようにするには、入力プリミティブの内容から <xref:System.Windows.Input.Manipulations.Manipulator2D> 構造体を作成してから、<xref:System.Windows.Input.Manipulations.ManipulationProcessor2D.ProcessManipulators%2A> メソッドを使用してその構造体を操作プロセッサに渡します。 操作プロセッサは、適切な方法でビジュアル コンポーネントを更新するためにアプリケーションが処理する必要のあるイベントを発生させます。  
  
 ![直接使用モデルの操作フロー。](../../../docs/framework/common-client-technologies/media/manipulation-flow.png "Manipulation_Flow")  
  
 操作の処理モデル  
  
## <a name="inertia"></a>慣性  
 慣性プロセッサを使用すると、アプリケーションは、実際の動作をシミュレートすることで、UI 要素の位置、向き、その他のプロパティを推定できます。  
  
 たとえば、ユーザーが要素をフリックすると、要素は引き続き動き、減速し、徐々に停止します。 慣性プロセッサは、2-D のアフィン値 (始点、スケール、変換、回転) を指定した減速率で指定した時間をかけて変化させることで、この動作を実行します。  
  
 操作の処理と同様、慣性プロセッサには、特定の UI 要素に関する情報はありません。 <xref:System.Windows.Input.Manipulations.InertiaProcessor2D> オブジェクトで発生するイベントに対応して、アプリケーションは、アプリケーション固有の要素への変更を個別に適用します。  
  
 慣性の処理と操作の処理は、多くの場合、一緒に使用されます。 これらのインターフェイスは類似しており、発生するイベントは (場合によって) 同一です。 一般に、UI 要素の操作が完了すると、慣性の処理が開始します。 これは、<xref:System.Windows.Input.Manipulations.ManipulationProcessor2D.Completed> イベントをリッスンして、そのイベント ハンドラーから慣性の処理を開始することで実現します。  
  
## <a name="see-also"></a>参照  
 <xref:System.Windows.Input.Manipulations>
