---
title: Windows フォームにおけるマウス入力のしくみ
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, mouse input
- mouse [Windows Forms], input
ms.assetid: 48fc5240-75a6-44bf-9fce-6aa21b49705a
ms.openlocfilehash: 265693eef3008362994ad04d9faaf8e20554d13e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33540870"
---
# <a name="how-mouse-input-works-in-windows-forms"></a>Windows フォームにおけるマウス入力のしくみ
受信とマウス入力の処理は、すべての Windows アプリケーションの重要な部分です。 アプリケーションで操作を実行するマウス イベントを処理するか、ヒット テストの実行にマウスの位置情報やその他のアクションを使用します。 さらに、アプリケーションでは、コントロールがマウス入力を処理する方法を変更することができます。 このトピックでは、これらのマウス イベントの詳細と、取得して、マウスのシステム設定を変更する方法について説明します。 イベントとする、マウスのクリックしてイベントの順序を発生するマウスで提供されるデータの詳細についてを参照してください[Windows フォームにおけるマウス イベント](../../../docs/framework/winforms/mouse-events-in-windows-forms.md)です。  
  
## <a name="mouse-location-and-hit-testing"></a>マウスの位置とヒット テスト  
 ユーザーがマウスを動かしたときに、オペレーティング システムは、マウス ポインターを移動します。 マウス ポインターには、オペレーティング システムを追跡し、ポインターの位置として認識するホット スポットと呼ばれる単一のピクセルが含まれています。 ユーザーがマウスを移動またはマウス ボタンを押したときに、<xref:System.Windows.Forms.Control>を格納している、<xref:System.Windows.Forms.Cursor.HotSpot%2A>適切なマウス イベントを発生させます。 現在のマウスの位置を取得することができます、<xref:System.Windows.Forms.MouseEventArgs.Location%2A>のプロパティ、<xref:System.Windows.Forms.MouseEventArgs>マウス イベントを処理するときに、またはを使用して、<xref:System.Windows.Forms.Cursor.Position%2A>のプロパティ、<xref:System.Windows.Forms.Cursor>クラスです。 その後マウスの位置情報を使用して、ヒット テストを実行し、マウスの位置に基づいてアクションを実行できます。 ヒット テストの機能に組み込まれている Windows フォームで複数のコントロールなど、 <xref:System.Windows.Forms.ListView>、 <xref:System.Windows.Forms.TreeView>、<xref:System.Windows.Forms.MonthCalendar>と<xref:System.Windows.Forms.DataGridView>コントロール。 適切なマウス イベントと共に使用<xref:System.Windows.Forms.Control.MouseHover>など、ヒット テストは、アプリケーションが特定のアクションを実行する場合を決定するために役立ちます。  
  
## <a name="mouse-events"></a>マウス イベント  
 マウス入力に応答する主な方法では、マウス イベントを処理します。 次の表は、マウス イベントの表示し、発生したときについて説明します。  
  
|マウス イベント|説明|  
|-----------------|-----------------|  
|<xref:System.Windows.Forms.Control.Click>|通常前に、マウス ボタンが離されると、このイベントが発生した、<xref:System.Windows.Forms.Control.MouseUp>イベント。 このイベントのハンドラーは、型 <xref:System.EventArgs> の引数を受け取ります。 のみクリックが発生する場合を判断する必要がある場合は、このイベントを処理します。|  
|<xref:System.Windows.Forms.Control.MouseClick>|このイベントは、ユーザーがマウスでコントロールをクリックしたときに発生します。 このイベントのハンドラーは、型 <xref:System.Windows.Forms.MouseEventArgs> の引数を受け取ります。 クリックが発生したときに、マウスに関する情報を取得する必要がある場合は、このイベントを処理します。|  
|<xref:System.Windows.Forms.Control.DoubleClick>|このイベントは、コントロールがダブルクリックされたときに発生します。 このイベントのハンドラーは、型 <xref:System.EventArgs> の引数を受け取ります。 のみ、ダブルクリックが発生した場合を決定する必要がある場合は、このイベントを処理します。|  
|<xref:System.Windows.Forms.Control.MouseDoubleClick>|このイベントは、ユーザーがマウスでコントロールをダブルクリックしたときに発生します。 このイベントのハンドラーは、型 <xref:System.Windows.Forms.MouseEventArgs> の引数を受け取ります。 ダブルクリックの発生時に、マウスに関する情報を取得する必要がある場合は、このイベントを処理します。|  
|<xref:System.Windows.Forms.Control.MouseDown>|このイベントは、マウス ポインターがコントロール上と、ユーザーがマウス ボタンを押したときに発生します。 このイベントのハンドラーは、型 <xref:System.Windows.Forms.MouseEventArgs> の引数を受け取ります。|  
|<xref:System.Windows.Forms.Control.MouseEnter>|このイベントは、マウス ポインターがコントロールの種類に応じて、コントロールの境界またはクライアントの領域に入ったときに発生します。 このイベントのハンドラーは、型 <xref:System.EventArgs> の引数を受け取ります。|  
|<xref:System.Windows.Forms.Control.MouseHover>|このイベントは、マウス ポインターが停止し、コントロールの上に置いたときに発生します。 このイベントのハンドラーは、型 <xref:System.EventArgs> の引数を受け取ります。|  
|<xref:System.Windows.Forms.Control.MouseLeave>|このイベントは、マウス ポインターがコントロールの種類に応じて、コントロールの境界またはクライアントの領域を離れると発生します。 このイベントのハンドラーは、型 <xref:System.EventArgs> の引数を受け取ります。|  
|<xref:System.Windows.Forms.Control.MouseMove>|このイベントは、マウス ポインターがコントロール上での移動したときに発生します。 このイベントのハンドラーは、型 <xref:System.Windows.Forms.MouseEventArgs> の引数を受け取ります。|  
|<xref:System.Windows.Forms.Control.MouseUp>|このイベントは、マウス ポインターがコントロール上と、ユーザーがマウス ボタンを離したときに発生します。 このイベントのハンドラーは、型 <xref:System.Windows.Forms.MouseEventArgs> の引数を受け取ります。|  
|<xref:System.Windows.Forms.Control.MouseWheel>|このイベントは、コントロールにフォーカスがあるときに、ユーザーがマウスのホイールを回転させるときに発生します。 このイベントのハンドラーは、型 <xref:System.Windows.Forms.MouseEventArgs> の引数を受け取ります。 使用することができます、<xref:System.Windows.Forms.MouseEventArgs.Delta%2A>プロパティの<xref:System.Windows.Forms.MouseEventArgs>をマウスのスクロールがどの程度を判断します。|  
  
## <a name="changing-mouse-input-and-detecting-system-settings"></a>マウス入力を変更して、システム設定の検出  
 検出し、コントロールがコントロールから派生させを使用してマウス入力を処理する方法を変更することができます、<xref:System.Windows.Forms.Control.GetStyle%2A>と<xref:System.Windows.Forms.Control.SetStyle%2A>メソッドです。 <xref:System.Windows.Forms.Control.SetStyle%2A>メソッドにはビットごとの組み合わせ<xref:System.Windows.Forms.ControlStyles>コントロールがクリックしてまたはダブルクリック動作の標準を持つかどうか、またはコントロールがマウス処理を処理するかどうかを決定する値。 さらに、<xref:System.Windows.Forms.SystemInformation>クラスには、マウスの機能を説明し、マウスがオペレーティング システムと対話する方法を指定するプロパティが含まれています。 次の表は、これらのプロパティをまとめたものです。  
  
|プロパティ|説明|  
|--------------|-----------------|  
|<xref:System.Windows.Forms.SystemInformation.DoubleClickSize%2A>|取得します (ピクセル単位)、ユーザーが、2 つの考慮すべきオペレーティング システムに対して 2 回クリックする必要があります、領域のクリックして、ダブルクリックします。|  
|<xref:System.Windows.Forms.SystemInformation.DoubleClickTime%2A>|最初のクリックと 2 番目のクリック、ダブルクリック マウス操作を検討するオペレーティング システムの間の経過時間をミリ秒単位の最大数を取得します。|  
|<xref:System.Windows.Forms.SystemInformation.MouseButtons%2A>|マウスのボタンの数を取得します。|  
|<xref:System.Windows.Forms.SystemInformation.MouseButtonsSwapped%2A>|左右のマウス ボタンの機能が入れ替わっているかどうかを示す値を取得します。|  
|<xref:System.Windows.Forms.SystemInformation.MouseHoverSize%2A>|マウス静止メッセージが生成されるためにマウス静止時間が経過するまでマウス ポインターをとどめておく必要がある四角形の領域のサイズ (ピクセル単位) を取得します。|  
|<xref:System.Windows.Forms.SystemInformation.MouseHoverTime%2A>|マウス静止メッセージが生成されるために静止領域内にマウス ポインターをとどめておく必要がある時間 (ミリ秒単位) を取得します。|  
|<xref:System.Windows.Forms.SystemInformation.MousePresent%2A>|マウスがインストールされているかどうかを示す値を取得します。|  
|<xref:System.Windows.Forms.SystemInformation.MouseSpeed%2A>|現在のマウス速度、1 ~ 20 を示す値を取得します。|  
|<xref:System.Windows.Forms.SystemInformation.MouseWheelPresent%2A>|マウス ホイール付きのマウスが取り付けられているかどうかを示す値を取得します。|  
|<xref:System.Windows.Forms.SystemInformation.MouseWheelScrollDelta%2A>|1 回のマウス ホイールの回転の増分の差分値を取得します。|  
|<xref:System.Windows.Forms.SystemInformation.MouseWheelScrollLines%2A>|マウス ホイールを回転したときにスクロールする行数を取得します。|  
  
## <a name="see-also"></a>関連項目  
 [Windows フォーム アプリケーションにおけるマウス入力](../../../docs/framework/winforms/mouse-input-in-a-windows-forms-application.md)  
 [Windows フォームにおけるマウスのキャプチャ](../../../docs/framework/winforms/mouse-capture-in-windows-forms.md)  
 [Windows フォームにおけるマウス ポインター](../../../docs/framework/winforms/mouse-pointers-in-windows-forms.md)
